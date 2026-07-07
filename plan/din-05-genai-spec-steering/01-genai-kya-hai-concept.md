# 1️⃣ GenAI + Spec + Steering Kya Hai? — Concept 🧠

> Aaj sirf **samajhna** hai. Har nayi term ko **alag box** me "actually ye kya hai + example" karke samjhaya hai.

📖 Kiro (AWS ka agentic IDE): https://kiro.dev/

---

## 🤖 Sabse Pehle — Real-Life Example

**Soch:** tumne ek **naya, tez, hoshiyaar contractor (mistri)** rakha hai jo ghar bana sakta hai bahut jaldi. Par usme do problem:
1. Agar tum sirf bolo "**ghar bana do**" — wo apne mann se kuch bhi bana dega (shayad tumhari zaroorat se alag).
2. Har baar naya kaam do to wo bhool jaata hai ki tum **kis style** me kaam chahte ho (kaunse material, kaunsa colour, kaunsa rule).

**Solution do cheez:**
- Ek **naksha/requirement sheet** do — "mujhe **ye** ghar chahiye: 2 kamre, ye size, ye budget." → Ye hai **Spec**.
- Ek **permanent rule-book** do — "hamesha ISI cement se, ISI colour me, ISI naap me kaam karna." → Ye hai **Steering**.

**AI (GenAI) bilkul wahi tez contractor hai.** Spec + Steering usko sahi disha aur sahi rule de dete hain — tab wo tumhare jaisa, galti kam karke, consistent kaam karta hai.

> **Ek line:** Spec = "kya banana hai", Steering = "kis rule/style se banana hai." Dono milke AI ko **tumhara** developer bana dete hain.

---

## 📦 Ye Kya Hai: **GenAI (Generative AI)**

**Definition:** GenAI = wo AI jo **naya content khud bana (generate) deta** hai — text, code, image, etc. Tum instruction (prompt) do, wo output bana ke deta hai. (Jaise ChatGPT/Claude code likh dena.)

**Example:** Ek bahut padha-likha assistant 🧑‍💻 jise tum bolo "Python me calculator likh do" aur wo turant likh de. Wo **naya** likhta hai (ratta nahi maarta) — isiliye "generative".

> 💡 Ye "haan/naa" wala AI nahi — ye **banane wala** AI hai. Code, notes, plan sab bana deta hai.

---

## 📦 Ye Kya Hai: **Agentic Development**

**Definition:** Agentic development = jab AI sirf ek jawab nahi deta, balki **ek agent (naukar) ki tarah khud plan banata hai, step-by-step kaam karta hai** — files banata, code likhta, test karta, galti sudharta. Tum bade goal do, wo chhote steps khud karta hai.

**Example:** Normal AI = ek waiter jo sirf tum jo bolo wahi ek plate laata hai. **Agentic AI = ek cook** jo "dinner bana do" sun ke khud sabzi kaatega, pakayega, plate lagayega — poora kaam khud steps me karega.

> 💡 Spec + Steering isi agentic AI ko **kaabu me** rakhte hain — warna wo apne mann se kuch bhi bana de.

---

## 📦 Ye Kya Hai: **Spec File** (Aaj Ki Star ⭐)

**Definition:** Spec (short for *specification*) file = ek document jisme tum **saaf-saaf likhte ho ki KYA banana hai**. Achhi spec ke aksar **3 hisse** hote hain:
- **Requirements** = kya-kya chahiye (feature list, "user ye kar paaye").
- **Design** = wo kaise banega (kaunse parts, kaunsa data, kaunsa flow).
- **Tasks** = chhote-chhote kadam (step 1, 2, 3...) jinhe AI ek-ek karke karega.

**Example:** Ghar banane ka **naksha + requirement sheet** 🏠 — "3 kamre chahiye (requirement) → aise layout me (design) → pehle neenv, phir deewar, phir chhat (tasks)." Spec waisa hi **software ka naksha** hai.

> 💡 Spec = "**kya** banana hai" ka clear document. Ye har naye project ke liye **alag** hota hai (kyunki har project alag hai).

---

## 📦 Ye Kya Hai: **Steering File**

**Definition:** Steering file = ek document jisme tum AI ke **permanent rules aur context** likhte ho — "hamesha aise karna, ye kabhi mat karna." Ye ek baar likha jaata hai aur **har kaam pe apne aap lagता** hai (spec badalti rehti, steering same rehti).

**Aksar isme likhते hain:**
- **Coding style** — "hamesha Python", "function ke naam chhote", "tab nahi space".
- **Libraries/tools** — "sirf ye library use karo", "database ye hi".
- **Naming / language** — "variable English me, comments Hindi me".
- **Project context** — "ye app sales ke liye hai, users non-technical hain."

**Example:** Office ka **rule-book / dress-code** 📋 — har naye kaam pe alag se nahi batana padta, wo **hamesha** apply hota hai. "Office me formal kapde" jaisa rule har din chalega. Steering waisa hi AI ke liye permanent rule-book hai.

> 💡 **Steering vs Spec — Crystal Clear:**
> - **Spec** = "**KYA** banao" (har project alag; badalta rehta hai).
> - **Steering** = "**KAISE/KIS RULE** se banao" (ek baar set; har project pe same lagta hai).

---

## 📦 Ye Kya Hai: **Kiro** (Optional Tool)

**Definition:** Kiro = **AWS ka agentic IDE** (code editor) jisme Spec aur Steering files ka concept **built-in** hai. Isme tum spec likhte ho, wo requirements→design→tasks banata hai, aur steering file se har baar tumhare rule follow karta hai.

**Example:** Ek **smart workshop** jaha naksha (spec) aur rule-book (steering) rakhne ki alag jagah bani hui hai — sab kuch sajaa-sajaya. Bina Kiro ke bhi ye concept kisi bhi AI chat me use kar sakte ho; Kiro bas isko aasaan banata hai.

> 💡 Aaj Kiro **zaroori nahi** — koi bhi AI chat (Claude etc.) me hum ye files paste karke wahi seekh lenge. Kiro dekhna optional bonus hai.

---

## 🖼️ Poori Picture — Ek Saath

```
        ┌──────────────────────────┐
        │  STEERING file           │  permanent rules
        │  (hamesha lagta hai)     │  "Python, chhote naam,
        │                          │   comments Hindi me..."
        └────────────┬─────────────┘
                     │  har kaam pe apply
                     ▼
   ┌─────────────┐   +   ┌──────────────────────────┐
   │ SPEC file   │──────▶│         AI (agent)        │──────▶  Achha, sahi,
   │ "KYA banao" │       │  (Claude / Kiro)          │         consistent CODE
   │ req+design+ │       │  plan → code → test       │
   │ tasks       │       └──────────────────────────┘
   └─────────────┘
```

**Padhne ka tareeka:** Steering (rule) + Spec (kya) → AI ko do → AI accurate code deta hai.

---

## ✅ Is File Ka "Ho Gaya" Check

- [ ] GenAI = naya content/code **banane wala** AI
- [ ] Agentic dev = AI khud plan+steps karke kaam karta (cook jaisa)
- [ ] **Spec** = "KYA banao" (Requirements + Design + Tasks) — har project alag
- [ ] **Steering** = "KIS RULE/style se banao" — permanent, har kaam pe lagta
- [ ] Spec vs Steering ka farak crystal clear
- [ ] Kiro = AWS ka agentic IDE (optional, isme ye built-in)

> ➡️ Ab pehle **Steering** file likho (rules pehle set) → [`02-steering-file-banana.md`](./02-steering-file-banana.md) 📋
