# 3️⃣ Din-Ba-Din 10 Din Ka Plan 🗓️

> Har din ka **theme, kya karna hai, kya banana hai (hands-on), aur "ho gaya" ka check** diya hai.
> Roz **3–4 ghante** kaafi hain. Jaldbaazi nahi — samajhna important hai.

> ⚠️ **Paise ka dhyaan:** AWS **Free Tier** account banao. Practice ke baad jo banaya use **delete/stop** kar dena (warna chhota bill aa sakta hai). Roz ke kaam me dhyaan rakhna.

---

## 📅 DIN 1 — Neenv: Cloud + AWS + IAM 🔑

**Theme:** "Pehle ghar me ghusna seekho." Account, login, permission.

**Kya samajhna hai:**
- Cloud kya hai (File 1 ka municipality wala example).
- AWS Console (website) kaise dikhti hai, "Region" kya hota hai (data kis sheher me rakha hai).
- **IAM** — User, Role, Permission. (Kis ko kis cheez ki chaabi mili hai.)

**Hands-on (karke seekho):**
1. AWS **Free Tier account** banao (card lagega par free tier me paise nahi katenge agar dhyaan rakho).
2. Root account ki jagah ek **IAM user** banao apne liye.
3. Us user ko **S3 ki permission** do (next day kaam aayega).

**✅ Ho Gaya Check:** Tum apne IAM user se login kar paa rahe ho, aur samajh gaye ki "Region" aur "permission" kya hai.

**📚 Aaj ke padhne ke links:**
- AWS Free Tier account banao → https://aws.amazon.com/free/
- IAM Getting Started → https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started.html
- Regions kya hote hain → https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html
- AWS Skill Builder (free courses) → https://skillbuilder.aws/

---

## 📅 DIN 2 — S3: Internet Ka Godown 🗄️

**Theme:** "File rakhna aur nikaalna seekho — sabki neenv."

**Kya samajhna hai:**
- Bucket vs Object vs Key (File 1 ka godown example).
- File upload/download, folder structure.
- Permission — bucket public/private kaise hota hai (security!).

**Hands-on:**
1. Ek **bucket** banao (jaise `mera-pehla-bucket-2026`).
2. Usme ek **CSV/Excel ya photo** upload karo.
3. Download karo, delete karo, dobara upload karo.
4. Ek folder structure banao: `raw-data/` aur `clean-data/` (aage kaam aayega).

**✅ Ho Gaya Check:** Tum aankh band karke bucket bana ke file daal-nikaal sakte ho.

**📚 Aaj ke padhne ke links:**
- S3 kya hai (overview) → https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html
- S3 Getting Started (bucket + file) → https://docs.aws.amazon.com/AmazonS3/latest/userguide/GetStartedWithS3.html
- Bucket ki security/permission → https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-overview.html

---

## 📅 DIN 3 — Lambda: Automatic Naukar ⚡

**Theme:** "Chhota kaam jo apne aap event pe ho jaaye."

**Kya samajhna hai:**
- Event-driven matlab kya (button dabao → kaam ho — vending machine).
- Trigger kya hota hai (jaise "S3 me file aayi to Lambda chalao").
- Lambda function ka basic structure (input aata hai, kaam, output).

**Hands-on:**
1. Ek simple Lambda banao jo "Hello, intern!" return kare (Python ya Node.js — jo aata ho).
2. Use **test** karo console se.
3. (Advance) S3 trigger lagao: "Jab `raw-data/` me file aaye, Lambda chale aur uska naam print kare."

**✅ Ho Gaya Check:** Tumhara Lambda chal raha hai aur tum samajh gaye "trigger" kya hai.

**📚 Aaj ke padhne ke links:**
- Lambda kya hai → https://docs.aws.amazon.com/lambda/latest/dg/welcome.html
- Lambda Getting Started → https://docs.aws.amazon.com/lambda/latest/dg/getting-started.html
- S3 trigger se Lambda chalana (tutorial) → https://docs.aws.amazon.com/lambda/latest/dg/with-s3-example.html

---

## 📅 DIN 4 — Glue: Data Ki Safai 🧹

**Theme:** "Kache gande data ko saaf aur taiyaar karna (ETL)."

**Kya samajhna hai:**
- **ETL** = Extract (uthao) → Transform (saaf/badlo) → Load (rakho).
- **Glue Data Catalog** = data ka register/index (kaunsa data kahan).
- **Crawler** = ek robot jo S3 me data dekhta hai aur catalog bana deta hai.

