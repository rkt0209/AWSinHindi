# 3️⃣ Lambda Ko Test Karo + Logs (Diary) Padho ▶️

> Function ban gaya. Ab **khud button daba ke** chala ke dekho ki chal raha hai ya nahi.
> Aur uske baad uski **diary (CloudWatch Logs)** padhna seekho — ye zindagi bhar kaam aayega. 📓

📖 Lambda test karna: https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html
📖 CloudWatch Logs: https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html

---

## 📦 Ye Kya Hai: **Test Event**

**Definition:** Test Event = ek **nakli parchi (event)** jo tum khud banate ho, taaki Lambda ko **bina asli trigger** ke chala ke dekh sako. Yani "doorbell nahi baji, par tumne khud jaake naukar ko bola — chal ke dikha."

**Example:** Naya mobile khareeda to pehle khud ek **test call** karte ho na — "hello sun raha hai?" Ye asli caller nahi, bas check karne ke liye. Test Event waisa hi hai.

---

## 🪜 PART A — Lambda Chala Ke Dekho (Test)

### Step 1 — Test Tab Kholo
- Apne function ke page pe **"Test"** tab (ya orange **"Test"** button ke paas dropdown) pe click.

**🖥️ Screen pe:** "Configure test event" jaisa box khulega.

### Step 2 — Test Event Banao
- **Event name**: `mera-test` daalo.
- Neeche JSON box me pehle se `{ "key1": "value1", ... }` jaisa kuch hoga — **rehne do** (abhi hume iski parwaah nahi).
- Neeche **"Save"** dabao.

### Step 3 — Test Chalao
- Ab orange **"Test"** button dabao.

**🖥️ Screen pe (thodi der baad):**
- Upar green box: **"Executing function: succeeded"** ✅
- **"Execution results"** section me:
  - **Response:** `{"statusCode": 200, "body": "\"Namaste Intern, tumhara Lambda chal gaya!\""}`
  - **Function Logs:** yaha wo `print(...)` wali lines dikhengi:
    ```
    Naukar jaag gaya! Kaam shuru.
    Namaste Intern, tumhara Lambda chal gaya!
    ```
  - Saath me **Duration** (kitne millisecond me chala) aur **memory used**.

> 🎉 **Ho gaya!** Tumne apna code cloud pe chala liya. Wo `print` wali lines "Function Logs" me isliye dikhi kyunki wo diary me likhi gayi.

---

## 📦 Ye Kya Hai: **Log Group / Log Stream** (Diary Ka Structure)

**Definition:**
- **Log Group** = ek **poori diary/register** — ek Lambda ke saare logs ek group me. Naam hota hai `/aws/lambda/mera-pehla-lambda`.
- **Log Stream** = us diary ke **andar ka ek page** — har baar jab Lambda alag session me chalta hai, ek naya stream/page ban sakta hai.

**Example:** Ek **class ka attendance register** (Log Group), aur usme har **din ka page** (Log Stream). Poore saal ka ek register, par roz ka alag page.

---

## 🪜 PART B — CloudWatch Logs Me Diary Padho

Test wale logs to wahi dikh gaye. Par asli/purane logs CloudWatch me milte hain:

### Step 1 — Monitor Tab
- Function page pe **"Monitor"** tab pe click → **"View CloudWatch logs"** (ya "Logs" button) dabao.

**🖥️ Screen pe:** naye tab me **CloudWatch** khulega, seedha tumhare function ke **Log Group** (`/aws/lambda/mera-pehla-lambda`) pe.

### Step 2 — Log Stream Kholo
- Neeche **Log streams** ki list dikhegi (time ke hisaab se).
- Sabse upar wale (latest) pe click karo.

**🖥️ Screen pe:** wo saari lines jo Lambda ne chalte waqt likhi — `print` wali baatein, START/END/REPORT lines (ye AWS khud likhta hai — kab shuru, kab khatam, kitna time/memory laga).

> 💡 **START / END / REPORT** — ye AWS ki apni lines hain: kab chala, kab ruka, kitna time+memory laga. Tumhari `print` lines inke beech me hoti hain.

---

## 🧪 Chhoti Practice

1. Code me ek nayi line `print("Practice line 123")` daalo → **Deploy** → **Test** → dekho ye line logs me aayi.
2. Code me `naam = "Intern"` ko badal ke apna naam daalo → Deploy → Test → response me apna naam dekho.

Itna ho gaya to Lambda ka basic "chalana + logs dekhna" **pakka**. 💪

---

## ⚠️ Common Cases / Errors

| Case (logs me dikhe) | Matlab / Solution |
|------|-------------------|
| **"succeeded" + green** | Sab sahi chala. ✅ |
| **"errored" / laal** | Code me galti. Logs me neeche error line padho (jaise `NameError`, `KeyError`). |
| **`KeyError: 'something'`** | Code `event` me se koi cheez maang raha jo test parchi me nahi. Abhi ignore, File 4 me sahi event aayega. |
| **`Task timed out after 3.00 seconds`** | Code 3 sec se zyada le raha. Timeout badhao (File 5 me). Abhi chhote code me nahi aayega. |
| **Logs khaali / purane** | Refresh (🔄) dabao; sahi (latest) log stream chuno. |
| **"View logs" pe Access Denied** | IAM user ko CloudWatch Logs padhne ki permission chahiye (File 6 dekho). |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Test event bana ke Lambda chalaya (succeeded dikha)
- [ ] Response aur Function Logs dekhe
- [ ] CloudWatch me jaake Log Group/Stream me diary padhi
- [ ] `print` wali lines logs me dikhi
- [ ] Samajh gaye: START/END/REPORT AWS ki apni lines hain

> ➡️ Ab asli maza — S3 me file aate hi Lambda **khud** chale → [`04-s3-trigger-lambda.md`](./04-s3-trigger-lambda.md) ⭐
