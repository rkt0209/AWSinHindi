# 🏗️ Din 6 — EMR (Bahut Bada Data — 500 Mazdooro Ki Team)

> Din 4 me **Glue** se chhota data (ek `sales.csv`) saaf kiya. Par socho data itna bada ho —
> **crore rows, GB-TB me** — ki ek machine ghante-din laga de ya haar hi jaaye. 😰
> Tab **EMR** aata hai: ek **machine nahi, poori team (cluster)** jo kaam **baant ke** saath-saath karti hai. 💪

---

## ⚠️ SABSE PEHLE — Paise Wali Baat (Ye Sabse Mehnga Din Hai, Zaroor Padho) 💸

> EMR ab tak ka **sabse mehnga** service hai. Kyun? Kyunki ye peeche **kai asli computers (EC2 machines) chalu** karta hai, aur wo **har ghante** paisa lete hain — chalu rehne bhar se, chahe tum kaam karo ya na karo.
>
> - **Glue:** kaam khatam → apne aap band (serverless). Bill chhota.
> - **EMR:** cluster tum **khud band (terminate)** na karo to **ghante-ghante chalta rehta** hai → **bada bill**. 😱
>
> **Isliye 2 raaste hain — apni himmat/budget se chuno:**
>
> **🅰️ Safe raasta (recommended intern ke liye):** Cluster **mat banao**. Sirf File 1 (concept) + File 6 (Glue vs EMR) **padh ke samajh lo**. Intern se yahi expect hota hai — "EMR kya, kyun, kab." **Koi paisa nahi lagega.** ✅
>
> **🅱️ Hands-on raasta (agar seekhne ki bhookh + thoda budget):** Ek **chhota** cluster banao (File 3), ek simple Spark job chalao (File 4), aur **turant terminate karo** (File 5). Poori practice **~₹30–100** tak aa sakti hai agar jaldi terminate karo. **Der ki to zyada.**
>
> 👉 Faisla: **abhi paisa nahi lagाना to 🅰️ chuno — bilkul theek hai.** Ek baar khud karke dekhna ho to 🅱️, par **timer dimaag me rakho — kaam ke baad turant band.**

---

## 🎯 Aaj Kya-Kya Karenge?

| Step | File | Kya Seekhoge |
|------|------|--------------|
| 1️⃣ | [`01-emr-kya-hai-concept.md`](./01-emr-kya-hai-concept.md) | EMR kya hai — 500 mazdoor wala example + har nayi term ka definition box (Big Data, Cluster, Node, Spark, MapReduce, Hadoop/HDFS) |
| 2️⃣ | [`02-emr-permissions-setup.md`](./02-emr-permissions-setup.md) | 🔑 EMR ke liye roles + permissions (do role: service + EC2) — warna cluster banega hi nahi |
| 3️⃣ | [`03-cluster-banana.md`](./03-cluster-banana.md) | 🅱️ Ek chhota EMR cluster banana (step-by-step) — ya bas padh ke samajhna |
| 4️⃣ | [`04-spark-job-chalana.md`](./04-spark-job-chalana.md) | 🅱️ Ek simple Spark job (word count) chalana + output dekhna |
| 5️⃣ | [`05-cluster-terminate-verify.md`](./05-cluster-terminate-verify.md) | 🚨 **SABSE ZAROORI:** cluster **turant terminate** karna (warna bada bill) + verify |
| 6️⃣ | [`06-checklist-aur-galtiyan.md`](./06-checklist-aur-galtiyan.md) | Checklist + terms + **Glue vs EMR** + galtiyan + permissions + **cleanup (bill se bacho)** |

> 💡 Agar tum 🅰️ (safe) raasta chun rahe ho, to sirf **File 1** aur **File 6** padho — baaki (2-5) tab ke liye jab hands-on karna ho.

---

## 🧠 Ek Line Me Aaj Ka Din

> "EMR = jab data itna **bada** ho ki ek computer kam pade, to **bahut saari machine ki team (cluster)** kaam **baant ke** ek saath karti hai (Spark). Par ye team **har ghante paisa** leti hai — kaam ke baad **turant terminate**."

---

## 🔑 Aaj Ke Naye Shabd (Box Me Detail Me — File 1)

- **Big Data** — itna bada data ki ek machine se sambhalna mushkil
- **Cluster** — bahut saari machine ek saath, ek team ki tarah
- **Node** — team ka ek member (ek machine) — Master / Core / Task
- **Spark** — kaam ko baant ke tez chalane wala engine (aaj ka star)
- **MapReduce** — kaam baant ke (Map) phir jod ke (Reduce) karne ka purana tareeka
- **Hadoop / HDFS** — bade data ko kai machine pe baant ke rakhne wala system
- **EMR** — AWS ka wo service jo ye poora cluster **khud bana ke** deta hai

---

## ✅ Aaj Ka Target

Din ke end me tum bata sako:
- **EMR kya hai, kyun chahiye, aur Glue se kaise alag hai** ✅
- (🅱️ waale) ek chhota cluster + Spark job chala ke **turant terminate** kiya ✅
- Aur bill safe rakha ✅

> Chalo, File 1 se shuru karo → [`01-emr-kya-hai-concept.md`](./01-emr-kya-hai-concept.md) 🚀
