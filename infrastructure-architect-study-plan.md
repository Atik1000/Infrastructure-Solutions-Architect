# Infrastructure & Solutions Architect — পূর্ণ স্টাডি প্ল্যান (বাংলা)
### Go → RabbitMQ → Kafka → Docker/Kubernetes → AWS Solutions Architecture
*দিনে ~২ ঘণ্টার জন্য সাজানো। বাস্তবসম্মত পূর্ণ সময়: ~৭ মাস। গতি নিজের মতো ঠিক করো — গতির চেয়ে নিয়মিততা বেশি জরুরি।*

---

## 🗺️ এক নজরে পুরো রোডম্যাপ

| Phase | বিষয় | সময় | ফলাফল | লিংক |
|-------|------|------|--------|------|
| 0 | Foundations (Linux, networking, HTTP) | চলমান | terminal-এ স্বচ্ছন্দ | [খুলো 👉](phase-0-foundations/00-index.md) |
| 1 | Go fundamentals | সপ্তাহ ১–৫ | idiomatic Go ও concurrency | [খুলো 👉](phase-1-go/00-index.md) |
| 2 | Go-তে backend service | সপ্তাহ ৬–৯ | REST API + PostgreSQL + Docker | [খুলো 👉](phase-2-backend/00-index.md) |
| 3 | Messaging: RabbitMQ → Kafka | সপ্তাহ ১০–১৪ | Go-তে producer/consumer app | [খুলো 👉](phase-3-messaging/00-index.md) |
| 4 | Docker + Kubernetes | সপ্তাহ ১৫–২০ | cluster-এ deploy (target: KCNA) | [খুলো 👉](phase-4-docker-kubernetes/00-index.md) |
| 5 | AWS Solutions Architecture | সপ্তাহ ২১–২৮ | cloud system design (target: SAA-C03) | [খুলো 👉](phase-5-aws/00-index.md) |
| 6 | System design + capstone + interview | সপ্তাহ ২৮–৩০+ | সব একসাথে জোড়া | [খুলো 👉](phase-6-system-design/00-index.md) |

> 🟢 **এখন তৈরি:** Phase 0-এর [Linux lessons](phase-0-foundations/linux/00-index.md) (১০টা বাংলা lesson, command + output সহ)।
> বাকি phase-গুলোর index তৈরি — lesson ধীরে ধীরে যোগ হচ্ছে।

---

## 🎯 এই প্ল্যান কীভাবে ব্যবহার করবে

**প্রতিদিন ২ ঘণ্টার ভাগ (৭০/৩০ নিয়ম):**
- **~৪০ মিনিট — শেখো:** দিনের topic পড়ো/দেখো।
- **~৭০ মিনিট — বানাও:** code লেখো, lab চালাও, ভাঙো, ঠিক করো। **আসল শেখা এখানেই হয়।**
- **~১০ মিনিট — লেখো:** একটা notes file-এ ৩ লাইন লেখো — *আজ কী শিখলাম, কী বুঝিনি, কাল কী চেষ্টা করব।* এই একটা অভ্যাসই শেষ করা আর ছেড়ে দেওয়ার মধ্যে পার্থক্য গড়ে দেয়।

**তোমার বাড়তি সুবিধা:** Laravel-এ তুমি ইতিমধ্যে queue worker, scheduler, dispatched job চালাও। RabbitMQ, Kafka বা Kubernetes-এ নতুন concept পেলেই ভাবো "এর Laravel সমতুল্য কী?" — যা জানো তার সাথে জুড়ে নিলে ২x দ্রুত শিখবে।

**নিয়ম:** কোনো phase-এ নিখুঁত হওয়ার পেছনে ছুটো না। লক্ষ্য রাখো — "একটা কাজ করা version বানাতে পারি ও ব্যাখ্যা করতে পারি।" গভীরতা আসবে capstone থেকে আর এই tool-গুলো বারবার ব্যবহার করতে করতে।

---

## 📂 Phase বিস্তারিত (প্রতিটা লিংকে ক্লিক করলে আলাদা folder খুলবে)

### [Phase 0 — Foundations](phase-0-foundations/00-index.md)
Linux, networking, HTTP। terminal-এ স্বচ্ছন্দ হওয়া — পুরো journey-জুড়ে চলবে।
→ ✅ [Linux lessons (১০টা, বাংলা)](phase-0-foundations/linux/00-index.md) · 🔜 [Networking](phase-0-foundations/networking/00-index.md)

### [Phase 1 — Go Fundamentals](phase-1-go/00-index.md)
idiomatic Go পড়া/লেখা, goroutine ও channel বোঝা। **Milestone:** goroutine vs thread ব্যাখ্যা করতে পারা।

