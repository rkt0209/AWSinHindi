# 6️⃣ Din 3 Final Checklist + Har Galti Ka Solution 🧾

> Sab tick ho gaya to Din 3 (Lambda) **pakka complete**. Neeche har common problem ka one-stop solution + saari nayi terms ek jagah.

---

## ✅ Din 3 Master Checklist

**Concept:**
- [ ] Lambda = "kaam aane pe apne-aap chalne wala code" (vending machine)
- [ ] Serverless = "server ka jhanjhat AWS ka"
- [ ] Trigger (doorbell) vs Event (parchi) ka farak clear
- [ ] IAM Role = machine ki wardi; User = insaan ki ID

**Function banana:**
- [ ] `mera-pehla-lambda` banaya (Python runtime)
- [ ] Apna code daal ke **Deploy** kiya
- [ ] Test event se chala ke "succeeded" dekha

**Logs:**
- [ ] Function Logs aur CloudWatch Logs (diary) padhi
- [ ] `print` wali lines logs me dikhi

**S3 Trigger (asli maza):**
- [ ] S3 ko trigger banaya (bucket + prefix `raw-data/`)
- [ ] File upload karke Lambda **apne-aap** chalaya
- [ ] Logs me file ka naam dikha

**Behind the scenes:**
- [ ] Execution role kaha hai — pata
- [ ] Timeout/Memory/Env variables ka idea

**Cleanup (bill se bacho):**
- [ ] S3 trigger + Lambda function + CloudWatch log group delete kiya
- [ ] Bucket/`raw-data/sales.csv`/IAM user NAHI delete kiya (aage kaam aayega)

---

## 🧠 Din 3 Ki 5 Sabse Badi Seekh (Zubaani Yaad Rakho)

1. **Lambda = automatic naukar — kaam aane pe jaage, warna soye (aur tabhi paisa).**
2. **Trigger = doorbell (chalne ka reason); Event = parchi (kya/kaha hua).**
3. **Role = machine ki wardi; User = insaan ki ID — dono alag.**
4. **`print` = diary (CloudWatch Logs); debugging ka main tareeka.**
5. **Deploy dabाना zaroori — warna purana code chalta hai.**

---

## 📦 Saari Nayi Terms — Ek Jagah (Revision Box)

| Term | Ek Line Definition | Example |
|------|--------------------|---------|
| **Lambda function** | Kaam aane pe chalne wala chhota code | Vending machine |
| **Serverless** | Server ka jhanjhat AWS ka, tumhara nahi | Ola (gaadi tumhari nahi) |
| **Runtime** | Code kaunsi bhasha (Python) me hai | "South-Indian chef chahiye" |
| **Handler** | Code ka main darwaza (yaha se shuru) | Building ka main gate |
| **Trigger** | Lambda ko chalane wali cheez | Doorbell 🔔 |
| **Event** | Chalte waqt milne wali parchi (data) | "Ravi aaya, front gate, 5 baje" |
| **IAM Role** | Machine/service ki wardi (login nahi) | Guard ki wardi |
| **Execution role** | Lambda chalte waqt jo role pehanta hai | Lambda ki keychain |
| **CloudWatch Logs** | Lambda ki diary/register | Hospital patient file |
| **Log Group / Stream** | Poori diary / uska ek din ka page | Attendance register / roz ka page |
| **Timeout** | Max kitna time chalega | Exam ki ghanti |
| **Memory** | Kitni RAM/CPU (tezi) | Chhoti vs badi mez |
| **Env variables** | Code se bahar rakhi settings | TV ka remote |
| **Cold start** | Pehli baar jaagne me extra time | Subah bike start |

---

## 🆘 Har Common Galti Ka Solution (One-Stop)

| Problem | Solution |
|---------|----------|
| **"Create function" pe Access Denied** | IAM user ko `AWSLambda_FullAccess` (admin se) lagwao. |
| **`iam:CreateRole` is not authorized** | Lambda ka role banane ki permission nahi. Root/admin se user pe `IAMFullAccess` + `AWSLambda_FullAccess` attach karo (File 2 ka "🔑 Permission Check" box). |
| **Code badla par asar nahi** | **Deploy** dabana bhool gaye. Deploy karo. |
| **Test pe `KeyError: 'Records'`** | Test button ki nakli parchi me `Records` nahi — asli test **file upload** se karo. |
| **`Task timed out after 3.00 sec`** | Timeout badhao (Configuration → General configuration). |
| **File upload ki par Lambda nahi chala** | Sahi folder (`raw-data/`)? Suffix `.csv` set hai to `.csv` daalo. Latest log stream refresh. |
| **Logs me kuch nahi** | Refresh (🔄); latest log stream chuno; Region Mumbai check. |
| **`AccessDenied` S3 padhne pe** | Lambda ke **role** me S3 read policy jodo (File 5). |
| **Galat Region me function** | Delete karke Mumbai me dobara, ya usi region me kaam. |
| **Do-do baar chal gaya** | File baar-baar upload/replace hui — har create pe chalta hai. Normal. |
| **Infinite loop dar** | Sirf tab jab output usi bucket/prefix me daalo. Hum nahi daal rahe — safe. |

---

