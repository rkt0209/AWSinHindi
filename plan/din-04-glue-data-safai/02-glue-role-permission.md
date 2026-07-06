# 2️⃣ 🔑 Glue Ke Liye Role + Permissions (Do Layer)

> Glue me **do jagah** permission chahiye hoti hai — isliye log yahi atakte hain.
> Ek baar theek se set kar lo, phir aage sab smooth. Dono ko alag box me samjhaya hai. 💪

📖 Glue permissions setup: https://docs.aws.amazon.com/glue/latest/dg/set-up-iam.html
📖 Glue service role: https://docs.aws.amazon.com/glue/latest/dg/create-an-iam-role.html

---

## 🤔 Pehle Samjho — Do Layer Kyun?

Yaad karo Din 3 ka farak: **User = insaan (tum)**, **Role = machine/service ki wardi**.

Glue me dono chahiye:
1. **Tumhe (User `rohit-iam-dev`)** — Glue console **chalane** ki permission (button dabana, crawler/job banana).
2. **Glue service ko (Role)** — tumhari taraf se **S3 padhne/likhne** ki wardi (kyunki asli kaam Glue karega, tum nahi).

> **Aasaan example:** Tum (user) **restaurant ke malik** ho — order dene ka haq. Par khana **cook (Glue)** banata hai, aur cook ko **kitchen/store ki chaabi (Role)** chahiye. Dono ke bina kaam nahi.

---

## 🅰️ LAYER 1 — User (Tumhe) Ki Permission

Taaki tum Glue console use kar sako aur Glue ko role "de" (pass) sako.

**Root/admin se** (IAM → Users → `rohit-iam-dev` → Add permissions → Attach policies directly) ye attach karo:

| Policy | Kis Kaam Ke Liye |
|--------|------------------|
| **`AWSGlueConsoleFullAccess`** | Glue console chalана — crawler/job/table banana |
| **`IAMFullAccess`** (Din 3 me mil chuki) | Glue ko role **pass** karne ke liye (`iam:PassRole`) |
| **`AmazonS3FullAccess`** (Din 1 me mil chuki) | S3 me data dekhna/daalna |

> 📦 **Ye Kya Hai: `iam:PassRole`** — "kisi service (Glue) ko koi role **de dena/saunp dena**." Jab tum Glue job ko bolte ho "ye wali wardi (role) pehen ke kaam kar," to us "dene" ke liye ye permission chahiye. `IAMFullAccess` me ye already hoti hai. **Example:** malik cook ko store ki chaabi **thama** raha hai — chaabi thamane ka haq = PassRole.

---

## 🅱️ LAYER 2 — Glue Service Role Banao (Glue Ki Wardi)

Ye wo **wardi** hai jo **Glue khud pehen ke** S3 se data padhega aur likhega.

### 📦 Ye Kya Hai: **Glue Service Role**
**Definition:** ek **IAM Role** jo **Glue service** kaam ke waqt pehenta hai, jisme do permission hoti hain — (1) Glue ke apne kaam (`AWSGlueServiceRole`), (2) tumhare S3 bucket padhna/likhna. Bina iske Glue tumhare data ko chhoo bhi nahi sakta.

### Banane Ke Steps:

**Step 1 — IAM me Role banao**
- Search me `IAM` → left me **"Roles"** → **"Create role"**.

**Step 2 — Trusted entity (kaun pehnega)**
- **"Trusted entity type"** = **AWS service**.
- **"Use case"** me dropdown/search me **Glue** chuno → **Next**.

> 📦 **Trusted entity ka matlab:** "ye wardi **kaun** pehen sakta hai." Yaha hum bol rahe "sirf **Glue** ye pehne" — koi aur service nahi. (Security ke liye zaroori.)

**Step 3 — Policies (permissions) jodo**
- Search karke ye do tick karo:
  - **`AWSGlueServiceRole`** → Glue ke apne kaam
  - **`AmazonS3FullAccess`** → tumhare S3 data padhne/likhne (seekhne ke liye theek; real me sirf apne bucket tak simit karte hain)
- **Next**.

**Step 4 — Naam do aur banao**
- **Role name**: `glue-mera-role` (ya `AWSGlueServiceRole-mera`) → **Create role**.

**🖥️ Screen pe:** Roles list me `glue-mera-role` dikhne lagega. ✅

> 💡 Isi role ka naam aage Crawler aur Job banate waqt **chunna** hoga ("Glue, ye wardi pehen ke kaam kar").

---

## ⚠️ Common Cases / Errors

| Case | Solution |
|------|----------|
| **Glue console pe "not authorized"** | User ko `AWSGlueConsoleFullAccess` attach karo (Layer 1). |
| **Job/Crawler save pe `iam:PassRole` denied** | User ko `IAMFullAccess` (ya PassRole wali policy) do — Glue ko role dene ke liye. |
| **Use case me Glue nahi dikh raha** | Search box me `Glue` type karo; ya "Service or use case" dropdown me dhoondho. |
| **Role banate waqt S3 policy bhool gaye** | Role → Add permissions → `AmazonS3FullAccess` baad me bhi jod sakte ho. |
| **Job chalne pe "Access Denied (S3)"** | Glue **service role** me S3 permission missing — Layer 2 dobara check karo. |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Layer 1: user pe `AWSGlueConsoleFullAccess` + (IAMFullAccess, S3FullAccess pehle se)
- [ ] Layer 2: `glue-mera-role` ban gaya (Glue trusted + Glue policy + S3 access)
- [ ] `iam:PassRole` ka matlab samajh gaye (service ko role dena)
- [ ] Do-layer permission ka concept clear (user chalाता, role kaam karta)

> ➡️ Ab Crawler banao aur data ka schema Catalog me laao → [`03-crawler-aur-catalog.md`](./03-crawler-aur-catalog.md) 🕵️
