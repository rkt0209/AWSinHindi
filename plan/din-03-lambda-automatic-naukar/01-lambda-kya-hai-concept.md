# 1️⃣ Lambda Kya Hai? — Concept (Aaram Se Samjho) ⚡

> Aaj sirf **samajhna** hai. Haath ka kaam File 2 se shuru hoga.
> Har nayi term ko **alag box** me "actually ye kya hai" karke samjhaya hai — ratna nahi, samajhna. 🧠

📖 Lambda kya hai (official): https://docs.aws.amazon.com/lambda/latest/dg/welcome.html

---

## 🥤 Sabse Pehle — Lambda Ka Real-Life Example

**Soch:** ek **vending machine** (wo automatic machine jisme paise/coin daalo aur cold-drink gir jaati hai). 🥤

- Machine **hamesha chalti nahi** rehti — bekaar bijli nahi jalti.
- Jaise hi tum **button dabate ho** (yaani "kaam aaya"), machine **jaagti hai**, drink deti hai, aur phir **so jaati hai**.
- Tumhe machine ke andar ka motor, wiring, kuch nahi dekhna — bas button aur drink.

**Lambda bilkul aisa hi hai:**
- Ye ek **chhota code** hai jo cloud me rehta hai.
- Jab tak koi "button" (kaam) nahi aata, ye **so raha hota hai** (paisa nahi lagta).
- Jaise hi kaam aata hai (jaise S3 me file aayi), ye **apne-aap jaagta hai**, kaam karta hai, phir **so jata hai**.
- Server, machine, setup — kuch nahi dekhna. Bas **apna code** likho.

> **Ek line:** Lambda = "kaam aane pe apne-aap chalne wala chhota code, jo warna so raha hota hai."

---

## 📦 Ye Kya Hai: **Lambda Function**

**Definition (crystal clear):** Lambda function = tumhara **apna likha hua chhota code** (ek chhota kaam karne wala), jo AWS ke computer pe **tumhare bina server sambhale** chalta hai.

- Ye "function" wahi hai jaisa programming me hota hai — kuch input lo, kaam karo, output do.
- Farak sirf itna: ise **tum apne laptop pe nahi**, AWS ke computer pe chalate ho, aur ye **kaam aane pe hi** chalta hai.

**Example:** ek code jo "jaise hi koi photo upload ho, uska chhota thumbnail bana do" — ye ek Lambda function ho sakta hai.

---

## 📦 Ye Kya Hai: **Serverless**

**Definition:** Serverless ka matlab "server hai hi nahi" **NAHI** hai. Matlab hai — "**server ka jhanjhat TUMHE nahi sambhalna**." Server chalta to hai (AWS ka), par uska rakh-rakhaav, on/off, size — sab AWS dekhta hai. Tum sirf code likhte ho.

**Example:** Ola/Uber me tumhe gaadi khareedni nahi padti, petrol/service nahi dekhni padti — bas "chalo" bolo, gaadi aa jati hai. Gaadi (server) hoti hai, par **tumhara sirdard nahi**. Yahi serverless hai.

---

## 📦 Ye Kya Hai: **Runtime**

**Definition:** Runtime = "tumhara code **kaunsi bhasha** me likha hai" — Python, Node.js (JavaScript), Java, etc. AWS ko batana padta hai taaki wo sahi bhasha wala environment de.

**Example:** Restaurant me tum bolte ho "mujhe South-Indian chef chahiye" ya "Punjabi chef chahiye" — taaki sahi khana bane. Runtime waise hi hai: "mera code Python hai" → AWS Python-wala setup de deta hai.

> 💡 Hum **Python** use karenge (aasaan hai, padhne me English jaisa lagta hai).

---

## 📦 Ye Kya Hai: **Handler**

**Definition:** Handler = tumhare code ka wo **exact darwaza (function ka naam)** jaha se AWS chalna **shuru** karta hai. Tumhare code me kai lines ho sakti hain, par AWS ko batana padta hai "yaha se ghusna."

**Example:** kisi building me kai kamre hain, par **main gate ek** hota hai jaha se sab andar aate hain. Handler wahi main gate hai. Python me by default iska naam `lambda_handler` hota hai.

```python
def lambda_handler(event, context):   # <-- YE hai handler (main darwaza)
    print("Main chal gaya!")
    return "Done"
```

---

## 📦 Ye Kya Hai: **Trigger**

**Definition:** Trigger = wo **cheez/ghatna jo Lambda ko bolti hai "ab chal ja bhai"**. Lambda khud se nahi chalta — koi na koi use "dhakka" deta hai. Wahi dhakka = trigger.

**Example:** Ghar ki **doorbell** 🔔. Tum ghar me baithe ho (so rahe ho = Lambda idle). Jaise hi koi bell bajata hai (trigger), tum uthke darwaza kholte ho (Lambda chal jata hai).

**Lambda ke common triggers:**
- **S3** — "file aayi/upload hui" → Lambda chala do (aaj yahi karenge!)
- **API Gateway** — "internet se request aayi" → Lambda chala do (Din 8 me)
- **Schedule** — "har roz subah 9 baje" → Lambda chala do
- **Step Functions** — "manager ne bola ab tera number" → Lambda chala do (Din 7)

---

## 📦 Ye Kya Hai: **Event**

