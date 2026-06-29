# Lesson 06 — Permissions (ফাইলের অনুমতি)

---

## 🎯 এই lesson-এ যা শিখবে
- Linux-এ কে কোন file-এ কী করতে পারে (read/write/execute)
- permission পড়তে শেখা (`rwxr-xr-x` মানে কী)
- permission বদলানো (`chmod`)
- মালিকানা বদলানো (`chown`)

> server-এ কাজ করলে এটা প্রতিদিন লাগবে। "Permission denied" error-এর সমাধানও এখানেই।

---

## ১. কেন permission দরকার?

একটা server-এ অনেক user থাকে। সবাই যেন সব file পড়তে/বদলাতে/মুছতে না পারে — তাই Linux প্রতিটা file-এ ঠিক করে দেয় **কে কী করতে পারবে**।

তিন ধরনের কাজ (permission):

| অক্ষর | মানে | file-এর ক্ষেত্রে | folder-এর ক্ষেত্রে |
|-------|------|----------------|---------------------|
| `r` | **read** (পড়া) | ভেতরের লেখা পড়া | ভেতরে কী আছে দেখা (`ls`) |
| `w` | **write** (লেখা) | পরিবর্তন/মোছা | ভেতরে file বানানো/মোছা |
| `x` | **execute** (চালানো) | program হিসেবে চালানো | folder-এ ঢোকা (`cd`) |

---

## ২. permission পড়া — `ls -l` এর মানে

```bash
$ ls -l
```

**Output:**
```
-rwxr-xr-x  1 foysal devteam  2048 Jun 29 10:00 script.sh
-rw-r--r--  1 foysal devteam   512 Jun 29 09:00 notes.txt
```

প্রথম অংশটা ভেঙে দেখি — `-rwxr-xr-x`:

```
-  rwx      r-x      r-x
│   │        │        │
│   │        │        └── অন্য সবাই (others)
│   │        └── group (একই দলের লোকেরা)
│   └── owner (মালিক)
└── type: -=file, d=folder
```

তিনটা ভাগ, প্রতিটায় ৩টা করে অক্ষর (rwx):

| কার জন্য | permission | মানে |
|----------|-----------|------|
| Owner (foysal) | `rwx` | পড়তে, লিখতে, চালাতে পারে |
| Group (devteam) | `r-x` | পড়তে ও চালাতে পারে, লিখতে পারে না |
| Others (বাকি সবাই) | `r-x` | পড়তে ও চালাতে পারে, লিখতে পারে না |

> `-` মানে ওই permission নেই। যেমন `r--` মানে শুধু read, write/execute নেই।

---

## ৩. `chmod` — permission বদলানো

**chmod** = **ch**ange **mod**e। দুইভাবে করা যায় — সংখ্যা দিয়ে আর অক্ষর দিয়ে।

### (ক) সংখ্যা দিয়ে (সবচেয়ে বেশি ব্যবহৃত)

প্রতিটা permission-এর একটা সংখ্যা আছে:

| permission | সংখ্যা |
|-----------|--------|
| `r` (read) | 4 |
| `w` (write) | 2 |
| `x` (execute) | 1 |

যোগ করে একেকজনের জন্য একটা সংখ্যা বানাও:

| চাই | হিসাব | সংখ্যা |
|-----|-------|--------|
| `rwx` | 4+2+1 | **7** |
| `rw-` | 4+2 | **6** |
| `r-x` | 4+1 | **5** |
| `r--` | 4 | **4** |

তিনজনের (owner, group, others) জন্য তিনটা সংখ্যা:

```bash
$ chmod 755 script.sh
```
মানে: owner=7(rwx), group=5(r-x), others=5(r-x) → `rwxr-xr-x`

```bash
$ chmod 644 notes.txt
```
মানে: owner=6(rw-), group=4(r--), others=4(r--) → `rw-r--r--`

> 📌 **মুখস্থ রাখার জন্য দুটো খুব কমন:**
> - `755` → program/script ও folder-এর জন্য (সবাই পড়া+চালানো, শুধু owner লিখতে পারে)
> - `644` → সাধারণ file-এর জন্য (owner লিখতে পারে, বাকিরা শুধু পড়ে)

### (খ) অক্ষর দিয়ে (সহজে মনে থাকে)

```bash
$ chmod +x script.sh
```
সবাইকে execute (চালানোর) permission দিল। একটা `.sh` script চালাতে হলে আগে এটা লাগে।

| লেখা | মানে |
|------|------|
| `chmod +x file` | execute permission যোগ |
| `chmod -w file` | write permission সরানো |
| `chmod u+x file` | শুধু owner-কে (u=user) execute |
| `chmod g-w file` | group থেকে write সরানো |

> u=user(owner), g=group, o=others, a=all

---

## ৪. `chown` — মালিকানা বদলানো

**chown** = **ch**ange **own**er। কোন user/group file-এর মালিক, সেটা বদলায়। (সাধারণত `sudo` লাগে — পরের lesson-এ।)

```bash
$ sudo chown foysal notes.txt
```
এখন `notes.txt`-এর মালিক হলো foysal।

owner ও group একসাথে বদলাতে:

```bash
$ sudo chown foysal:devteam notes.txt
```
মালিক = foysal, group = devteam।

---

## ৫. বাস্তব উদাহরণ: একটা script বানিয়ে চালানো

```bash
$ echo 'echo "Hello from script!"' > hello.sh
$ ./hello.sh
```

**Output:**
```
bash: ./hello.sh: Permission denied
```
😱 কারণ file-টায় execute (`x`) permission নেই। ঠিক করি:

```bash
$ chmod +x hello.sh
$ ./hello.sh
```

**Output:**
```
Hello from script!
```
✅ এখন চলল। **"Permission denied" দেখলেই মনে করবে `chmod +x` লাগবে কিনা।**

---

## ✅ Practice Task

1. `touch test.sh` দিয়ে file বানাও
2. `ls -l test.sh` দিয়ে এখনকার permission দেখো
3. `chmod 755 test.sh` দিয়ে বদলাও, আবার `ls -l` দিয়ে পার্থক্য দেখো
4. `chmod 644 test.sh` দিয়ে আবার বদলাও, দেখো `x` চলে গেছে
5. `echo 'echo "চলছে!"' > run.sh` → `chmod +x run.sh` → `./run.sh` চালাও

---

## 📌 সারসংক্ষেপ

| Command | কাজ |
|---------|-----|
| `ls -l` | permission দেখা |
| `chmod 755 file` | rwxr-xr-x সেট করা |
| `chmod 644 file` | rw-r--r-- সেট করা |
| `chmod +x file` | execute যোগ করা |
| `chown user file` | মালিক বদলানো |
| `chown user:group file` | মালিক+group বদলানো |

**সংখ্যা মনে রাখো:** r=4, w=2, x=1 → যোগ করো।

---

পরের lesson 👉 [Lesson 07 — User ও sudo](07-users-sudo.md)
