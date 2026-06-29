# Lesson 04 — File-এর ভেতরে দেখা ও লেখা

---

## 🎯 এই lesson-এ যা শিখবে
- file-এর ভেতরের লেখা দেখা (`cat`, `less`)
- শুরুর/শেষের কয়েক লাইন দেখা (`head`, `tail`)
- terminal থেকেই file edit করা (`nano`)
- command-এর output file-এ লেখা (`>` ও `>>`)

প্রথমে একটা practice file বানিয়ে নিই যাতে দেখাতে পারি:

```bash
$ echo "line 1" > demo.txt
$ echo "line 2" >> demo.txt
$ echo "line 3" >> demo.txt
```

---

## ১. `cat` — পুরো file স্ক্রিনে দেখাও

**cat** = con**cat**enate। ছোট file দেখার সবচেয়ে দ্রুত উপায়।

```bash
$ cat demo.txt
```

**Output:**
```
line 1
line 2
line 3
```

> ⚠️ বড় file-এ `cat` চালালে হাজার হাজার লাইন একসাথে চলে আসবে — তখন `less` ভালো (নিচে দেখো)।

---

## ২. `less` — বড় file ধীরে ধীরে পড়ো

```bash
$ less /etc/passwd
```

এটা file-টা একটা scroll করার মতো screen-এ খুলে দেয়। ভেতরে থাকা অবস্থায়:

| Key | কাজ |
|-----|-----|
| ↑ / ↓ | উপরে-নিচে যাও |
| Space | এক পেজ নিচে |
| `/শব্দ` | কোনো শব্দ খোঁজো |
| `q` | বের হও |

> 💡 `less` থেকে বের হতে **`q`** চাপো — অনেকে আটকে যায় এখানে!

---

## ৩. `head` ও `tail` — শুরু আর শেষ

### `head` — উপরের ১০ লাইন:

```bash
$ head demo.txt
```

**Output:**
```
line 1
line 2
line 3
```

লাইন সংখ্যা বলে দিতে `-n`:

```bash
$ head -n 2 demo.txt
```

**Output:**
```
line 1
line 2
```

### `tail` — শেষের ১০ লাইন:

```bash
$ tail -n 2 demo.txt
```

**Output:**
```
line 2
line 3
```

### ⭐ `tail -f` — সবচেয়ে কাজের, log দেখার জন্য

```bash
$ tail -f /var/log/syslog
```
`-f` = follow। file-এ নতুন লাইন যোগ হলে **লাইভ** স্ক্রিনে দেখাবে। server-এর log দেখতে এটা প্রতিদিন লাগবে। বের হতে `Ctrl + C`।

> 💡 **Laravel মিল:** এটা অনেকটা `php artisan log` বা `tail -f storage/logs/laravel.log` দেখার মতো — চলমান log লাইভ দেখা।

---

## ৪. `nano` — terminal থেকেই file লেখা/edit করা

`nano` হলো সহজ একটা text editor।

```bash
$ nano demo.txt
```

এতে file খুলবে, তুমি লিখতে/বদলাতে পারবে। নিচে শর্টকাট দেখাবে (`^` মানে Ctrl):

| শর্টকাট | কাজ |
|---------|-----|
| `Ctrl + O` | save করো (তারপর Enter) |
| `Ctrl + X` | বের হও |
| `Ctrl + K` | পুরো লাইন কেটে ফেলো |
| `Ctrl + W` | শব্দ খোঁজো |

> nano সহজ বলে শুরুতে এটাই ভালো। পরে `vim` শিখতে পারো (server-এ সব জায়গায় থাকে), তবে এখন nano-ই যথেষ্ট।

---

## ৫. `>` ও `>>` — output file-এ লেখা (Redirection)

সাধারণত command-এর output স্ক্রিনে আসে। কিন্তু `>` দিয়ে সেটা file-এ পাঠানো যায়।

### `>` — file-এ লেখো (আগের সব মুছে নতুন করে):

```bash
$ echo "Hello" > greet.txt
$ cat greet.txt
```

**Output:**
```
Hello
```

### `>>` — file-এর শেষে যোগ করো (আগেরটা থাকবে):

```bash
$ echo "World" >> greet.txt
$ cat greet.txt
```

**Output:**
```
Hello
World
```

> **পার্থক্য মনে রাখো:**
> - `>` = পুরো file মুছে নতুন করে লেখে (⚠️ সাবধান)
> - `>>` = শেষে যোগ করে (নিরাপদ)

---

## ✅ Practice Task

1. `echo "প্রথম লাইন" > test.txt` দিয়ে file বানাও
2. `echo "দ্বিতীয় লাইন" >> test.txt` দিয়ে আরেকটা লাইন যোগ করো
3. `cat test.txt` দিয়ে পুরো দেখো
4. `head -n 1 test.txt` দিয়ে শুধু প্রথম লাইন দেখো
5. `nano test.txt` দিয়ে খুলে একটা লাইন বদলাও, `Ctrl+O` → Enter → `Ctrl+X` দিয়ে save করে বের হও
6. আবার `cat test.txt` দিয়ে পরিবর্তন দেখো

---

## 📌 সারসংক্ষেপ

| Command | কাজ |
|---------|-----|
| `cat file` | পুরো file দেখা |
| `less file` | বড় file ধীরে পড়া (q দিয়ে বের) |
| `head file` | উপরের ১০ লাইন |
| `tail file` | শেষের ১০ লাইন |
| `tail -f file` | লাইভ log দেখা |
| `nano file` | file edit করা |
| `>` | file-এ লেখা (নতুন করে) |
| `>>` | file-এ যোগ করা |

---

পরের lesson 👉 [Lesson 05 — File খোঁজা ও লেখা ফিল্টার করা](05-find-grep.md)
