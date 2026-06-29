# Infrastructure & Solutions Architect Study Plan
### Go → RabbitMQ → Kafka → Docker/Kubernetes → AWS Solutions Architecture
*Built for ~2 hours/day. Realistic full timeline: ~7 months. Adjust pace freely — consistency beats speed.*

---

## How to use this plan

**Daily 2-hour split (the 70/30 rule):**
- **~40 min — Learn:** watch/read the day's topic.
- **~70 min — Build:** write code, run labs, break things, fix them. This is where the real learning happens.
- **~10 min — Log:** write 3 lines in a notes file: *what I learned, what confused me, what to try tomorrow.* This single habit is the difference between finishing and quitting.

**Your unfair advantage:** You already run queue workers, schedulers, and dispatched jobs in Laravel. Whenever you hit a new concept in RabbitMQ, Kafka, or Kubernetes, ask "what's the Laravel equivalent?" — you'll learn 2x faster by anchoring to what you know.

**Rule:** Don't chase perfection in any phase. Aim for "I can build a working version and explain it." Depth comes from the capstone and from re-using these tools.

---

## Roadmap at a glance

| Phase | Topic | Weeks | Outcome |
|-------|-------|-------|---------|
| 0 | Foundations (Linux, networking, HTTP) | ongoing, woven in | Comfortable in the terminal |
| 1 | Go fundamentals | Weeks 1–5 | Read/write idiomatic Go, understand concurrency |
| 2 | Backend services in Go | Weeks 6–9 | REST API + PostgreSQL + Docker |
| 3 | Messaging: RabbitMQ then Kafka | Weeks 10–14 | Producer/consumer apps in Go |
| 4 | Docker + Kubernetes | Weeks 15–20 | Deploy your Go services to a cluster (target: KCNA) |
| 5 | AWS Solutions Architecture | Weeks 21–28 | Design cloud systems (target: SAA-C03) |
| 6 | System design + capstone + interview prep | Weeks 28–30+ | Tie everything together |

---

## Phase 1 — Go Fundamentals (Weeks 1–5)

