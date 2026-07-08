# 3️⃣ Ek Chhota EMR Cluster Banao (Team Khadi Karo) 🏗️

> ⚠️ Ye **🅱️ hands-on** step hai — isme **paisa lagता hai** (cluster chalu hote hi meter start). 🅰️ waale sirf padh ke samajh lo.
> 🚨 **Golden rule:** jaise hi kaam ho, **turant terminate** (File 5). Cluster chhota rakho.

📖 Cluster banana (Getting Started): https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-gs.html

---

## 🧭 Step 0 — EMR Console Kholo

- AWS Console → search me `EMR` → **Amazon EMR** pe click.
- Region **Mumbai (ap-south-1)** check karo (upar-right). S3 data bhi isi region me ho.

**🖥️ Screen pe:** EMR home — left me **"Clusters"**, upar **"Create cluster"** button.

> ⚠️ **Yaad rakho:** ye sabse mehnga service hai. Chhota cluster + jaldi terminate = chhota bill.

---

## 🪜 Step 1 — Create Cluster Shuru

- **"Create cluster"** dabao. Ek form khulega (naam, software, machine, roles).

---

## 🪜 Step 2 — Naam aur Software

- **Cluster name**: `mera-chhota-cluster`
- **Amazon EMR release**: latest jo default aaye (jaise `emr-7.x`) rehne do.
- **Application bundle**: **Spark** wala option chuno (ya "Spark" tick karo).

> 📦 **Ye Kya Hai: Application bundle** — cluster pe **kaunse software** pehle se install honge (Spark, Hadoop, Hive...). Hum **Spark** chahiye (aaj ka kaam), isliye Spark wala chuno. **Example:** naya laptop lete waqt "kaunse app pre-install ho" chunna.

---

## 🪜 Step 3 — Cluster Machine (Sabse Zaroori — Paisa Yahi Se)

**"Cluster configuration"** me machine (node) chuno. **Chhota rakho:**

- **Instance type**: sabse chhota/sasta jo mile — jaise **`m5.xlarge`** (ya list me sabse chhota general-purpose).
- **Number of instances / Core**: **1 Master + 1 Core** kaafi hai practice ke liye. (Task node **0** — zaroorat nahi.)

> 📦 **Ye Kya Hai: Instance type** — machine kitni **badi/powerful** hai (CPU + RAM) uska naam. Badi machine = tez, par **zyada paisa/ghanta**. **Example:** chhoti gaadi vs bada truck kiraye pe — truck mehnga. Practice me chhoti hi lo. 🚗

> ⚠️ **Paisa dhyaan:** har node ek EC2 (kiraye ki machine). 2 machine × per-ghanta rate = tumhara bill. Isliye **kam se kam machine** + **turant terminate**.

---

## 🪜 Step 4 — Roles (Wardi Chuno)

**"Security and permissions"** / roles section me:
- **Service role**: `EMR_DefaultRole` chuno — ya **"Create a default role"** dabao (File 2 Tareeka A).
- **Instance profile (EC2 role)**: `EMR_EC2_DefaultRole` chuno — ya default create.

> 🔑 **Permission yaad (File 2):** ye dono role na ho / na chuno → cluster **banega hi nahi** ya S3 pe Access Denied aayega. Auto-create aasaan hai.

> 💡 **EC2 key pair** maange to abhi **skip/none** kar sakte ho (hum SSH se login nahi karenge; job console/Steps se chalayenge). Chaho to ek key pair bana lena, koi extra charge nahi.

---

## 🪜 Step 5 — Review aur Create

- Sab dekh lo (naam, Spark, 1+1 machine, dono role) → **"Create cluster"** dabao.

**🖥️ Screen pe:**
- Cluster ka status **"Starting"** ⏳ → phir **"Running" / "Waiting"** (5–10 min lagta hai — machine boot ho rahi).
- 🚨 **Yaad rakho:** "Starting" hote hi **meter chalu** ho gaya. Kaam ho → turant terminate.

> 📦 **Ye Kya Hai: "Waiting" status** — cluster **taiyaar hai aur khali baitha** hai, tumse kaam (Step/job) ka wait kar raha. **Waiting me bhi paisa lagता hai** (machine chalu hai). Isliye taiyaar hote hi jaldi job chala ke (File 4) terminate karo.

---

## ⚠️ Common Cases / Errors

| Case | Solution |
|------|----------|
| **"Create cluster" pe role error** | File 2 ke dono role (service + EC2) chuno / "Create default roles". |
| **`iam:PassRole` denied** | User ko `IAMFullAccess` (Layer 1). |
| **EC2 limit / capacity error** | Doosra chhota instance type chuno; ya kam machine. |
| **Cluster "Terminated with errors"** | Logs dekho (S3 log path); aksar role/permission ya instance-type issue. |
| **Bahut der "Starting"** | Normal (5-10 min). 20+ min atke to terminate karke dobara. |
| **Region alag** | EMR + S3 dono Mumbai. |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] `mera-chhota-cluster` bana (Spark, chhoti machine, 1 Master + 1 Core)
- [ ] Dono role (service + EC2) chune/auto-create hue
- [ ] Status **Running/Waiting** aa gaya
- [ ] Dimaag me note: **meter chalu hai → jaldi kaam + terminate**

> ➡️ Ab ek chhota Spark job chalao → [`04-spark-job-chalana.md`](./04-spark-job-chalana.md) ⚡
> ⏱️ (Jaldi karo — cluster khali chalega to bekaar paisa lagega.)
