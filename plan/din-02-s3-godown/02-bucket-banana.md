# 2️⃣ Apna Pehla Bucket Banao — Step By Step

> Ek-ek click, saath me "screen pe kya dikhega". Bilkul isi order me karo.

📖 Create bucket docs: https://docs.aws.amazon.com/AmazonS3/latest/userguide/create-bucket-overview.html
📖 Bucket naming rules: https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucketnamingrules.html

---

## 🪜 STEP 1 — S3 Kholo

- Pehle check: IAM user se login ho, Region **Mumbai** ho (top-right).
- Upar 🔍 search me `S3` type karo → **S3** pe click.

**🖥️ Screen pe:** "Amazon S3" page khulega. Left menu me **"Buckets"**, aur beech me tumhare buckets ki list (abhi khaali hogi). Right upar ek orange **"Create bucket"** button.

> ℹ️ **Dhyaan do:** S3 ki bucket list **saare Region ki ek saath** dikhti hai (S3 ka console aisa hai). Par bucket khud ek Region me banta hai — hum Mumbai chunenge.

---

## 🪜 STEP 2 — "Create Bucket" Dabao

- Right upar **"Create bucket"** button dabao.

**🖥️ Screen pe:** "Create bucket" ka form khulega — ismein settings bharni hain (neeche ek-ek batayi hain).

---

## 🪜 STEP 3 — Bucket Ka Naam + Region

### Bucket name (sabse zaroori):
- Ek **unique naam** daalo. **Naming rules yaad rakho:**
  - Sirf **chhote (lowercase)** letters, numbers, aur hyphen `-`.
  - **3 se 63** character.
  - Space nahi, underscore `_` nahi, capital letter nahi.
  - Poori duniya me unique — isliye apna kuch daalo.
- **Accha naam example:** `rohit-sales-data-2026`
- **Galat naam:** `Sales_Data` ❌ (capital + underscore), `my bucket` ❌ (space)

### Region:
- **"AWS Region"** me **Asia Pacific (Mumbai) ap-south-1** chuno.

**🖥️ Agar naam already liya hua hai:** Neeche laal error aayega — *"Bucket with this name already exists"*. To naam me kuch aur jodo (jaise date/number) aur dobara try karo.

---

## 🪜 STEP 4 — Object Ownership (Default Rehne Do)

- **"Object Ownership"** section: **"ACLs disabled"** hi rehne do (ye default aur recommended hai).

> 💡 Iska matlab: bucket ka control tumhare (owner ke) paas rahega, purana ACL wala jhanjhat nahi. Beginner ke liye default best.

---

## 🪜 STEP 5 — Block Public Access (BAHUT ZAROORI — Default Rehne Do)

- **"Block Public Access settings for this bucket"** section me **saare 4 checkbox TICK (ON) rehne do** — matlab "Block all public access" ON.

**Kyun?** Ye tumhari files ko **internet se chhupa ke** rakhta hai (private). Agar ye off kar diya to galti se poori duniya tumhari files dekh legi. **Abhi ON hi rakho.** (Public kaise karte hain, wo File 4 me — soch-samajh ke.)

**🖥️ Screen pe:** Ek warning dikh sakti hai "you are turning off block public access" — tab jab tum galti se off karo. Abhi tick rehne do, koi warning nahi aayegi.

---

## 🪜 STEP 6 — Versioning + Encryption (Default Theek Hai)

- **Bucket Versioning:** abhi **"Disable"** rehne do (File 5 me samjhenge).
- **Default encryption:** **"SSE-S3"** (Amazon-managed) default on rehta hai — rehne do. Iska matlab files apne-aap "tale me band (encrypted)" rehti hain. ✅

---

## 🪜 STEP 7 — Bucket Banao

- Sabse neeche **"Create bucket"** dabao.

**🖥️ Screen pe:** Upar green message *"Successfully created bucket 'rohit-sales-data-2026'"* ✅ — aur bucket list me tumhara bucket dikhne lagega.

---

## 🎉 Ho Gaya! Ab Bucket Kholo

- Bucket list me apne bucket ke **naam pe click** karo.

**🖥️ Screen pe:** Bucket ke andar aa gaye — abhi khaali hai ("This bucket is empty"). Upar tabs dikhenge: **Objects, Properties, Permissions, Metrics, Management...**. Ek **"Upload"** button bhi dikhega (agli file me use karenge).

---

## ⚠️ Common Cases / Errors

| Case | Solution |
|------|----------|
| **"Bucket name already exists"** | Naam duniya me kisi ne le liya. Kuch alag jodo (date, apna naam). |
| **"Invalid bucket name"** | Capital letter / underscore / space hata do. Sirf lowercase + number + hyphen. |
| **"Access Denied" bucket banane pe** | IAM user me S3 permission nahi. Din 1 wali `AmazonS3FullAccess` policy check karo. |
| **Bucket galat Region me ban gaya** | Delete karke Mumbai me dobara banao (bucket ka Region baad me badal nahi sakte). |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Bucket ban gaya (unique naam, Mumbai region)
- [ ] Block Public Access ON hai (private, safe)
- [ ] Bucket khol ke dekha (khaali dikh raha hai)

> ➡️ Ab File 3: file upload/download/delete karo → [`03-file-upload-download-delete.md`](./03-file-upload-download-delete.md)
