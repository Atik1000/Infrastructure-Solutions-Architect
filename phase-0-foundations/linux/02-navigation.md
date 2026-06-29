# Lesson 02 — File ও Folder Navigation

---

## 🎯 এই lesson-এ যা শিখবে
- Linux-এ folder structure কেমন
- তুমি এখন কোথায় আছো বের করা (`pwd`)
- কোন folder-এ কী আছে দেখা (`ls`)
- এক folder থেকে আরেক folder-এ যাওয়া (`cd`)

---

## ১. আগে বুঝি: Linux-এ folder সাজানো থাকে গাছের মতো

Windows-এ যেমন `C:\`, `D:\` থাকে — Linux-এ তেমন drive letter নেই। এখানে সব শুরু হয় একটা জায়গা থেকে: **`/`** (একে বলে **root**)।

```
/                  ← সব কিছুর শুরু (root)
├── home/
│   └── foysal/    ← তোমার home folder (এখানে তোমার সব file)
├── etc/           ← system-এর config file থাকে
├── var/           ← log, database ইত্যাদি
└── usr/           ← installed program
```

দুটো শব্দ মনে রাখো:
- **`/`** = root, সবকিছুর শুরু
- **`~`** = তোমার home folder (যেমন `/home/foysal`)

---

## ২. `pwd` — আমি এখন কোথায়?

**pwd** = **P**rint **W**orking **D**irectory। তুমি এখন কোন folder-এ দাঁড়িয়ে আছো সেটা দেখায়।

```bash
$ pwd
```

**Output:**
```
/home/foysal
```

মানে তুমি এখন তোমার home folder-এ আছো।

---

## ৩. `ls` — এই folder-এ কী কী আছে?

**ls** = **l**i**s**t। বর্তমান folder-এর ভেতরের file ও folder দেখায়।

```bash
$ ls
```

**Output:**
```
Desktop  Documents  Downloads  notes.txt  projects
```

### দরকারি option:

**`ls -l`** — বিস্তারিত তথ্য সহ দেখায় (permission, size, তারিখ):

```bash
$ ls -l
```

**Output:**
```
drwxr-xr-x  2 foysal foysal 4096 Jun 29 10:00 Desktop
drwxr-xr-x  2 foysal foysal 4096 Jun 29 10:00 Documents
-rw-r--r--  1 foysal foysal  220 Jun 28 09:15 notes.txt
```
> শুরুতে `d` থাকলে সেটা folder (directory), `-` থাকলে file।

**`ls -a`** — লুকানো file ও দেখায় (যেগুলোর নাম `.` দিয়ে শুরু):

```bash
$ ls -a
```

**Output:**
```
.  ..  .bashrc  .config  Desktop  Documents  notes.txt
```

**`ls -la`** — দুটো একসাথে (বিস্তারিত + লুকানো):

```bash
$ ls -la
```

> 💡 একাধিক option একসাথে লেখা যায়: `-la` মানে `-l` আর `-a` দুটোই।

---

## ৪. `cd` — অন্য folder-এ যাওয়া

**cd** = **c**hange **d**irectory।

```bash
$ cd Documents
$ pwd
```

**Output:**
```
/home/foysal/Documents
```

### দরকারি shortcut:

| Command | কাজ |
|---------|-----|
| `cd folder_name` | ওই folder-এ ঢোকো |
| `cd ..` | এক ধাপ পেছনে (parent folder-এ) যাও |
| `cd ~` | সোজা home folder-এ ফিরে যাও |
| `cd /` | একদম root-এ যাও |
| `cd -` | আগের যে folder-এ ছিলে সেখানে ফিরে যাও |

**উদাহরণ:**

```bash
$ cd ..
$ pwd
```

**Output:**
```
/home/foysal
```

---

## ৫. Absolute vs Relative path (গুরুত্বপূর্ণ ধারণা)

path দু-রকমভাবে লেখা যায়:

- **Absolute path:** `/` দিয়ে শুরু — root থেকে পুরো ঠিকানা।
  ```bash
  $ cd /home/foysal/Documents
  ```
- **Relative path:** তুমি এখন যেখানে আছো সেখান থেকে।
  ```bash
  $ cd Documents
  ```

> **মনে রাখার সহজ উপায়:** Absolute = তোমার বাড়ির পুরো ঠিকানা (দেশ, শহর, রোড)। Relative = "এখান থেকে দু বাড়ি পরে"।

---

## ✅ Practice Task

1. `pwd` দিয়ে দেখো তুমি কোথায় আছো
2. `ls` দিয়ে দেখো কী কী আছে
3. `ls -la` দিয়ে লুকানো file সহ বিস্তারিত দেখো
4. `cd Documents` (বা যেকোনো folder) দিয়ে ভেতরে ঢোকো, তারপর `pwd` দিয়ে নিশ্চিত হও
5. `cd ..` দিয়ে আবার বের হও
6. `cd ~` দিয়ে home-এ ফিরে যাও

---

## 📌 সারসংক্ষেপ

| Command | কাজ |
|---------|-----|
| `pwd` | আমি কোন folder-এ আছি |
| `ls` | folder-এর ভেতরে কী আছে |
| `ls -l` | বিস্তারিত তালিকা |
| `ls -a` | লুকানো file সহ |
| `cd folder` | folder-এ ঢোকা |
| `cd ..` | এক ধাপ পেছনে |
| `cd ~` | home-এ ফেরা |

---

পরের lesson 👉 [Lesson 03 — File ও Folder তৈরি/মোছা](03-create-delete.md)
