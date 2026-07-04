# ⚡ Din 3 — Lambda (Automatic Naukar)

> Din 2 me humne **godown (S3)** banaya jahan data rakha.
> Aaj hum ek **"automatic naukar" (Lambda)** banayenge jo **kaam apne-aap** karta hai —
> jaise hi S3 me file aati hai, ye khud jaag ke chal jata hai. Koi button dabane ki zaroorat nahi. 🪄

---

## 🎯 Aaj Kya-Kya Karenge?

| Step | File | Kya Seekhoge |
|------|------|--------------|
| 1️⃣ | [`01-lambda-kya-hai-concept.md`](./01-lambda-kya-hai-concept.md) | Lambda kya hai — vending machine wala example + saari nayi terms ke definition box |
| 2️⃣ | [`02-pehla-lambda-banana.md`](./02-pehla-lambda-banana.md) | Apna pehla Lambda function banana — step-by-step, screen output |
| 3️⃣ | [`03-lambda-test-run.md`](./03-lambda-test-run.md) | Lambda ko test karna (Test event) + logs (CloudWatch) dekhna |
| 4️⃣ | [`04-s3-trigger-lambda.md`](./04-s3-trigger-lambda.md) | ⭐ Asli maza — S3 me file aate hi Lambda **apne-aap** chale (Trigger) |
| 5️⃣ | [`05-role-cloudwatch-env.md`](./05-role-cloudwatch-env.md) | Role, permission, environment variables, timeout — behind the scenes |
| 6️⃣ | [`06-checklist-aur-galtiyan.md`](./06-checklist-aur-galtiyan.md) | Final checklist + har error ka solution + saare doc links |

---

## 🧠 Ek Line Me Aaj Ka Din

> "Lambda = ek chhota **naukar/code** jo internet pe rehta hai, **kaam aane pe apne-aap chalta hai**, kaam khatam to **so jata hai** (aur tabhi paisa lagta hai jab chalta hai)."

---

## 🔑 Aaj Ke Naye Shabd (Jo Box Me Detail Me Aayenge)

Ghabrana nahi — har ek ko File 1 me **alag box** me "actually ye kya hai + example" ke saath samjhaya hai:

- **Lambda function** — khud ka chhota code jo cloud me chalta hai
- **Serverless** — "server ka jhanjhat nahi" wala matlab
- **Runtime** — code kis bhasha me hai (Python/Node...)
- **Handler** — code ka wo darwaza jaha se chalna shuru hota hai
- **Trigger** — wo cheez jo Lambda ko "chal ja bhai" bolti hai
- **Event** — Lambda ko milne wali "parchi" (kya hua, kaha hua)
- **IAM Role** — Lambda ki apni ID-card + permission (User se ALAG)
- **CloudWatch Logs** — Lambda ki diary (kya-kya hua likha rehta hai)

---

## ✅ Aaj Ka Target

Din ke end me tumhare paas hoga:
- Ek chalta-firta Lambda function ✅
- Jo S3 me file aate hi **khud chal jaye** ✅
- Aur uske logs padhna aa jaye ✅

> Chalo, File 1 se shuru karo → [`01-lambda-kya-hai-concept.md`](./01-lambda-kya-hai-concept.md) 🚀
