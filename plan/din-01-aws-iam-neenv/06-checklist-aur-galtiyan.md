# 6️⃣ Din 1 Final Checklist + Har Galti Ka Solution 🧾

> Ye Din 1 ka "closing" page hai. Sab tick ho gaya to Din 1 **pakka complete**.
> Neeche har common problem ka one-stop solution bhi hai.

---

## ✅ Din 1 Master Checklist

Ek-ek karke tick karo. Sab ✅ = Din 1 done, kal S3 (Din 2).

**Account:**
- [ ] AWS Free Tier account ban gaya
- [ ] Root user se login ho gaya
- [ ] Account activate ho gaya (koi "under review" nahi)

**Security:**
- [ ] Root pe MFA (authenticator app) laga diya
- [ ] Root password + MFA safe jagah note kiya
- [ ] Samajh gaye: root = malik, kam use karna hai

**Console:**
- [ ] Search bar use karna aa gaya
- [ ] Region **Mumbai (ap-south-1)** set kar diya
- [ ] Samajh gaye: Region badalne se cheezein "gayab" dikhti hain (delete nahi)

**IAM User:**
- [ ] Apna IAM user banaya (jaise `rohit-dev`)
- [ ] `AmazonS3FullAccess` policy lagayi
- [ ] Sign-in URL bookmark kiya
- [ ] IAM user se login karke dekha
- [ ] "Access Denied" ka matlab samajh gaye

**Paisa:**
- [ ] Billing alerts ON
- [ ] Ek Budget banaya
- [ ] Aadat samajh li: banaya hua delete/stop karna hai

---

## 🧠 Din 1 Ki 5 Sabse Badi Seekh (Zubaani Yaad Rakho)

1. **Root = malik (emergency), IAM user = tum (roz ka kaam).**
2. **Region = data ka sheher; galat sheher me cheezein gayab dikhti hain.**
3. **Permission nahi to "Access Denied" — ye normal hai, galti nahi.**
4. **MFA = doosra tala, chori se bachata hai.**
5. **Banaya hua delete/stop karo, warna bill aata hai.**

---

## 🆘 Har Common Galti Ka Solution (One-Stop)

| Problem | Solution |
|---------|----------|
| **Email OTP nahi aaya** | Spam check, 2 min ruk ke "Resend". Email sahi likhi? |
| **Card decline** | International transaction ON karo, Visa/Mastercard use karo (RuPay kabhi issue). Ya doosra card. |
| **Account "under review" / activate nahi** | Normal — kuch min se 24 ghante lagte hain. Email aayega. Intezaar karo. |
| **Login hone ke baad sab khaali** | Region galat hai. Top-right se **Mumbai** karo — sab wapas. |
| **Kisi service pe "Access Denied"** | Us service ki policy IAM user me nahi. IAM → Users → user → Add permissions. |
| **IAM user login nahi ho raha** | Root wale page pe mat jao; IAM ka **alag sign-in URL** use karo. |
| **MFA "Invalid code"** | Phone ka time "Automatic" karo (Date & Time settings). |
| **Phone/MFA kho gaya** | AWS Support se MFA reset (email verification se). Recovery email sahi rakho. |
| **Password bhool gaye (IAM)** | Root se login → us user ka password reset. |
| **Password bhool gaye (Root)** | Login page pe "Forgot password" → email pe reset link. |
| **Bill aa gaya (chhota)** | Kuch chalta reh gaya. Us Region me ja ke resource delete/terminate karo. Support se baat bhi kar sakte ho. |

---

## 📚 Din 1 Ke Saare Documentation Links (Ek Jagah)

- AWS account banana → https://docs.aws.amazon.com/accounts/latest/reference/manage-acct-creating.html
- Free Tier → https://aws.amazon.com/free/
- Region samajhna → https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html
- MFA lagana → https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable.html
- IAM Getting Started → https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started.html
- IAM user banana → https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html
- IAM best practices → https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html
- Billing alarm → https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html
- Budgets → https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-create.html
- Free courses (Skill Builder) → https://skillbuilder.aws/

---

## 🎉 Din 1 Complete!

Agar upar sab ✅ hai, to **mubarak ho** — AWS ki neenv tumhare haath me hai. 💪

Ab dimaag me ye picture rakho:
> "Maine account banaya → console samjha → Region set kiya → apna IAM user banaya → paise safe kiye."

**Kal:** Din 2 — **S3 (internet ka godown)**. File rakhna aur nikaalna seekhenge, jo baaki sabki neenv hai.

> Aaram karo, kal milte hain! 😴➡️🚀
