# Lesson 08 — Process ও System দেখা

---

## 🎯 এই lesson-এ যা শিখবে
- চলমান program (process) দেখা (`ps`, `top`)
- আটকে যাওয়া program বন্ধ করা (`kill`)
- disk কতটা ভরা দেখা (`df`, `du`)
- RAM কতটা ব্যবহার হচ্ছে দেখা (`free`)

> server slow হলে বা কিছু আটকে গেলে — এই lesson-এর command দিয়ে কারণ খুঁজে বের করবে।

---

## ১. Process কী?

যেকোনো চলমান program-ই একটা **process**। প্রতিটা process-এর একটা নম্বর থাকে — **PID** (Process ID)। এই নম্বর দিয়েই আমরা process-কে চিনি ও নিয়ন্ত্রণ করি।

> 💡 **Laravel মিল:** তোমার `php artisan queue:work` চালালে যে worker চলে — ওটাও একটা process, ওরও একটা PID থাকে।

---

## ২. `ps aux` — এখন কী কী চলছে?

```bash
$ ps aux
```

**Output (অংশবিশেষ):**
```
USER   PID  %CPU %MEM    VSZ   RSS   STAT  START  TIME  COMMAND
root     1   0.0  0.1  16800  9000   Ss    10:00  0:01  /sbin/init
foysal 845   1.2  3.0 720000 60000   Sl    10:30  0:05  /usr/bin/go run main.go
foysal 901   0.0  0.1  12000  3000   R     10:45  0:00  ps aux
```

কলামগুলোর মানে:

| কলাম | মানে |
|------|------|
| `USER` | কে চালাচ্ছে |
| `PID` | process-এর নম্বর (গুরুত্বপূর্ণ) |
| `%CPU` | কত % CPU খাচ্ছে |
| `%MEM` | কত % RAM খাচ্ছে |
| `COMMAND` | কোন program |

### নির্দিষ্ট program খুঁজতে pipe + grep:

```bash
$ ps aux | grep "go"
```

**Output:**
```
foysal 845  1.2  3.0 720000 60000  Sl  10:30  0:05  /usr/bin/go run main.go
```
> Lesson 05-এর pipe (`|`) এখানে কাজে লাগল — হাজার লাইন থেকে শুধু "go"-ওয়ালা লাইন বের করল।

---

## ৩. `top` (বা `htop`) — লাইভ system monitor

```bash
$ top
```
এটা একটা **লাইভ আপডেট হওয়া** স্ক্রিন দেখায় — কোন process এখন সবচেয়ে বেশি CPU/RAM খাচ্ছে, উপরে উঠে আসে।

**Output (অংশবিশেষ):**
```
top - 14:30:01 up 4:30, 1 user, load average: 0.15, 0.10, 0.05
Tasks: 120 total, 1 running, 119 sleeping
%Cpu(s):  2.3 us,  0.7 sy
MiB Mem :  7920.0 total,  3200.0 free,  2100.0 used

  PID USER   %CPU %MEM  COMMAND
  845 foysal  1.2  3.0  go
  512 mysql   0.8  5.0  mysqld
```

- বের হতে **`q`** চাপো।
- `htop` (যদি install করা থাকে) আরও সুন্দর ও রঙিন — `sudo apt install htop` দিয়ে বসানো যায়।

---

## ৪. `kill` — আটকে যাওয়া program বন্ধ করা

কোনো program ঝুলে গেলে বা বন্ধ করতে চাইলে তার PID দিয়ে kill করো।

```bash
$ kill 845
```
PID 845-এর process-কে ভদ্রভাবে বন্ধ হতে বলবে।

### জোর করে বন্ধ (একদম রেসপন্স না করলে):

```bash
$ kill -9 845
```
- `-9` = জোরপূর্বক, সাথে সাথে মেরে ফেলা। শেষ উপায় হিসেবে ব্যবহার করো।

### নাম দিয়ে kill করা:

```bash
$ pkill go
```
"go" নামের সব process বন্ধ করবে।

> 💡 প্রথমে `ps aux | grep নাম` দিয়ে PID বের করো, তারপর `kill PID`।

---

## ৫. `df` — disk কতটা ভরা?

**df** = **d**isk **f**ree। `-h` দিলে মানুষের পড়ার মতো (GB/MB) দেখায়।

```bash
$ df -h
```

**Output:**
```
Filesystem      Size  Used  Avail  Use%  Mounted on
/dev/sda1        50G   30G    18G   63%  /
```
- `Use%` = কত % ভরা। ৯০%+ হলে সাবধান, server-এ সমস্যা হতে পারে।

---

## ৬. `du` — কোন folder কত জায়গা খাচ্ছে?

**du** = **d**isk **u**sage।

```bash
$ du -sh *
```
- `-s` = সারসংক্ষেপ (ভেতরের প্রতিটা না দেখিয়ে মোট)
- `-h` = পড়ার মতো আকার

**Output:**
```
1.2G   Downloads
500M   projects
20K    notes.txt
```
> "আমার disk কে ভরাচ্ছে?" — এই command দিয়ে বড় folder খুঁজে বের করো।

---

## ৭. `free` — RAM কতটা ব্যবহার হচ্ছে?

```bash
$ free -h
```

**Output:**
```
              total   used   free   available
Mem:          7.7Gi  2.1Gi  3.1Gi      5.2Gi
Swap:         2.0Gi    0Bi  2.0Gi
```
- `available` = এখনো কত RAM ব্যবহারের জন্য আছে।

---

## ✅ Practice Task

1. `ps aux` চালাও, কয়টা process চলছে দেখো
2. `ps aux | grep bash` দিয়ে নিজের shell খোঁজো
3. `top` চালাও, কোন process বেশি CPU খাচ্ছে দেখো, তারপর `q` দিয়ে বের হও
4. `df -h` দিয়ে disk কতটা ভরা দেখো
5. `free -h` দিয়ে RAM দেখো
6. `du -sh *` দিয়ে কোন folder বড় দেখো

---

## 📌 সারসংক্ষেপ

| Command | কাজ |
|---------|-----|
| `ps aux` | সব চলমান process |
| `ps aux \| grep নাম` | নির্দিষ্ট process খোঁজা |
| `top` | লাইভ monitor (q দিয়ে বের) |
| `kill PID` | process বন্ধ |
| `kill -9 PID` | জোর করে বন্ধ |
| `df -h` | disk কতটা ভরা |
| `du -sh *` | folder-এর আকার |
| `free -h` | RAM ব্যবহার |

---

পরের lesson 👉 [Lesson 09 — Package install (software বসানো)](09-packages.md)
