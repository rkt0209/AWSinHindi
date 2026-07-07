# 2️⃣ Steering File Banao (AI Ke Permanent Rules) 📋

> Pehle **rule-book** likhenge — taaki AI har kaam tumhare style me kare. Ye ek baar likho, baar-baar kaam aayega.

📖 Steering files (Kiro docs): https://kiro.dev/docs/steering/

---

## 🧠 Yaad Karo (File 1)

**Steering = office ka rule-book.** "KYA banao" nahi — "KIS RULE/style se banao." Ek baar set, har kaam pe apne-aap lagता hai.

---

## 🪜 Step 1 — Ek Text File Banao

- Apne computer me ek folder banao, jaise `mera-project/`.
- Usme ek file banao: **`steering.md`** (ya Kiro me: `.kiro/steering/` folder me file).

> 💡 Koi khaas jagah zaroori nahi — ye seekhne ke liye simple `.md` (markdown) file kaafi hai. Isko baad me AI ko dena hai.

---

## 🪜 Step 2 — Isme Ye 4 Cheez Likho

Steering file me aksar ye 4 tarah ke rule hote hain. Apne project ke hisaab se bharo:

### 1) Language / Tech Rules
```
- Hamesha Python 3 me code likho.
- Sirf standard library use karo (bina extra install ke chale).
- Framework chahiye to Flask use karo, doosra nahi.
```

### 2) Style / Naming Rules
```
- Function aur variable ke naam chhote aur saaf rakho (jaise add_task, not fn1).
- Indentation: 4 space (tab nahi).
- Har function ke upar ek chhota comment ho — Hindi/Hinglish me.
```

### 3) Behaviour Rules (AI kaise kaam kare)
```
- Pehle plan batao, phir code likho.
- Bina bataye koi nayi library mat add karo.
- Error handling zaroor daalo (khaali input, galat value).
```

### 4) Project Context (AI ko background do)
```
- Ye ek chhoti to-do list app hai.
- Users non-technical hain, isliye messages simple English/Hindi me ho.
- Data abhi file me save karo (database abhi nahi).
```

---

## 📄 Poora Example — Copy Karke Shuru Karo

Neeche ek ready `steering.md` — ise apni file me paste karo, phir apne hisaab se badlo:

```markdown
# Steering — Mere Permanent Rules

## Tech
- Language: Python 3 hamesha.
- Sirf standard library; koi extra install nahi (jab tak main na bolu).
- UI chahiye to command-line (terminal) rakho — abhi web nahi.

## Style
- Naam chhote aur clear: add_task, delete_task (fn1/fn2 nahi).
- 4-space indent. Line 80 char se choti.
- Har function ke upar 1-line comment Hinglish me.

## Behaviour
- Pehle short plan do, tab code likho.
- Har input validate karo (khaali/galat pe achha message).
- Bina puche nayi library ya file structure mat badlo.

## Context
- Project: chhoti CLI To-Do app.
- User non-technical; messages simple aur friendly ho.
- Data ko ek local file (tasks.txt) me save/padho.
```

> 💡 **Beginner tip:** shuru me chhoti steering rakho (5-8 rule). Zyada rule ek saath mat likho — jaise-jaise zaroorat lage, add karte jao.

---

## 🧪 Ek Chhoti Samajh — Steering "Permanent" Kyun?

- Aaj tum "to-do app" ka code maangoge, kal "calculator" ka — **spec badal jayegi**.
- Par tumhare rule (Python, chhote naam, comments Hinglish) **dono me same** rahenge.
- Isliye steering **ek baar** likho; har spec ke saath ye **automatic** lag jaayega. Yahi iska faayda.

---

## ⚠️ Common Galtiyan

| Galti | Theek Kaise |
|-------|-------------|
| Steering me "kya banao" likh dena | Nahi — wo **Spec** me jaata hai. Steering me sirf **rule/style/context**. |
| Bahut saare rule ek saath | Confusing. 5-8 saaf rule se shuru karo. |
| Ulta-seedha (contradicting) rule | "Python use karo" + "JS use karo" dono? AI confuse. Ek hi rakho. |
| Rule bahut vague | "Achha code likho" bekaar hai. "4-space indent, chhote naam" — aisa concrete likho. |

---

## ✅ Is File Ka "Ho Gaya" Check

- [ ] Ek `steering.md` file bani
- [ ] Usme Tech + Style + Behaviour + Context ke rule likhe
- [ ] Rule **concrete** hain (vague nahi)
- [ ] Samajh gaye: steering = permanent rule, spec = kya banao (alag)

> ➡️ Ab **Spec** likho — "kya banana hai" → [`03-spec-file-banana.md`](./03-spec-file-banana.md) ⭐
