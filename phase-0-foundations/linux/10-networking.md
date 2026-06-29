# Lesson 10 — Networking Basics

---

## 🎯 এই lesson-এ যা শিখবে
- IP ও port আসলে কী (সহজ ভাষায়)
- সংযোগ আছে কিনা পরীক্ষা (`ping`)
- terminal থেকে website/API ডাকা (`curl`, `wget`)
- দূরের server-এ ঢোকা (`ssh`)
- কোন port-এ কী চলছে দেখা (`netstat`/`ss`)

> এটা Phase 0-এর শেষ Linux lesson। এখান থেকেই server, API, cloud-এর জগতে ঢোকা শুরু।

---

## ১. আগে বুঝি: IP আর Port

- **IP address** = computer-এর ঠিকানা। যেমন `192.168.0.10` বা `8.8.8.8`। ইন্টারনেটে প্রতিটা machine-এর একটা ঠিকানা থাকে।
- **Port** = ওই machine-এর ভেতরের নির্দিষ্ট "দরজা"। একটা server-এ অনেক service চলে, প্রতিটা আলাদা port-এ।

> **সহজ উপায়:** IP হলো বাড়ির ঠিকানা, আর port হলো ওই বাড়ির কোন ফ্ল্যাট/রুম। ঠিকানা + রুম মিলেই সঠিক জায়গায় পৌঁছানো যায়।

কিছু পরিচিত port:

| Port | কী চলে |
|------|--------|
| 22 | SSH (server-এ ঢোকা) |
| 80 | HTTP (সাধারণ website) |
| 443 | HTTPS (নিরাপদ website) |
| 3306 | MySQL |
| 5432 | PostgreSQL |
| 6379 | Redis |

---

## ২. `ping` — সংযোগ আছে কিনা?

```bash
$ ping google.com
```

**Output:**
```
PING google.com (142.250.183.14): 56 data bytes
64 bytes from 142.250.183.14: icmp_seq=0 ttl=118 time=24.5 ms
64 bytes from 142.250.183.14: icmp_seq=1 ttl=118 time=23.8 ms
^C
--- google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss
```
- প্রতিটা লাইন মানে একটা সফল উত্তর এসেছে। `time=24.5 ms` = কত দ্রুত উত্তর এলো।
- বন্ধ করতে **`Ctrl + C`**।
- উত্তর না এলে (`100% packet loss`) → হয় ইন্টারনেট নেই, নয় server বন্ধ।

---

## ৩. `curl` — terminal থেকে website/API ডাকা

**curl** দিয়ে browser ছাড়াই কোনো URL-এ request পাঠানো যায়। API টেস্ট করতে এটা অপরিহার্য।

```bash
$ curl https://api.github.com/zen
```

**Output:**
```
Keep it logically awesome.
```
GitHub-এর API একটা random লাইন ফেরত দিল।

### দরকারি option:

| Command | কাজ |
|---------|-----|
| `curl -I url` | শুধু header দেখা (status code ইত্যাদি) |
| `curl -o file url` | response file-এ save করা |
| `curl -X POST url` | POST request পাঠানো |

**status code দেখা:**

```bash
$ curl -I https://google.com
```

**Output:**
```
HTTP/2 200
content-type: text/html
...
```
`200` মানে সব ঠিক আছে। (`404` = খুঁজে পাওয়া যায়নি, `500` = server-এ সমস্যা।)

> 💻 তোমার Go API বানানোর সময় (Phase 2) এই `curl` দিয়েই endpoint টেস্ট করবে।

---

## ৪. `wget` — file ডাউনলোড করা

```bash
$ wget https://example.com/file.zip
```
URL থেকে সরাসরি file নামিয়ে নেয়। `curl` request পাঠানোয় ভালো, `wget` download-এ ভালো।

---

## ৫. `ssh` — দূরের server-এ ঢোকা (সবচেয়ে গুরুত্বপূর্ণ)

