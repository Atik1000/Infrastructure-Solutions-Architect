# Phase 2 — Backend Services in Go (Weeks 6–9)

> **লক্ষ্য:** production-আকৃতির একটা backend বানানো। এখানে তোমার Laravel অভিজ্ঞতা সরাসরি কাজে লাগবে।

[👈 মূল study plan-এ ফিরে যাও](../infrastructure-architect-study-plan.md)

---

## 📚 Lesson তালিকা (আসছে 🔜)

| # | Lesson | কী শিখবে |
|---|--------|----------|
| 01 | HTTP server in Go | router (`chi`/Gin), route, handler |
| 02 | Request handling | JSON parse, validation, response |
| 03 | PostgreSQL সংযোগ | `pgx`, connection pool |
| 04 | `sqlc` দিয়ে type-safe query | SQL থেকে Go code generate |
| 05 | Migration | database schema পরিবর্তন সামলানো |
| 06 | JWT Authentication | login, token, protected route |
| 07 | Structured logging | log কীভাবে production-grade হয় |
| 08 | Dockerize | `Dockerfile` + `docker-compose.yml` |
| 09 | Testing | কয়েকটা test লেখা |

---

## 🔗 ফ্রি রিসোর্স
- **Alex Edwards "Let's Go"** concepts — তার ফ্রি blog post (Go web app structure-এর সোনা)
- **Gin** — `gin-gonic.com` (অথবা `net/http` + `chi` router — দুটোই ঠিক)
- **`pgx` ও `sqlc` docs** — `sqlc` SQL থেকে type-safe Go বানায়
- **Docker "Get Started"** — `docs.docker.com/get-started`

---

## 🛠️ যা বানাবে (পুরো phase জুড়ে একটাই শক্ত project)
তোমার চেনা একটা ছোট domain-এর জন্য **REST API** (যেমন mini election/committee tracker)। থাকবে:
- CRUD endpoint, request validation, structured logging
- PostgreSQL + migration
- JWT auth
- `Dockerfile` ও `docker-compose.yml` (app + database)
- কয়েকটা test

---

## 🎯 Milestone
`docker compose up` দিয়ে তোমার Go API চালাতে পারবে। **এই project-টাই পরের প্রতিটা phase-এ deploy করবে।**

---

পরের phase 👉 [Phase 3 — Messaging (RabbitMQ + Kafka)](../phase-3-messaging/00-index.md)
