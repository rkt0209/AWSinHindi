# 4️⃣ AI Se Code Likhwao (Spec + Steering Ke Saath) 🤖

> Ab do files (`steering.md` + `spec.md`) taiyaar hain. Inhe AI ko de ke **step-by-step** code likhwate hain — aur dekhte hain wo tumhare rule + naksha follow karta hai ki nahi.

📖 Kiro se kaam: https://kiro.dev/docs/ · 📖 Spec-driven flow: https://kiro.dev/docs/specs/

---

## 🧰 Kaunsa Tool? (Koi Bhi Chalega)

- **Sabse aasaan:** koi AI chat (Claude etc.) — bas files ka text paste kar do.
- **Ya Kiro** (AWS agentic IDE) — isme steering/spec ka apna structure hai (`.kiro/steering/`, `.kiro/specs/`), aur wo khud tasks ek-ek karke karta hai.

> 💡 Aaj koi AWS login/permission nahi chahiye. Sirf ek AI tool aur tumhari do files.

---

## 🪜 Step 1 — AI Ko Steering (Rules) Do — Pehle

AI chat me sabse pehle ye bhejo (steering ka poora text), aur likho:

> "Ye mere **permanent rules (steering)** hain. Aage jo bhi code banao, **hamesha inhe follow karo**:"
> *(neeche `steering.md` ka poora content paste karo)*

**Kyun pehle?** Taaki jab code maango, rule pehle se AI ke dimaag me ho.

---

## 🪜 Step 2 — AI Ko Spec (Kya Banao) Do

Ab bhejo:

> "Ye is project ka **spec** hai (Requirements, Design, Tasks). Upar wale rules ke hisaab se, **Tasks ko ek-ek karke** poora karo. Pehle **Task 1** ka code do, phir main 'aage badho' bolun tab Task 2:"
> *(neeche `spec.md` ka poora content paste karo)*

> 💡 "Ek-ek task" isliye — taaki har step chhota rahe, tum verify kar sako, aur galti jaldi pakdi jaaye. (Yahi agentic tareeka hai.)

---

## 🪜 Step 3 — Task-By-Task Aage Badho

- AI **Task 1** ka code dega. Padho: kya ye tumhare **steering rules** follow kar raha? (Python? chhote naam? Hinglish comment?)
- Theek lage to bolo: **"Sahi hai, ab Task 2 karo."**
- Aise-aise saare 6 tasks poore karwao.

**🖥️ Har step pe dekho:**
- Function ke naam chhote/clear hain? ✅ (steering rule)
- Comments Hinglish me? ✅
- Sirf standard library? ✅ (extra install to nahi kar raha?)

---

## 🪜 Step 4 — Chala Ke Test Karo

- Saara code ek file me daalo, jaise `todo.py`.
- Terminal me chalao:
  ```
  python todo.py
  ```
- Menu aaye → task add karo → list dekho → delete karo. Spec ke saare **Requirements** poore ho rahe? ✅

**🖥️ Screen pe:** menu (1 Add / 2 List / 3 Delete / 4 Exit), task add hote, list dikhti, delete hota. Bilkul spec jaisa.

> 🎉 **Ho gaya!** Tumne AI se "kuch bhi" nahi — apne **rule aur naksha** ke hisaab se code likhwaya. Yahi asli skill hai.

---

## 🪜 Step 5 — Ek Chhota Change Maang Ke Dekho (Power Feel Karo)

Bolo: **"Ab ek naya requirement add karo spec me — 'task ko done mark kar sako' — aur usi rules ke hisaab se code update karo."**

- Dekho AI **usi steering** ke saath naya feature jodta hai (naye naam bhi chhote, comment Hinglish).
- Yahi Spec/Steering ka faayda: **badalna aasaan, consistency bani rehti.**

---

## ⚠️ Common Cases / Galtiyan

| Case | Solution |
|------|----------|
| AI rules bhool gaya (bade chat me) | Beech-beech me steering dobara yaad dila do ("rules yaad hain na?"). |
| Ek saath poori app maang li | Task-by-task maango — verify aasaan, galti kam. |
| AI extra library laga raha | Steering me "sirf standard library" tha na? Bolo "rule follow karo". |
| Code chala nahi | Error AI ko paste karo: "ye error aaya, rules ke hisaab se theek karo." |
| Comments English me aa rahe | Steering rule (Hinglish comment) dobara point out karo. |

---

## ✅ Is File Ka "Ho Gaya" Check

- [ ] AI ko pehle **steering**, phir **spec** diya
- [ ] Tasks **ek-ek** karke karwaye (poori app ek saath nahi)
- [ ] Har step pe check kiya: rules follow ho rahe (naam/comment/library)
- [ ] `todo.py` chala ke test kiya — requirements poore
- [ ] Ek naya requirement add karke consistency dekhi

> ➡️ Ab asli mazaa: **bina** files ke vs **saath** — farak apni aankh se → [`05-farak-dekho-with-vs-without.md`](./05-farak-dekho-with-vs-without.md) 🔍