**Goal:** Read and write idiomatic Go, and genuinely understand goroutines and channels (this is Go's whole reason to exist for infra work).

**Free resources (in order):**
1. **A Tour of Go** — `go.dev/tour` — official, interactive, do this first.
2. **Go by Example** — `gobyexample.com` — your reference for "how do I do X."
3. **Learn Go with Tests** — `quii.gitbook.io/learn-go-with-tests` — free book, teaches Go + testing together (a pro habit).
4. **freeCodeCamp Go course** (YouTube, ~7 hrs) — good for video learners.
5. **Boot.dev "Learn Go"** — hands-on, free portion available; excellent if you like in-browser exercises.

**What to build (don't skip these):**
- Week 1–2: A CLI tool — e.g. a "todo" or "expense tracker" that reads/writes a JSON file.
- Week 3: A number-guessing game or a URL-status checker (intro to error handling).
- Week 4 (concurrency week): A concurrent web scraper or a "ping 100 URLs at once" tool using goroutines + channels + `sync.WaitGroup`. **Spend real time here.**
- Week 5: A simple REST API using only the standard library `net/http` (no framework yet).

**Milestone:** You can explain the difference between a goroutine and a thread, and why channels are preferred over shared memory.

---

## Phase 2 — Backend Services in Go (Weeks 6–9)

**Goal:** Build a production-shaped backend. This is where your Laravel experience transfers directly.

**Free resources:**
- **Backend Engineering with Go** patterns — search "Alex Edwards Let's Go" concepts (his free blog posts on structuring Go web apps are gold).
- **Gin framework docs** — `gin-gonic.com` (or stick with `net/http` + `chi` router — both fine).
- **PostgreSQL + Go**: the `pgx` and `sqlc` docs. `sqlc` generates type-safe Go from SQL — you'll love it.
- **Docker official "Get Started"** — `docs.docker.com/get-started`.

**What to build — one solid project across the whole phase:**
A **REST API for a small domain you know** (e.g. a mini version of an election/committee tracker, since that's your world). Include:
- CRUD endpoints, request validation, structured logging.
- PostgreSQL with migrations.
- JWT auth.
- A `Dockerfile` and `docker-compose.yml` (app + database).
- A few tests.

**Milestone:** You can `docker compose up` and hit your Go API. This single project becomes the thing you deploy in every later phase.

---

## Phase 3 — Messaging: RabbitMQ then Kafka (Weeks 10–14)

Learn RabbitMQ first (simpler, closest to the Laravel queues you already know), then Kafka (different beast — streaming, not just queuing).

### RabbitMQ (Weeks 10–11)
**Free resources:**
- **Official RabbitMQ tutorials** — `rabbitmq.com/tutorials` — they have **Go versions** of all 6 tutorials. Do all six.
- **CloudAMQP blog** — clear explanations of exchanges, queues, routing.

**Concepts to nail:** producer/consumer, exchanges (direct, topic, fanout), routing keys, acknowledgements, dead-letter queues. *Map each to "how would I have done this with a Laravel queue?"*

**Build:** An order/notification system — one Go service publishes events, another consumes and "processes" them. Add a retry + dead-letter flow.

### Kafka (Weeks 12–14)
**Free resources:**
- **Confluent Developer** — `developer.confluent.io` — "Apache Kafka 101" and "Kafka for Developers" are free and the best intro anywhere.
- **Apache Kafka Quickstart** — `kafka.apache.org/quickstart`.
- Go client: the `segmentio/kafka-go` or `confluent-kafka-go` library docs.

**Concepts to nail:** topics, partitions, offsets, consumer groups, replication, why Kafka keeps messages (log) vs RabbitMQ deleting them. **This partition/consumer-group model is a top interview topic.**

**Build:** A Go producer streaming events into a Kafka topic + a consumer group with 2+ consumers, so you *see* partition rebalancing happen.

**Milestone:** You can explain in plain words when you'd choose RabbitMQ vs Kafka (task queue vs event stream).

---

## Phase 4 — Docker + Kubernetes (Weeks 15–20)

**Goal:** Containerize and orchestrate your Go services. Target the **KCNA** certification.

**Free resources:**
- **KodeKloud free courses** — `kodekloud.com/free-courses` — "Docker for the Absolute Beginner" and "Kubernetes for the Absolute Beginner" (free portions) + free hands-on labs. **Time this phase to land on their next Free Learning Week** for full access.
- **Kubernetes official interactive tutorial** — `kubernetes.io/docs/tutorials/kubernetes-basics`.
- **Play with Kubernetes** — `labs.play-with-k8s.com` — free browser cluster.
- **freeCodeCamp Kubernetes course** (YouTube).
- Local cluster tools: **kind** or **minikube** (free, run K8s on your laptop).

**Concepts to nail:** Pods, Deployments, Services, ConfigMaps/Secrets, namespaces, kubectl basics, the control plane vs worker nodes, scaling, rolling updates.

**Build:** Deploy your Phase-2 Go API + PostgreSQL + (optionally) RabbitMQ/Kafka into a local cluster (kind/minikube). Expose it via a Service. Scale the API to 3 replicas. Do a rolling update.

**Certification target:** **KCNA** — multiple-choice, conceptual, 75% to pass, beginner-friendly. Great confidence-builder before the harder hands-on **CKA** later.

**Milestone:** `kubectl apply -f` deploys your whole stack and you can explain what each manifest does.

---

## Phase 5 — AWS Solutions Architecture (Weeks 21–28)

**Goal:** Think like an architect — design secure, resilient, performant, cost-optimized systems. Target **SAA-C03**.

**Free resources:**
- **AWS Skill Builder** — `skillbuilder.aws` — free digital courses *and* a free SAA-C03 exam-prep course with practice questions.
- **freeCodeCamp SAA-C03 course** (~16 hrs, YouTube) — solid free full course.
- **Adrian Cantrill** — has free mini-courses; his paid SAA course is the gold standard if you ever spend money.
- **AWS Free Tier** — `aws.amazon.com/free` — 12 months of hands-on (EC2 t-micro, S3, RDS). **Set a billing alarm immediately so you never get surprised.**
- **AWS Well-Architected Framework** whitepaper — read it; the exam is built on it.

**Core services to master (these dominate the exam):**
- Compute: EC2, Auto Scaling, Lambda, ECS/Fargate
- Storage: S3 (and its classes), EBS, EFS
- Database: RDS, Aurora, DynamoDB
- Networking: VPC, subnets, security groups, route tables, load balancers, Route 53
- Security: IAM (policies — study hard, Security is 30% of the exam), KMS, encryption
- Integration: SQS, SNS, EventBridge — *you'll recognize these from your messaging phase*
- Plus: Amazon MSK (managed Kafka) and Amazon MQ (managed RabbitMQ) — full-circle with Phase 3.

**Study rhythm for this phase:** 1 hr course video + 1 hr in the AWS console actually building the thing you just learned. Then practice exams in the final 2 weeks.

**Certification target:** **SAA-C03** — $150, 65 questions, 130 min, 720/1000 to pass.

**Milestone:** Given a scenario ("highly available web app, low cost, can't lose data"), you can sketch an architecture and justify each choice.

---

## Phase 6 — System Design + Capstone + Interview Prep (Weeks 28–30+)

**Free resources:**
- **System Design Primer** — `github.com/donnemartin/system-design-primer` (free, comprehensive).
- **ByteByteGo** — free newsletter/YouTube for visual system-design explainers.

### Capstone project (the thing you show in interviews)
Build **one project that uses everything**:
> A Go-based event-driven system — REST API + a Kafka (or RabbitMQ) event pipeline + PostgreSQL — containerized with Docker, deployed to Kubernetes, and architected to run on AWS (even if you only deploy a slice of it to the free tier).

Write a one-page architecture doc with a diagram explaining your trade-offs (cost vs resilience vs performance). **This doc + repo is your portfolio.**

---

## Certifications — the honest breakdown

### Free *completion* certificates (good for learning + LinkedIn, not industry-graded)
- **Great Learning Academy** — free Golang course with completion certificate.
- **KodeKloud Free Learning Week** — finish courses during the free week, keep the certificates.
- **Confluent Developer** — free Kafka courses with badges.
- **AWS Skill Builder** — free courses and some free digital badges.
- **Microsoft Learn** — free learning paths with achievements.

### Paid but industry-recognized (worth it when you're job-targeting)
| Cert | Approx. cost | When |
|------|-------------|------|
| KCNA (Kubernetes) | ~$250 | After Phase 4 |
| AWS SAA-C03 | $150 | After Phase 5 |
| CKA (Kubernetes, hands-on) | ~$395 | Later, if going deep into K8s |
| Confluent CCDAK (Kafka) | ~$150 | Optional, if Kafka becomes your focus |

### Ways to pay less (relevant from Bangladesh)
- AWS regularly runs **free exam voucher** campaigns and offers a **50% retake/next-exam discount** once you hold any AWS cert — earn the cheapest one first.
- The **Linux Foundation / CNCF** (KCNA, CKA) runs frequent bundle discounts and occasional scholarships — never pay full price; wait for a sale.
- Look for **AWS Community Day / user-group vouchers** in Dhaka — local AWS communities sometimes distribute exam credits.
- **Truth:** the knowledge gets you hired; the certificate just opens the door. Build the projects first, sit the paid exam only when you're confident and ready to job-hunt.

---

## Viva / Interview Prep — questions to be able to answer

Practice *explaining out loud*, as if to an interviewer. If you can't explain it simply, you don't understand it yet.

**Go**
- What's a goroutine, and how is it different from an OS thread?
- Channels vs mutexes — when do you use each?
- How does Go handle errors, and why no exceptions?
- What's a `defer` and when does it run?

**Messaging**
- RabbitMQ vs Kafka — when would you choose each?
- Explain Kafka partitions and consumer groups.
- What's a dead-letter queue and why does it matter?
- How do you guarantee a message is processed at least once / exactly once?

**Docker / Kubernetes**
- Container vs virtual machine?
- What is a Pod, and why not just run containers directly?
- Deployment vs Service vs ConfigMap?
- How does a rolling update work without downtime?
- How does Kubernetes self-heal a crashed pod?

**AWS / Architecture**
- Walk me through designing a highly-available web app.
- When do you use SQS vs SNS vs Kafka (MSK)?
- How do you secure an S3 bucket?
- Explain the Shared Responsibility Model.
- How do you optimize a cloud bill that's spiraling?

**System design (the big one)**
- Design a URL shortener / a notification service / an event-driven order system.
- Always cover: trade-offs between cost, resilience, and performance — that phrasing is what makes you sound like an *architect*, not just an engineer.

---

## Staying consistent (the part that actually decides success)

- **Same 2 hours, same time, every day.** A fixed slot beats motivation.
- **Build > watch.** A finished tiny project teaches more than 10 hours of video.
- **Keep the daily 3-line log.** Reviewing it weekly shows real progress and fights burnout.
- **One project carried through all phases** (your Go API) means each phase deepens the same thing instead of starting over.
- **Don't wait to feel "ready"** for the next phase. ~80% understanding is enough to move on; the rest fills in with reuse.

*You've got this. Seven months of steady 2-hour days will take you from "small backend knowledge" to genuinely architect-shaped thinking.*
