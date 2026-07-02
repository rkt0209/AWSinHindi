# 5️⃣ Billing Alert Lagao — Paise Safe 💰

> AWS "jitna use utna paisa" hai. Galti se koi cheez chalti reh jaye to bill aa sakta hai.
> Isliye ek **alarm** laga do — ₹ cross ho to turant email aa jaye. Tension khatam.

📖 Billing alarm docs: https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html
📖 AWS Budgets docs: https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-create.html

---

## 🤔 Kyun Zaroori?

**Real-life example:** Mobile me tumne data-limit alert lagaya hota hai — "1GB khatam hone wala hai". Waisa hi yahan: "paisa ₹80 cross hone wala hai" ka alert. Bill kabhi surprise nahi karega. 😌

Hum 2 cheezein karenge:
1. **Billing alerts ON** karo (ek baar ka setting).
2. **AWS Budget** banao — jaise "₹100 se zyada ho to email bhejo".

> ℹ️ **Note:** Billing/Budget cheezein **root user** se best set hoti hain (IAM user ko permission alag se deni padti hai). Ye setup ke liye **root se login** kar lo, phir wapas IAM par aa jaana.

---

## 🪜 PART A — Billing Alerts ON Karo

### Step 1 — Billing Preferences Kholo
- 🔍 search me `Billing` type karo → **"Billing and Cost Management"** kholo.
- Left menu me **"Billing preferences"** pe click.

### Step 2 — Alerts Chalu Karo
- **"Alert preferences"** section me **"Edit"** dabao.
- **"Receive AWS Free Tier alerts"** pe ✅ tick karo (Free Tier limit paas aate hi email).
- Ek email daalo jahan alert chahiye.
- **"Receive CloudWatch billing alerts"** pe bhi ✅ tick karo.
- **Save** dabao.

**🖥️ Screen pe:** "Preferences updated" ✅

---

## 🪜 PART B — Ek Budget Banao (₹ Limit Alert)

### Step 1 — Budgets Kholo
- Billing page ke left menu me **"Budgets"** → **"Create budget"** dabao.

### Step 2 — Budget Set Karo
- **"Use a template (simplified)"** chuno.
- Template me **"Monthly cost budget"** ya **"Zero spend budget"** chuno.
  - *Zero spend budget* = jaise hi ₹0 se upar kuch bhi kharcha ho, email aa jaye (Free Tier ke liye best!).
- **Budget name:** koi bhi (jaise `Mera-Kharcha-Alert`).
- **Amount:** jaise `100` (₹ ya $ jo dikhe — beginner ke liye chhota rakho).
- **Email:** apni email daalo (yahin alert aayega).
- **"Create budget"** dabao.

**🖥️ Screen pe:** Budget list me tumhara budget dikhega. Ab limit cross hote hi **email** aa jayega. ✅

---

## 🪜 PART C — Roz Ki Aadat (Sabse Bada Bachav)

Alert to backup hai. **Asli bachav ye aadatein hain:**

1. **Practice ke baad banaya hua sab delete/stop karo:**
   - S3 me daali test files → delete.
   - Lambda function → zaroorat na ho to delete.
   - **EMR cluster → kaam ke turant baad TERMINATE** (ye sabse mehnga, bhoolna mat!).
2. **Ek hi Region** me kaam karo — warna cheezein alag-alag jagah chhoot jaati hain aur bill banati hain.
3. **Hafte me ek baar** Billing page kholo → "kितna kharcha hua" dekho (aadat daalo).

---

## ⚠️ Cases / FAQ

| Sawaal / Case | Jawab |
|---------------|-------|
| **"Free Tier me bhi paise kat sakte hain?"** | Haan, agar limit cross ki (jaise EMR chalta chhod diya). Isliye alert + delete ki aadat. |
| **Budget banane pe "Access Denied"** | IAM user se try kar rahe ho — root se karo, ya IAM user ko Billing permission do. |
| **Alert email nahi aaya** | Kharcha limit cross hi nahi hua (achhi baat). Test ke liye limit bahut chhoti (jaise ₹1) rakh ke dekh sakte ho. |
| **Card se ₹2/₹15 kata** | Wo sirf account-verification tha, refund ho jaata hai — bill nahi. |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Billing alerts ON (Free Tier + CloudWatch)
- [ ] Ek Budget bana diya (email ke saath)
- [ ] Samajh gaye: banaya hua cheez delete/stop karni hai (khaaskar EMR)

> ➡️ Ab last file: pura Din 1 checklist + har error ka solution → [`06-checklist-aur-galtiyan.md`](./06-checklist-aur-galtiyan.md)
