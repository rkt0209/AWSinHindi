# 4️⃣ ⭐ Glue Studio Me ETL Job Banao (Raw → Saaf → Clean)

> Ab asli cook ka kaam. Glue Studio me **box jod-jod ke** ek job banayenge jo:
> `raw-data/sales.csv` **uthaye** → thoda **saaf/badle** → **`clean-data/`** me daale. Bina bhaari coding. 💪

📖 Glue Studio (visual jobs): https://docs.aws.amazon.com/glue/latest/ug/what-is-glue-studio.html
📖 Visual ETL banana: https://docs.aws.amazon.com/glue/latest/ug/creating-jobs-chapter.html

---

## 🧠 Yaad Karo (File 1)

ETL job = 3 box ki chain:
```
[Source: raw-data padho]  →  [Transform: saaf karo]  →  [Target: clean-data me likho]
   (Extract)                     (Transform)                  (Load)
```
Glue Studio me hum yahi **3 box** jodenge.

---

## 🪜 Step 1 — ETL Jobs Kholo

- Glue console → left menu → **"ETL jobs"** (ya "Visual ETL").
- **"Visual ETL"** (blank visual editor) chuno → ek khaali canvas khulega.

**🖥️ Screen pe:** left me **"Sources / Transforms / Targets"** ke nodes, beech me khaali canvas.

---

## 🪜 Step 2 — SOURCE Box (Extract — Data Uthao)

1. Upar **"+"** / "Add nodes" → **Sources** → **"Amazon S3"** (ya **"AWS Glue Data Catalog"**) chuno.

**Do tareeke — koi bhi:**
- **Data Catalog wala (aasaan):** Source type = **AWS Glue Data Catalog** → Database `mera_data_db` → Table `raw_data` (jo Crawler ne banayi). Schema apne-aap aa jayega. ✅
- **Ya S3 direct:** S3 URL me `s3://tumhara-bucket/raw-data/` → Data format **CSV** → "Infer schema".

**🖥️ Screen pe:** canvas me ek **S3/Catalog source box** aa gaya. Uspe click karke right panel me uska schema (order_id, city, amount) dikhega.

---

## 🪜 Step 3 — TRANSFORM Box (Saaf/Badlo)

Source box selected rakh ke **"+"** → **Transforms** → koi ek simple transform chuno. Beginner ke liye do aasaan:

### Option A — "Change Schema" (columns rename/drop/type)
- Isse column ka naam badal sakte ho, ya koi column hata sakte ho, ya type badal sakte ho.
- Jaise: `city` ko `sheher` rename kar do, ya koi bekaar column drop kar do.

### Option B — "Filter" (kuch rows hatao)
- Jaise: sirf wahi rows rakho jinme `amount > 0` (kharab/khaali amount hatao).

> 📦 **Ye Kya Hai: Transform Node** — ek **step jo data ko beech me badalta hai** (rename, filter, drop, join...). Ek job me kai transform jod sakte ho (safai ke alag-alag steps). **Example:** sabzi pehle dho (filter), phir kaato (change schema) — do steps.

**🖥️ Screen pe:** Source ke aage ek Transform box jud gaya (arrow se connected). Right panel me setting bharo.

> 💡 **Beginner tip:** ek hi simple transform kaafi hai (jaise Filter `amount > 0`). Zyada complicate mat karo pehli baar.

---

## 🪜 Step 4 — TARGET Box (Load — Clean-data Me Likho)

1. Transform box selected → **"+"** → **Targets** → **"Amazon S3"**.
2. Right panel me:
   - **S3 Target Location**: **Browse** → apne bucket ka **`clean-data/`** folder (`s3://tumhara-bucket/clean-data/`).
   - **Data format**: ⚠️ **`CSV`** ZAROOR chuno! (Default aksar **Parquet** hota hai — usse `.parquet` file banti hai jo Excel me nahi khulti. Dropdown me `CSV` select karo.)
   - **Compression**: None (abhi).

> ⚠️ **SABSE COMMON GALTI (dhyaan!):** ye **"Data format" dropdown** chhod dena. Default **Parquet** hai, isliye `clean-data/` me `.csv` ki jagah `.parquet` file aa jaati hai. **Solution:** dropdown me **CSV** chuno, phir Save + Run. (Parquet galat nahi — bas Excel me nahi khulti; abhi CSV aasaan hai.)

> 📦 **Ye Kya Hai: Parquet vs CSV**
> - **CSV** = simple text, comma se columns alag (`order_id,city,amount`). **Excel/Notepad me aaram se khulti**, insaan padh le.
> - **Parquet** = **compressed, columnar** format — Spark/big-data ke liye fast+chhoti, par **Excel me seedhe nahi khulti** (special tool chahiye).
> - **Example:** CSV = handwritten list (koi bhi padh le); Parquet = zip+coded list (machine fast padhe, insaan ko tool chahiye). Practice ke liye **CSV** best.

**🖥️ Screen pe:** teen box ki chain ban gayi:
```
[S3/Catalog: raw-data] → [Filter/Change] → [S3: clean-data]
```

---

## 🪜 Step 5 — Job Settings (Role + Naam)

1. Upar **"Job details"** tab pe click.
2. Bharo:
   - **Name**: `raw-to-clean-job`
   - **IAM Role**: File 2 wala **`glue-mera-role`** chuno ← **zaroori** (warna S3 access nahi).
   - **Type**: Spark (default).
   - **Requested number of workers / DPU**: default (2 ya jo aaye) rehne do — **kam se kam** taaki paisa kam.
   - **Number of retries**: 0 (practice me).
3. Upar **"Save"** dabao.

**🖥️ Screen pe:** upar "Job saved successfully" ✅. Job ban gaya, ab chalana baaki (File 5).

> 🔑 **Permission yaad:** agar Save/Run pe `iam:PassRole` ya S3 denied aaye → File 2 (Layer 1 user permission + Layer 2 role) dobара check karo.

---

## ⚠️ Common Cases / Errors

| Case | Solution |
|------|----------|
| **Source me table nahi dikh rahi** | Pehle Crawler chalाya? (File 3) `mera_data_db` me table honi chahiye. |
| **Target folder `clean-data/` nahi dikhta** | Din 2 me banaya tha; na ho to S3 me `clean-data/` folder bana lo. |
| **Save pe `iam:PassRole` denied** | User ko IAMFullAccess/PassRole; job me `glue-mera-role` chuna? |
| **Schema galat aa raha** | Source me "CSV" + header sahi set karo; ya Catalog wala source use karo. |
| **Job details me role blank** | `glue-mera-role` list me na ho to File 2 se role banao. |
| **Output `.parquet` aa raha, CSV nahi** | Target (S3) node → **Data format** dropdown → **CSV** chuno → Save → Run. Default Parquet hota hai. |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Visual ETL me Source box (raw-data / catalog table) laga
- [ ] Ek Transform box (Filter ya Change Schema) laga
- [ ] Target box → `clean-data/` (CSV) set kiya
- [ ] Job details me naam `raw-to-clean-job` + role `glue-mera-role`
- [ ] Job **Save** ho gaya

> ➡️ Ab job chalao aur clean-data me output dekho → [`05-job-run-verify.md`](./05-job-run-verify.md) ▶️
