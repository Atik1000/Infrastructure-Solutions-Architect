# Lesson 01 — Linux কী ও Terminal পরিচিতি

---

## 🎯 এই lesson-এ যা শিখবে
- Linux আসলে কী, আর কেন infrastructure-এ এটা এত গুরুত্বপূর্ণ
- Terminal আর Shell বলতে কী বোঝায়
- প্রথম কয়েকটা command চালানো

---

## ১. Linux কী?

Linux হলো একটা **Operating System (OS)** — ঠিক যেমন Windows বা macOS। OS হলো সেই software যেটা তোমার computer-এর hardware (CPU, RAM, disk) আর তোমার program-এর মাঝে কাজ করে।

তাহলে Linux কেন শিখব?

- 🌐 পৃথিবীর প্রায় **সব server** Linux-এ চলে (AWS, Google, Facebook — সব)।
- 🐳 Docker, Kubernetes, Go server — সবকিছুর ভিত্তি Linux।
- 💰 এটা **ফ্রি ও open-source** — যে কেউ ব্যবহার ও পরিবর্তন করতে পারে।

> **সহজ কথায়:** তুমি যদি server, cloud বা DevOps-এ কাজ করতে চাও, Linux-এর terminal-এ কাজ করা **must**। মাউস দিয়ে নয়, লেখা command দিয়ে কাজ হয়।

---

## ২. Terminal আর Shell — পার্থক্য

দুটো শব্দ বারবার শুনবে, তাই এখনই পরিষ্কার করে নাও:

| শব্দ | মানে |
|------|------|
| **Terminal** | যে কালো window-তে তুমি লেখা টাইপ করো (এটা শুধু একটা box) |
| **Shell** | যে program তোমার লেখা command **বোঝে ও চালায়** (যেমন `bash`, `zsh`) |

**উদাহরণ দিয়ে বুঝি:** Terminal হলো খাতা, আর Shell হলো সেই লোক যে খাতায় লেখা পড়ে কাজ করে দেয়।

আজকাল বেশিরভাগ Linux-এ shell হিসেবে **bash** বা **zsh** থাকে। চিন্তা নেই — command প্রায় একই।

---

## ৩. Prompt কী?

Terminal খুললে এমন একটা লাইন দেখবে:

```
foysal@ubuntu:~$
```

এটাকে বলে **prompt**। ভেঙে দেখি:

| অংশ | মানে |
|-----|------|
| `foysal` | তোমার username (কে log in করেছে) |
| `ubuntu` | computer/server-এর নাম |
| `~` | তুমি এখন কোন folder-এ আছো (`~` মানে তোমার home folder) |
| `$` | তুমি সাধারণ user (`#` হলে তুমি root/admin) |

`$` চিহ্নের পরে তুমি command লিখবে। (এই lesson-গুলোতে `$` দেখলে বুঝবে এর পরেরটা হলো command, তুমি `$` টা টাইপ করবে না।)

---

## ৪. প্রথম command — চলো চালাই

### `whoami` — আমি কে?

তুমি এখন কোন user হিসেবে আছো সেটা দেখায়।

```bash
$ whoami
```

**Output:**
```
foysal
```

---

### `date` — এখন কত তারিখ ও সময়?

```bash
$ date
```

**Output:**
```
Mon Jun 29 14:32:10 +06 2026
```

---

### `echo` — স্ক্রিনে কিছু লেখা দেখাও

`echo` মানে "যা বলব তা ফেরত বলো"। program লেখার সময় খুব কাজে লাগে।

```bash
$ echo "Hello Linux"
```

**Output:**
```
Hello Linux
```

---

### `clear` — স্ক্রিন পরিষ্কার করো

স্ক্রিনে অনেক লেখা জমে গেলে পরিষ্কার করতে:

```bash
$ clear
```

**Output:** (স্ক্রিন ফাঁকা হয়ে যাবে, কিছু লেখা দেখাবে না)

> 💡 **শর্টকাট:** `clear` টাইপ না করে `Ctrl + L` চাপলেও স্ক্রিন পরিষ্কার হয়।

---

## ৫. কাজে লাগার মতো টিপস

- ⬆️ **আগের command:** কীবোর্ডে **উপরের তীর (↑)** চাপলে আগে চালানো command ফিরে আসে — আবার টাইপ করতে হয় না।
- ⏩ **Auto-complete:** কোনো নাম অর্ধেক লিখে **Tab** চাপলে Linux বাকিটা নিজে লিখে দেয়।
- ❌ **আটকে গেলে:** কোনো command চলতেই থাকলে **Ctrl + C** চেপে থামাও।

---

## ✅ Practice Task (এটা না করে পরের lesson-এ যেও না)

নিজের terminal খুলে নিচের command গুলো একটা একটা করে চালাও:

1. `whoami` — তোমার নাম দেখো
2. `date` — আজকের তারিখ দেখো
3. `echo "আমি Linux শিখছি"` — নিজের নাম দিয়ে একটা লাইন দেখাও
4. উপরের তীর (↑) চেপে আগের command ফিরিয়ে আনো
5. `clear` দিয়ে স্ক্রিন পরিষ্কার করো

---

## 📌 মনে রাখার সারসংক্ষেপ

| Command | কাজ |
|---------|-----|
| `whoami` | আমি কোন user |
| `date` | তারিখ ও সময় |
| `echo "text"` | লেখা স্ক্রিনে দেখায় |
| `clear` | স্ক্রিন পরিষ্কার করে |

---

পরের lesson 👉 [Lesson 02 — File ও Folder navigation](02-navigation.md)