### [Phase 2 — Backend Services in Go](phase-2-backend/00-index.md)
production-আকৃতির REST API + PostgreSQL + JWT + Docker। **Milestone:** `docker compose up` দিয়ে নিজের API চালানো।

### [Phase 3 — Messaging](phase-3-messaging/00-index.md)
[RabbitMQ](phase-3-messaging/rabbitmq/00-index.md) (আগে, সহজ) → [Kafka](phase-3-messaging/kafka/00-index.md) (পরে, streaming)। **Milestone:** কখন কোনটা বেছে নেবে বলতে পারা।

### [Phase 4 — Docker + Kubernetes](phase-4-docker-kubernetes/00-index.md)
Go service container-এ মুড়ে cluster-এ deploy। Target **KCNA**। **Milestone:** `kubectl apply -f` দিয়ে পুরো stack deploy।

### [Phase 5 — AWS Solutions Architecture](phase-5-aws/00-index.md)
secure, resilient, cost-optimized system design। Target **SAA-C03**। **Milestone:** scenario দিলে architecture এঁকে যুক্তি দেওয়া।

### [Phase 6 — System Design + Capstone](phase-6-system-design/00-index.md)
সব একসাথে জুড়ে একটা portfolio project + interview prep।

---

## 🎓 Certifications — সৎ পর্যালোচনা

### ফ্রি *completion* certificate (শেখা + LinkedIn-এর জন্য ভালো, industry-graded নয়)
- **Great Learning Academy** — ফ্রি Golang course + certificate
- **KodeKloud Free Learning Week** — ফ্রি week-এ course শেষ করে certificate রাখো
- **Confluent Developer** — ফ্রি Kafka course + badge
- **AWS Skill Builder** — ফ্রি course ও কিছু ফ্রি digital badge
- **Microsoft Learn** — ফ্রি learning path

### Paid কিন্তু industry-recognized (job-targeting-এর সময় মূল্যবান)
| Cert | আনুমানিক খরচ | কখন |
|------|-------------|------|
| KCNA (Kubernetes) | ~$250 | Phase 4-এর পর |
| AWS SAA-C03 | $150 | Phase 5-এর পর |
| CKA (Kubernetes, hands-on) | ~$395 | পরে, K8s-এ গভীরে গেলে |
| Confluent CCDAK (Kafka) | ~$150 | ঐচ্ছিক, Kafka মূল focus হলে |

### কম খরচে করার উপায় (বাংলাদেশের জন্য প্রাসঙ্গিক)
- AWS প্রায়ই **ফ্রি exam voucher** campaign চালায়, আর একটা AWS cert থাকলে পরের exam-এ **৫০% discount** দেয় — সবচেয়ে সস্তাটা আগে নাও।
- **Linux Foundation / CNCF** (KCNA, CKA) ঘনঘন bundle discount ও মাঝে মাঝে scholarship দেয় — কখনো full price দিও না, sale-এর অপেক্ষা করো।
- ঢাকায় **AWS Community Day / user-group voucher** খোঁজো — local AWS community মাঝে মাঝে exam credit দেয়।
- **সত্য কথা:** জ্ঞানটাই চাকরি দেয়; certificate শুধু দরজা খোলে। আগে project বানাও, আত্মবিশ্বাসী হয়ে তবেই paid exam দাও।

---

## 🔥 নিয়মিত থাকার উপায় (যা আসলে সফলতা ঠিক করে)

- **একই ২ ঘণ্টা, একই সময়, প্রতিদিন।** নির্দিষ্ট slot motivation-কে হারায়।
- **বানানো > দেখা।** একটা শেষ করা ছোট project ১০ ঘণ্টা video-র চেয়ে বেশি শেখায়।
- **প্রতিদিনের ৩-লাইন log রাখো।** সপ্তাহে একবার পড়লে অগ্রগতি দেখা যায়, burnout কমে।
- **একটাই project সব phase-জুড়ে** (তোমার Go API) — প্রতি phase একই জিনিসকে গভীর করে, নতুন করে শুরু করতে হয় না।
- **"ready" বোধ করার অপেক্ষা করো না।** ~৮০% বুঝলেই পরের phase-এ যাও; বাকিটা ব্যবহার করতে করতে পূর্ণ হবে।

*তুমি পারবে। সাত মাসের ধারাবাহিক ২-ঘণ্টার দিন তোমাকে "অল্প backend জ্ঞান" থেকে সত্যিকারের architect-সুলভ চিন্তায় নিয়ে যাবে।*