**Hands-on:**
1. Din 2 wale CSV ko `raw-data/` me rakho.
2. Ek **Glue Crawler** chalao jo us data ko padhe aur **catalog** bana de.
3. Ek chhota **Glue Job** banao jo data saaf kare (jaise khaali rows hatao) aur `clean-data/` me daal de.

**✅ Ho Gaya Check:** Tumhara kacha data saaf hoke `clean-data/` me pahunch gaya, aur catalog me table dikh raha hai.

**📚 Aaj ke padhne ke links:**
- Glue kya hai → https://docs.aws.amazon.com/glue/latest/dg/what-is-glue.html
- Glue Data Catalog samajho → https://docs.aws.amazon.com/glue/latest/dg/start-data-catalog.html
- Crawler kaise banaye → https://docs.aws.amazon.com/glue/latest/dg/add-crawler.html

---

## 📅 DIN 5 — EMR + Big Data Basics 🏭

**Theme:** "Bahut bada data — mazdooro ki team se."

**Kya samajhna hai:**
- Bada data kyun ek computer se nahi hota (pahaad hatane wala example).
- **Cluster** kya hai (bahut computers ek saath).
- **Spark / MapReduce** ka basic idea (kaam baant ke karna).
- **Glue vs EMR** kab kya use kare.

**Hands-on (halka rakho, ye heavy hai):**
1. EMR ka concept video/doc padho (account me cluster banana mehnga ho sakta hai — pehle sirf samajh lo).
2. Agar himmat ho: ek **chhota EMR cluster** banao, ek simple Spark job chalao (jaise ek bade file me words count karo), phir **cluster turant terminate karo** (paise bachao!).
3. Nahi to: bas concept aur "kab use hota hai" samajh lo — intern ke liye itna kaafi.

**✅ Ho Gaya Check:** Tum bata sakte ho "EMR kyun, kab, aur Glue se kaise alag hai."

**📚 Aaj ke padhne ke links:**
- EMR kya hai → https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html
- EMR Getting Started → https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-gs.html
- EMR pe Spark → https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark.html

---

## 📅 DIN 6 — Step Functions: Manager 🔀

**Theme:** "Sab kaamo ko sahi order me chalana."

**Kya samajhna hai:**
- **State Machine** = flowchart/naqsha (abhi kaunse step pe hain).
- Steps ko jodna: "pehle ye → phir ye → agar error to ye."
- **Lambda ko Step Functions se call karna.**
- Error handling, Retry (fail ho to dobara try).

**Hands-on:**
1. Do chhote Lambda banao: ek "order lo", doosra "order confirm karo".
2. Ek **Step Function** banao jo pehle pehla Lambda chalaye, phir doosra.
3. **Visual flow** (graph) dekho console me — kaise ek box se doosre box ja raha hai.
4. Ek step me jaan ke error daalo aur dekho **Retry/Catch** kaise kaam karta hai.

**✅ Ho Gaya Check:** Tumhara Step Function 2 Lambda ko order me chala raha hai, aur tum visual graph samajh paa rahe ho.

**📚 Aaj ke padhne ke links:**
- Step Functions kya hai → https://docs.aws.amazon.com/step-functions/latest/dg/welcome.html
- Step Functions Getting Started → https://docs.aws.amazon.com/step-functions/latest/dg/getting-started-with-sfn.html
- Error handling (Retry/Catch) → https://docs.aws.amazon.com/step-functions/latest/dg/concepts-error-handling.html

---

## 📅 DIN 7 — APIs through Step Functions 🌐

**Theme:** "Bahar se request lekar pura flow chalana."

**Kya samajhna hai:**
- API / API Gateway kya hai (waiter + main darwaza wala example).
- **REST API** basics — GET (data lo), POST (data bhejo).
- API Gateway ko **Step Functions se jodna** — bahar se request aaye, manager chale, jawab wapas jaaye.

**Hands-on:**
1. **API Gateway** me ek simple API banao.
2. Use Din 6 wale **Step Function se connect** karo.
3. Browser/Postman se request bhejo → dekho Step Function chala → response wapas aaya.
4. (Bonus) Postman tool seekh lo — APIs test karne ka standard tool hai.

**✅ Ho Gaya Check:** Tum bahar se (Postman) request bhej ke pura Step Function chala paa rahe ho aur response mil raha hai.

