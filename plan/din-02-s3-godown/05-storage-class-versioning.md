# 5️⃣ Storage Classes + Versioning (Good-To-Know) 📦

> Ye "extra" hai par interview aur real kaam me poochha jaata hai.
> Sirf **samajhna** hai — ratna nahi. 15–20 min me ho jayega.

📖 Storage classes docs: https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage-class-intro.html
📖 Versioning docs: https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html
📖 Lifecycle docs: https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html

---

## 📦 PART A — Storage Classes ("File Rakhne Ke Alag Plan")

**Real-life example:** Saamaan rakhne ke alag tareeke:
- **Ghar ki almari** = jo cheez roz chahiye (turant nikaal lo, par mehngi jagah).
- **Store room** = kabhi-kabhi chahiye (thodi door, par sasti).
- **Bank locker / godown baahar** = saalon me ek baar chahiye (sabse sasta, par nikaalne me time).

**S3 me bhi waise hi "classes" hain** — jitna kam use, utna sasta:

| Storage Class | Kab Use | Aasaan Matlab |
|---------------|---------|---------------|
| **S3 Standard** | Roz use hone wala data | Almari — turant, thoda mehnga (default) |
| **S3 Standard-IA** (Infrequent Access) | Mahine me kabhi-kabhi | Store room — sasta, par nikaalne pe thoda charge |
| **S3 Intelligent-Tiering** | Pata nahi kitna use hoga | AWS khud decide karta hai kaunsa plan — smart! |
| **S3 Glacier / Deep Archive** | Saalon purana backup | Bank locker — sabse sasta, nikaalne me minute/ghante |

> 💡 **Kahan dikhta hai:** Upload karte waqt ya object ki **Properties** me "Storage class" option milta hai.
> **Beginner rule:** Standard hi rehne do. Bade paise bachane ke liye baaki classes hoti hain.

---

## 🕰️ PART B — Versioning ("File Ka Purana Version Bacha Ke Rakhna")

**Real-life example:** Word/Google Docs me "version history" hoti hai na — galti se kuch delete/edit ho jaye to purana wapas la sakte ho. **Versioning wahi hai.**

**Bina versioning:** file edit/delete ki → purani hamesha ke liye gayi. ❌
**Versioning ON:** har badlav ka **purana version bhi save** rehta hai → kabhi bhi wapas la sakte ho. ✅

### Versioning ON Karke Dekho:
1. Bucket → **"Properties"** tab → **"Bucket Versioning"** → **Edit** → **Enable** → Save.
2. Ab ek file (jaise `sales.csv`) me thoda change karke **dobara upload** karo (same naam).
3. Object me **"Versions"** toggle/show karo → **do version** dikhenge (purana + naya). 🎉
4. Galti se delete kiya to bhi "delete marker" ke peechhe purani version bachi rehti hai — wapas la sakte ho.

> ⚠️ **Case:** Versioning har version ka **storage count karta hai** — matlab thoda zyada jagah (aur Free Tier me thoda zyada). Practice ke baad extra versions delete kar dena.

---

## 🔄 PART C — Lifecycle Rule (Bonus, Bas Idea)

**Real-life:** "30 din purana saamaan store room me daal do, 1 saal purana godown bhej do, 2 saal purana phenk do" — ye rule automatic.

**S3 Lifecycle rule** wahi karta hai automatically:
- "30 din baad file ko Standard-IA me daal do" (sasta).
- "1 saal baad Glacier me daal do."
- "2 saal baad delete kar do."

**Kahan:** Bucket → **"Management"** tab → **"Create lifecycle rule"**.

> 💡 Abhi banane ki zaroorat nahi — bas jaan lo ki "purani files ko automatic sasta/delete karne ka tareeka hai". Companies isse **bahut paisa** bachati hain.

---

## 🧠 Interview Ke Liye 3 One-Liner

1. **Storage class** = "file kitni baar use hoti hai, uske hisaab se sasta/mehnga plan."
2. **Versioning** = "file ke purane versions bacha ke rakhna, galti se recover karne ke liye."
3. **Lifecycle rule** = "purani files ko automatic sasti class me daalna ya delete karna."

---

## ✅ Is Step Ka "Ho Gaya" Check

- [ ] Storage classes ka idea (Standard vs IA vs Glacier)
- [ ] Versioning ON karke 2 version dekhe
- [ ] Lifecycle rule kya karta hai — pata hai
- [ ] Practice ke extra versions/files delete kar diye (jagah safe)

> ➡️ Ab last file: checklist + errors + doc links → [`06-checklist-aur-galtiyan.md`](./06-checklist-aur-galtiyan.md)
