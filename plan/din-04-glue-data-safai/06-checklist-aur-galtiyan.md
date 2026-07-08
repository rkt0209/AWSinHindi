# 6️⃣ Din 4 Final Checklist + Errors + Permissions + Cleanup 🧾

> Sab tick ho gaya to Din 4 (Glue) **pakka complete**. Neeche one-stop sab kuch.
> ⚠️ Glue paisa leta hai — **cleanup section (neeche) zaroor karo.**

---

## ✅ Din 4 Master Checklist

**Concept:**
- [ ] Glue = automatic kitchen (raw → clean)
- [ ] ETL = Extract + Transform + Load
- [ ] Data Catalog = data ka register; Table = schema (data nahi)
- [ ] Crawler = khud schema banane wala helper; Job = asli safai
- [ ] DPU = power/mehnat ka naap (isi se paisa)

**Permissions:**
- [ ] User (Layer 1): `AWSGlueConsoleFullAccess` + IAMFullAccess + S3FullAccess
- [ ] Glue role (Layer 2): `glue-mera-role` (Glue + S3 access)

**Hands-on:**
- [ ] Database `mera_data_db` bana
- [ ] Crawler chalaya → table + schema bani
- [ ] Visual ETL job (source → transform → target `clean-data/`)
- [ ] Job run → Succeeded → `clean-data/` me output aaya

**Cleanup:**
- [ ] Crawler/Job/Database/Table delete kiye (bill se bacho)
- [ ] Bucket/data/user NAHI delete kiya

---

## 🧠 Din 4 Ki 5 Sabse Badi Seekh

1. **Glue = serverless ETL kitchen: uthao (E) → saaf karo (T) → rakho (L).**
2. **Crawler sirf DEKHता hai (schema banata); Job asli KAAM karता hai (safai).**
3. **Data Catalog me sirf naksha (metadata) hota hai — asli data S3 me.**
4. **Do-layer permission: User console chalाता, Glue Role S3 chhoota.**
5. **Glue paisa leta hai (DPU-time) — chhoti file + turant cleanup.**

---

## 📦 Saari Nayi Terms — Ek Jagah (Revision)

| Term | Ek Line | Example |
|------|---------|---------|
| **ETL** | Extract-Transform-Load | Kapde: uthao-dho-almari |
| **Data Catalog** | Data ka register (metadata) | Library catalog |
| **Database (Glue)** | Catalog me tables ka group | Naam ka dabba |
| **Table (Glue)** | Data ka schema/naksha | Ghar ka blueprint |
| **Schema** | Column ka dhaancha (naam+type) | order_id:number, city:text |
| **Crawler** | Khud ghoom ke schema banata | Store manager ginti |
| **ETL Job** | Asli data safai (code/visual) | Cook |
| **Glue Studio** | Drag-drop job editor | Video-edit app |
| **Transform node** | Beech me data badalne wala step | Sabzi kaatna |
| **DPU** | Power/mehnat ka naap (paisa) | Kitne cook × time |
| **CSV** | Simple text, comma-separated; Excel me khulti | Handwritten list |
| **Parquet** | Compressed columnar (Spark fast), Excel me nahi | Zip+coded list |
| **iam:PassRole** | Service ko role dena/saunpna | Cook ko chaabi thamana |
| **Glue Service Role** | Glue jo wardi pehen ke S3 chhoota | Cook ki kitchen-chaabi |

---

## 🆘 Har Common Galti Ka Solution (One-Stop)

| Problem | Solution |
|---------|----------|
| **Glue console "not authorized"** | User ko `AWSGlueConsoleFullAccess` do. |
| **`iam:PassRole` denied** | User ko IAMFullAccess/PassRole; job/crawler me `glue-mera-role` chuna? |
| **Crawler/Job "Access Denied" S3** | `glue-mera-role` me `AmazonS3FullAccess` hai? (Layer 2) |
| **0 tables created** | S3 path galat / `raw-data/` me `sales.csv` nahi. |
| **clean-data khaali** | Target path galat, ya transform ne sab filter kar diya. |
| **Output `part-0000` naam** | Normal — Spark parts me likhta hai. |
| **Output `.parquet`, CSV nahi** | Target (S3) node → **Data format = CSV** → Save → Run (default Parquet hota hai). |
| **Job bahut der / Failed schema** | Chhoti file; source-transform ke column match karo. |
| **Logs Access Denied** | User ko `CloudWatchLogsFullAccess` (Din 3). |
| **Sab Mumbai me?** | Glue + S3 same region (ap-south-1). |

