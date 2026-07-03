# 4️⃣ Public vs Private — S3 Security 🔒

> Ye file dhyaan se padho. Duniya me **sabse badi data-leak galtiyan** S3 bucket galti se
> "public" chhod dene se hoti hain. Tum ye galti kabhi nahi karoge. 💪

📖 Block Public Access docs: https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html
📖 Bucket policy docs: https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucket-policies.html

---

## 🤔 Private vs Public — Aasaan Farak

**Real-life example:**
- **Private locker** 🔒 = sirf tum (aur jisko chaabi do) khol sakte ho. **Default S3 aisa hi hai.**
- **Public notice board** 📢 = raaste pe chalne wala koi bhi padh sakta hai. (Kabhi-kabhi zaroori, jaise website ki images.)

**S3 me by default sab PRIVATE hai** — yahi safe hai. Public sirf **soch-samajh ke** karte hain.

---

## 🛡️ "Block Public Access" — Tumhara Main Guard

Ye ek **master switch** hai. Jab ON (default), to bucket galti se bhi public nahi ho sakta.

**Kahan dekho:** Bucket → **"Permissions"** tab → **"Block public access (bucket settings)"** section. Yahan chaar setting ON dikhengi = "Block all public access: On" ✅.

> 💡 **Rule:** Jab tak koi khaas reason na ho, **ye ON hi rakho.** 99% cases me isko chhedne ki zaroorat nahi.

---

## 🔑 Permission Kaun-Kaun Se Tareeke Se Milti Hai?

S3 me access control ke 3 tareeke (bas naam jaan lo):

| Tareeka | Aasaan Matlab | Kab |
|---------|---------------|-----|
| **IAM Policy** | "Ye USER kya kar sakta hai" (Din 1 wali) | Apne users ke liye — sabse common |
| **Bucket Policy** | "Is BUCKET pe kaun kya kar sakta hai" (JSON me likhi) | Poore bucket ke rule; public karne ke liye bhi |
| **ACL** | Purana tareeka (ab off/recommended nahi) | Modern setup me use nahi karte |

> 💡 Beginner ko: **IAM policy** yaad rakho (users ke liye). **Bucket policy** tab jab poore bucket ke liye rule chahiye.

---

## 🧪 (Optional) Ek File Public Karke Dekho — Phir Turant Wapas Private

> ⚠️ Sirf **seekhne** ke liye, ek **bekaar test file** pe. Asli/personal data pe **kabhi mat** karo.

Modern S3 me file public karne ke liye **do** cheezein karni padti hain (isliye galti se public hona mushkil — accha hai):

**Step 1 — Block Public Access off karo (bucket level):**
- Bucket → Permissions → "Block public access" → **Edit** → "Block all public access" ka tick hatao → Save → confirm me `confirm` likho.

**Step 2 — Bucket Policy lagao (poore bucket ko read-public banane wali):**
- Permissions tab → "Bucket policy" → **Edit** → ye JSON daalo (`BUCKET-NAAM` apna daalo):
  ```json
  {
    "Version": "2012-10-17",
    "Statement": [
      {
        "Sid": "PublicRead",
        "Effect": "Allow",
        "Principal": "*",
        "Action": "s3:GetObject",
        "Resource": "arn:aws:s3:::BUCKET-NAAM/*"
      }
    ]
  }
  ```
- **Save changes** dabao.

**Ab test:** us file ka **Object URL** browser me kholo → **ab file khul jayegi** (public ho gayi). 🎉

**🖥️ Screen pe:** Bucket ke naam ke aage laal **"Publicly accessible"** likha aa jayega — ye AWS ki warning hai ki "bhai ye public hai, dhyaan rakhna".

**Step 3 — Turant Wapas Private Karo (IMPORTANT):**
- Bucket policy **delete** kar do (Edit → sab hata ke Save).
- Block Public Access dobara **ON** kar do.
- Ab file dobara private ✅.

> 💡 Isse tumne khud dekh liya ki public/private kaise hota hai — bina kisi risk ke.

---

## ⚠️ Zaroori Cases / Galtiyan

| Case | Solution / Samajh |
|------|-------------------|
| **Bucket pe laal "Publicly accessible"** | Koi cheez public hai. Zaroorat na ho to Block Public Access ON karo. |
| **"Access Denied" file kholne pe** | Bucket private hai (default) — ye **sahi** hai, galti nahi. |
| **Bucket policy save nahi ho rahi** | Block Public Access ON hone pe public policy block hoti hai. Pehle wo off karni padti hai (soch-samajh ke). |
| **JSON me error** | `BUCKET-NAAM` sahi daalo, `/*` lagana mat bhoolo (files ke liye), comma/bracket check karo. |
| **Personal data galti se public** | Turant Block Public Access ON + policy delete. |

---

## 🧠 Yaad Rakhne Wali 3 Baatein

1. **Default private = safe.** Isko aise hi rehne do jab tak zaroorat na ho.
2. **Public karne ke 2 lock** todne padte hain (Block Public Access off + Bucket Policy) — isliye galti mushkil.
3. **"Access Denied" hamesha bura nahi** — matlab security kaam kar rahi hai.

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Block Public Access ka matlab samajh gaye
- [ ] IAM policy vs Bucket policy vs ACL — farak pata hai
- [ ] (Optional) ek test file public-private karke dekhi
- [ ] Samajh gaye: default private = safe, public soch-samajh ke

> ➡️ Ab File 5: Storage classes + versioning (good-to-know) → [`05-storage-class-versioning.md`](./05-storage-class-versioning.md)
