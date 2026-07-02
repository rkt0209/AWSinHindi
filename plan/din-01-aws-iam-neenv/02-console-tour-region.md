# 2️⃣ AWS Console Ki Tour + Region Samjho

> Ab tum andar aa gaye ho. Chalo ghar (console) ghum ke dekho —
> kaunsi cheez kahan hai, taaki aage kabhi kho na jao.

📖 Region docs: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html

---

## 🗺️ Console Ka Naksha — Kya Kahan Hai

Jab tum login karte ho, screen kuch aisi dikhti hai:

```
┌───────────────────────────────────────────────────────────────┐
│ [AWS logo] [🔍 Search bar........]   [🔔]  [Mumbai ▾]  [Account ▾]│  ← UPAR WALI PATTI (top bar)
├───────────────────────────────────────────────────────────────┤
│                                                                 │
│   Console Home                                                  │
│   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │
│   │ Recently    │  │ Applications│  │ Cost & usage│  ← boxes    │
│   │ visited     │  │             │  │             │  (widgets)  │
│   └─────────────┘  └─────────────┘  └─────────────┘             │
│                                                                 │
└───────────────────────────────────────────────────────────────┘
```

### Top bar ke 4 sabse zaroori hisse:

| Kahan (position) | Kya hai | Kaam |
|------------------|---------|------|
| **Left me logo** | AWS logo | Kabhi bhi ispe click → wapas Console Home |
| **Beech me 🔍 Search** | Search bar | **Sabse important!** Yahan koi bhi service ka naam type karo (S3, Lambda, IAM) → seedha wahan pahunch jao |
| **Right me sheher ka naam** | Region selector | Data kis sheher me — jaise "Mumbai" |
| **Sabse right** | Account menu | Tumhara account, billing, logout yahan |

---

## 🔍 Search Bar — Tumhara Sabse Bada Dost

AWS me **200+ services** hain. Menu me dhundhne ki zaroorat nahi.

**Kaise use karo:** Upar 🔍 me service ka naam likho, dropdown me aayega, click karo.

**Practice karo abhi:**
1. Search me `S3` type karo → "S3" dikhega → **abhi click mat karo, bas dekho**.
2. Search me `IAM` type karo → "IAM" dikhega.
3. Search me `Billing` type karo → "Billing and Cost Management" dikhega.

> 💡 Aage har din hum bolenge "search me ye type karo" — bas yahi search bar hai.

---

## 🌍 Region Kya Hai? (Bahut Zaroori — Confusion Yahin Hota Hai)

**Real-life example:** Socho tumhare paas alag-alag sheharo me **lockers** hain — ek Mumbai me, ek Singapore me. Jo Mumbai wale locker me rakhoge, wo **sirf Mumbai** wale me dikhega, Singapore me nahi.

**AWS me bhi waisa hi:**
- AWS ke data centers duniya ke alag-alag **sheharo (Regions)** me hain.
- Jab tum koi cheez banate ho (file, function), wo **ek Region** me banti hai.
- **Agar Region badal doge, to purani cheezein "gayab" dikhengi** (wo doosre sheher me hain, delete nahi huin).

### 👉 Kya Karna Hai:
- Top-right me Region dropdown kholo.
- **`Asia Pacific (Mumbai) ap-south-1`** chuno (India ke liye — fast aur sasta).
- **Ab poore Din 1–10 isi Region me kaam karna.** Badalna mat.

**🖥️ Screen pe:** Top-right me ab "Mumbai" ya "ap-south-1" likha dikhega.

> ⚠️ **Sabse common galti:** File Mumbai me banaya, baad me Region galti se "N. Virginia" ho gaya, ab file nahi dikh rahi → "mera data delete ho gaya!" 😱
> **Sach:** Data safe hai, bas galat sheher me dekh rahe ho. **Region wapas Mumbai karo, sab dikh jayega.**

> ⚠️ **Exception:** Kuch cheezein "global" hoti hain (jaise **IAM** aur **Billing**) — ye har Region me same dikhti hain, inke liye Region matter nahi karta. Baaki sab (S3 files, Lambda) Region-wise hoti hain.

---

## 🧭 Ek Chhoti Practice (5 Min)

1. Region ko Mumbai set karo. ✅
2. Search bar me `EC2` type karke kholo → upar-right dekho, Region "Mumbai" hona chahiye.
3. Ab Region ko galti se "Singapore" karo → dekho sab khali. Phir wapas Mumbai karo. **Ye "gayab-wapas" wala khel khud dekh lo** — taaki aage kabhi na ghabrao.

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Search bar use karna aa gaya
- [ ] Region ko Mumbai set kar diya
- [ ] Samajh gaye: "Region badalne se cheezein gayab dikhti hain, delete nahi hotin"
- [ ] IAM/Billing global hain, ye pata chal gaya

> ➡️ Ab File 3: Root account pe security (MFA) lagao → [`03-root-security-mfa.md`](./03-root-security-mfa.md)