## 🔑 Din 3 Me Kaunsi Permission Chahiye (One-Stop)

> Din 1 wale IAM user ke paas sirf **S3** permission thi. Din 3 (Lambda) ke liye ye chahiye — root/admin se user pe attach karo (IAM → Users → `rohit-iam-dev` → Add permissions → Attach policies directly):

| Policy | Kis Kaam Ke Liye | Kis Error Se Pata Chalta Hai |
|--------|------------------|------------------------------|
| **`AWSLambda_FullAccess`** | Lambda function banana/chalana | "Create function" pe Access Denied |
| **`IAMFullAccess`** | Lambda ka role (wardi) banana | `iam:CreateRole is not authorized` |
| **`AmazonS3FullAccess`** (Din 1 me mil chuki) | S3 trigger + file upload | S3 pe Access Denied |

> 💡 Aage jab Lambda ko S3 ka **content padhna** ho (Din 4), tab Lambda ke **role** me `AmazonS3ReadOnlyAccess` bhi jodenge (File 5).

---

## 📚 Din 3 Ke Saare Documentation Links (Ek Jagah)

- Lambda kya hai → https://docs.aws.amazon.com/lambda/latest/dg/welcome.html
- Getting started → https://docs.aws.amazon.com/lambda/latest/dg/getting-started.html
- Function banana (console) → https://docs.aws.amazon.com/lambda/latest/dg/getting-started.html#getting-started-create-function
- Test karna → https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html
- CloudWatch logs → https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html
- S3 trigger tutorial → https://docs.aws.amazon.com/lambda/latest/dg/with-s3-example.html
- Execution role → https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html
- Configuration (memory/timeout) → https://docs.aws.amazon.com/lambda/latest/dg/configuration-function-common.html
- Environment variables → https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html
- Python me Lambda → https://docs.aws.amazon.com/lambda/latest/dg/lambda-python.html

---

## 🧹 Din Ke End Me Cleanup (Bill Se Bacho)

> ⚠️ **Zaroori aadat:** Cloud me jo bhi banaya, use ke baad **delete** kar do. Free Tier me abhi kharcha **na ke barabar** hai, par (a) aadat achhi banti hai, aur (b) kuch cheezein chhup ke thoda-thoda charge karti rehti hain (jaise CloudWatch logs, S3 versions). Isliye aaj ka kaam ho jaye to ye **order me** delete karo:

### 1️⃣ Sabse Pehle — S3 Trigger Hatao
> Warna jab bhi bucket me file aayegi, Lambda chalta rahega (bekaar).
- Lambda → apna function → **Configuration** tab → **Triggers** → S3 trigger select → **Delete**.

### 2️⃣ Lambda Function Delete Karo
- Lambda console → **Functions** → `mera-pehla-lambda` select → **Actions** → **Delete** → confirm me `delete` likho → Delete.

### 3️⃣ CloudWatch Log Group Delete Karo (Chhupa Hua Kharcha!)
> Logs (diary) delete na karo to storage ka thoda-thoda charge chalta rehta hai.
- Search me `CloudWatch` → **Log groups** → `/aws/lambda/mera-pehla-lambda` select → **Actions** → **Delete log group(s)**.

### 4️⃣ (Optional) IAM Role Delete Karo
> Role (wardi) ka **koi charge nahi**, par safai ke liye:
- Search me `IAM` → **Roles** → `mera-pehla-lambda-role-xxxx` dhoondho → select → **Delete**.

### 5️⃣ S3 Ke Extra Test Files/Versions
- Jo test files (`test2.csv` etc.) practice me daali, unhe delete karo. Versioning ON kiya tha to purane **versions** bhi delete karo (warna jagah/charge count hoti hai).

---

### ✋ Ye MAT Delete Karo (Aage Kaam Aayega)
- **Apna S3 bucket** aur usme `raw-data/sales.csv` — **Din 4 (Glue)** me isi ka use hoga.
- **IAM user `rohit-iam-dev`** aur uski permissions — ye roz login ke liye chahiye.

> 💡 **Ek line:** "Jo aaj sirf practice ke liye banaya (Lambda, trigger, logs) — wo delete. Jo aage kaam aayega (bucket, data, user) — wo rakho."

> 🧾 **Confirm:** Delete karne ke 1-2 din baad **Billing → Free Tier** aur **Cost Explorer** (Din 1 wala) me check kar lena ki koi unexpected charge to nahi.

---

## 🎉 Din 3 Complete!

Agar upar sab ✅ hai, to **shabaash!** 💪 Ab tumhare paas:
- Ek **godown (S3)** hai jaha data rakhte ho (Din 2), aur
- Ek **automatic naukar (Lambda)** hai jo file aate hi **khud kaam** karta hai (Din 3).

Dimaag me picture:
> "File S3 me aayi → doorbell baji → Lambda jaaga → parchi padhi → kaam kiya → diary me likha."

**Kal:** Din 4 — **Glue (data saaf karne wala)** 🧽. Aaj wale `raw-data/sales.csv` ko uthayenge, saaf karenge, aur `clean-data/` me daalenge. Aaj wali `raw-data/` `clean-data/` mehnat wahin kaam aayegi!

> Aaram karo, kal milte hain! 😴➡️🚀
