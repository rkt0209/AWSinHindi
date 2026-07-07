# 2️⃣ Kya Pehle, Kya Baad Me? — Dependency Map

> "Pehle aata seekhna padta hai, tabhi roti banti hai."
> Yahan samjhenge **kaunsi cheez kis pe depend karti hai**, taaki sahi order me seekho aur kahin atko nahi.

---

## 🪜 Seekhne Ki Seedhi (Ladder) — Neeche Se Upar

```
                 ┌─────────────────────────────────────┐
   LEVEL 5  →    │  APIs through Step Functions         │  (sabse upar)
                 │  (bahar se request leke pura flow)   │
                 └──────────────────▲──────────────────┘
                                    │ depends on
                 ┌──────────────────┴──────────────────┐
   LEVEL 4  →    │  Step Functions (Manager)            │
                 │  Lambda + Glue + EMR ko jodta hai    │
                 └──────────────────▲──────────────────┘
                                    │ depends on
        ┌───────────────┬───────────┴────────┬──────────────────┐
LEVEL 3 │   Lambda      │      Glue          │      EMR          │
        │ (chhota kaam) │  (data safai)      │  (bada data)      │
        └───────▲───────┴─────────▲──────────┴────────▲──────────┘
                │                  │                   │  sab depend karte hain
                └──────────────────┼───────────────────┘
                                   │
                 ┌─────────────────┴───────────────────┐
   LEVEL 2  →    │  S3 (Godown) — sabka data yahin     │
                 └─────────────────▲───────────────────┘
                                   │ depends on
                 ┌─────────────────┴───────────────────┐
   LEVEL 1  →    │  AWS Basics + IAM (account, login,   │  (neenv / foundation)
                 │  permissions) + Cloud kya hai        │
                 └─────────────────────────────────────┘


   🤖 ALAG TRACK (parallel me seekh sakte ho):
        Spec & Steering Files (AI/Agentic dev) — AWS pe depend nahi karta
```

---

## 🔢 Order Kyun Aisa Hai? (Har Step Ka Logic)

### Level 1 — AWS Basics + IAM 🔑 (SABSE PEHLE, ye neenv hai)
- **Kya:** AWS account, console (website) kaise chalti hai, aur **IAM** (kis ko kis cheez ki permission hai).
- **Kyun pehle:** Ghar me ghusne ke liye **chaabi (login + permission)** chahiye na? Bina IAM samjhe har jagah "Access Denied" aayega aur tum confuse hoge.
- **Real-life:** Office me joining pe pehle **ID card + access** milta hai, tabhi tum kisi room me ghus paate ho.

### Level 2 — S3 🗄️ (NEENV KA AGLA PATTHAR)
- **Kya:** File rakhna, nikaalna, folders/buckets banana.
- **Kyun yahan:** **Baaki sab cheezein S3 ka data use karti hain.** Lambda S3 se file uthata hai, Glue S3 ka data saaf karta hai, EMR S3 ka bada data padhta hai.
- **Depends on:** Level 1 (account + permission chahiye S3 use karne ko).

### Level 3 — Lambda, Glue, EMR ⚙️ (TEEN "KAAM KARNE WALE")
Ye teeno **S3 pe depend** karte hain (data wahin se aata-jaata hai). Inko **kisi bhi order** me seekh sakte ho, par suggested:
1. **Lambda pehle** — sabse aasaan, chhota concept, jaldi samajh aata hai.
2. **Glue doosra** — Lambda samajhne ke baad ETL ka concept easy lagta hai.
3. **EMR teesra** — sabse heavy (Spark/big data), isliye end me.
- **Depends on:** S3 (Level 2) + IAM (Level 1).

### Level 4 — Step Functions 🔀 (MANAGER — INKO JODNE WALA)
- **Kyun yahan:** Manager tabhi kaam baant sakta hai jab **kaam karne wale (Lambda, Glue, EMR) ko tum pehle se jaante ho.** Pehle "workers" samjho, phir "manager".
- **Depends on:** Level 3 (kam se kam Lambda zaroor aana chahiye).

### Level 5 — APIs through Step Functions 🌐 (SABSE UPAR)
- **Kyun last:** Ye **bahar ki duniya (user/internet) ko** tumhare pure system se jodta hai. Iske liye Step Functions (manager) pehle samajhna zaroori hai.
- **Depends on:** Level 4 (Step Functions) + thoda API basics.

### 🤖 Alag Track — Spec & Steering Files
- **Kab seekho:** Kabhi bhi! Ye **AWS data-stack pe depend nahi karta.** Ye AI se code likhwane ka tareeka hai.
- **Suggestion:** Beech me 1 din ya thoda-thoda roz, dimaag fresh karne ke liye. (Plan me **Day 5** rakha hai — Glue ke baad, EMR se pehle, ek halka fresh din.)

---

## ⏱️ Har Cheez Kitni "Mushkil" Hai? (Taaki time sahi baant sako)

| Cheez | Mushkil Level | Time Lagega (approx) |
|-------|---------------|---------------------|
| AWS Basics + IAM | 🟢 Aasaan | Half day |
| S3 | 🟢 Aasaan | 1 din |
| Lambda | 🟡 Medium | 1 din |
| Glue | 🟡 Medium | 1 din |
| EMR | 🔴 Thoda Heavy | 1–1.5 din |
| Step Functions | 🟡 Medium | 1 din |
| APIs + API Gateway | 🟡 Medium | 1 din |
| Spec & Steering | 🟢 Aasaan-Medium | 1 din |

---

## ✅ Yaad Rakhne Wali 3 Baatein

1. **Neenv kabhi mat chhodo** — IAM aur S3 thoda boring lag sakte hain, par inke bina aage sab atkega.
2. **"Worker" pehle, "Manager" baad me** — Lambda/Glue/EMR pehle, Step Functions baad me.
3. **Spec/Steering ko parallel rakho** — jab AWS se bore ho jao, isko chhू lo, fresh feel hoga.

> ➡️ Ab File 3 kholo: **Din 1 se Din 10** tak ka exact plan.