**Definition:** Event = ek **parchi (data)** jo Lambda ko chalte waqt milti hai, jisme likha hota hai "**kya hua, kaha hua, kis cheez pe hua**". Lambda isi parchi ko padh ke kaam karta hai.

**Example:** Doorbell bajti hai (trigger), aur saath me ek **parchi** aati hai: "Ravi aaya hai, front gate pe, 5 baje." Ye parchi = event. Isse tumhe pata chalta hai kaun/kya aaya.

**S3 wala event aisa dikhta hai (asaan me):**
> "Bucket `mera-bucket` me, `raw-data/sales.csv` naam ki file, abhi-abhi upload hui."

Lambda code me ye `event` naam ke box (variable) me aata hai — `event` padh ke pata chal jata hai kaunsi file aayi.

---

## 📦 Ye Kya Hai: **IAM Role** (Ye User Se ALAG Hai — Dhyaan Se!)

> Din 1 me humne **IAM User** aur **IAM Policy** dekhi thi. **Role ek nayi cheez hai** — confuse mat hona, box padh lo.

**Definition:** IAM Role = ek **ID-card + permission set jo kisi INSAAN ka nahi, balki kisi MACHINE/SERVICE (jaise Lambda) ka hota hai**. Isme password/login nahi hota — ye "pehna" jata hai kaam ke waqt.

**User vs Role — ekdum clear farak:**

| Cheez | Kiske Liye | Login/Password? | Example |
|-------|-----------|-----------------|---------|
| **IAM User** | **Insaan** ke liye (tum) | Haan, login hota hai | Tum jo Din 1 me bana ke login karte ho |
| **IAM Role** | **Machine/Service** ke liye (Lambda, EC2) | Nahi, "pehna" jata hai | Lambda jo role pehen ke S3 padhta hai |

**Real-life example:** Socho ek **security guard ki wardi** 🦺. Wardi kisi ek aadmi ki nahi hoti — **jo bhi duty pe aata hai wo wardi pehen leta hai**, aur wardi ke saath aati hai "andar jaane ki permission". Lambda bhi kaam ke waqt ye "wardi (Role)" pehen leta hai, jisme likha hota hai "ye S3 padh sakta hai, logs likh sakta hai."

> 💡 **Ek line:** User = insaan ki ID (login wali). Role = machine/service ki wardi (login ke bina, kaam ke waqt pehni jane wali).

**Aur IAM Policy?** (Din 1 wali yaad karo) — Policy = ek **likha hua permission ka kaagaz** ("ye kaam allowed, ye nahi"). Ye kaagaz **User pe bhi chipka sakte ho aur Role pe bhi**. Yani:
- Policy = permission ki **list** (kaagaz).
- User/Role = wo **jisko** wo list di jati hai (insaan ya machine).

---

## 📦 Ye Kya Hai: **CloudWatch Logs**

**Definition:** CloudWatch Logs = Lambda (aur baaki AWS cheezon) ki **diary/register** — jab bhi Lambda chalta hai, wo "kya-kya hua", "kya print kiya", "koi error aaya kya" — sab yaha likh deta hai. Baad me tum ye diary padh ke samajh sakte ho ki andar kya hua.

**Example:** Hospital me har patient ki ek **file/register** hoti hai jisme roz likha jata hai "aaj ye dawai di, ye report aayi." Kuch gadbad ho to doctor wahi file dekhta hai. Lambda me kuch gadbad ho to hum **CloudWatch Logs** dekhte hain.

> 💡 Jo bhi tum code me `print("kuch")` karoge, wo CloudWatch Logs me dikhega. Debugging ka main tareeka yahi hai.

---

## 🖼️ Poori Picture — Ek Saath (S3 + Lambda)

```
   Tum file upload karte ho
        (raw-data/sales.csv)
              │
              ▼
   ┌─────────────────────┐
   │      S3 (godown)     │   Din 2 wala
   └─────────┬───────────┘
             │  "file aayi!" (ye TRIGGER hai)
             │  saath me parchi (ye EVENT hai)
             ▼
   ┌─────────────────────┐
   │   LAMBDA (naukar)    │   so raha tha, ab jaag gaya
   │   - Role pehna       │   (permission mili)
   │   - event padha      │   (kaunsi file aayi)
   │   - kaam kiya        │   (jaise: naam print kiya)
   └─────────┬───────────┘
             │  jo hua wo diary me likha
             ▼
   ┌─────────────────────┐
   │  CloudWatch Logs     │   (diary — baad me padh sakte ho)
   └─────────────────────┘
```

---

## ✅ Is File Ka "Ho Gaya" Check

- [ ] Lambda = "kaam aane pe apne-aap chalne wala code" — samajh gaye
- [ ] Serverless = "server ka jhanjhat AWS ka, tumhara nahi"
- [ ] Trigger (doorbell) vs Event (parchi) ka farak clear
- [ ] **IAM Role = machine ki wardi; User = insaan ki ID** — ye ekdum clear
- [ ] CloudWatch Logs = Lambda ki diary
- [ ] Runtime (Python) aur Handler (main darwaza) pata hai

> ➡️ Ab haath ka kaam: apna pehla Lambda banao → [`02-pehla-lambda-banana.md`](./02-pehla-lambda-banana.md) 🚀
