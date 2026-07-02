# 3️⃣ Root Account Pe MFA (Extra Tala) Lagao 🔒

> Root user = ghar ka malik. Agar iska password kisi ke haath lag gaya to **poora account** khatre me.
> Isliye ispe **doosra tala (MFA)** lagana zaroori hai. 5 minute ka kaam, par bahut important.

📖 MFA docs: https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable.html

---

## 🤔 MFA Hai Kya? (Aasaan Example)

**Real-life:** Bank locker me **do chaabi** lagti hai — ek tumhari, ek bank ki. Dono ke bina locker nahi khulta.

**MFA (Multi-Factor Authentication) waisa hi:**
- Pehla tala = **password** (jo tum jaante ho).
- Doosra tala = **phone pe aaya 6-digit OTP** (jo har 30 second me badalta hai).
- Password chori ho bhi jaye, to bina tumhare phone ke koi login nahi kar sakta. ✅

---

## 📱 Pehle Phone Me Ek App Install Karo

MFA ke liye ek **authenticator app** chahiye. Koi ek install karo:
- **Google Authenticator** (sabse aasaan) — Play Store / App Store
- ya **Microsoft Authenticator**
- ya **Authy**

Ye app har 30 second me naya 6-digit code banati hai.

---

## 🪜 STEP BY STEP — MFA Lagao

### Step 1 — Security Settings Kholo
- Top-right me apne **account naam pe click** karo → dropdown me **"Security credentials"** chuno.

**🖥️ Screen pe:** "My security credentials" page khulega. Thoda neeche **"Multi-factor authentication (MFA)"** ka section dikhega.

### Step 2 — MFA Assign Karo
- **"Assign MFA device"** button dabao.
- **Device name** koi bhi daalo (jaise `Mera-Phone`).
- MFA type me **"Authenticator app"** chuno. **Next** dabao.

**🖥️ Screen pe:** Ek **QR code** dikhega.

### Step 3 — Phone Se Scan Karo
- Phone me Google Authenticator kholo → **"+"** → **"Scan a QR code"** → screen wala QR scan karo.
- App me ab **AWS ka ek 6-digit code** aane lagega (har 30 sec badalta hai).

### Step 4 — Do Code Daalo
- AWS screen pe do box honge (**Code 1** aur **Code 2**).
- App me jo code hai wo **Code 1** me daalo → 30 sec ruko → **agla code** **Code 2** me daalo.
- **"Add MFA"** dabao.

**🖥️ Screen pe:** "MFA device assigned successfully" ✅ — ab MFA list me tumhara device dikhega.

---

## 🧪 Test Karo (Optional Par Accha)
- Logout karo → dobara root se login karo.
- Ab password ke baad **MFA code maangega** → app se code daalo → andar. ✅
- Iska matlab tala kaam kar raha hai. 🎉

---

## ⚠️ Zaroori Cases / Galtiyan

| Case | Solution |
|------|----------|
| **"Invalid MFA code":** | Phone ka time galat ho sakta hai. Phone settings → Date & Time → "Automatic" ON karo. |
| **QR scan nahi ho raha:** | QR ke neeche "show secret key" hoga — wo key app me manually daalo. |
| **Phone kho gaya to?** | Ghabrana nahi — AWS support se "MFA reset" ho jaata hai (email + verification se). Isliye recovery email/phone sahi rakho. |
| **Do code kyun?** | AWS confirm karta hai ki app sahi sync hai (ek code ab, ek 30 sec baad). |

> 💡 **Best practice:** Root user ko ab **band karke rakho** — sirf emergency me use karo (jaise billing, account close). Roz ka kaam **IAM user** (agli file) se karna.

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Authenticator app phone me install ho gayi
- [ ] Root account pe MFA lag gaya ("successfully" dikha)
- [ ] Samajh gaye: root = malik, ise kam use karna hai

> ➡️ Ab File 4: Apna IAM user banao (roz ka kaam isse hoga) → [`04-iam-user-banana.md`](./04-iam-user-banana.md)
