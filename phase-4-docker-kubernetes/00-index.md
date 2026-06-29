# Phase 4 — Docker + Kubernetes (Weeks 15–20)

> **লক্ষ্য:** তোমার Go service container-এ মুড়ে orchestrate করা। Target: **KCNA** certification।

[👈 মূল study plan-এ ফিরে যাও](../infrastructure-architect-study-plan.md)

---

## 📚 Lesson তালিকা (আসছে 🔜)

| # | Lesson | কী শিখবে |
|---|--------|----------|
| 01 | Container vs VM | container আসলে কী |
| 02 | Docker basics | image, container, `docker run` |
| 03 | Dockerfile | নিজের image বানানো |
| 04 | docker-compose | একাধিক service একসাথে |
| 05 | Kubernetes কী | কেন orchestration দরকার |
| 06 | Pod ও Deployment | app চালানো |
| 07 | Service | network access |
| 08 | ConfigMap ও Secret | config ও গোপন তথ্য |
| 09 | Scaling ও Rolling update | replica বাড়ানো, downtime ছাড়া update |

---

## 🔗 ফ্রি রিসোর্স
- **KodeKloud free courses** — `kodekloud.com/free-courses` ("Docker/Kubernetes for the Absolute Beginner")। **এদের Free Learning Week-এর সময়ে এই phase রাখো** পূর্ণ access-এর জন্য।
- **Kubernetes interactive tutorial** — `kubernetes.io/docs/tutorials/kubernetes-basics`
- **Play with Kubernetes** — `labs.play-with-k8s.com` (ফ্রি browser cluster)
- **freeCodeCamp Kubernetes** (YouTube)
- Local cluster: **kind** বা **minikube** (laptop-এ K8s চালাও)

---

## 🛠️ যা বানাবে
Phase-2-এর Go API + PostgreSQL + (ঐচ্ছিক) RabbitMQ/Kafka একটা local cluster-এ (kind/minikube) deploy করো। Service দিয়ে expose করো। API-কে ৩ replica-তে scale করো। একটা rolling update করো।

---

## 🎯 Milestone ও Certification
- `kubectl apply -f` দিয়ে পুরো stack deploy করতে পারবে এবং প্রতিটা manifest কী করে ব্যাখ্যা করতে পারবে।
- **KCNA** — multiple-choice, conceptual, পাশ ৭৫%, beginner-friendly।

---

পরের phase 👉 [Phase 5 — AWS Solutions Architecture](../phase-5-aws/00-index.md)
