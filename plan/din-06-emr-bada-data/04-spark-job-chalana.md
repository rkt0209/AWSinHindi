# 4️⃣ Ek Simple Spark Job Chalao (Word Count) ⚡

> Cluster taiyaar (Waiting) hai. Ab uspe ek **chhota Spark kaam** chalayenge — ek text file me
> **kaunsa shabd kitni baar aaya (word count)** ginwaayenge. Ye "hello world" of big-data hai. 💪
> ⏱️ Jaldi karo — cluster ka meter chal raha hai.

📖 EMR pe Spark: https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark.html
📖 Steps se kaam chalana: https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-work-with-steps.html

---

## 🧠 Pehle Samjho — "Step" Kya Hai

### 📦 Ye Kya Hai: **Step** (EMR Me Kaam Ka Tukda)
**Definition:** Step = cluster ko diya gaya **ek kaam ka order** — "ye script/job chala do." Tum cluster ko ek ya kai Steps dete ho, wo baari-baari chalata hai. (Ye Din 7 wale Step Functions se **alag** cheez hai — bas naam mila-julta.)

**Example:** Cook (cluster) ko parchi (Step) do — "ye recipe bana do." Cook bana ke bata deta "ho gaya (Completed)." 🍳

> 💡 Do tareeke se Spark chala sakte ho: **(A) Step add karke** (console se, aasaan — yahi karenge), ya **(B) cluster me SSH kar ke spark-shell** (advance). Beginner: **Step** wala.

---

## 🗂️ Step 0 — Input Data Taiyaar Karo (S3 Me)

Word count ke liye ek text file chahiye.

1. S3 → apna bucket → ek folder `emr-input/` banao.
2. Usme ek text file `words.txt` upload karo (koi bhi paragraph — kuch lines likh do, jaise ek kahani ya "apple banana apple mango banana apple").
3. Ek output folder soch lo: `emr-output/` (isme result aayega — **pehle se khali/na-bani honi chahiye**).

> ⚠️ **Zaroori:** output path (`emr-output/result/`) **pehle se maujood na ho** — Spark khud banata hai; agar folder pehle se hai to job **fail** ho jata hai. Har run pe **naya** output naam do (jaise `result1`, `result2`).

> 💡 Bade data ka asli maza tab hai jab file **GB me** ho — par practice/paisa ke liye chhoti file bilkul theek. Concept wahi rehta hai.

---

## 🅰️ Tareeka A — Step Ke Zariye Spark Chalao (Aasaan)

EMR me ready-made **word count** example jar hoti hai. Use Step se chalate hain.

### Step 1 — Cluster Pe Steps Kholo
- EMR → **Clusters** → `mera-chhota-cluster` pe click → **"Steps"** tab → **"Add step"**.

### Step 2 — Step Bharo
- **Type**: **Spark application** (ya "Custom JAR" agar Spark option na dikhe).
- **Name**: `word-count`
- **Deploy mode / Application location**: EMR ke Spark examples me word-count milta hai. Aasaan raasta — **apni chhoti PySpark script** do (neeche box). Uss `.py` file ko S3 me `emr-input/wordcount.py` daal do aur yaha uska path do.
- **Arguments** me apna **input** aur **output** S3 path do:
  ```
  s3://tumhara-bucket/emr-input/words.txt
  s3://tumhara-bucket/emr-output/result1/
  ```
- **Action on failure**: **Continue** (cluster fail pe band na ho, taaki tum khud terminate kar sako).
- **"Add step"** dabao.

> 📦 **Chhoti PySpark word-count script** (`wordcount.py` — S3 me daal do):
> ```python
> import sys
> from pyspark.sql import SparkSession
>
> spark = SparkSession.builder.appName("WordCount").getOrCreate()
> text = spark.sparkContext.textFile(sys.argv[1])          # input path (arg 1)
> counts = (text.flatMap(lambda line: line.split(" "))     # har line ko shabdo me todo (Map)
>                .map(lambda word: (word, 1))               # har shabd ko (shabd, 1)
>                .reduceByKey(lambda a, b: a + b))          # same shabd jodo (Reduce)
> counts.saveAsTextFile(sys.argv[2])                        # output path (arg 2)
> spark.stop()
> ```
> Dekha? `flatMap` = **Map** (baanto), `reduceByKey` = **Reduce** (jodo) — File 1 wala MapReduce yahi hai! 🎯

### Step 3 — Status Dekho
- Steps tab me `word-count` ka status: **Pending** → **Running** ⏳ → **Completed** ✅ (ya **Failed** ❌).
- 1-3 min lag sakte hain (chhoti file me).

---

## 📤 Step 4 — Output Dekho (`emr-output/result1/` Me)

1. S3 → apna bucket → `emr-output/result1/` kholo.

**🖥️ Screen pe:**
- `part-00000` jaisi file(s) + ek `_SUCCESS` file dikhegi (job theek chala).
- `part-00000` download karke kholo → dikhega:
  ```
  ('apple', 3)
  ('banana', 2)
  ('mango', 1)
  ```
  Yani **har shabd kitni baar aaya**. 🎉

> 💡 `_SUCCESS` file ka matlab "job poora sahi chala." Data `part-...` files me hota hai (Spark tukdo me likhta hai — jaise Glue me tha).

---

## ⚠️ Common Cases / Errors

| Case | Solution |
|------|----------|
| **Step "Failed" — output path exists** | Output folder pehle se hai → **naya** naam do (`result2/`). Spark purana folder pe likhne se mana karta. |
| **"Access Denied (S3)"** | **EC2 role** (`EMR_EC2_DefaultRole`) me S3 permission missing (File 2 Layer 2). |
| **Script not found** | `wordcount.py` ka S3 path galat — S3 me file check karo. |
| **Cluster "Waiting" par Step nahi chal raha** | Add step dobara; cluster Running/Waiting me hona chahiye. |
| **Bahut der Running** | Chhoti file me nahi hona chahiye; bade data me normal. |
| **Region mismatch** | Cluster + S3 dono Mumbai. |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Input `words.txt` (aur `wordcount.py`) S3 me daala
- [ ] Cluster pe `word-count` Step add kiya → **Completed**
- [ ] `emr-output/result1/` me `part-...` + `_SUCCESS` aaya
- [ ] Output me shabd-ginti dekhi (MapReduce ka asar)
- [ ] Samajh gaye: Spark ne kaam baant ke (Map→Reduce) kiya

> 🚨 ➡️ **AB SABSE ZAROORI — cluster TURANT terminate karo (warna bill badhega)** → [`05-cluster-terminate-verify.md`](./05-cluster-terminate-verify.md) 🛑
