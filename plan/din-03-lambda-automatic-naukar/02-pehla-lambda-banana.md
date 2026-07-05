# 2️⃣ Apna Pehla Lambda Function Banao 🛠️

> Ab machine chala ke dekhte hain. Step-by-step, har step ka **screen output** bhi diya hai.
> Ghabrana nahi — koi galti hui to File 6 me har error ka solution hai. 💪

📖 Pehla Lambda banana (official): https://docs.aws.amazon.com/lambda/latest/dg/getting-started.html

---

## 🧭 Step 0 — Console Me Lambda Kaha Milega?

1. AWS Console me login (Din 1 wala **IAM user**, root nahi).
2. Upar-right me **Region** dekho — **Mumbai (ap-south-1)** hona chahiye (Din 1/2 jaisa hi).
3. Upar **search bar** me `Lambda` type karo → **Lambda** pe click.

**🖥️ Screen pe:** Lambda ka home page — beech me/right me orange **"Create function"** button dikhega.

---

## 🔑 SABSE PEHLE — Permission Check (Warna Ye Error Aayega)

> ⚠️ **Ye box zaroor padho — bahut log yahi atakte hain.**
> Lambda banate waqt AWS ek **naya role (wardi)** bhi banata hai (File 1 me role = machine ki wardi wala box yaad karo). Agar tumhare Din 1 wale IAM user ke paas **role banane ki permission nahi**, to ye error aata hai:
>
> ```
> User: arn:aws:iam::842756176543:user/rohit-iam-dev is not authorized to
> perform: iam:CreateRole ... because no identity-based policy allows the
> iam:CreateRole action
> ```
>
> **Matlab (aasaan):** "Tumhe Lambda banane ki permission to hai, par uski **wardi (role) banane** ki nahi." Din 1 me humne user ko sirf **S3** wali permission di thi — Lambda/role wali nahi.

### 📦 Ye Kya Hai: `iam:CreateRole`

**Definition:** `iam:CreateRole` ek **permission ka naam** hai jiska matlab — "ye user nayi **role (wardi)** bana sakta hai." Lambda ko chalane ke liye ek role chahiye, aur console tumhare liye wo role **banane ki koshish** karta hai — par banane ke liye ye permission user ke paas honi chahiye.

**Example:** Naya employee (Lambda) join kar raha hai, use ID-card (role) chahiye. Par ID-card **banane** ka haq sirf HR ke paas hai. Tum (user) HR nahi ho, isliye "ID-card nahi bana sakte" — yahi error hai.

### 🛠️ Isko Theek Kaise Karein (Permission Do)

Permission dena bada kaam hai, isliye ye **root user** (ya kisi admin) se hoga:

1. **Root user** se AWS Console me login karo (Din 1 wala main email/password wala).
2. Upar search me **`IAM`** → **IAM** → left me **"Users"** → apne user **`rohit-iam-dev`** pe click.
3. **"Add permissions"** (ya "Permissions" tab → "Add permissions") → **"Attach policies directly"** chuno.
4. Search karke ye **do policy** tick karo:
   - **`AWSLambda_FullAccess`** → Lambda banane/chalane ke liye
   - **`IAMFullAccess`** → role (wardi) banane ke liye ← **ye error isi ke bina aaya tha**
5. **"Next" → "Add permissions"** dabao.
6. Ab **wapas `rohit-iam-dev`** se login karke Lambda banao — ab chalega. ✅

> ⚠️ **Chhoti si safety baat:** `IAMFullAccess` kaafi **powerful** hai (poore IAM pe control). **Seekhne** ke liye theek hai. Asli company me itni badi permission nahi dete — wahan sirf utni hi denge jitni chahiye (neeche "safe tareeka" dekho).

<details>
<summary>🔒 (Optional) Safe/Targeted Tareeka — sirf utni permission jitni chahiye</summary>

