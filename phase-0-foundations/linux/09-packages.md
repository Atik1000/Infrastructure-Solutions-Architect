# Lesson 09 — Package Install (software বসানো)

---

## 🎯 এই lesson-এ যা শিখবে
- Package manager কী ও কেন দরকার
- Ubuntu/Debian-এ `apt` দিয়ে software বসানো/মোছা
- list update ও upgrade করা
- কোন Linux-এ কোন manager (`apt`, `yum`, `dnf`)

---

## ১. Package Manager কী?

Windows-এ software বসাতে তুমি website থেকে `.exe` নামিয়ে double-click করো। Linux-এ এর চেয়ে সহজ — একটা command দিলেই software নিজে নেমে, বসে, configure হয়ে যায়।

এই কাজটা করে **package manager**। এটা একটা app-store-এর মতো, কিন্তু terminal থেকে।

> 💡 **মিল:** এটা অনেকটা `composer require` (PHP) বা `npm install` (Node)-এর মতো — কিন্তু পুরো system-এর software-এর জন্য।

কোন Linux-এ কোন manager:

| Linux | Package Manager |
|-------|-----------------|
| Ubuntu, Debian, Mint | **`apt`** (এটাই সবচেয়ে কমন) |
| RHEL, CentOS, Rocky | `yum` বা নতুন `dnf` |
| Fedora | `dnf` |
| Arch | `pacman` |

> আমরা `apt` দিয়ে শিখব, কারণ Ubuntu সবচেয়ে বেশি ব্যবহৃত। অন্যগুলোর command প্রায় একই ধরনের।

---

## ২. `apt update` — list হালনাগাদ করো (প্রথম ধাপ)

কিছু বসানোর আগে সবসময় software-এর তালিকা আপডেট করতে হয়। এটা software বসায় না — শুধু "কোথায় কী নতুন version আছে" সেই তালিকা নবায়ন করে।

```bash
$ sudo apt update
```

**Output (অংশবিশেষ):**
```
Hit:1 http://archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://archive.ubuntu.com/ubuntu jammy-updates InRelease
...
Reading package lists... Done
12 packages can be upgraded.
```

---

## ৩. `apt install` — software বসাও

```bash
$ sudo apt install git
```

প্রথমবার জিজ্ঞেস করবে:
```
Do you want to continue? [Y/n]
```
`Y` চেপে Enter দাও। বসে গেলে যাচাই করো:

```bash
$ git --version
```

**Output:**
```
git version 2.34.1
```
✅ বসে গেছে।

### একসাথে কয়েকটা বসানো:

```bash
$ sudo apt install curl wget htop -y
```
- `-y` দিলে "Y/n" জিজ্ঞেস করবে না, সরাসরি হ্যাঁ ধরে নেবে (script-এ কাজে লাগে)।

---

## ৪. `apt upgrade` — বসানো software নতুন version-এ নেওয়া

```bash
$ sudo apt upgrade
```
সব বসানো software-এর নতুন version থাকলে আপডেট করবে।

> 📌 কমন রুটিন (নতুন server-এ প্রথমেই এটা করা হয়):
> ```bash
> $ sudo apt update && sudo apt upgrade -y
> ```
> এখানে `&&` মানে — প্রথমটা সফল হলে তবেই দ্বিতীয়টা চালাও।

---

## ৫. `apt remove` ও `apt purge` — software মোছা

```bash
$ sudo apt remove git
```
software মুছবে, কিন্তু তার config file রেখে দিতে পারে।

পুরোপুরি মুছতে (config সহ):

```bash
$ sudo apt purge git
```

অপ্রয়োজনীয় বাকি ফাইল পরিষ্কার করতে:

```bash
$ sudo apt autoremove
```

---

## ৬. software খোঁজা — `apt search`

নাম ঠিক না জানলে খুঁজে নাও:

```bash
$ apt search nginx
```

**Output (অংশবিশেষ):**
```
nginx/jammy  web server, reverse proxy, load balancer
nginx-core/jammy  nginx web server (core version)
```

---

## ৭. একটা পূর্ণ উদাহরণ — `tree` বসিয়ে ব্যবহার

`tree` একটা সুন্দর command যা folder structure গাছের মতো দেখায়।

```bash
$ sudo apt install tree -y
$ tree
```

**Output:**
```
.
├── Documents
│   └── notes.txt
├── Downloads
└── projects
    └── app.go

3 directories, 2 files
```

---

## ✅ Practice Task

1. `sudo apt update` দিয়ে list আপডেট করো
2. `sudo apt install tree -y` দিয়ে tree বসাও
3. `tree` চালিয়ে নিজের folder structure দেখো
4. `git --version` / `curl --version` দিয়ে দেখো কী কী আগে থেকে বসানো আছে
5. (ঐচ্ছিক) `apt search htop` দিয়ে খোঁজো, তারপর install করো

---

## 📌 সারসংক্ষেপ

| Command | কাজ |
|---------|-----|
| `sudo apt update` | software list আপডেট |
| `sudo apt install নাম` | software বসানো |
| `sudo apt install নাম -y` | জিজ্ঞেস ছাড়া বসানো |
| `sudo apt upgrade` | বসানো software আপডেট |
| `sudo apt remove নাম` | মোছা |
| `sudo apt purge নাম` | config সহ মোছা |
| `apt search নাম` | software খোঁজা |

> RHEL/CentOS হলে `apt`-এর জায়গায় `yum` বা `dnf` লিখবে — বাকি প্রায় একই।

---

পরের lesson 👉 [Lesson 10 — Networking basics](10-networking.md)
