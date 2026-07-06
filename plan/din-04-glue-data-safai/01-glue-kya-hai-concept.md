# 1️⃣ Glue Kya Hai? — Concept (Aaram Se Samjho) 🧽

> Aaj sirf **samajhna** hai. Haath ka kaam File 2 se. Har nayi term ko **alag box** me
> "actually ye kya hai + example" karke samjhaya hai. 🧠

📖 Glue kya hai (official): https://docs.aws.amazon.com/glue/latest/dg/what-is-glue.html

---

## 🍳 Sabse Pehle — Glue Ka Real-Life Example

**Soch:** ek **badi automatic kitchen** 🍳. Mandi se kacchi, gandi, bina-dhuli sabzi aati hai (raw data). Kitchen ka kaam:
1. Saamaan **uthao** (mandi/godown se).
2. **Dho-kaat-chhaant** ke saaf karo (kharab hissa hatao, sahi size me kaato).
3. Ready plate **rakh do** (serve ke liye).

**Data ki duniya me bhi bilkul yahi hota hai:**
- Raw data aksar **ganda** hota hai — khaali cell, galat spelling, extra column, duplicate rows.
- Use **uthana, saaf karna, aur sahi jagah rakhna** padta hai — tabhi wo report/analysis me kaam aata hai.

**Glue = wahi automatic kitchen** jo ye "uthao-saaf-karo-rakho" ka kaam **khud (serverless)** kar deti hai. Tumhe server/machine nahi sambhalni.

> **Ek line:** Glue = "raw data ko uthaने, saaf karne aur clean jagah rakhने wali automatic (serverless) kitchen."

---

## 📦 Ye Kya Hai: **ETL** (Glue Ka Dil)

**Definition:** ETL teen kaam ka short form hai — data ke saath jo hota hai:
- **E = Extract (Uthao):** data ko source se **nikalna** (jaise S3 ke `raw-data/` se).
- **T = Transform (Saaf/Badlo):** data ko **saaf karna / badalna** (khaali hatao, format theek karo, jodna-todna).
- **L = Load (Rakho):** saaf data ko **kahin rakhna** (jaise S3 ke `clean-data/` me).

**Example:** Kapde dhona — **E:** ganda kapda tokri se uthao → **T:** machine me dho-nichod ke saaf karo → **L:** almari me tah karke rakh do. Bas isi ko data pe karo = ETL.

> 💡 Glue ka har "Job" asal me ek ETL hi karta hai: Extract → Transform → Load.

---

## 📦 Ye Kya Hai: **Data Catalog**

**Definition:** Data Catalog = poore data ka ek **register/index** — "kaunsa data kaha hai, uska dhaancha (columns) kya hai." Ye **asli data nahi rakhta**, sirf data ke baare me **jaankari (metadata)** rakhta hai.

**Example:** Library ka **catalog/register** 📖 — isme kitaabein nahi hoti, par likha hota hai "kaunsi kitaab kis almari-shelf me hai, kis topic ki hai." Data Catalog waise hi data ka register hai.

> 💡 Isme "Databases" aur "Tables" hote hain (neeche box). Glue ke saare tools isi register ko dekh ke kaam karte hain.

---

## 📦 Ye Kya Hai: **Database aur Table** (Glue Wale)

> ⚠️ Dhyaan: ye "Database/Table" wo **normal MySQL wala nahi** — ye sirf Catalog ke andar **naam aur schema** hai. Asli data to S3 me hi pada rehta hai.

**Definition:**
- **Database (Glue)** = Catalog me ek **folder/group** jisme milti-julti tables rakhte ho. (Sirf naam ka dabba.)
- **Table (Glue)** = ek data-file (jaise `sales.csv`) ka **schema (dhaancha)** — kaunse column hain, kis type ke (number/text), data kaha (S3 path) hai. **Data nahi, sirf naksha.**

**Example:** Ghar ka **naksha (blueprint)** 🏠 — naksha ghar nahi hota, par batata hai "3 kamre, 2 bathroom, kaha kya hai." Table waise hi data ka naksha hai; asli data (ghar) S3 me hai.

**Schema kya hai?** = column ka dhaancha. Jaise `sales.csv` ka schema:
```
order_id : number
city     : text
amount   : number
```

---

## 📦 Ye Kya Hai: **Crawler** (Sabse Important Aaj)

