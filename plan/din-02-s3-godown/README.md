# 📅 DIN 2 — S3: Internet Ka Godown 🗄️

> Aaj ka goal: **File rakhna aur nikaalna seekho.** S3 baaki sabki neenv hai —
> Lambda, Glue, EMR sab S3 ka hi data use karte hain. Isliye ye pakka karo.
>
> ⏱️ Time: 3–4 ghante | 😌 Mushkil: 🟢 Aasaan | 💰 Kharcha: ₹0 (Free Tier: 5GB free)

---

## 🎯 Aaj Ke Baad Tumhe Ye Sab Aayega

- [ ] S3 kya hai + Bucket/Object/Key ka matlab (real-life se)
- [ ] Apna pehla **bucket** banaya (naming rules ke saath)
- [ ] File **upload, download, delete** karna aa gaya
- [ ] Folder structure banaya (`raw-data/`, `clean-data/`)
- [ ] Bucket ki **security** (public vs private) samajh gaye
- [ ] Storage classes + versioning ka basic idea (good-to-know)

> Itna ho gaya to Din 2 **100% complete**. Kal Din 3 (Lambda).

---

## 📂 Is Folder Ki Files (Isi Order Me Karna)

| # | File | Kya Karoge |
|---|------|-----------|
| 1️⃣ | [`01-s3-kya-hai-concept.md`](./01-s3-kya-hai-concept.md) | S3 ka concept — Bucket, Object, Key aasaan bhasha me |
| 2️⃣ | [`02-bucket-banana.md`](./02-bucket-banana.md) | Apna pehla bucket step-by-step banao |
| 3️⃣ | [`03-file-upload-download-delete.md`](./03-file-upload-download-delete.md) | File upload/download/delete + folders |
| 4️⃣ | [`04-permission-security.md`](./04-permission-security.md) | Public vs Private — security (bahut zaroori) |
| 5️⃣ | [`05-storage-class-versioning.md`](./05-storage-class-versioning.md) | Storage classes + versioning (good-to-know) |
| 6️⃣ | [`06-checklist-aur-galtiyan.md`](./06-checklist-aur-galtiyan.md) | Final checklist + har error ka solution + doc links |

---

## 🧠 Aaj Ke 4 Zaroori Shabd (Pehle Ye Samjho)

| Shabd | Aasaan Matlab (Real-Life) |
|-------|---------------------------|
| **S3** | Internet ka **godown/warehouse** — kuch bhi rakho, kabhi bhi nikaalo |
| **Bucket** | Godown ka ek **bada kamra** (jiska naam poori duniya me unique hota hai) |
| **Object** | Us kamre me rakhi **ek cheez** (ek file — photo, CSV, video) |
| **Key** | Us cheez ka **poora naam/address** (jaise `raw-data/sales.csv`) |

> 💡 **Ek line:** Bucket = kamra, Object = us kamre me rakhi file, Key = us file ka address.

---

## ⚠️ Shuru Karne Se Pehle

1. **Din 1 wale IAM user se login karo** (root se nahi). Usme `AmazonS3FullAccess` pehle se laga hai. ✅
2. Region **Mumbai (ap-south-1)** set hai — top-right me check kar lo.
3. Ek chhoti test file ready rakho — ek **CSV ya Excel ya photo** (desktop pe). Agar CSV chahiye to Notepad me ye likh ke `sales.csv` naam se save kar lo:
   ```
   order_id,city,amount
   1,Mumbai,500
   2,Delhi,300
   3,Mumbai,700
   ```

---

➡️ Chalo File 1 se shuru: [`01-s3-kya-hai-concept.md`](./01-s3-kya-hai-concept.md)
