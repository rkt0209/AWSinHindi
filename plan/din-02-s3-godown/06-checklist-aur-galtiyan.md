# 6️⃣ Din 2 Final Checklist + Har Galti Ka Solution 🧾

> Sab tick ho gaya to Din 2 (S3) **pakka complete**. Neeche har common problem ka one-stop solution.

---

## ✅ Din 2 Master Checklist

**Concept:**
- [ ] S3 = internet ka godown — samajh gaye
- [ ] Bucket = kamra, Object = file, Key = address
- [ ] "Folder asli folder nahi, naam ka prefix hai"

**Bucket:**
- [ ] Apna bucket banaya (unique naam, Mumbai region)
- [ ] Naming rules pata hai (lowercase, no space/underscore, 3-63 char)
- [ ] Block Public Access ON rakha (private/safe)

**Files:**
- [ ] File upload / download / delete kiya
- [ ] `raw-data/` aur `clean-data/` folder banaye
- [ ] `sales.csv` ko `raw-data/` me daala

**Security:**
- [ ] Private vs Public samajh gaye
- [ ] "Object URL pe Access Denied = private = normal" clear hai
- [ ] IAM policy vs Bucket policy ka farak pata hai

**Good-to-know:**
- [ ] Storage classes ka idea (Standard/IA/Glacier)
- [ ] Versioning karke dekha
- [ ] Practice ka extra data delete kiya (jagah safe)

---

## 🧠 Din 2 Ki 5 Sabse Badi Seekh (Zubaani Yaad Rakho)

1. **S3 = internet ka unlimited godown; Bucket=kamra, Object=file, Key=address.**
2. **Bucket ka naam poori duniya me unique hota hai (lowercase, no space).**
3. **Default sab private/safe — public soch-samajh ke (2 lock todne padte hain).**
4. **"Access Denied" hamesha bura nahi — security kaam kar rahi hai.**
5. **Storage class = sasta/mehnga plan; Versioning = purana version bachana.**

---

## 🆘 Har Common Galti Ka Solution (One-Stop)

| Problem | Solution |
|---------|----------|
| **"Bucket name already exists"** | Naam duniya me le liya gaya. Date/apna naam jodo. |
| **"Invalid bucket name"** | Lowercase karo, space/underscore/capital hatao (3-63 char). |
| **Upload/Delete pe "Access Denied"** | IAM user me `AmazonS3FullAccess` policy check karo (Din 1). |
| **Object URL pe "Access Denied"** | Normal — bucket private hai. Download button use karo. |
| **File dikh nahi rahi** | Galat folder/Region? Refresh (🔄) dabao, Region Mumbai check karo. |
| **Bucket delete nahi ho raha** | Pehle andar ki saari files delete karo, phir bucket. |
| **Galti se file delete** | Versioning off tha to gayi. Aage se versioning ON rakho. |
| **Bucket galat Region me** | Region baad me nahi badalta — delete karke Mumbai me dobara banao. |
| **Bucket pe laal "Publicly accessible"** | Kuch public hai. Zaroorat na ho to Block Public Access ON. |
| **Bucket policy save nahi hoti** | Public policy ke liye pehle Block Public Access off karna padta hai. |

---

## 📚 Din 2 Ke Saare Documentation Links (Ek Jagah)

- S3 kya hai → https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html
- Getting Started → https://docs.aws.amazon.com/AmazonS3/latest/userguide/GetStartedWithS3.html
- Bucket banana → https://docs.aws.amazon.com/AmazonS3/latest/userguide/create-bucket-overview.html
- Naming rules → https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucketnamingrules.html
- File upload → https://docs.aws.amazon.com/AmazonS3/latest/userguide/upload-objects.html
- File download → https://docs.aws.amazon.com/AmazonS3/latest/userguide/download-objects.html
- Folders/prefixes → https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-folders.html
- Block Public Access → https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html
- Bucket policy → https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucket-policies.html
- Storage classes → https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage-class-intro.html
- Versioning → https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html
- Lifecycle → https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html

---

## 🎉 Din 2 Complete!

Agar upar sab ✅ hai, to **shabaash** — ab tumhare paas "godown" hai jahan data rakh-nikaal sakte ho. Ye baaki sabki neenv hai. 💪

Dimaag me picture:
> "Bucket banaya → file upload/download/delete ki → folders banaye → private/public samjha → versioning dekhi."

**Kal:** Din 3 — **Lambda (automatic naukar)** ⚡. Hum ek Lambda banayenge jo S3 me file aate hi apne-aap chal jaye. Aaj wale `raw-data/` folder ka wahin use hoga!

> Aaram karo, kal milte hain! 😴➡️🚀
