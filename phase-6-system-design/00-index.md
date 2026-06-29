# Phase 6 — System Design + Capstone + Interview Prep (Weeks 28–30+)

> **লক্ষ্য:** সব শেখা একসাথে জুড়ে একটা portfolio project বানানো এবং interview-এর জন্য প্রস্তুত হওয়া।

[👈 মূল study plan-এ ফিরে যাও](../infrastructure-architect-study-plan.md)

---

## 🔗 ফ্রি রিসোর্স
- **System Design Primer** — `github.com/donnemartin/system-design-primer` (ফ্রি, বিস্তারিত)
- **ByteByteGo** — ফ্রি newsletter/YouTube (visual system-design)

---

## 🏆 Capstone Project (interview-এ যেটা দেখাবে)
একটা project যা **সবকিছু ব্যবহার করে**:

> একটা Go-ভিত্তিক event-driven system — REST API + Kafka (বা RabbitMQ) event pipeline + PostgreSQL — Docker দিয়ে containerized, Kubernetes-এ deployed, এবং AWS-এ চলার মতো architected (free tier-এ অন্তত একটা অংশ deploy করলেও)।

একটা এক-পৃষ্ঠার architecture doc লেখো diagram সহ, যেখানে trade-off (cost vs resilience vs performance) ব্যাখ্যা থাকবে। **এই doc + repo-ই তোমার portfolio।**

---

## 🎤 Interview Prep — যে প্রশ্নগুলোর উত্তর মুখে বলতে পারতে হবে

**Go:** goroutine vs thread? channel vs mutex? Go-তে error handling কেন exception নেই? `defer` কখন চলে?

**Messaging:** RabbitMQ vs Kafka কখন? partition ও consumer group ব্যাখ্যা করো। dead-letter queue কী ও কেন? at-least-once vs exactly-once কীভাবে নিশ্চিত করো?

**Docker/K8s:** container vs VM? Pod কী, কেন সরাসরি container নয়? Deployment vs Service vs ConfigMap? rolling update কীভাবে downtime ছাড়া হয়? K8s কীভাবে crashed pod self-heal করে?

**AWS/Architecture:** highly-available web app design করে দেখাও। SQS vs SNS vs Kafka(MSK) কখন? S3 bucket কীভাবে secure করো? Shared Responsibility Model ব্যাখ্যা করো। বাড়তে থাকা cloud bill কীভাবে কমাও?

**System design:** URL shortener / notification service / event-driven order system design করো। সবসময় cost, resilience, performance-এর trade-off-এর কথা বলো — এই ভাষাই তোমাকে engineer নয়, **architect** শোনায়।

> 💡 প্রতিটা প্রশ্ন **জোরে জোরে, interviewer-কে বলার মতো করে** প্র্যাকটিস করো। সহজে বোঝাতে না পারলে এখনো বোঝোনি।

---

👈 [মূল study plan-এ ফিরে যাও](../infrastructure-architect-study-plan.md)