**ssh** = **S**ecure **Sh**ell। তোমার laptop থেকে দূরের একটা server-এ নিরাপদে ঢুকে কাজ করতে দেয়। cloud/server-এর কাজে এটা প্রতিদিন লাগবে।

গঠন: `ssh username@server_ip`

```bash
$ ssh foysal@203.0.113.25
```

প্রথমবার জিজ্ঞেস করবে:
```
The authenticity of host '203.0.113.25' can't be established.
Are you sure you want to continue connecting (yes/no)? yes
foysal@203.0.113.25's password:
```
password দিলে তুমি এখন ওই দূরের server-এর ভেতরে — prompt বদলে যাবে। বের হতে `exit`।

### SSH key দিয়ে password ছাড়া ঢোকা (পেশাদার পদ্ধতি):

```bash
$ ssh-keygen
```
এটা একজোড়া key বানায় (একটা গোপন, একটা public)। public key-টা server-এ বসিয়ে দিলে আর password লাগে না — বেশি নিরাপদ। AWS/cloud-এ এভাবেই ঢোকা হয়।

> ☁️ Phase 5-এ AWS EC2 server-এ ঢুকতে ঠিক এই `ssh -i key.pem ...` ব্যবহার করবে।

---

## ৬. `ip addr` — নিজের IP দেখা

```bash
$ ip addr
```

**Output (অংশবিশেষ):**
```
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500
    inet 192.168.0.10/24 brd 192.168.0.255 scope global eth0
```
`inet 192.168.0.10` = এই machine-এর local IP।

> (পুরোনো command `ifconfig`-ও একই কাজ করে, কিন্তু এখন `ip addr` ব্যবহার করা হয়।)

---

## ৭. `ss` — কোন port-এ কী চলছে?

```bash
$ ss -tuln
```

**Output:**
```
Netid  State   Local Address:Port
tcp    LISTEN  0.0.0.0:22
tcp    LISTEN  127.0.0.1:5432
tcp    LISTEN  0.0.0.0:80
```
- `:22` = SSH চলছে, `:80` = web server চলছে, `:5432` = PostgreSQL চলছে।
- "আমার server-এ কোন কোন service চালু আছে?" — এই command-এ উত্তর।

> (পুরোনো command `netstat -tuln`-ও একই কাজ করে।)

---

## ✅ Practice Task

1. `ping google.com` দিয়ে ইন্টারনেট আছে কিনা দেখো (Ctrl+C দিয়ে থামাও)
2. `curl https://api.github.com/zen` দিয়ে একটা API response দেখো
3. `curl -I https://google.com` দিয়ে status code (200) দেখো
4. `ip addr` দিয়ে নিজের IP বের করো
5. `ss -tuln` দিয়ে দেখো তোমার machine-এ কোন port চালু আছে
6. (ঐচ্ছিক) যদি কোনো server থাকে, `ssh user@ip` দিয়ে ঢোকার চেষ্টা করো

---

## 📌 সারসংক্ষেপ

| Command | কাজ |
|---------|-----|
| `ping host` | সংযোগ পরীক্ষা |
| `curl url` | URL/API ডাকা |
| `curl -I url` | header/status দেখা |
| `wget url` | file ডাউনলোড |
| `ssh user@ip` | দূরের server-এ ঢোকা |
| `ssh-keygen` | SSH key বানানো |
| `ip addr` | নিজের IP দেখা |
| `ss -tuln` | চালু port দেখা |

---

## 🎉 অভিনন্দন!

তুমি Phase 0-এর Linux foundations শেষ করেছ! এখন তুমি:
- terminal-এ স্বচ্ছন্দে চলাফেরা করতে পারো
- file ও folder নিয়ন্ত্রণ করতে পারো
- permission, user, process বুঝো
- software বসাতে ও network পরীক্ষা করতে পারো

**পরবর্তী ধাপ:** Study plan অনুযায়ী এবার **Phase 1 — Go Fundamentals**। বলো, Go-এর জন্যও কি একইভাবে বাংলায় lesson বানিয়ে দেব? 🚀

👈 [সূচিপত্রে ফিরে যাও](00-index.md)
