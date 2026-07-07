# 6️⃣ Din 5 Final Checklist + Terms + Galtiyan + Cleanup ✅

> Sab tick ho gaya to Din 5 (GenAI: Spec & Steering) **pakka complete**. Neeche one-stop sab kuch.
> 😌 Achhi baat: **aaj koi AWS bill nahi** (koi service nahi chalayi).

---

## ✅ Din 5 Master Checklist

**Concept:**
- [ ] GenAI = naya content/code banane wala AI
- [ ] Agentic dev = AI khud plan+steps karke kaam kare
- [ ] Spec = "KYA banao"; Steering = "KIS RULE se banao"
- [ ] Spec har project alag; Steering permanent (har kaam pe lagta)

**Hands-on:**
- [ ] `steering.md` likha (Tech + Style + Behaviour + Context rules)
- [ ] `spec.md` likha (Requirements + Design + Tasks)
- [ ] AI ko steering→spec de ke **task-by-task** code likhwaya
- [ ] `todo.py` chala ke test kiya (requirements poore)
- [ ] Bina-files vs saath-files ka **farak** dekha

---

## 🧠 Din 5 Ki 5 Sabse Badi Seekh

1. **AI ko disha chahiye — warna "kuch bhi" deta hai.** Spec + Steering wahi disha hain.
2. **Spec = correctness (exactly kya chahiye). Steering = consistency (har baar same rule).**
3. **Task-by-task karwao — control aur galti-pakad aasaan.**
4. **Steering ek baar, har project pe lagta; Spec har project ka alag.**
5. **Ye AWS pe depend nahi karta — kabhi bhi, kisi bhi AI tool me use ho sakta hai.**

---

## 📦 Saari Nayi Terms — Ek Jagah (Revision)

| Term | Ek Line | Example |
|------|---------|---------|
| **GenAI** | Naya content/code banane wala AI | Assistant jo code likh de |
| **Agentic dev** | AI khud plan+steps karke kaam kare | Cook jo pura khana khud banaye |
| **Spec** | "KYA banao" (Req+Design+Tasks) | Ghar ka naksha + requirement |
| **Requirements** | User kya kar paayega | "Task add kar saku" |
| **Design** | Kaise banega (parts/data/flow) | Ghar ka layout |
| **Tasks (spec)** | Chhote order-wale steps | Neenv→deewar→chhat |
| **Steering** | Permanent rules/style/context | Office ka rule-book |
| **Kiro** | AWS ka agentic IDE (ye built-in) | Smart workshop |

---

## 🆘 Har Common Galti Ka Solution (One-Stop)

| Problem | Solution |
|---------|----------|
| **AI apne mann se (galat lang) code** | Steering me "Python hi" + shuru me steering do. |
| **Har baar alag style** | Steering fix karo aur har baar saath do. |
| **AI rules bhool gaya** | Beech me "rules yaad hain na?" bol ke dobara do. |
| **Poora blob, galti nahi milti** | Task-by-task maango, ek step verify karke aage. |
| **Extra library laga raha** | Steering "sirf standard library" — point out karo. |
| **Spec me code-detail ghus gaya** | Requirements = "kya"; "kaise" Design/Tasks me. |
| **Steering me "kya banao" likh diya** | Wo Spec me jaata hai; Steering me sirf rule/style. |

---

## 🔑 Din 5 Me Kaunsi Permission Chahiye?

> ✅ **Koi AWS permission NAHI.** Aaj koi AWS service (IAM/S3/Glue) use nahi hui.
> Bas ek **AI tool** (Claude/Kiro) aur ek **text editor** kaafi hai. Kiro use karna ho to uski website se free download — koi AWS IAM policy nahi chahiye.

---

## 🧹 Din Ke End Me Cleanup (Bill Se Bacho)

> 😌 **Aaj bill ki koi tension nahi** — kyunki koi AWS resource (cluster/job/bucket) banaya hi nahi. Fir bhi thoda tidy kar lo:

### 1️⃣ AWS Pe — Kuch Delete Karne Ki Zaroorat Nahi
- Aaj koi Glue/EMR/Lambda nahi chalaya, isliye **AWS pe aaj ka koi charge nahi**. ✅

### 2️⃣ Local Files (Apne Computer Par)
- `steering.md`, `spec.md`, `todo.py` — ye **rakh lo** (achha reference; kal bhi kaam aa sakte).
- Chaho to inhe repo ke ek `practice/` folder me rakh do (yaad ke liye).

### 3️⃣ AI Tool
- Kuch band nahi karna — chat band kar do bas. Koi paisa nahi lagta (free tool use kiya to).

### ✋ Ye MAT Delete Karo (Aage Kaam Aayega)
- **S3 bucket + `raw-data/sales.csv`** — kal Din 6 (EMR) me bada-data practice me kaam aa sakta hai.
- **IAM user `rohit-iam-dev`** aur permissions — roz chahiye.
- Din 2-4 ka koi bhi zaroori setup mat hatao.

> 🧾 **Confirm:** Billing me aaj Glue/EMR ka koi naya charge nahi hona chahiye (kuch chalaya hi nahi).

---

## 📚 Din 5 Ke Saare Documentation Links (Ek Jagah)

- Kiro (AWS agentic IDE) → https://kiro.dev/
- Spec files samajho → https://kiro.dev/docs/specs/
- Steering files samajho → https://kiro.dev/docs/steering/
- Kiro docs (home) → https://kiro.dev/docs/
- (Bonus) Prompt/agentic basics → https://www.anthropic.com/

---

## 🎉 Din 5 Complete!

Agar upar sab ✅ hai, to **shabaash!** 💪 Ab tumhare paas ek naya, bahut kaam ka skill hai:
- **AI se "kuch bhi" nahi — apne rule (Steering) aur naksha (Spec) ke hisaab se** achha, consistent code likhwana.

Dimaag me picture:
> "Steering (rules) + Spec (kya) → AI ko do → tumhara jaisa, sahi, ek-jaisa code."

**Kal:** Din 6 — **EMR (500 mazdoor — bahut bada data)** 🏗️. Jab data itna bada ho ki ek machine kam pade, tab kya karte hain — wo seekhenge. (Ye thoda heavy din hai, aaj fresh ho ke jao.)

> Ready ho to kal milte hain! 😴➡️🚀
