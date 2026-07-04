# 5️⃣ Behind The Scenes — Role, Timeout, Memory, Env Variables ⚙️

> Lambda chal to gaya. Ab thoda "andar jhaank ke" samjho — ye interview me poochha jata hai
> aur real kaam me har roz kaam aata hai. Sirf **samajhna** hai, ratna nahi. 🧠

📖 Execution role: https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html
📖 Configuration (memory/timeout): https://docs.aws.amazon.com/lambda/latest/dg/configuration-function-common.html
📖 Environment variables: https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html

---

## 📦 Ye Kya Hai: **Execution Role** (Lambda Ki Wardi — Detail Me)

**Definition:** Execution Role = wo **IAM Role (wardi)** jo Lambda **chalte waqt pehenta hai**, jisme likha hota hai "**ye Lambda kin-kin AWS cheezon ko chhoo sakta hai**" — jaise logs likhna, S3 padhna, etc.

**Yaad karo (File 1 box):** Role = machine ki wardi (User = insaan ki ID). Execution role bas "wo wardi jo **Lambda** chalte waqt pehenta hai."

**Kaha dekho:**
- Function → **"Configuration"** tab → **"Permissions"** → **"Execution role"** ke neeche role ka naam (jaise `mera-pehla-lambda-role-xxxx`) dikhega.
- Us role pe click karoge to IAM khulega, jisme **policies (permission ke kaagaz)** dikhengi.

**Isme by default kya hota hai?**
- **"AWSLambdaBasicExecutionRole"** naam ki policy — iska matlab: "**logs (CloudWatch) likhne** ki permission." Isliye tumhare `print` diary me likhe gaye. ✅

**Kab badalna padta hai?**
- Agar Lambda ko **S3 se file ka content padhna** ho, ya kahin **likhna** ho, to us role me aur policy jodni padti hai (jaise `AmazonS3ReadOnlyAccess`).
- Abhi hum sirf **naam** padh rahe hain (content nahi), isliye zaroorat nahi. Din 4 (Glue) tak ye samajh kaam aayegi.

> 💡 **Ek line:** Execution role = "Lambda ki chaabi-guchcha (keychain)" — jitni chaabiyaan, utne darwaze khol sakta hai.

---

## 📦 Ye Kya Hai: **Timeout**

**Definition:** Timeout = "Lambda ko **kitna zyada se zyada time** milega ek baar me kaam karne ka." Utne second me kaam na hua to AWS use **zabardasti rok** deta hai (taaki bekaar paisa/time na lage).

**Default:** 3 second. **Max:** 15 minute.

**Example:** Exam me time limit — ghanti bajte hi pen neeche, chahe answer adha ho. Timeout waisa hi hai.

**Kaha badlo:** Configuration → **"General configuration"** → **Edit** → **Timeout** badhao (jaise 10 sec ya 1 min bade kaam ke liye).

> ⚠️ Agar logs me `Task timed out after 3.00 seconds` dikhe → timeout badha do.

---

## 📦 Ye Kya Hai: **Memory (aur usse juda CPU)**

**Definition:** Memory = "Lambda ko chalte waqt **kitni RAM (dimaag ki jagah)** milegi." Zyada memory = zyada tezi (CPU bhi memory ke saath badhta hai) = thoda zyada paisa.

**Default:** 128 MB. Badha sakte ho 10240 MB (10 GB) tak.

**Example:** chhoti mez pe kaam karo vs badi mez — badi mez pe zyada saamaan phaila ke tez kaam. Memory waisa hi.

**Kaha:** Configuration → General configuration → Edit → **Memory**.

> 💡 Beginner: default (128 MB) theek hai. Bade data pe hi badhane ki zaroorat.

---

## 📦 Ye Kya Hai: **Environment Variables**

**Definition:** Environment Variables = "**bahar likhe hue setting/values**" jo tumhare code ke andar hard-code kiye bina, code use kar sakta hai. Jaise koi naam, koi bucket ka naam, koi "on/off" setting — code se **alag** rakhna.

**Kyun?** Taaki setting badalni ho to **code chheده bina** bas value badal do. Aur secret cheezein code me dikhti nahi.

**Example:** TV ka **remote** 📺 — TV (code) andar fix hai, par volume/channel (settings) tum remote se bahar se badalte ho, TV khol ke nahi. Env variables wahi "bahar wale knobs" hain.

**Kaise banao:**
1. Configuration → **"Environment variables"** → **Edit** → **Add environment variable**.
2. **Key**: `INTERN_NAAM`, **Value**: `Rohit` → Save.
3. Code me aise use karo:
   ```python
   import os
   naam = os.environ['INTERN_NAAM']   # bahar wali value andar aa gayi
   print(f"Namaste {naam}")
   ```

> 💡 Value badalni ho to sirf console me badlo — code same rahega. Yahi iska faayda.

---

## 📦 Ye Kya Hai: **Cold Start** (Bas Jaan Lo)

**Definition:** Cold Start = jab Lambda **bahut der se soya hua tha** aur pehli baar jaagta hai, to use **thoda extra time** lagta hai (machine "garam" karne me). Baar-baar chalne pe ye time nahi lagta ("warm").

**Example:** Bike subah pehli baar start karo to thoda time/choke lagta hai (cold). Din bhar chalti rahe to turant start (warm). Cold start waisa hi.

> 💡 Interview me poochh sakte hain. Beginner ko bas itna: "pehli baar thoda slow, phir fast." Chhote apps me farak nahi padta.

---

## 🧠 Interview Ke Liye 5 One-Liner

1. **Execution role** = "Lambda ki wardi/keychain — kin cheezon ko chhoo sakta hai."
2. **Timeout** = "max kitna time chalega, warna zabardasti band."
3. **Memory** = "kitni RAM/CPU — zyada = tez = thoda mehnga."
4. **Env variables** = "code se bahar rakhi settings (remote ke knobs)."
5. **Cold start** = "pehli baar jaagne me thoda extra time."

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Execution role kaha dikhta hai — pata hai (Configuration → Permissions)
- [ ] Timeout/Memory kaha badalte hain — pata hai
- [ ] Ek environment variable bana ke code me use karke dekha (optional)
- [ ] Cold start ka matlab pata hai
- [ ] Samajh gaye: role me policy jodo to Lambda naye kaam kar sakta hai

> ➡️ Ab final: checklist + saare errors + doc links → [`06-checklist-aur-galtiyan.md`](./06-checklist-aur-galtiyan.md) 🧾
