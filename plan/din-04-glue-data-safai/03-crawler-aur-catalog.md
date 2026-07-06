# 3️⃣ Database + Crawler Banao → Data Ki Table (Schema) Banti Hai 🕵️

> Ab Glue ko bolenge "ye `raw-data/` folder dekho." Wo khud ghoom (crawl) karके
> `sales.csv` ka schema samjhega aur Catalog me ek **table** bana dega. 💪

📖 Crawler kya hai: https://docs.aws.amazon.com/glue/latest/dg/add-crawler.html
📖 Data Catalog: https://docs.aws.amazon.com/glue/latest/dg/populate-data-catalog.html

---

## 🧭 Step 0 — Glue Console Kholo

- AWS Console → search me `Glue` → **AWS Glue** pe click.
- Region **Mumbai (ap-south-1)** check karo (upar-right).

**🖥️ Screen pe:** Glue ka home — left side me menu: **Data Catalog** (Databases, Tables, Crawlers), **ETL jobs**, etc.

> ⚠️ **Yaad rakho (File 1):** Crawler/Job chalane pe **thoda paisa** lagta hai. Practice `sales.csv` (chhoti file) pe hi karo.

---

## 🪜 PART A — Pehle Ek Database Banao (Catalog Ka Folder)

> Yaad karo (File 1): Database = Catalog ke andar ka **naam ka dabba** jisme tables rakhte hain.

1. Left menu → **"Databases"** (Data Catalog ke neeche) → **"Add database"**.
2. **Name**: `mera_data_db` (chhote akshar, underscore chalega) → **Create database**.

**🖥️ Screen pe:** Databases list me `mera_data_db` dikhne lagega. ✅

---

## 🪜 PART B — Crawler Banao

### Step 1 — Add Crawler
- Left menu → **"Crawlers"** → **"Create crawler"**.

### Step 2 — Naam
- **Name**: `raw-data-crawler` → **Next**.

### Step 3 — Data Source (kaha dekhna hai)
- **"Is your data already mapped to Glue tables?"** → **"Not yet"** rehne do.
- **"Add a data source"** dabao:
  - **Data source**: **S3**.
  - **S3 path**: **Browse** karke apne bucket ka **`raw-data/`** folder chuno (jaise `s3://tumhara-bucket/raw-data/`).
  - Baaki default → **"Add an S3 data source"**.
- **Next**.

> 💡 Hum poora `raw-data/` folder de rahe hain — Crawler usme ki saari files ka schema dekh lega.

### Step 4 — Role (Wardi Chuno)
- **"Existing IAM role"** me File 2 wala **`glue-mera-role`** chuno → **Next**.

> 📦 Yahi wo "wardi" hai — Crawler isi ko pehen ke tumhara S3 padhega. Na chuna to Access Denied.

### Step 5 — Output (Table Kaha Banegi)
- **Target database**: `mera_data_db` chuno.
- **Table name prefix** (optional): khaali chhod do ya `raw_` daal do.
- **Next**.

### Step 6 — Review aur Create
- Sab dekh ke **"Create crawler"** dabao.

**🖥️ Screen pe:** Crawler `raw-data-crawler` ban gaya (status: **Ready**). ✅

---

## 🪜 PART C — Crawler Chalao (Run)

1. Crawler list me `raw-data-crawler` select → **"Run crawler"** (ya "Run") dabao.

**🖥️ Screen pe:**
- Status **Running** → thodi der (1–2 min) → **Stopping** → **Ready**.
- Ho jaane pe **"Table changes"** me dikhega: **1 table created** (ya "1 created"). 🎉

> ⚠️ Ye 1-2 min chal ke thoda paisa (chhota) lagता hai — normal.

---

## 🪜 PART D — Table (Schema) Dekho

1. Left menu → **"Tables"** → apni nayi table (jaise `raw_data` ya `sales`) pe click.

**🖥️ Screen pe:** table ka **schema** dikhega:
```
order_id : bigint   (number)
city     : string   (text)
amount   : bigint   (number)
```
- Saath me **Location** (S3 path), **Classification** (`csv`), row count etc.

> 🎉 **Ho gaya!** Crawler ne khud `sales.csv` padh ke schema bana diya — tumne ek column bhi haath se nahi likha. Yahi Crawler ka jaadu.

---

## 🧪 Chhoti Samajh

- Agar `sales.csv` me pehli row header (`order_id,city,amount`) hai, to Glue usse column-naam le leta hai. Agar column-naam `col0, col1...` dikhein, to file me header missing hai ya classifier ne header nahi pehchaana — abhi ke liye theek, aage seekhoge.

---

## ⚠️ Common Cases / Errors

| Case | Solution |
|------|----------|
| **Crawler pe "Access Denied" / role error** | Crawler me `glue-mera-role` chuna? Us role me S3 permission hai? (File 2 Layer 2) |
| **0 tables created** | S3 path galat (`raw-data/` khaali?) — `sales.csv` us folder me hai check karo. |
| **Column `col0,col1` dikhe** | File me header row nahi/ya galat. Abhi ignore; ya CSV me pehli row header rakho. |
| **Crawler bahut der Running** | Chhoti file me 1-2 min normal. Bade data me zyada. |
| **`iam:PassRole` error** | User (Layer 1) ko IAMFullAccess/PassRole chahiye. |
| **Region alag** | Glue aur S3 dono **Mumbai** me hone chahiye. |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] `mera_data_db` database bana
- [ ] `raw-data-crawler` bana (role `glue-mera-role` chuna)
- [ ] Crawler run kiya → 1 table created
- [ ] Table ka schema (order_id, city, amount) dekha
- [ ] Samajh gaye: Crawler ne khud schema banaya, data abhi bhi S3 me hai

> ➡️ Ab asli safai — ETL job banao (raw → clean) → [`04-etl-job-banana.md`](./04-etl-job-banana.md) ⭐
