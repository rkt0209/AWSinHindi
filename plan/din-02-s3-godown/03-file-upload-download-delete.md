# 3️⃣ File Upload / Download / Delete + Folders

> Ab godown me saamaan rakhna aur nikaalna seekho. Ye roz kaam aayega.

📖 Upload objects docs: https://docs.aws.amazon.com/AmazonS3/latest/userguide/upload-objects.html
📖 Download objects docs: https://docs.aws.amazon.com/AmazonS3/latest/userguide/download-objects.html

---

## 🪜 PART A — File Upload Karo

### Step 1 — Bucket Kholo
- S3 → apne bucket ke naam pe click → **"Objects"** tab (default yahi khulta hai).

### Step 2 — Upload Dabao
- **"Upload"** button (right upar ya beech me) dabao.

**🖥️ Screen pe:** "Upload" page — do button: **"Add files"** aur **"Add folder"**.

### Step 3 — File Chuno
- **"Add files"** dabao → apni test file (jaise `sales.csv`) chuno → **Open**.
- File list me dikhne lagegi (naam + size).

### Step 4 — Upload Karo
- Sabse neeche **"Upload"** button dabao.

**🖥️ Screen pe:** Upload hone lagega, phir green **"Upload succeeded"** ✅ dikhega. **"Close"** dabao.

- Ab bucket me tumhari file dikhne lagegi. 🎉

> ⚠️ **Case: bahut badi file / net slow** → upload ruk sakta hai. Chhoti file se practice karo. AWS bade file ke liye "multipart upload" khud kar leta hai.

---

## 🪜 PART B — File Ki Jaankari Dekho

- File ke **naam pe click** karo.

**🖥️ Screen pe:** File ka detail page — **Object URL**, size, type, date, etc.

> ⚠️ **Object URL pe click karoge to "Access Denied" aayega** — ye **bilkul sahi hai!** Kyunki bucket private hai (Block Public Access ON). File tumhari hai, par internet se open nahi hogi. (Public karna File 4 me.)

---

## 🪜 PART C — File Download Karo

Do tareeke:
1. File ke naam pe click → upar **"Download"** button dabao. **✅ Ye sahi tareeka** (private file bhi download ho jaati hai kyunki tum owner ho).
2. Ya Objects list me file ke aage checkbox tick → **"Download"**.

**🖥️ Screen pe:** File tumhare computer me download ho jayegi (browser ke downloads me).

---

## 🪜 PART D — Folder Banao (Data Ko Organize Karo)

Aage Din 4 (Glue) me kaam aayega. Do folder banao:

### Step 1 — Create Folder
- Bucket ke Objects tab me **"Create folder"** button dabao.
- Folder name: `raw-data` daalo → **"Create folder"**.
- Aise hi ek aur banao: `clean-data`.

**🖥️ Screen pe:** Ab bucket me 2 folder dikhenge: `raw-data/` aur `clean-data/`.

### Step 2 — Folder Ke Andar File Daalo
- `raw-data/` folder pe click → **Upload** → apni `sales.csv` daalo.
- Ab is file ka **Key** = `raw-data/sales.csv` ho gaya (poora address).

> 💡 Yaad rakho (File 1 se): folder asal me naam ka hissa (prefix) hai. `raw-data/sales.csv` = poora key.

---

## 🪜 PART E — File / Folder Delete Karo

> ⚠️ Delete **permanent** hota hai (versioning off hai to wapas nahi aati). Dhyaan se.

- File ke aage checkbox tick karo → upar **"Delete"** button dabao.
- Confirm ke liye box me **`permanently delete`** likhna padta hai → **"Delete objects"** dabao.

**🖥️ Screen pe:** "Successfully deleted" ✅

> ⚠️ **Case: bucket delete karna hai** → pehle uske andar ki **saari files delete** karni padti hain, tabhi khaali bucket delete hota hai. (Bharā bucket delete nahi hota.)

---

## 🧪 Chhoti Practice (Khud Karo)

1. `sales.csv` upload karo → download karo → delete karo → dobara upload karo.
2. `raw-data/` aur `clean-data/` folder banao.
3. `sales.csv` ko `raw-data/` ke andar daalo.

Itna aankh band karke aa gaya to S3 ka basic **pakka** ho gaya. 💪

---

## ⚠️ Common Cases / Errors

| Case | Solution |
|------|----------|
| **Object URL pe "Access Denied"** | Normal hai — bucket private hai. Download button use karo, URL nahi. |
| **Upload pe "Access Denied"** | IAM user me S3 write permission nahi (`AmazonS3FullAccess` check karo). |
| **File dikh nahi rahi upload ke baad** | Galat folder me ho sakti hai; ya "Refresh" (🔄) dabao. Region bhi check karo. |
| **Delete nahi ho raha (bucket)** | Pehle andar ki files delete karo, phir bucket. |
| **Galti se delete kar di** | Versioning off tha to wapas nahi aayegi. (File 5 me versioning se ye bachta hai.) |

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] File upload/download/delete kar liya
- [ ] `raw-data/` aur `clean-data/` folder ban gaye
- [ ] `sales.csv` ko `raw-data/` me daala
- [ ] "Object URL pe Access Denied = normal" samajh gaye

> ➡️ Ab File 4: Public vs Private — security samjho → [`04-permission-security.md`](./04-permission-security.md)
