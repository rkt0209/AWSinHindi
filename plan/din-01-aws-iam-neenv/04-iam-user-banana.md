# 4️⃣ Apna IAM User Banao — Permission + Login 🔑

> Ye Din 1 ka **sabse important** part hai. Root (malik) se roz kaam nahi karte.
> Tum apne liye ek **IAM user** banaoge, use limited permission doge, aur usse login karoge.

📖 IAM Getting Started: https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started.html
📖 IAM user banana: https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html
📖 IAM best practices: https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html

---

## 🤔 Pehle Samjho: User, Group, Policy, Role

**Real-life example — ek office:**

| AWS Shabd | Office Me | Matlab |
|-----------|-----------|--------|
| **IAM User** | Ek employee (tum) | Ek insaan jo login karta hai |
| **Policy** | Ek permission-slip | Likha document: "ye-ye kaam kar sakte ho" (jaise "S3 use kar sakte ho") |
| **Group** | Ek department | Ek jhund; department ko permission do, sab members ko mil jaati |
| **Role** | Ek duty/uniform (kisi ko udhaar) | Temporary permission — insaan ko nahi, machine ya doosri service ko di jaati hai |

> 💡 Aaj hum sirf **User** banayenge aur usme **Policy** lagayenge. Group/Role aage kaam aayenge.

---

## 🪜 STEP 1 — IAM Kholo

- Upar 🔍 search me `IAM` type karo → **IAM** pe click.

**🖥️ Screen pe:** IAM Dashboard khulega. Left side me menu: **Users, User groups, Roles, Policies** waghera.

> ℹ️ IAM **global** hai — Region ki tension nahi (har jagah same dikhega).

---

## 🪜 STEP 2 — Naya User Banao

- Left menu me **"Users"** pe click → right upar **"Create user"** button dabao.

**🖥️ Screen pe:** "Specify user details" page.

- **User name:** apna naam daalo (jaise `rohit-dev`).
- **"Provide user access to the AWS Management Console"** wale checkbox pe ✅ tick karo (taaki ye user website se login kar sake).
- Ab option aayenge:
  - **"I want to create an IAM user"** chuno (simple, beginner ke liye best).
  - Password: **"Custom password"** chuno, ek password set karo.
  - **"Users must create a new password at next sign-in"** ka tick **hata do** (apne liye zaroorat nahi).
- **Next** dabao.

---

## 🪜 STEP 3 — Permission Do (Sabse Important)

**🖥️ Screen pe:** "Set permissions" page — 3 option:
1. Add user to group
2. Copy permissions
3. **Attach policies directly** ← ye chuno

- **"Attach policies directly"** pe click.
- Neeche search box me policy dhundo aur tick karo. **Aaj ke liye ye lagao:**
  - `AmazonS3FullAccess` (kal S3 ka kaam hai) ✅
  - *(Chaho to abhi `IAMReadOnlyAccess` bhi laga sakte ho, dekhne ke liye.)*
- **Next** dabao → **Create user** dabao.

**🖥️ Screen pe:** "User created successfully" ✅

> ⚠️ **Bade log ki salah / cases:**
> - **`AdministratorAccess`** ek policy hoti hai jo "sab kuch" kholti hai. Seekhne ke liye kuch log yahi laga lete hain (aasaan), **par ye kam-permission wale principle ke against hai**. Interview/office me best practice: **utni hi permission do jitni chahiye** (isse "least privilege" kehte hain).
> - Beginner ke liye theek: abhi `AmazonS3FullAccess` kaafi hai. Aage jis din jo service chahiye, us din uski policy add kar dena.

---

## 🪜 STEP 4 — Login Ka Address (Sign-in URL) Le Lo

IAM user root se **alag tareeke** se login karta hai. Uska apna URL hota hai.

- User ban-ne ke baad screen pe **"Console sign-in URL"** dikhega, jaise:
  `https://123456789012.signin.aws.amazon.com/console`
  (`123456789012` = tumhara **12-digit Account ID**).
- Isko **copy karke safe rakho** (bookmark kar lo).

**🖥️ Kahan milega baad me?** IAM Dashboard ke right side me "Sign-in URL for IAM users in this account" likha hota hai — wahan se bhi le sakte ho.

---

## 🪜 STEP 5 — IAM User Se Login Karke Dekho

- Ab **root se logout** karo.
- Upar wala **sign-in URL** kholo.
- Login page pe:
  - **Account ID** (ya alias) — pehle se bhara hoga URL se.
  - **IAM user name:** `rohit-dev`
  - **Password:** jo tumne set kiya.
- **Sign in** dabao.

**🖥️ Screen pe:** Console Home khulega — par ab tum **IAM user** ke roop me ho (top-right me `rohit-dev @ account-id` dikhega).

> ✅ **Aaj se roz ka kaam isi IAM user se karna. Root ko haath mat lagana.**

---

## 🧪 Permission Sahi Lagi? Test Karo

- IAM user se login rehte hue, 🔍 search me `S3` kholo → tumhe S3 ka page dikhna chahiye (permission hai). ✅
- Ab search me `EC2` kholo → **"Access Denied"** type message aa sakta hai (kyunki EC2 ki permission nahi di). Ye **galti nahi** — iska matlab permission system kaam kar raha hai! 👍

---

## ⚠️ Common Errors Aur Solution

| Error / Case | Kyun / Solution |
|--------------|-----------------|
| **"Access Denied"** kisi service pe | Us service ki policy nahi lagi. IAM → Users → apna user → "Add permissions" → policy lagao. |
| **Login nahi ho raha (IAM URL pe)** | Root wale login page pe mat jao. IAM user ka **alag sign-in URL** use karo. |
| **Account ID yaad nahi** | Root se login → top-right account menu me 12-digit ID dikhti hai. |
| **Password bhool gaye (IAM user)** | Root se login karke us user ka password reset kar do (IAM → Users → user → Security credentials). |
| **Bahut saari policy me confuse** | Beginner ho — bas `AmazonS3FullAccess` rakho abhi. Baaki jarurat pe add karna. |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] IAM user ban gaya (`rohit-dev` jaisa)
- [ ] Usme `AmazonS3FullAccess` policy lagi
- [ ] Sign-in URL bookmark kar liya
- [ ] IAM user se login ho gaya
- [ ] Samajh gaye: "permission nahi hai to Access Denied aata hai — ye normal hai"

> ➡️ Ab last setup — File 5: Billing Alert lagao taaki paise safe rahein → [`05-billing-alert-paise-safe.md`](./05-billing-alert-paise-safe.md)
