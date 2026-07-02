# 📅 DIN 1 — AWS Ki Neenv: Account + Console + IAM 🔑

> Aaj ka goal: **AWS me ghusna seekho.** Account banao, console (website) samjho,
> apne liye ek safe IAM user banao, aur paise safe karne ka setup karo.
>
> ⏱️ Time: 3–4 ghante | 😌 Mushkil: 🟢 Aasaan | 💰 Kharcha: ₹0 (bas card verify hoga)

---

## 🎯 Aaj Ke Baad Tumhe Ye Sab Aayega

- [ ] AWS Free Tier account ban gaya (root user)
- [ ] Root account pe security (MFA) laga di
- [ ] AWS Console (website) ki tour — Region, Search bar samajh gaye
- [ ] Apne liye ek **IAM user** banaya (root ki jagah ye use karoge)
- [ ] IAM user ko permission di aur usse login karke dekha
- [ ] **Billing Alert** laga diya (₹1 bhi kate to email aayega)

> Itna ho gaya to Din 1 **100% complete**. Kal Din 2 (S3) pe jaana.

---

## 📂 Is Folder Ki Files (Isi Order Me Karna)

| # | File | Kya Karoge |
|---|------|-----------|
| 1️⃣ | [`01-aws-account-banana.md`](./01-aws-account-banana.md) | AWS Free Tier account step-by-step banao |
| 2️⃣ | [`02-console-tour-region.md`](./02-console-tour-region.md) | Console kaisi dikhti hai, Region kya hai — samjho |
| 3️⃣ | [`03-root-security-mfa.md`](./03-root-security-mfa.md) | Root account pe MFA (extra tala) lagao |
| 4️⃣ | [`04-iam-user-banana.md`](./04-iam-user-banana.md) | Apna IAM user banao + permission do + login karo |
| 5️⃣ | [`05-billing-alert-paise-safe.md`](./05-billing-alert-paise-safe.md) | Billing alert lagao — paise safe |
| 6️⃣ | [`06-checklist-aur-galtiyan.md`](./06-checklist-aur-galtiyan.md) | Final checklist + har common error ka solution |

---

## 🧠 Aaj Ke 4 Zaroori Shabd (Pehle Ye Samjho)

| Shabd | Aasaan Matlab (Real-Life) |
|-------|---------------------------|
| **Root User** | Ghar ka **malik** — sab kuch kar sakta hai. Isliye ise roz use nahi karte (khatarnak). |
| **IAM User** | Ghar ka **member/naukar** jise tum limited chaabi dete ho. Roz kaam isi se karte hain. |
| **Region** | AWS ka data kis **sheher** ke computer me rakha hai (jaise Mumbai). |
| **MFA** | Password ke upar **doosra tala** (phone pe OTP). Chori se bachata hai. |

> 💡 **Yaad rakho:** Root = malik (kabhi-kabhi use), IAM user = tum (roz use). Ye Din 1 ki sabse badi seekh hai.

---

## ⚠️ Shuru Karne Se Pehle 3 Cheezein Ready Rakho

1. **Email ID** (jo tumhare paas ho — OTP aayega ispe).
2. **Mobile number** (OTP + verification ke liye).
3. **Debit/Credit card** (verification ke liye — chhota ₹2–₹15 ka charge aata hai jo **wapas** aa jaata hai). Card ke bina account nahi banta.

> Agar card nahi hai to ghar me kisi ka le lo (sirf verify hoga, paise nahi katenge agar Free Tier me raho).

---

➡️ Chalo, File 1 kholo aur account banana shuru karo: [`01-aws-account-banana.md`](./01-aws-account-banana.md)
