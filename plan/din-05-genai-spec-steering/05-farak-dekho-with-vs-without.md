# 5️⃣ Farak Dekho — Bina Files Vs Spec+Steering Ke Saath 🔍

> Ye din ka **sabse important experiment**. Ek hi cheez AI se **do tarah** maango aur **farak apni aankh se dekho**. Tabhi dil se samajh aayega ki spec/steering kyun matter karte hain.

---

## 🧪 Experiment — Same Kaam, Do Tareeke

Ek **naya AI chat** kholo (purana context na ho). Ab do baari:

### 🅰️ Baari 1 — BINA Files (Sirf Ek Line)

AI ko sirf itna bolo:
> "Ek to-do list app bana do."

**🖥️ Kya hoga (aksar):**
- AI apne mann se kuch bhi bana dega — shayad **JavaScript** me (tumne Python socha tha).
- Function ke naam lambe/random, comments English me (ya bilkul nahi).
- Data kaha save hoga — pata nahi, apne hisaab se.
- Agar dobara maango to **alag** hi code — har baar naya style.

> ❌ Problem: **tumhara** style/rule nahi, aur **har baar alag** (inconsistent).

---

### 🅱️ Baari 2 — Spec + Steering Ke Saath

Naya chat, aur pehle steering + spec do (File 4 wala tareeka), phir code maango.

**🖥️ Kya hoga:**
- **Python** me (steering rule), function naam **chhote/clear** (add_task, list_tasks).
- Comments **Hinglish** me, sirf **standard library**.
- Data `tasks.txt` me (spec ka design), saare 5 requirements poore.
- Dobara maango to **wahi consistent style** — kyunki rules fix hain.

> ✅ Faayda: **tumhara** style, **tumhara** naksha, aur **har baar same** (predictable).

---

## 📊 Side-By-Side (Yaad Rakhne Ke Liye)

| Cheez | Bina Files 🅰️ | Spec + Steering 🅱️ |
|-------|---------------|---------------------|
| Language | AI ke mann se (kabhi JS, kabhi Py) | **Python** (rule) — fix |
| Naam/style | Random, lamba | **Chhote, clear** (rule) |
| Comments | English/nahi | **Hinglish** (rule) |
| Kya banega | AI ki guess | **Tumhara spec** (exact) |
| Har baar | Alag-alag | **Same, consistent** |
| Badalna | Mushkil (fir se samjhao) | **Aasaan** (spec update) |
| Galti pakadna | Mushkil (bada blob) | **Aasaan** (task-by-task) |

---

## 🧠 Isse Kya Seekha? (Din Ki Asli Baat)

1. **AI powerful hai, par bina disha ke "kuch bhi" deta hai.** Spec + Steering usse **disha** dete hain.
2. **Steering = consistency** (har baar same rule). **Spec = correctness** (exactly wahi jo chahiye).
3. **Task-by-task = control** — chhote steps me galti jaldi pakadti hai.
4. Isiliye asli companies (aur Kiro jaise tools) **spec-driven / steering-based** kaam karte hain — team ka code ek jaisa aur sahi rehta hai.

> 💡 **Ek line yaad rakho:** "Bina spec/steering AI ek tez par bina-naksha mistri hai; unke saath wo **tumhara** trained developer ban jaata hai."

---

## 🎯 Ek Chhota Bonus Experiment (Optional)

- Steering me **ek rule badlo** — jaise "ab comments English me karo" — aur wahi spec dobara do.
- Dekho: sirf comments English ho gaye, **baaki sab same**. Ye dikhata hai steering ka **direct control**.

---

## ✅ Is File Ka "Ho Gaya" Check

- [ ] Bina files wala code dekha (random/inconsistent laga)
- [ ] Spec+Steering wala code dekha (tumhare rule + naksha ke hisaab se)
- [ ] Dono ka farak samajh aaya (table wali baatein)
- [ ] Samajh gaye: steering = consistency, spec = correctness, task-by-task = control

> ➡️ Ab final: checklist + terms revision + galtiyan + cleanup → [`06-checklist-aur-galtiyan.md`](./06-checklist-aur-galtiyan.md) ✅
