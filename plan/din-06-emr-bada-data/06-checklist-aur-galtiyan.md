# 6️⃣ Din 6 Final Checklist + Glue-vs-EMR + Galtiyan + Cleanup 🧾

> Sab tick ho gaya to Din 6 (EMR) **pakka complete**. Neeche one-stop sab kuch.
> 🚨 EMR sabse mehnga hai — **cluster terminate ho gaya na? (File 5)** dobara confirm kar lo.

---

## ✅ Din 6 Master Checklist

**Concept (ye sabke liye — 🅰️ bhi):**
- [ ] EMR = bade data ke liye machine ki **team (cluster)**
- [ ] Big Data = ek machine se na sambhalne wala data
- [ ] Node (Master/Core/Task) = cluster ki machine; asal me **EC2** (isliye paisa)
- [ ] Spark = kaam baant ke tez engine; MapReduce = baanto (Map) → jodo (Reduce)
- [ ] Hadoop/HDFS = bada data baant ke rakhne wala system
- [ ] **Glue vs EMR** ka farak zubaani aata hai

**Permissions (🅱️ hands-on):**
- [ ] User: `AmazonEMRFullAccessPolicy_v2` + IAMFullAccess + S3FullAccess + EC2FullAccess
- [ ] Do role: `EMR_DefaultRole` (service) + `EMR_EC2_DefaultRole` (EC2)

**Hands-on (🅱️):**
- [ ] Chhota cluster (Spark, 1 Master + 1 Core) bana
- [ ] Spark word-count Step chalaya → Completed
- [ ] `emr-output/` me result dekha
- [ ] 🚨 Cluster **Terminated** + EC2 verify

**Cleanup:**
- [ ] Cluster terminate + S3 test data/logs delete
- [ ] Bucket / IAM user / roles NAHI delete kiye

---

## 🧠 Din 6 Ki 5 Sabse Badi Seekh

1. **Bahut bada data = ek machine kam → machine ki team (cluster) chahiye.** Yahi EMR.
2. **Spark kaam baant ke (Map) chalata, phir jod ke (Reduce) jawab deta — tez.**
3. **Har node ek EC2 (kiraye ki machine) — chalu rehne bhar se paisa.**
4. **EMR "Waiting" me bhi paisa leta — kaam ke baad TURANT terminate.**
5. **Chhota/aasaan ETL → Glue; bahut bada / poora control → EMR.**

---

## 🆚 Glue vs EMR — One-Stop (Interview Me Kaam Aayega)

| | **Glue** | **EMR** |
|--|----------|---------|
| **Type** | Serverless ETL (auto) | Cluster tumhare control me |
| **Kaun sambhale** | AWS | **Tum** (banao/terminate) |
| **Setup** | Aasaan (click) | Thoda mehnat (roles + cluster) |
| **Best kab** | Chhota-medium ETL, kam jhanjhat | Bahut bada data, heavy/custom Spark, poora control |
| **Paisa** | Kaam bhar (auto band) | Chalu rehne bhar (khud band) — **mehnga** |
| **Andar** | Spark (chhupa) | Spark/Hadoop (khula, tumhare haath) |

> 🧠 **Ek line jawab:** "Rozmarra ETL ke liye Glue (serverless, sasta). Jab data bahut bada ho ya Spark pe full control chahiye tab EMR — par cluster turant terminate warna mehnga."

---

## 📦 Saari Nayi Terms — Ek Jagah (Revision)

| Term | Ek Line | Example |
|------|---------|---------|
| **Big Data** | Ek machine se na sambhalne wala bada data | 50,000 logo ka khana |
| **Cluster** | Judi hui machine ki team | Music band |
| **Node** | Cluster ki ek machine | Team ka member |
| **Master node** | Manager — kaam baanta | Site thekedar |
| **Core node** | Kaam + data dono | Pakka mazdoor |
| **Task node** | Sirf extra kaam | Dihaadi mazdoor |
| **EC2** | Kiraye pe milne wali machine | Ola/Uber gaadi |
| **Spark** | Kaam baant ke tez chalane wala engine | 500 cook saath likhein |
| **MapReduce** | Baanto (Map) → jodo (Reduce) | Copies baant ke check |
| **Hadoop** | Purana big-data framework | Base system |
| **HDFS** | Data kai machine pe baant ke rakhna | Moti kitaab alag almari |
| **EMR** | Cluster khud bana ke dene wali AWS service | 500 mazdoor bulao |
| **Step** | Cluster ko diya ek kaam ka order | Cook ko parchi |
| **Terminate** | Cluster (machine) band karna | Kiraye ki gaadi wapas |
| **Instance type** | Machine kitni badi/powerful | Chhoti gaadi vs truck |
| **Termination protection** | Galti-se-band na ho wala lock | Safety lock |

---

## 🆘 Har Common Galti Ka Solution (One-Stop)

