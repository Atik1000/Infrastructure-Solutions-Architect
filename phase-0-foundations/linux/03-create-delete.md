# Lesson 03 — File ও Folder তৈরি, কপি, সরানো ও মোছা

---

## 🎯 এই lesson-এ যা শিখবে
- নতুন folder বানানো (`mkdir`)
- খালি file বানানো (`touch`)
- file/folder কপি করা (`cp`)
- নাম বদলানো বা সরানো (`mv`)
- মুছে ফেলা (`rm`, `rmdir`)

---

## ১. `mkdir` — নতুন folder বানাও

**mkdir** = **m**a**k**e **dir**ectory।

```bash
$ mkdir myproject
$ ls
```

**Output:**
```
myproject
```

### একসাথে অনেক ধাপের folder বানাতে `-p`:

```bash
$ mkdir -p project/src/utils
```

এটা একবারেই `project`, ভেতরে `src`, তার ভেতরে `utils` — তিনটাই বানিয়ে দেবে। `-p` ছাড়া করলে error দিত, কারণ parent folder আগে থাকতে হতো।

---

## ২. `touch` — খালি file বানাও

```bash
$ touch notes.txt
$ ls
```

**Output:**
```
notes.txt
```

একসাথে কয়েকটাও বানানো যায়:

```bash
$ touch a.txt b.txt c.txt
```

> 💡 `touch` মূলত file-এর সময় (timestamp) আপডেট করার command, কিন্তু file না থাকলে নতুন খালি file বানিয়ে দেয় — তাই দ্রুত file বানাতে এটা ব্যবহার হয়।

---

## ৩. `cp` — file বা folder কপি করো

**cp** = **c**o**p**y। গঠন: `cp [কোনটা] [কোথায়]`

```bash
$ cp notes.txt backup.txt
$ ls
```

**Output:**
```
backup.txt  notes.txt
```

### folder কপি করতে `-r` (recursive) লাগে:

```bash
$ cp -r project project_copy
```
> folder-এর ভেতরে আরও file/folder থাকে, তাই `-r` দিয়ে বলতে হয় "ভেতরের সবকিছু সহ কপি করো"।

---

## ৪. `mv` — সরানো বা নাম বদলানো

**mv** = **m**o**v**e। এই একটাই command দুটো কাজ করে:

### (ক) নাম বদলানো:

```bash
$ mv notes.txt mynotes.txt
$ ls
```

**Output:**
```
mynotes.txt
```

### (খ) অন্য folder-এ সরানো:

```bash
$ mv mynotes.txt Documents/
```
এখন file টা `Documents` folder-এ চলে গেল।

> **মনে রাখো:** Linux-এ আলাদা "rename" command নেই — নাম বদলানো মানেই `mv` দিয়ে একই জায়গায় নতুন নামে সরানো।

---

## ৫. `rm` — file মুছে ফেলা

**rm** = **r**e**m**ove।

```bash
$ rm backup.txt
```
কোনো output আসবে না — চুপচাপ মুছে যাবে।

### folder মুছতে `-r`:

```bash
$ rm -r project_copy
```

### ⚠️ সাবধান — সবচেয়ে গুরুত্বপূর্ণ সতর্কতা

```bash
$ rm -rf folder_name
```
- `-f` = force (কোনো জিজ্ঞাসা ছাড়াই মুছবে)।
- Linux-এ **Recycle Bin নেই** — `rm` দিয়ে মুছলে file চিরতরে চলে যায়, ফেরত আনা যায় না।
- 🚫 **কখনো `rm -rf /` চালাবে না** — এটা পুরো system মুছে ফেলে! (অনেকের জীবনে ভয়ংকর ভুল এটাই।)

> 💡 নিরাপদে থাকতে `rm -i` ব্যবহার করো — প্রতিটা file মোছার আগে "মুছবে? (y/n)" জিজ্ঞেস করবে।

---

## ৬. `rmdir` — শুধু খালি folder মোছে

```bash
$ rmdir emptyfolder
```
folder-এর ভেতরে কিছু থাকলে এটা মুছবে না (নিরাপত্তার জন্য)। ভেতরে জিনিস থাকলে `rm -r` লাগবে।

---

## ✅ Practice Task

1. `mkdir practice` দিয়ে একটা folder বানাও, `cd practice` দিয়ে ভেতরে ঢোকো
2. `touch file1.txt file2.txt` দিয়ে দুটো file বানাও
3. `cp file1.txt copy1.txt` দিয়ে একটা কপি করো
4. `mv file2.txt renamed.txt` দিয়ে নাম বদলাও
5. `ls` দিয়ে সব দেখো
6. `rm copy1.txt` দিয়ে একটা মুছে ফেলো
7. বাইরে এসে (`cd ..`) `rm -r practice` দিয়ে পুরো folder মুছে ফেলো

---

## 📌 সারসংক্ষেপ

| Command | কাজ |
|---------|-----|
| `mkdir folder` | নতুন folder |
| `mkdir -p a/b/c` | একসাথে nested folder |
| `touch file` | নতুন খালি file |
| `cp a b` | file কপি |
| `cp -r a b` | folder কপি |
| `mv a b` | সরানো / নাম বদলানো |
| `rm file` | file মোছা |
| `rm -r folder` | folder মোছা |
| `rmdir folder` | খালি folder মোছা |

---

পরের lesson 👉 [Lesson 04 — File-এর ভেতরে দেখা ও লেখা](04-view-files.md)