**📚 Aaj ke padhne ke links:**
- API Gateway kya hai → https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html
- API Gateway Getting Started → https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started.html
- API Gateway + Step Functions jodna → https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started-with-stepfunctions.html
- Postman tool → https://www.postman.com/

---

## 📅 DIN 8 — Spec & Steering Files (AI / Agentic Dev) 🤖

**Theme:** "AI ko sahi se guide karke code likhwana."

**Kya samajhna hai:**
- **Spec file** = AI ko batao **kya banana hai** (Requirements → Design → Tasks).
- **Steering file** = AI ko **permanent rules + context** do (coding style, libraries, naming).
- Agentic development matlab kya — AI khud plan banake step-by-step code likhe.
- (Optional) AWS ka **Kiro** tool dekho — ye isi pe based hai.

**Hands-on:**
1. Ek chhote project ka **spec** likho: "Ek to-do list app banao" — requirements, design, tasks alag-alag.
2. Ek **steering file** likho: "Hamesha Python use karo, function ke naam chhote rakho, comments Hindi me."
3. Kisi AI tool (jaise Claude/Kiro) se in files ke saath code likhwao — aur **bina** files ke bhi. **Farak dekho.**

**✅ Ho Gaya Check:** Tum samajh gaye ki spec/steering se AI zyada accurate aur consistent code deta hai.

**📚 Aaj ke padhne ke links:**
- Kiro (AWS ka agentic IDE) → https://kiro.dev/
- Spec files samajho → https://kiro.dev/docs/specs/
- Steering files samajho → https://kiro.dev/docs/steering/

---

## 📅 DIN 9 — Mini Project: Sabko Jodo 🛠️

**Theme:** "Aaj sab cheezein ek saath use karo — ek chhota real project."

**Project idea:** *"Daily Sales Report Banane Wala System"* (File 4 me iska pura flow hai — wahin se follow karo).

**Karna kya hai:**
1. S3 me ek sales CSV daalo (raw-data).
2. Lambda/Glue se use saaf karo (clean-data).
3. Step Functions se pura order chalao.
4. API Gateway se "report do" request banao.
5. Test karo end-to-end.

**✅ Ho Gaya Check:** Ek chhota system khud banaya jahan **5 cheezein milke** kaam kar rahi hain. (Confidence ++)

**📚 Aaj ke padhne ke links:**
- AWS hands-on Workshops (free practical labs) → https://workshops.aws/
- Serverless data pipeline example → https://aws.amazon.com/serverless/

---

## 📅 DIN 10 — Revision + Day-1 Ki Taiyaari 🎯

**Theme:** "Sab dohrao, confidence banao, sawaal taiyaar karo."

**Karna kya hai:**
1. File 1 (concepts) aur File 4 (flow) dobara padho — ek baar me sab connect ho jayega.
2. Har cheez ka **ek-line example** zubaani bolo (jaise dost ko samjha rahe ho).
3. **Sawaal likho** jo Day 1 pe team se pooch sako (ye accha impression banata hai!).
4. Apne resume/notes me likho "main ye sab basic level pe jaanta hoon."
5. Aaram karo — fresh dimaag se join karna best hai. 😌

**✅ Ho Gaya Check:** Tum aankh band karke pura flow bata sakte ho. Ready for Day 1! 🚀

**📚 Aaj ke padhne ke links:**
- File 1 (concepts) aur File 4 (final flow) dobara padho — isi folder me hain.
- AWS Skill Builder pe revision quiz → https://skillbuilder.aws/

---

## 🧾 Quick Summary Table

| Din | Theme | Main Cheez |
|-----|-------|-----------|
| 1 | Neenv | AWS + IAM (login + permission) |
| 2 | Storage | S3 (godown) |
| 3 | Chhota kaam | Lambda (vending machine) |
| 4 | Data safai | Glue (ETL) |
| 5 | Bada data | EMR (mazdooro ki team) |
| 6 | Manager | Step Functions (flowchart) |
| 7 | Bahar ki request | APIs + API Gateway |
| 8 | AI guide | Spec & Steering files |
| 9 | Sab jodo | Mini Project |
| 10 | Dohraav | Revision + Day-1 prep |

> ➡️ Ab File 4 kholo — **pura real-life flow** jisme sab cheezein milke kaam karti hain. (Sabse zaroori file!)