| Problem | Solution |
|---------|----------|
| **EMR console "not authorized"** | User ko `AmazonEMRFullAccessPolicy_v2`. |
| **`iam:PassRole` denied** | User ko `IAMFullAccess`; cluster me dono role chuna? |
| **Cluster banne pe role error** | `EMR_DefaultRole` + `EMR_EC2_DefaultRole` (ya "Create default roles"). |
| **Job "Access Denied (S3)"** | **EC2 role** me S3 permission (Layer 2). |
| **Step Failed — output exists** | Output folder naya do (`result2/`); purana pe Spark likhta nahi. |
| **Cluster khali "Waiting" me paisa lag raha** | Waiting me bhi charge — **terminate** karo. |
| **Terminate nahi ho raha** | Termination protection **OFF** karo. |
| **EC2 me machine abhi running** | EC2 se manually terminate; verify (File 5). |
| **Sab Mumbai me?** | EMR + S3 same region (ap-south-1). |

---

## 🔑 Din 6 Me Kaunsi Permission Chahiye (One-Stop)

**User `rohit-iam-dev` par** (IAM → Users → Add permissions → Attach policies directly):

| Policy | Kis Kaam | Error Jo Batata Hai |
|--------|----------|---------------------|
| **`AmazonEMRFullAccessPolicy_v2`** | EMR console + cluster | "not authorized" EMR pe |
| **`IAMFullAccess`** (Din 3) | EMR ko role dena (PassRole) + default roles | `iam:PassRole` denied |
| **`AmazonS3FullAccess`** (Din 1) | Input/output data | S3 Access Denied |
| **`AmazonEC2FullAccess`** | EMR peeche EC2 chalata | EC2 authorization error |

**Do EMR Role** (cluster banate waqt auto-create ho sakte):
- `EMR_DefaultRole` (service) + `EMR_EC2_DefaultRole` (EC2/S3)

---

## 🧹 Din Ke End Me Cleanup (Bill Se Bacho) — Aaj SABSE Zaroori

> 🚨 EMR sabse mehnga service. Order me pakka karo:

### 1️⃣ Cluster Terminate (Sabse Pehle!)
- EMR → Clusters → `mera-chhota-cluster` → **Terminate** → status **Terminated**. (File 5)

### 2️⃣ EC2 Verify
- EC2 → Instances → koi EMR machine **running na ho** (terminated dikhe).

### 3️⃣ S3 Test Data + Logs
- `emr-input/`, `emr-output/`, aur `aws-logs-.../elasticmapreduce/` — delete karo (storage).

### ✋ Ye MAT Delete Karo (Aage Kaam Aayega)
- **Bucket** + **`raw-data/sales.csv`** — Din 9 mini-project me chahiye.
- **IAM user `rohit-iam-dev`** + permissions — roz chahiye.
- **`EMR_DefaultRole`, `EMR_EC2_DefaultRole`, `glue-mera-role`** — rakhne me **koi charge nahi**; aage kaam aa sakte. Nahi chahiye to IAM → Roles se delete.

> 🧾 **Confirm:** 1-2 din baad **Billing → Cost Explorer** me EMR + EC2 charge dekh lo — chhota + **ruka hua** (badhता nahi) hona chahiye. Agar badh raha hai → koi machine abhi chalu hai, EC2 me jaake band karo!

---

## 📚 Din 6 Ke Saare Documentation Links (Ek Jagah)

- EMR kya hai → https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html
- EMR Getting Started → https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-gs.html
- EMR IAM roles → https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-iam-roles.html
- EMR pe Spark → https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark.html
- Steps se kaam → https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-work-with-steps.html
- Cluster terminate → https://docs.aws.amazon.com/emr/latest/ManagementGuide/UsingEMR_TerminateJobFlow.html
- EMR pricing (paisa samajhne ko) → https://aws.amazon.com/emr/pricing/

---

## 🎉 Din 6 Complete!

Agar upar sab ✅ hai (aur cluster **terminated** hai 🙏), to **shabaash!** 💪 Ab tumhare paas:
- **S3 godown** (2), **Lambda naukar** (3), **Glue kitchen** (4), **AI guide** (5), aur ab **EMR — bade data ki mazdoor-team** (6).

Dimaag me picture:
> "Data chhota → Glue. Data bahut bada → EMR cluster (Spark kaam baant ke kare) → jawab → **turant terminate**."

**Kal:** Din 7 — **Step Functions: Manager (sab kaamo ko sahi order me chalana)** 🔀. Ab tak alag-alag tukdे seekhe (S3, Lambda, Glue...) — kal seekhenge inhe **ek flow me jodना** (pehle ye → phir ye → error to ye).

> Cluster terminate kar liya? ✅ Bill safe? ✅ Ab aaram karo, kal milte hain! 😴➡️🚀
