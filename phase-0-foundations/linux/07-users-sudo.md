# Lesson 07 — User ও sudo (root power)

---

## 🎯 এই lesson-এ যা শিখবে
- Linux-এ user ও root কী
- `sudo` দিয়ে admin-এর কাজ করা
- user দেখা ও তৈরি করা
- password বদলানো

---

## ১. Linux-এ user মানে কী?

Linux একটা **multi-user** system — একই computer/server অনেক মানুষ ব্যবহার করতে পারে। প্রত্যেকের আলাদা:
- username
- home folder (`/home/username`)
- নিজের file ও permission

দুই ধরনের user:

| ধরন | বর্ণনা |
|-----|--------|
| **সাধারণ user** | তুমি, আমি — শুধু নিজের জিনিসে হাত দিতে পারি। prompt-এ `$` দেখায়। |
| **root (superuser)** | সর্বশক্তিমান admin — যেকোনো কিছু করতে পারে। prompt-এ `#` দেখায়। |

> ⚠️ root হলো অনেকটা "সব দরজার মাস্টার চাবি"। ভুল করলে পুরো system নষ্ট হতে পারে, তাই সবসময় root হয়ে কাজ করা হয় না।

---

## ২. `whoami` ও `id` — আমি কে?

```bash
$ whoami
```

**Output:**
```
foysal
```

```bash
$ id
```

**Output:**
```
uid=1000(foysal) gid=1000(foysal) groups=1000(foysal),27(sudo)
```
- `uid` = তোমার user ID number
- `groups` = তুমি কোন কোন দলে আছো (এখানে `sudo` দলে আছো মানে তুমি admin কাজ করতে পারবে)

---

## ৩. `sudo` — সাময়িকভাবে admin হওয়া

**sudo** = **s**uper**u**ser **do**। কোনো command-এর আগে `sudo` লাগালে সেটা root-এর ক্ষমতায় চলে।

### উদাহরণ — root ছাড়া যা পারবে না:

```bash
$ apt install nginx
```

**Output:**
```
E: Could not open lock file - are you root?
```
😅 সাধারণ user software install করতে পারে না। এখন `sudo` দিয়ে:

```bash
$ sudo apt install nginx
[sudo] password for foysal:
```
তোমার password চাইবে (টাইপ করলে স্ক্রিনে দেখাবে না — এটা স্বাভাবিক, ভয় পেও না)। সঠিক হলে command চলবে।

> 💡 **কখন sudo লাগে?** software install, system file বদলানো, অন্যের file-এ হাত দেওয়া, service চালু/বন্ধ — এসবে। নিজের home folder-এ সাধারণ কাজে লাগে না।

> ⚠️ **সাবধান:** `sudo` দিয়ে চালানো command-এ ভুল হলে সরাসরি system ক্ষতিগ্রস্ত হয়। তাই `sudo rm -rf ...` জাতীয় command চালানোর আগে দুবার পড়ো।

---

## ৪. user দেখা ও তৈরি করা

### system-এ কারা আছে দেখা:

```bash
$ cat /etc/passwd
```

**Output (অংশবিশেষ):**
```
root:x:0:0:root:/root:/bin/bash
foysal:x:1000:1000:Foysal:/home/foysal:/bin/bash
```
প্রতিটা লাইন একজন user। প্রথম শব্দটা username, শেষেরটা তার shell।

### নতুন user বানানো (sudo লাগে):

```bash
$ sudo adduser rahim
```
এটা `rahim` নামে নতুন user বানাবে, password চাইবে, আর `/home/rahim` folder বানিয়ে দেবে।

### একজনকে sudo (admin) ক্ষমতা দেওয়া:

```bash
$ sudo usermod -aG sudo rahim
```
- `-aG sudo` মানে rahim-কে `sudo` group-এ যোগ করো। এখন rahim-ও admin কাজ করতে পারবে।

---

## ৫. password বদলানো

### নিজের password:

```bash
$ passwd
```
পুরোনো একবার, নতুন দুবার চাইবে।

### অন্য user-এর password (sudo লাগে):

```bash
$ sudo passwd rahim
```

---

## ৬. user বদলে অন্য user হওয়া — `su`

```bash
$ su rahim
```
rahim-এর password দিয়ে তার হিসেবে কাজ করতে পারবে। ফিরে আসতে `exit`।

root হতে (যদি অনুমতি থাকে):
```bash
$ sudo su
```
prompt `$` থেকে `#`-এ বদলে যাবে — মানে এখন তুমি root। কাজ শেষে `exit` দিয়ে বের হও।

---

## ✅ Practice Task

1. `whoami` দিয়ে নিজের নাম দেখো
2. `id` দিয়ে দেখো তুমি `sudo` group-এ আছো কিনা
3. `cat /etc/passwd` দিয়ে system-এর user-দের তালিকা দেখো
4. `sudo whoami` চালাও — output হবে `root` (কারণ sudo দিয়ে root হিসেবে চলল)
5. (ঐচ্ছিক) `sudo apt update` চালিয়ে দেখো sudo কীভাবে কাজ করে

---

## 📌 সারসংক্ষেপ

| Command | কাজ |
|---------|-----|
| `whoami` | আমি কোন user |
| `id` | user ID ও group দেখা |
| `sudo command` | admin হিসেবে চালানো |
| `cat /etc/passwd` | সব user-এর তালিকা |
| `sudo adduser নাম` | নতুন user |
| `sudo usermod -aG sudo নাম` | admin ক্ষমতা দেওয়া |
| `passwd` | নিজের password বদল |
| `su নাম` | অন্য user হওয়া |

---

পরের lesson 👉 [Lesson 08 — Process ও system দেখা](08-process-system.md)
