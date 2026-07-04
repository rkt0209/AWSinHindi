# 4️⃣ ⭐ Asli Maza — S3 Me File Aate Hi Lambda Khud Chale (Trigger)

> Ab tak tumne **khud button daba ke** Lambda chalaya. Aaj wo automatic karenge:
> **jaise hi S3 (Din 2 wala godown) me file aati hai, Lambda apne-aap jaag ke chal jaye.** 🪄
> Yahi cheez real companies me sabse zyada use hoti hai.

📖 S3 se Lambda trigger (official tutorial): https://docs.aws.amazon.com/lambda/latest/dg/with-s3-example.html
📖 Trigger add karna: https://docs.aws.amazon.com/lambda/latest/dg/invocation-eventsourcemapping.html

---

## 🔔 Yaad Karo (File 1 Se)

- **Trigger** = doorbell 🔔 — wo cheez jo Lambda ko bolti hai "chal ja".
- **Event** = parchi 📄 — "kaunsi file, kaha aayi".
- Aaj **S3 ko doorbell** banayenge: S3 me file aayi → S3 ne Lambda ki bell bajayi → Lambda chala → parchi me file ka naam mila.

```
File upload → S3 → (bell baji) → Lambda jaaga → parchi padhi → kaam kiya → logs
```

---

## 🪜 STEP 1 — Pehle Code Ko "File Ka Naam" Padhne Layak Banao

Ab Lambda ke paas asli **event (parchi)** aayega jisme file ki jaankari hogi. Code badlo taaki wo parchi padh ke file ka naam nikaale:

- Apne function → **Code source** editor me ye daalo → **Deploy**:

```python
import json

def lambda_handler(event, context):
    print("Naukar jaag gaya! S3 me kuch aaya.")

    # parchi (event) me se bucket aur file ka naam nikaalo
    record = event['Records'][0]
    bucket = record['s3']['bucket']['name']
    file_key = record['s3']['object']['key']

    print(f"Bucket: {bucket}")
    print(f"Aayi hui file: {file_key}")

    return {
        'statusCode': 200,
        'body': json.dumps(f"{file_key} process ho gayi!")
    }
```

**Samajh (aasaan):**
- `event['Records'][0]` → parchi me ek list hoti hai; uska pehla item lo.
- `...['bucket']['name']` → us item me se **bucket ka naam**.
- `...['object']['key']` → us item me se **file ka key** (poora address, jaise `raw-data/sales.csv`).
- Phir bas `print` karke diary me likh do.

> ⚠️ **Deploy dabana mat bhoolna** — warna purana code chalega.

---

## 🪜 STEP 2 — Trigger Add Karo (S3 Ko Doorbell Banao)

### Step 2.1 — Add Trigger
- Function page pe upar **"Function overview"** diagram me **"+ Add trigger"** button dabao.
  (Ya thoda scroll — "Add trigger" box left me dikhta hai.)

**🖥️ Screen pe:** "Add trigger" page — ek dropdown "Select a source".

### Step 2.2 — S3 Chuno
- Dropdown me `S3` search karke **S3** chuno.

**🖥️ Screen pe:** neeche naye field aa jayenge:

| Field | Kya Daalo | Samajh |
|-------|-----------|--------|
| **Bucket** | Apna Din 2 wala bucket chuno | Wahi godown |
| **Event types** | **"All object create events"** (`s3:ObjectCreated:*`) | "Jab bhi koi file aaye/upload ho" |
| **Prefix** (optional) | `raw-data/` | Sirf is folder me file aaye tabhi (warna poore bucket pe) |
| **Suffix** (optional) | `.csv` | Sirf `.csv` file pe (chaho to khaali chhod do) |

> 📦 **Prefix/Suffix kya hai?** Ye "**chhanni (filter)**" hai — "sirf `raw-data/` folder ki `.csv` file pe hi Lambda chalao, baaki pe nahi." Jaise chowkidar ko bolna "sirf blue gate se aane walon ki bell bajao."

### Step 2.3 — Recursion Warning Tick
- Neeche ek checkbox: **"I acknowledge that using the same S3 bucket for input and output..."** — ise **tick** karo.

> ⚠️ **Ye warning kyun?** Agar Lambda apne output ko **wapas usi bucket** me daale to wo phir se apne aap ko trigger kar sakta hai — infinite loop! (Naukar apni hi bell baja-baja ke pagal.) Hum abhi output wapas nahi daal rahe, isliye safe — bas tick karke aage badho.

### Step 2.4 — Add Dabao
- **"Add"** button dabao.

**🖥️ Screen pe:** wapas function page pe — ab diagram me **S3** ek trigger ke roop me juda dikhega. ✅

> 🪄 **Behind the scene:** AWS ne khud tumhare Lambda ke **role (wardi)** ko permission de di ki "S3 ise bell baja sakta hai." Isliye alag se kuch nahi karna pada.

---

## 🪜 STEP 3 — Test Karo (Asli Wala!) — File Upload Karke

Ab **koi test button nahi** — asli tareeke se:

1. **S3 console** kholo → apna bucket → `raw-data/` folder.
2. Din 2 wali `sales.csv` (ya koi bhi chhoti file) **upload** karo.
3. Bas! Upload hote hi Lambda **apne-aap** chal gaya hoga. 🎉

### Kaise Confirm Karein Ki Chala?
- Lambda console → apna function → **"Monitor"** tab → **"View CloudWatch logs"** → latest log stream.

**🖥️ Screen pe (logs me):**
```
Naukar jaag gaya! S3 me kuch aaya.
Bucket: tumhara-bucket-naam
Aayi hui file: raw-data/sales.csv
```

> 🎉🎉 **Ye lambda moment hai!** Tumne kuch button nahi dabaya — sirf file upload ki, aur Lambda **khud** jaag ke file ka naam padh gaya. Yahi automation ka asli jaadu hai.

---

## 🧪 Chhoti Practice

1. `raw-data/` me ek aur file (`test2.csv`) upload karo → logs me uska naam aana chahiye.
2. `clean-data/` folder me file daalo → Lambda **nahi** chalega (kyunki prefix `raw-data/` set kiya tha). Isse prefix-filter ka asar samajh aayega.

---

## ⚠️ Common Cases / Errors

| Case | Solution |
|------|----------|
| **File upload ki par log nahi aaya** | (a) Sahi folder (`raw-data/`) me daali? (b) Suffix `.csv` set hai to `.csv` hi daalo. (c) Latest log stream refresh karo. |
| **`KeyError: 'Records'`** | Lambda ko **test button** se chalaya (nakli parchi) jisme `Records` nahi. Asli test **file upload** se karo. |
| **Trigger add pe Access Denied** | IAM user ko Lambda + S3 config permission chahiye (File 6). |
| **Do baar chal gaya** | Ek hi file baar-baar upload/replace ki hogi — har create pe chalega. Normal. |
| **Infinite loop dar** | Sirf tab jab Lambda output **usi bucket/prefix** me daale. Hum nahi daal rahe — safe. |
| **Trigger delete karna hai** | Function → Configuration → Triggers → trigger select → Delete. |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Code ko event (parchi) padhne layak banaya + Deploy kiya
- [ ] S3 ko trigger (doorbell) banaya — bucket + event type + prefix
- [ ] File upload karke Lambda **apne-aap** chalaya
- [ ] Logs me bucket + file ka naam dikha 🎉
- [ ] Prefix filter ka asar samajh gaye (clean-data pe nahi chala)

> ➡️ Ab thoda behind-the-scenes: role, timeout, env variables → [`05-role-cloudwatch-env.md`](./05-role-cloudwatch-env.md) ⚙️