---

## 🔑 Din 4 Me Kaunsi Permission Chahiye (One-Stop)

**User `rohit-iam-dev` par** (IAM → Users → Add permissions → Attach policies directly):

| Policy | Kis Kaam | Error Jo Batata Hai |
|--------|----------|---------------------|
| **`AWSGlueConsoleFullAccess`** | Glue console chalाना | "not authorized" Glue pe |
| **`IAMFullAccess`** (Din 3) | Glue ko role dena (PassRole) | `iam:PassRole` denied |
| **`AmazonS3FullAccess`** (Din 1) | S3 data | S3 Access Denied |
| **`CloudWatchLogsFullAccess`** (Din 3) | Glue logs dekhna | logs Access Denied |

**Glue Service Role `glue-mera-role` me** (ye Glue khud pehanta hai):
- `AWSGlueServiceRole` + `AmazonS3FullAccess`

---

## 🧹 Din Ke End Me Cleanup (Bill Se Bacho) — Aaj EXTRA Zaroori

> ⚠️ Glue Data Catalog aur pichli practice storage chhota-chhota charge kar sakti hai. Kaam ho gaya to ye **order me** delete karo:

### 1️⃣ ETL Job Delete
- Glue → **ETL jobs** → `raw-to-clean-job` select → **Actions** → **Delete**.

### 2️⃣ Crawler Delete
- Glue → **Crawlers** → `raw-data-crawler` select → **Actions** → **Delete**.

### 3️⃣ Table + Database Delete
- Glue → **Tables** → apni table select → **Action** → **Delete**.
- Phir **Databases** → `mera_data_db` select → **Action** → **Delete**.

### 4️⃣ CloudWatch Logs (Glue Ke)
- CloudWatch → **Log groups** → `/aws-glue/...` wale delete kar do (storage charge).

### 5️⃣ S3 `clean-data/` Ke Test Output
- `clean-data/` me jo `part-0000...` files bani, unhe delete kar do (bill/jagah).

### ✋ Ye MAT Delete Karo (Aage Kaam Aayega)
- **Bucket** aur **`raw-data/sales.csv`** — Din 6 (EMR) me bada-data practice me kaam aa sakta hai.
- **IAM user `rohit-iam-dev`** aur uski permissions — roz chahiye.
- **`glue-mera-role`** — chaho to rakho (koi charge nahi), aage Glue phir use karo to kaam aayega. Nahi chahiye to IAM → Roles se delete.

> 🧾 **Confirm:** 1-2 din baad **Billing → Cost Explorer** me "Glue" ka charge check kar lena — chhota hi hona chahiye.

---

## 📚 Din 4 Ke Saare Documentation Links (Ek Jagah)

- Glue kya hai → https://docs.aws.amazon.com/glue/latest/dg/what-is-glue.html
- IAM setup → https://docs.aws.amazon.com/glue/latest/dg/set-up-iam.html
- Service role → https://docs.aws.amazon.com/glue/latest/dg/create-an-iam-role.html
- Crawler → https://docs.aws.amazon.com/glue/latest/dg/add-crawler.html
- Data Catalog → https://docs.aws.amazon.com/glue/latest/dg/populate-data-catalog.html
- Glue Studio → https://docs.aws.amazon.com/glue/latest/ug/what-is-glue-studio.html
- Jobs banana → https://docs.aws.amazon.com/glue/latest/ug/creating-jobs-chapter.html
- Monitor/logs → https://docs.aws.amazon.com/glue/latest/dg/monitor-glue.html
- Pricing (paisa samajhne ke liye) → https://aws.amazon.com/glue/pricing/

---

## 🎉 Din 4 Complete!

Agar upar sab ✅ hai, to **shabaash!** 💪 Ab tumhare paas:
- **S3 godown** (Din 2), **Lambda naukar** (Din 3), aur ab **Glue kitchen** (Din 4) jo data **saaf** karti hai.

Dimaag me picture:
> "Crawler ne data ka schema samjha → ETL job ne raw-data uthaya, saaf kiya, clean-data me daala."

**Kal:** Din 5 — **GenAI: Spec & Steering Files (AI se code likhwana)** 🤖. AWS se thoda break — ek halka, mazedaar din jaha AI ko sahi se guide karke kaam karwana seekhoge. (EMR/bada data ab Din 6 pe shift ho gaya.)

> Cleanup kar liya? ✅ Ab aaram karo, kal milte hain! 😴➡️🚀
