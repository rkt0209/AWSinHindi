# 5️⃣ 🚨 Cluster TURANT Terminate Karo (Warna Bada Bill) 🛑

> **Ye file poore Din 6 ki sabse zaroori file hai.** EMR cluster chalu rehne bhar se **har ghante paisa**
> leta hai — chahe tum kuch kar rahe ho ya nahi. Kaam ho gaya? **Abhi band karo.** ⏱️💸

📖 Cluster terminate karna: https://docs.aws.amazon.com/emr/latest/ManagementGuide/UsingEMR_TerminateJobFlow.html

---

## 🤔 Pehle Samjho — "Terminate" Kya Aur Kyun Turant?

### 📦 Ye Kya Hai: **Terminate (Cluster Band Karna)**
**Definition:** Terminate = cluster ki **saari machine (EC2 nodes) band + chhod dena** — team ko "ghar bhej dena." Iske baad cluster ka **paisa lagna band** ho jaata hai (jo data S3 me hai wo safe rehta, sirf machine jaati hai).

**Example:** Kiraye pe li gaadi/mazdoor **wapas kar do** — meter/majdoori ruk jaati. Gaadi khadी rakhoge to meter chalta rahega. 🚕🛑

> 🚨 **Yaad rakho:** cluster **"Waiting" (khali baitha)** ho tab bhi **paisa lag raha hai** (machine chalu hai). Isliye job Completed hote hi **turant terminate**. "Baad me kar dunga" = bill badhता rehta.

---

## 🛑 Step 1 — Cluster Terminate Karo

1. EMR → **Clusters** → `mera-chhota-cluster` select karo.
2. Upar **"Terminate"** button dabao.
3. Confirm karo (agar **"Termination protection ON"** hai to pehle usse **OFF** karo, phir terminate).

**🖥️ Screen pe:**
- Status **"Terminating"** ⏳ → thodi der me **"Terminated"** ✅.
- Bas! Ab is cluster ka **paisa lagna band**. 🎉

> 📦 **Ye Kya Hai: Termination Protection** — ek "galti se band na ho jaye" wala **lock**. ON ho to seedhe terminate nahi hota (pehle lock hataao). Practice cluster me isse **OFF** rakhna aasaan (taaki turant band kar sako).

---

## 🔍 Step 2 — Verify (Sach Me Band Hua?)

Bill se bachne ke liye **confirm** karo:

- [ ] **EMR → Clusters** me `mera-chhota-cluster` ka status **"Terminated"** dikh raha (Running/Waiting **nahi**).
- [ ] **EC2 console** → **Instances** kholo → dekho koi EMR wali machine **"running"** to nahi (thodi der me sab **"terminated"** ho jaani chahiye). ⬅️ Ye **sabse pakka** check hai (kyunki asli paisa EC2 machine ka hai).

> 💡 EMR cluster terminate karte hi uski EC2 machine bhi apne-aap band ho jaati hain. Fir bhi EC2 me ek nazar daal lena — **peace of mind**.

---

## 🧹 Step 3 — Baaki Cleanup (Bill Se Poora Bacho)

Cluster band ho gaya, par kuch chhoti cheezein bacha reh sakti hain:

### 1️⃣ S3 Ke Test Data / Output
- `emr-input/` (words.txt, wordcount.py) aur `emr-output/result1/` — **jaroorat na ho to delete** kar do (chhoti storage cost).

### 2️⃣ EMR Logs (S3 Me)
- Cluster ne logs ka ek S3 folder banaya ho sakta (jaise `aws-logs-.../elasticmapreduce/`) → **delete** kar do (storage bachega).

### 3️⃣ EC2 Key Pair (Agar Banaya Tha)
- Cluster ke liye key pair banaya tha to **rakh sakte ho** (koi charge nahi) ya EC2 → Key Pairs se delete.

---

## ✋ Ye MAT Delete Karo (Aage Kaam Aayega)

- **S3 bucket** aur **`raw-data/sales.csv`** — Din 9 mini-project me kaam aayega.
- **IAM user `rohit-iam-dev`** aur uski permissions — roz chahiye.
- **`EMR_DefaultRole` + `EMR_EC2_DefaultRole`** — rakh lo (role rakhne ka **koi charge nahi**), dobara EMR karo to kaam aayenge. Nahi chahiye to IAM → Roles se delete.
- **`glue-mera-role`** (Din 4) — rakho, aage kaam aa sakta.

---

## ⚠️ Common Cases / Errors

| Case | Solution |
|------|----------|
| **Terminate button disabled** | **Termination protection OFF** karo, phir terminate. |
| **Status bahut der "Terminating"** | Thoda wait; machine band ho rahi. Zyada der to refresh/check EC2. |
| **EC2 me machine abhi "running"** | Thodi der do; na ho to EC2 se un instances ko manually **terminate** karo. |
| **Galti se cluster fir ban gaya** | EMR me koi auto-scaling/step-loop nahi; naya "Create" hi banata. Terminate rakho. |
| **Bill me EMR/EC2 dikh raha** | 1-2 din baad **Cost Explorer** me confirm; machine terminated honi chahiye. |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Cluster status **Terminated** ✅
- [ ] EC2 me EMR wali machine **running nahi** (verify)
- [ ] S3 ke test input/output/logs delete kiye
- [ ] Bucket, IAM user, roles — **NAHI** delete kiye
- [ ] Samajh gaye: **Waiting me bhi paisa lagता → turant terminate**

> 🧾 **Confirm:** 1-2 din baad **Billing → Cost Explorer** me "EMR"/"EC2" ka charge dekh lena — chhota + rukا hua hona chahiye.

> ➡️ Ab final: checklist + Glue-vs-EMR + galtiyan + cleanup summary → [`06-checklist-aur-galtiyan.md`](./06-checklist-aur-galtiyan.md) 🧾
