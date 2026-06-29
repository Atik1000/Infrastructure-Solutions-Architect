# Lesson 05 — File খোঁজা ও লেখা ফিল্টার করা

---

## 🎯 এই lesson-এ যা শিখবে
- নাম দিয়ে file খোঁজা (`find`)
- লেখার ভেতরে শব্দ খোঁজা (`grep`)
- pipe `|` দিয়ে একটা command-এর output আরেকটায় পাঠানো
- `wc`, `sort`, `uniq` দিয়ে দ্রুত বিশ্লেষণ

> এই lesson টা একটু "জাদুর" মতো — এখান থেকেই Linux-এর আসল শক্তি বোঝা শুরু হবে।

---

## ১. `find` — নাম দিয়ে file খুঁজে বের করো

গঠন: `find [কোথায় খুঁজবে] [শর্ত]`

### নাম দিয়ে খোঁজা:

```bash
$ find . -name "notes.txt"
```
- `.` মানে "এই folder থেকে শুরু করে ভেতরের সব জায়গায়"।
- `-name` মানে এই নামের file খোঁজো।

**Output:**
```
./Documents/notes.txt
```

### সব `.txt` file খোঁজা (wildcard `*`):

```bash
$ find . -name "*.txt"
```

**Output:**
```
./demo.txt
./Documents/notes.txt
./test.txt
```
> `*` মানে "যেকোনো কিছু"। তাই `*.txt` মানে "যেকোনো নামের .txt file"।

### শুধু folder খোঁজা:

```bash
$ find . -type d -name "src"
```
- `-type d` = শুধু directory (folder)
- `-type f` = শুধু file

---

## ২. `grep` — লেখার ভেতরে শব্দ খোঁজো

**grep** দিয়ে file-এর ভেতরে কোনো শব্দ আছে কিনা খুঁজে বের করা যায়। এটা প্রতিদিন লাগবে।

ধরো `demo.txt`-এ আছে:
```
apple
banana
apple pie
orange
```

### একটা শব্দ খোঁজা:

```bash
$ grep "apple" demo.txt
```

**Output:**
```
apple
apple pie
```
যে যে লাইনে "apple" আছে, সব দেখাবে।

### দরকারি option:

| Command | কাজ |
|---------|-----|
| `grep -i "apple"` | বড়/ছোট হাতের অক্ষর আলাদা ধরবে না (Apple = apple) |
| `grep -n "apple"` | লাইন নম্বর সহ দেখাবে |
| `grep -r "apple" .` | পুরো folder-এর সব file-এ খুঁজবে |
| `grep -v "apple"` | যে লাইনে "apple" **নেই** সেগুলো দেখাবে |

**উদাহরণ (`-rn` — folder-জুড়ে লাইন নম্বর সহ):**

```bash
$ grep -rn "TODO" .
```

**Output:**
```
./app.go:42:  // TODO: error handling যোগ করো
./utils.go:13:  // TODO: এই function refactor করো
```
> 💻 কোডে কোথায় কোথায় "TODO" লিখেছ — এক command-এই বের। ডেভেলপারদের প্রিয় command এটা।

---

## ৩. `|` (Pipe) — এক command-এর output আরেকটায় পাঠানো

**Pipe** (`|`) হলো Linux-এর সবচেয়ে শক্তিশালী ধারণা। এটা একটা command-এর output নিয়ে সরাসরি আরেকটা command-কে দেয়।

**ধারণা:** `command1 | command2` মানে → command1 যা বের করবে, command2 সেটা নিয়ে কাজ করবে।

### উদাহরণ ১ — folder-এ অনেক file, শুধু `.txt`-গুলো দেখি:

```bash
$ ls | grep ".txt"
```

**Output:**
```
demo.txt
notes.txt
test.txt
```
এখানে `ls` সব নাম বের করল, আর `grep ".txt"` সেখান থেকে শুধু .txt-ওয়ালাগুলো ছেঁকে নিল।

### উদাহরণ ২ — running process-এর মধ্যে "go" খোঁজা:

```bash
$ ps aux | grep "go"
```
(ps নিয়ে বিস্তারিত Lesson 08-এ।)

> **মনে রাখার সহজ উপায়:** Pipe হলো পানির পাইপের মতো — এক command থেকে data বের হয়ে পাইপ দিয়ে আরেক command-এ ঢোকে।

---

## ৪. বোনাস: `wc`, `sort`, `uniq` — pipe-এর সাথে দারুণ জোড়া

### `wc -l` — কয়টা লাইন গুনে দেয়:

```bash
$ cat demo.txt | wc -l
```

**Output:**
```
4
```
"file-এ কয়টা লাইন আছে?" — উত্তর।

### `sort` — সাজিয়ে দেয়:

```bash
$ sort demo.txt
```

**Output:**
```
apple
apple pie
banana
orange
```

### `uniq` — পরপর থাকা একই লাইন একবার দেখায়:

```bash
$ sort demo.txt | uniq
```
> 💡 `sort | uniq` জুটি দিয়ে duplicate বাদ দেওয়া যায়।

---

## ✅ Practice Task

1. একটা file বানাও কয়েকটা লাইন দিয়ে (`echo` আর `>>` দিয়ে)
2. `grep "শব্দ" file.txt` দিয়ে কোনো শব্দ খোঁজো
3. `grep -n` দিয়ে লাইন নম্বর সহ দেখো
4. `ls | grep ".md"` দিয়ে শুধু .md file দেখো (pipe প্র্যাকটিস)
5. `cat file.txt | wc -l` দিয়ে লাইন গুনো
6. `find . -name "*.md"` দিয়ে সব .md file খোঁজো

---

## 📌 সারসংক্ষেপ

| Command | কাজ |
|---------|-----|
| `find . -name "x"` | নাম দিয়ে file খোঁজা |
| `find . -type d` | শুধু folder খোঁজা |
| `grep "word" file` | লেখায় শব্দ খোঁজা |
| `grep -rn "word" .` | পুরো folder-এ লাইন নম্বর সহ |
| `grep -v "word"` | যেখানে শব্দ নেই |
| `cmd1 \| cmd2` | output পাইপে পাঠানো |
| `wc -l` | লাইন গোনা |
| `sort` / `uniq` | সাজানো / duplicate বাদ |

---

পরের lesson 👉 [Lesson 06 — Permissions (অনুমতি)](06-permissions.md)
