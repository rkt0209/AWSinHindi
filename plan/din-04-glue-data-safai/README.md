# 🧽 Din 4 — Glue (Data Saaf Karne Wali Automatic Kitchen)

> Din 2 me **godown (S3)** banaya, Din 3 me **automatic naukar (Lambda)**.
> Aaj **Glue** seekhenge — ek **automatic kitchen** jo **kacchi/gandi sabzi (raw data)** ko
> **dho-kaat ke ready (clean data)** kar deti hai. Yani `raw-data/sales.csv` ko saaf karke `clean-data/` me daalenge. 🍳

---

## ⚠️ SABSE PEHLE — Paise Wali Baat (Zaroor Padho)

> Lambda/S3 ki tarah Glue **free tier me lagbhag-muft NAHI** hai.
> - **Data Catalog** (data ki list rakhna) → lagbhag free (1 million objects tak).
> - **Crawler chalाना + ETL Job chalाना** → **paise lagte hain** (per-minute, chhota amount — poori practice ~₹5–20 tak aa sakti hai).
>
> **Iska matlab:** Ghabrao mat, amount chhota hai — par (a) kaam ke baad **turant cleanup** karo (File 6), aur (b) baar-baar bekaar mat chalao.
> Agar bilkul paise nahi lagane, to tum sirf **padh ke samajh** sakte ho — par ek baar khud karke dekhne se hi asli seekh milti hai. Decision tumhara. 💡

---

## 🎯 Aaj Kya-Kya Karenge?

| Step | File | Kya Seekhoge |
|------|------|--------------|
| 1️⃣ | [`01-glue-kya-hai-concept.md`](./01-glue-kya-hai-concept.md) | Glue kya hai — kitchen wala example + saari nayi terms ke definition box (ETL, Crawler, Data Catalog, Job, DPU) |
| 2️⃣ | [`02-glue-role-permission.md`](./02-glue-role-permission.md) | 🔑 Glue ke liye role + permissions (do layer) — warna har jagah Access Denied |
| 3️⃣ | [`03-crawler-aur-catalog.md`](./03-crawler-aur-catalog.md) | Database + Crawler banana, chalाना → data ki "table" ban-ti hai (schema) |
| 4️⃣ | [`04-etl-job-banana.md`](./04-etl-job-banana.md) | ⭐ Glue Studio me visual ETL job — raw-data padho, saaf karo, clean-data me likho |
| 5️⃣ | [`05-job-run-verify.md`](./05-job-run-verify.md) | Job chalाना + `clean-data/` me output check + logs |
| 6️⃣ | [`06-checklist-aur-galtiyan.md`](./06-checklist-aur-galtiyan.md) | Checklist + errors + permissions summary + **cleanup (bill se bacho)** |

---

## 🧠 Ek Line Me Aaj Ka Din

> "Glue = ek **automatic kitchen** — pehle **Crawler** (chef ka helper) dekhta hai kaunsa saamaan (data) hai, phir **ETL Job** us kacche saamaan ko **dho-kaat-pakā ke** ready plate (clean data) bana deta hai."

---

## 🔑 Aaj Ke Naye Shabd (Box Me Detail Me)

- **ETL** — Extract (uthao) → Transform (saaf karo) → Load (rakh do)
- **Data Catalog** — poore data ki "index/register" (kaha kya data hai)
- **Database & Table** — data ka naam-pata aur uska "schema" (column ka dhaancha)
- **Crawler** — apne-aap ghoom ke data ka schema pata karne wala helper
- **ETL Job** — asli saaf-safai wala kaam (code/visual)
- **Glue Studio** — job banane ka drag-drop wala aasaan screen
- **DPU** — Glue kitni "mehnat/power" laga raha (isi se paisa banta hai)

---

## ✅ Aaj Ka Target

Din ke end me:
- `raw-data/sales.csv` ka schema Catalog me table ban jaye ✅
- Ek ETL job jo data saaf karke **`clean-data/`** me daale ✅
- Aur cleanup karke bill safe ✅

> Chalo, File 1 se shuru karo → [`01-glue-kya-hai-concept.md`](./01-glue-kya-hai-concept.md) 🚀
