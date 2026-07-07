# 3️⃣ ⭐ Spec File Banao (Kya Banana Hai) 📝

> Ab asli naksha. Spec = "**KYA** banana hai" — Requirements → Design → Tasks. Ye AI ko clear disha deta hai, taaki wo apne mann se kuch bhi na bana de.

📖 Spec files (Kiro docs): https://kiro.dev/docs/specs/

---

## 🧠 Yaad Karo (File 1)

Spec ke **3 hisse**:
```
[Requirements: kya chahiye]  →  [Design: kaise banega]  →  [Tasks: chhote kadam]
```
Ghar ka naksha jaisa — pehle "kitne kamre" (requirement), phir layout (design), phir "pehle neenv phir deewar" (tasks).

---

## 🪜 Step 1 — Spec File Banao

- Usi `mera-project/` folder me ek file: **`spec.md`** (Kiro me: `.kiro/specs/todo-app/` jaisa).
- Aaj ka chhota project: **"CLI To-Do List App"** (terminal me task add/dekho/delete).

---

## 🪜 Step 2 — Hissa 1: REQUIREMENTS (Kya Chahiye)

> 📦 **Ye Kya Hai: Requirement** — ek saaf line jo batati hai "**user kya kar paayega**." Aksar "As a user, I want ... so that ..." style me likhte hain (user story). **Example:** "Main task add kar paun, taaki bhoolu nahi."

Apni spec me aise likho:
```markdown
## Requirements
1. User ek naya task add kar sake.
2. User saare tasks ki list dekh sake (number ke saath).
3. User kisi task ko number se delete kar sake.
4. Tasks band karne ke baad bhi save rahein (file me).
5. Galat input (khaali task / galat number) pe achha message aaye.
```

> 💡 Requirement = **kya** hoga, **kaise** nahi. "Task add ho" — theek. "Python list me append karo" — ye design/task me jaayega, yaha nahi.

---

## 🪜 Step 3 — Hissa 2: DESIGN (Kaise Banega)

> 📦 **Ye Kya Hai: Design** — requirements ko **kaise** poora karenge uska plan: kaunse parts/functions, data kaha aur kis format me, flow kya. **Example:** "3 kamron ke ghar" ke liye layout banana — kaunsa kamra kaha, darwaza kidhar.

Aise likho:
```markdown
## Design
- Data: har task ek line, file `tasks.txt` me save (simple text).
- Main functions:
  - add_task(text)      → nayi line file me jodo
  - list_tasks()        → file padho, number ke saath print
  - delete_task(num)    → us number ki line hatao
- Flow: menu dikhao (1 Add, 2 List, 3 Delete, 4 Exit) → user choose kare → wahi function chale → dobara menu.
- Errors: khaali task na jud e; galat number pe "aisa task nahi" message.
```

---

## 🪜 Step 4 — Hissa 3: TASKS (Chhote Kadam)

> 📦 **Ye Kya Hai: Task (spec me)** — kaam ke **chhote-chhote steps** jinhe AI ek-ek karke poora karega (aur tum tick kar sako). **Example:** ghar banana = "1. neenv, 2. deewar, 3. chhat" — har ek alag, order me.

Aise likho:
```markdown
## Tasks
- [ ] 1. File setup + menu loop (1/2/3/4) banao.
- [ ] 2. add_task() — input lo, tasks.txt me save karo.
- [ ] 3. list_tasks() — file padho, number ke saath dikhao.
- [ ] 4. delete_task() — number lo, us line ko hatao.
- [ ] 5. Input validation (khaali/galat number) add karo.
- [ ] 6. Ek baar chala ke test karo (add→list→delete→list).
```

> 💡 Tasks chhote rakho — taaki AI ek-ek karke kare aur tum har step verify kar sako. Bade task (jaise "poori app bana do") me galti pakadni mushkil.

---

## 📄 Poora `spec.md` — Ek Nazar Me

```markdown
# Spec — CLI To-Do List App

## Requirements
1. Task add kar sake.
2. Saare tasks list (number ke saath) dekh sake.
3. Number se task delete kar sake.
4. Tasks file me save rahein (band karne pe bhi).
5. Galat input pe achha message.

## Design
- Data: `tasks.txt` (har task ek line).
- Functions: add_task(text), list_tasks(), delete_task(num).
- Flow: menu (1 Add / 2 List / 3 Delete / 4 Exit) → function → wapas menu.
- Errors: khaali task nahi; galat number pe friendly message.

## Tasks
- [ ] 1. Menu loop + file setup.
- [ ] 2. add_task().
- [ ] 3. list_tasks().
- [ ] 4. delete_task().
- [ ] 5. Input validation.
- [ ] 6. End-to-end test.
```

---

## ⚠️ Common Galtiyan

| Galti | Theek Kaise |
|-------|-------------|
| Sab kuch ek line me ("todo app bana do") | Tootega. Requirements/Design/Tasks alag likho. |
| Requirement me code-detail likhna | Requirement = "kya"; "kaise" Design me. |
| Bahut bade tasks | Chhote steps me todo — verify aasaan. |
| Steering wali baat spec me daalna | "Python use karo" steering me; spec me sirf is project ka "kya". |

---

## ✅ Is File Ka "Ho Gaya" Check

- [ ] `spec.md` bana with **Requirements + Design + Tasks**
- [ ] Requirements = "kya" (user stories), design/code nahi
- [ ] Design = functions + data + flow
- [ ] Tasks = chhote, order wale steps
- [ ] Samajh gaye: Spec (kya) alag, Steering (rule) alag

> ➡️ Ab dono files AI ko de ke code likhwao → [`04-ai-se-code-likhwana.md`](./04-ai-se-code-likhwana.md) 🤖
