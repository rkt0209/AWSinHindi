# 6️⃣ Din 3 Final Checklist + Har Galti Ka Solution 🧾

> Sab tick ho gaya to Din 3 (Lambda) **pakka complete**. Neeche har common problem ka one-stop solution + saari nayi terms ek jagah.

---

## ✅ Din 3 Master Checklist

**Concept:**
- [ ] Lambda = "kaam aane pe apne-aap chalne wala code" (vending machine)
- [ ] Serverless = "server ka jhanjhat AWS ka"
- [ ] Trigger (doorbell) vs Event (parchi) ka farak clear
- [ ] IAM Role = machine ki wardi; User = insaan ki ID

**Function banana:**
- [ ] `mera-pehla-lambda` banaya (Python runtime)
- [ ] Apna code daal ke **Deploy** kiya
- [ ] Test event se chala ke "succeeded" dekha

**Logs:**
- [ ] Function Logs aur CloudWatch Logs (diary) padhi
- [ ] `print` wali lines logs me dikhi

**S3 Trigger (asli maza):**
- [ ] S3 ko trigger banaya (bucket + prefix `raw-data/`)
- [ ] File upload karke Lambda **apne-aap** chalaya
- [ ] Logs me file ka naam dikha

**Behind the scenes:**
- [ ] Execution role kaha hai — pata
- [ ] Timeout/Memory/Env variables ka idea

---

## 🧠 Din 3 Ki 5 Sabse Badi Seekh (Zubaani Yaad Rakho)

1. **Lambda = automatic naukar — kaam aane pe jaage, warna soye (aur tabhi paisa).**
2. **Trigger = doorbell (chalne ka reason); Event = parchi (kya/kaha hua).**
3. **Role = machine ki wardi; User = insaan ki ID — dono alag.**
4. **`print` = diary (CloudWatch Logs); debugging ka main tareeka.**
5. **Deploy dabाना zaroori — warna purana code chalta hai.**

---

## 📦 Saari Nayi Terms — Ek Jagah (Revision Box)

| Term | Ek Line Definition | Example |
|------|--------------------|---------|
| **Lambda function** | Kaam aane pe chalne wala chhota code | Vending machine |
| **Serverless** | Server ka jhanjhat AWS ka, tumhara nahi | Ola (gaadi tumhari nahi) |
| **Runtime** | Code kaunsi bhasha (Python) me hai | "South-Indian chef chahiye" |
| **Handler** | Code ka main darwaza (yaha se shuru) | Building ka main gate |
| **Trigger** | Lambda ko chalane wali cheez | Doorbell 🔔 |
| **Event** | Chalte waqt milne wali parchi (data) | "Ravi aaya, front gate, 5 baje" |
| **IAM Role** | Machine/service ki wardi (login nahi) | Guard ki wardi |
| **Execution role** | Lambda chalte waqt jo role pehanta hai | Lambda ki keychain |
| **CloudWatch Logs** | Lambda ki diary/register | Hospital patient file |
| **Log Group / Stream** | Poori diary / uska ek din ka page | Attendance register / roz ka page |
| **Timeout** | Max kitna time chalega | Exam ki ghanti |
| **Memory** | Kitni RAM/CPU (tezi) | Chhoti vs badi mez |
| **Env variables** | Code se bahar rakhi settings | TV ka remote |
| **Cold start** | Pehli baar jaagne me extra time | Subah bike start |

---

## 🆘 Har Common Galti Ka Solution (One-Stop)

| Problem | Solution |
|---------|----------|
| **"Create function" pe Access Denied** | IAM user ko `AWSLambda_FullAccess` (admin se) lagwao. |
| **Code badla par asar nahi** | **Deploy** dabana bhool gaye. Deploy karo. |
| **Test pe `KeyError: 'Records'`** | Test button ki nakli parchi me `Records` nahi — asli test **file upload** se karo. |
| **`Task timed out after 3.00 sec`** | Timeout badhao (Configuration → General configuration). |
| **File upload ki par Lambda nahi chala** | Sahi folder (`raw-data/`)? Suffix `.csv` set hai to `.csv` daalo. Latest log stream refresh. |
| **Logs me kuch nahi** | Refresh (🔄); latest log stream chuno; Region Mumbai check. |
| **`AccessDenied` S3 padhne pe** | Lambda ke **role** me S3 read policy jodo (File 5). |
| **Galat Region me function** | Delete karke Mumbai me dobara, ya usi region me kaam. |
| **Do-do baar chal gaya** | File baar-baar upload/replace hui — har create pe chalta hai. Normal. |
| **Infinite loop dar** | Sirf tab jab output usi bucket/prefix me daalo. Hum nahi daal rahe — safe. |

---

## 📚 Din 3 Ke Saare Documentation Links (Ek Jagah)

- Lambda kya hai → https://docs.aws.amazon.com/lambda/latest/dg/welcome.html
- Getting started → https://docs.aws.amazon.com/lambda/latest/dg/getting-started.html
- Function banana (console) → https://docs.aws.amazon.com/lambda/latest/dg/getting-started.html#getting-started-create-function
- Test karna → https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html
- CloudWatch logs → https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html
- S3 trigger tutorial → https://docs.aws.amazon.com/lambda/latest/dg/with-s3-example.html
- Execution role → https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html
- Configuration (memory/timeout) → https://docs.aws.amazon.com/lambda/latest/dg/configuration-function-common.html
- Environment variables → https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html
- Python me Lambda → https://docs.aws.amazon.com/lambda/latest/dg/lambda-python.html

---

## 🎉 Din 3 Complete!

Agar upar sab ✅ hai, to **shabaash!** 💪 Ab tumhare paas:
- Ek **godown (S3)** hai jaha data rakhte ho (Din 2), aur
- Ek **automatic naukar (Lambda)** hai jo file aate hi **khud kaam** karta hai (Din 3).

Dimaag me picture:
> "File S3 me aayi → doorbell baji → Lambda jaaga → parchi padhi → kaam kiya → diary me likha."

**Kal:** Din 4 — **Glue (data saaf karne wala)** 🧽. Aaj wale `raw-data/sales.csv` ko uthayenge, saaf karenge, aur `clean-data/` me daalenge. Aaj wali `raw-data/` `clean-data/` mehnat wahin kaam aayegi!

> Aaram karo, kal milte hain! 😴➡️🚀
