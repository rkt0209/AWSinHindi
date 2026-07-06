# 5️⃣ Job Chalao + Clean-data Me Output Check + Logs ▶️

> Job ban gaya. Ab **Run** karke dekho — asli data `clean-data/` me saaf hoke aa jaye. 🎉

📖 Job run + monitor: https://docs.aws.amazon.com/glue/latest/dg/monitor-glue.html
📖 Job runs dekhna: https://docs.aws.amazon.com/glue/latest/ug/managing-jobs-chapter.html

---

## 🪜 PART A — Job Run Karo

1. `raw-to-clean-job` khol ke upar **"Run"** button dabao.

**🖥️ Screen pe:** upar green "Job run started" jaisa message. Job background me chalne lagega.

### Run Ka Status Kaha Dekho
- Job ke **"Runs"** tab pe jao (ya left "ETL jobs" → job → Runs).

**🖥️ Screen pe:** ek run dikhega with status:
- **Running** ⏳ → thodi der (2–4 min, kyunki Spark machine start hoti hai — thoda "cold start" jaisa)
- → **Succeeded** ✅ (ya **Failed** ❌ agar koi galti)

> ⚠️ **Paisa:** ye 2–4 min chalne pe DPU-time ka chhota charge lagता hai. Isliye baar-baar bekaar run mat karo.

---

## 🪜 PART B — Output Dekho (`clean-data/` Me)

1. S3 console → apna bucket → **`clean-data/`** folder kholo.

**🖥️ Screen pe:**
- Ek ya zyada nayi file(s) dikhengi — Glue (Spark) aksar naam deta hai jaise `run-XXXX-part-0000` ya `part-00000-....csv`.
- File download karke kholo → tumhara **saaf kiya hua data** dikhega (jaise sirf `amount > 0` wali rows, ya renamed columns). 🎉

> 💡 **Note:** Spark data ko **tukdon (parts) me** likhta hai — isliye ek `part-000...` file ban sakti hai (ya kai, bade data me). Ye normal hai.

> 🎉🎉 **Mubarak!** Tumne raw data ko Glue se saaf karke clean-data me daal diya — poora **ETL (Extract-Transform-Load)** khud chal ke ho gaya!

---

## 🪜 PART C — Logs (Kuch Galat Ho To Yaha Dekho)

Yaad karo Din 3: logs = diary. Glue bhi **CloudWatch** me logs likhta hai.

1. Job → **"Runs"** tab → us run pe → **"Output logs"** / **"Error logs"** (CloudWatch link) dabao.

**🖥️ Screen pe:** CloudWatch me Glue ke logs — kya hua, koi error to nahi.

> 🔑 **Permission:** logs dekhne pe Access Denied aaye to user ko **`CloudWatchLogsFullAccess`** chahiye (Din 3 me add ki thi).

---

## ⚠️ Common Cases / Errors

| Case (run me) | Matlab / Solution |
|------|-------------------|
| **Succeeded ✅** | Sab sahi. `clean-data/` me output check karo. |
| **Failed — "Access Denied" S3** | Glue **service role** (`glue-mera-role`) me S3 permission missing (File 2 Layer 2). |
| **Failed — `iam:PassRole`** | User (Layer 1) permission (File 2). |
| **clean-data khaali** | Job Target path galat, ya Transform ne saara data filter kar diya (jaise `amount>1000` galti se). |
| **Output `part-0000` naam se** | Normal — Spark parts me likhta hai. |
| **Bahut der Running** | Spark start hone me 2-4 min normal. Bahut zyada = bada data / DPU kam. |
| **Failed — schema/column error** | Source schema aur transform ke column-naam match karo (File 4). |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Job **Run** kiya → **Succeeded**
- [ ] `clean-data/` me output file aayi
- [ ] File khol ke saaf data dekha (filter/rename ka asar)
- [ ] Logs kaha milte hain — pata
- [ ] Samajh gaye: Spark parts me likhta hai; run me thoda paisa lagता hai

> ➡️ Ab final: checklist + errors + permissions + **cleanup (bill se bacho)** → [`06-checklist-aur-galtiyan.md`](./06-checklist-aur-galtiyan.md) 🧾