**Definition:** Crawler = ek **automatic helper jo tumhare data (S3 folder) ko khud ghoom ke dekhta hai**, samajh leta hai "isme kaunse column hain, kis type ke," aur Catalog me apne-aap ek **Table (schema)** bana deta hai. Tumhe schema haath se likhne ki zaroorat nahi.

**Example:** Naya **store manager** 🕵️ jo godown me ghoom ke saara saamaan dekhta hai aur ek **list bana leta hai** — "5 bori chawal, 3 peti tel..." Tumhe khud ginna nahi padta, wo khud crawl (ghoom) karke list (schema) bana deta hai. Yahi Crawler hai.

> 💡 **Kaam:** Crawler ko bolo "ye `raw-data/` folder dekho" → wo chal ke `sales.csv` padhta hai → Catalog me `sales` naam ki table (order_id, city, amount) bana deta hai. ✅

---

## 📦 Ye Kya Hai: **ETL Job**

**Definition:** ETL Job = asli **saaf-safai wala kaam (code ya visual steps)** — jo data ko uthata hai (Extract), saaf/badalta hai (Transform), aur nayi jagah rakhta hai (Load). Crawler sirf **dekhta** hai; Job asli **kaam** karta hai.

**Example:** Crawler = helper ne bata diya "ye kacchi sabzi hai." **Job = asli cook** jo us sabzi ko dho-kaat-pakā ke plate ready karta hai.

> 💡 Aaj hum ek job banayenge jo `raw-data/sales.csv` uthaye, thoda saaf kare, aur `clean-data/` me daale.

---

## 📦 Ye Kya Hai: **Glue Studio**

**Definition:** Glue Studio = Glue ka **drag-and-drop (visual) screen** jaha bina zyada code likhe, **box jod-jod ke** ETL job bana lete ho ("yaha se data lo → ye badlo → yaha rakho"). Andar-andar ye khud code (Spark) bana deta hai.

**Example:** Video banane ki app jaha **clips drag karke** jodte ho, coding nahi karni padti. Glue Studio waisa hi ETL ke liye hai.

---

## 📦 Ye Kya Hai: **DPU** (Isi Se Paisa Banta Hai — Dhyaan!)

**Definition:** DPU = **Data Processing Unit** — "Glue ek kaam me **kitni power/mehnat (CPU + memory)** laga raha hai" uska naap. Job/Crawler jitni der aur jitne DPU pe chalega, **utna paisa** lagega (per-minute charge).

**Example:** Kitchen me **kitne cook + kitni der** lage — 2 cook 1 ghante → utni majdoori. DPU + time = utna bill. Isliye chhota data + kam DPU rakhо, aur kaam ke baad band/delete karo.

> 💡 **Beginner rule:** default DPU/worker rehne do, **chhoti file** pe practice karo, aur **kaam ke baad cleanup** (File 6). Tabhi bill chhota rahega.

---

## 🖼️ Poori Picture — Ek Saath (S3 + Glue)

```
   S3: raw-data/sales.csv   (kacchi sabzi — Din 2 me daali)
              │
              ▼
   ┌───────────────────────┐
   │  CRAWLER (helper)      │  ghoom ke dekha → schema samjha
   └───────────┬───────────┘
               │ Table bana di
               ▼
   ┌───────────────────────┐
   │  DATA CATALOG          │  register: table `sales`
   │  (database > table)    │  (order_id, city, amount)
   └───────────┬───────────┘
               │ Job ne table/data uthaya
               ▼
   ┌───────────────────────┐
   │  ETL JOB (cook)        │  Extract → Transform (saaf) → Load
   │  (Glue Studio)         │
   └───────────┬───────────┘
               │ saaf data likha
               ▼
   S3: clean-data/...       (ready plate ✅)
```

---

## ✅ Is File Ka "Ho Gaya" Check

- [ ] Glue = automatic kitchen (raw → clean) — samajh gaye
- [ ] ETL = Extract (uthao) + Transform (saaf) + Load (rakho)
- [ ] Data Catalog = data ka register (metadata, asli data nahi)
- [ ] Table = data ka naksha/schema; asli data S3 me
- [ ] Crawler = khud ghoom ke schema banane wala helper
- [ ] ETL Job = asli saaf-safai; Glue Studio = visual screen
- [ ] DPU = power/mehnat ka naap — **isi se paisa** banta hai

> ➡️ Ab permissions set karo (warna aage Access Denied) → [`02-glue-role-permission.md`](./02-glue-role-permission.md) 🔑
