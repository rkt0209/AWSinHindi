# 2️⃣ 🔑 EMR Ke Liye Roles + Permissions (Do Role Lagte Hain)

> ⚠️ Ye file sirf **🅱️ hands-on** waalो ke liye. (🅰️ safe waale skip kar sakte hain.)
> EMR me Glue jaisi hi **do-layer** baat hai — par yaha **do alag role** chahiye. Ek baar set, phir smooth. 💪

📖 EMR IAM roles: https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-iam-roles.html

---

## 🤔 Pehle Samjho — EMR Me Kaun-Kaun Permission?

Yaad karo (Din 3/4): **User = insaan (tum)**, **Role = machine/service ki wardi**.

EMR me **teen** cheezein chahiye:

1. **Tumhe (User `rohit-iam-dev`)** — EMR console chalane + cluster banane ki permission.
2. **EMR service ko (Service Role)** — tumhari taraf se **cluster khadा karne** (EC2 machine maangna, manage karna) ki wardi.
3. **Cluster ki machine ko (EC2 Instance Profile Role)** — cluster ki **har machine** ko **S3 se data padhne/likhne** ki wardi.

> **Aasaan example:** Tum (user) **building ke malik** — kaam order karte ho. **Service Role** = **thekedar** ki chaabi (mazdoor bulana, site chalана). **EC2 role** = har **mazdoor** ki chaabi (godown/saamaan chhoone ke liye). Teeno bina kaam nahi.

> 😌 **Good news:** naye EMR console me cluster banate waqt ye dono role **"Create default roles"** se **ek click me apne aap** ban jate hain (`EMR_DefaultRole` + `EMR_EC2_DefaultRole`). Neeche dono tareeke diye hain.

---

## 🅰️ LAYER 1 — User (Tumhe) Ki Permission

**Root/admin se** (IAM → Users → `rohit-iam-dev` → Add permissions → Attach policies directly):

| Policy | Kis Kaam Ke Liye | Error Jo Batata Hai |
|--------|------------------|---------------------|
| **`AmazonEMRFullAccessPolicy_v2`** | EMR console + cluster banana/chalana | EMR pe "not authorized" |
| **`IAMFullAccess`** (Din 3 me mili) | EMR ko role dena (`iam:PassRole`) + default roles banana | `iam:PassRole` denied |
| **`AmazonS3FullAccess`** (Din 1 me mili) | S3 me input data + output rakhna | S3 Access Denied |
| **`AmazonEC2FullAccess`** | EMR peeche EC2 machine chala/band karta | EC2 authorization error |

> 📦 **Ye Kya Hai: `iam:PassRole`** (Din 4 me mila tha) — "kisi service (EMR) ko koi role **de dena/saunpna**." Jab tum EMR ko bolte ho "ye service-role aur ye EC2-role pehen ke cluster chala," to us "dene" ke liye ye permission chahiye. `IAMFullAccess` me hoti hai. **Example:** malik thekedar ko site ki chaabi **thama** raha — thamane ka haq = PassRole.

---

## 🅱️ LAYER 2 — Do EMR Roles (Sabse Aasaan: Auto-Create)

### 📦 Ye Kya Hai: **EMR Service Role** aur **EC2 Instance Profile**

**Definition:**
- **EMR Service Role** (`EMR_DefaultRole`) = wo wardi jo **EMR service khud** pehanta hai — cluster khada karne, EC2 machine maangне-manage karne ke liye.
- **EC2 Instance Profile** (`EMR_EC2_DefaultRole`) = wo wardi jo **cluster ki har machine (EC2 node)** pehanti hai — S3 se data padhne/likhne ke liye.

> 💡 **Instance Profile ka matlab:** "ek EC2 machine ko role pehnane ka tareeka." Machine seedhe role nahi pehen sakti, isliye role ko ek "profile" me lapet ke machine ko dete hain. (Bas itna samajh lo.)

### ✅ Tareeka A — Auto (Recommended, Ek Click)

Cluster banate waqt (File 3) **"Service role"** / **"Instance profile"** wale section me **"Create a default role" / "Create default roles"** ka option milta hai. Usse dono role (`EMR_DefaultRole` + `EMR_EC2_DefaultRole`) **apne aap ban jate hain** — tumhe kuch nahi karna. **Yahi use karo.**

### 🛠️ Tareeka B — Manually (Agar Auto Na Aaye)

**Service Role banao:**
- IAM → Roles → Create role → Trusted entity = **AWS service** → use case me **EMR** chuno → policy **`AmazonEMRServicePolicy_v2`** → naam `EMR_DefaultRole` → Create.

**EC2 Instance Profile role banao:**
- IAM → Roles → Create role → Trusted entity = **AWS service** → use case me **EC2** → policy **`AmazonElasticMapReduceforEC2Role`** (S3 access ke liye, chaho to `AmazonS3FullAccess` bhi) → naam `EMR_EC2_DefaultRole` → Create.

> 📦 **Trusted entity ka matlab** (Din 4 se yaad): "ye wardi **kaun** pehen sakta hai." Service role EMR pehnega, EC2 role EC2 machine pehnegi — isliye trusted entity alag-alag.

---

## ⚠️ Common Cases / Errors

| Case | Solution |
|------|----------|
| **EMR console "not authorized"** | User ko `AmazonEMRFullAccessPolicy_v2` attach karo (Layer 1). |
| **Cluster banate `iam:PassRole` denied** | User ko `IAMFullAccess`/PassRole — EMR ko role dene ke liye. |
| **"Create default roles" pe error** | User ko `IAMFullAccess` chahiye (role banane ke liye). |
| **Cluster start pe EC2 authorization fail** | User ko `AmazonEC2FullAccess`; EC2 role (`EMR_EC2_DefaultRole`) laga? |
| **Job pe "Access Denied (S3)"** | **EC2 role** me S3 permission missing (Layer 2 — machine ki wardi). |
| **Region alag** | EMR + S3 dono **Mumbai (ap-south-1)** me rakho. |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Layer 1: user pe `AmazonEMRFullAccessPolicy_v2` + IAMFullAccess + S3FullAccess + EC2FullAccess
- [ ] Layer 2: `EMR_DefaultRole` (service) + `EMR_EC2_DefaultRole` (EC2) taiyaar — auto ya manual
- [ ] `iam:PassRole` aur Instance Profile ka matlab samajh gaye
- [ ] EMR + S3 same region (Mumbai)

> ➡️ Ab chhota cluster banao → [`03-cluster-banana.md`](./03-cluster-banana.md) 🏗️