`IAMFullAccess` ki jagah ek **custom policy** bana ke sirf role-banane wali permission do. IAM → Policies → Create policy → JSON → ye daalo (account number apna):

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "LambdaKeLiyeRoleBanane",
      "Effect": "Allow",
      "Action": [
        "iam:CreateRole",
        "iam:AttachRolePolicy",
        "iam:PutRolePolicy",
        "iam:PassRole",
        "iam:GetRole"
      ],
      "Resource": "arn:aws:iam::842756176543:role/service-role/*"
    }
  ]
}
```

Isko `AWSLambda_FullAccess` ke saath user pe attach karo. Ye sirf Lambda ke role (`service-role/`) tak simit hai — zyada safe.
</details>

---

## 🪜 Step 1 — Create Function Dabao

- **"Create function"** button dabao.

**🖥️ Screen pe:** ek page khulega jisme upar 3 option (cards) honge:
- **Author from scratch** ✅ (ye chuno — khaali se apna banayenge)
- Use a blueprint (ready-made template — abhi nahi)
- Container image (advanced — abhi nahi)

> **Author from scratch** hi rehne do (by default yahi selected hota hai).

---

## 🪜 Step 2 — Basic Jaankari Bharo

Neeche form aayega:

| Field | Kya Daalo | Samajh |
|-------|-----------|--------|
| **Function name** | `mera-pehla-lambda` | Koi bhi naam (space nahi, dash chalega) |
| **Runtime** | **Python 3.12** (ya jo latest Python dikhe) | Humara code Python me hai ([runtime kya hai — File 1 box](./01-lambda-kya-hai-concept.md)) |
| **Architecture** | `x86_64` (default) | Chhedना nahi, default theek |

**Permissions section** (thoda neeche, "Change default execution role" pe click karke dikhta hai):
- Default option **"Create a new role with basic Lambda permissions"** hi rehne do. ✅

> 📦 **Yaad karo (File 1):** ye "role" hi Lambda ki **wardi** hai. AWS khud ek basic wardi bana dega jisme "logs likhne" ki permission hoti hai. Isliye alag se kuch nahi karna abhi.

---

## 🪜 Step 3 — Create Dabao

- Neeche orange **"Create function"** button dabao.

**🖥️ Screen pe:**
- Thodi der loading, phir upar green ribbon: **"Successfully created the function mera-pehla-lambda"** ✅
- Ek naya page khulega — tumhare function ka **dashboard**.
- Neeche **"Code source"** naam ka editor dikhega jisme pehle se thoda Python code likha hoga:

```python
import json

def lambda_handler(event, context):
    # TODO implement
    return {
        'statusCode': 200,
        'body': json.dumps('Hello from Lambda!')
    }
```

> 🎉 **Mubarak ho!** Tumhara pehla Lambda ban gaya. Ye abhi kuch khaas nahi karta — bas "Hello from Lambda!" wapas karta hai. Ab isme apna chhota kaam daalte hain.

---

## 🪜 Step 4 — Code Thoda Apna Karo (Optional Par Mazedaar)

Editor me code ko **badal ke** ye daalo (copy-paste):

```python
import json

def lambda_handler(event, context):
    print("Naukar jaag gaya! Kaam shuru.")     # ye CloudWatch Logs me dikhega
    naam = "Intern"
    message = f"Namaste {naam}, tumhara Lambda chal gaya!"
    print(message)
    return {
        'statusCode': 200,
        'body': json.dumps(message)
    }
```

**Samajh (line-by-line, aasaan):**
- `def lambda_handler(event, context):` → **handler** (main darwaza — File 1 box). AWS yahi se shuru karta hai.
- `print(...)` → diary (CloudWatch Logs) me likh dega. Debugging ka tareeka.
- `event` → wo **parchi** (File 1 box) — abhi khaali hai kyunki hum khud test karenge.
- `return {...}` → kaam ka **jawab** (result) wapas bhejta hai.

---

## 🪜 Step 5 — Deploy Dabao (Zaroori!)

> ⚠️ Code likhne se kaam nahi hota — **"Deploy"** dabana padta hai, tabhi naya code "lag" jata hai.

- Editor ke upar **"Deploy"** button (ya `Ctrl+S`) dabao.

**🖥️ Screen pe:** upar green: **"Successfully updated the function"** ✅. Ab tumhara naya code live hai.

> 💡 **Deploy = "save + lagana".** Har baar code badlo to Deploy dabana zaroori, warna purana hi chalega.

---

## ⚠️ Common Cases / Errors

| Case | Solution |
|------|----------|
| **"Create function" par Access Denied** | IAM user ke paas Lambda permission nahi. Root se ya admin se `AWSLambda_FullAccess` policy lagwao. |
| **Runtime me Python nahi dikh raha** | List me scroll karo — "Python 3.12 / 3.11" milega. Koi bhi Python chalega. |
| **Code badla par purana chal raha** | **Deploy** dabana bhool gaye. Deploy karo phir chalao. |
| **Galat Region me bana diya** | Koi baat nahi, delete karke Mumbai me dobara bana lo (ya wahi region me kaam karo). |
| **Function name already exists** | Tumhare account me wahi naam pehle se hai — thoda alag naam do (`mera-pehla-lambda-2`). |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] `mera-pehla-lambda` function ban gaya (green success dikha)
- [ ] Runtime = Python chuna
- [ ] Default role (wardi) apne aap ban gaya
- [ ] Apna chhota code daal ke **Deploy** kiya
- [ ] Samajh gaye: Deploy = save + lagana

> ➡️ Ab ise chala ke dekhte hain aur logs padhte hain → [`03-lambda-test-run.md`](./03-lambda-test-run.md) ▶️
