# Phase 3 — Messaging: RabbitMQ then Kafka (Weeks 10–14)

> **লক্ষ্য:** আগে RabbitMQ (সহজ, তোমার চেনা Laravel queue-এর কাছাকাছি), তারপর Kafka (আলাদা জিনিস — streaming, শুধু queue নয়)।

[👈 মূল study plan-এ ফিরে যাও](../infrastructure-architect-study-plan.md)

---

## 🐰 RabbitMQ (Weeks 10–11)

👉 [RabbitMQ lessons](rabbitmq/00-index.md)

**যে concept গুলো নিখুঁত করতে হবে:** producer/consumer, exchange (direct, topic, fanout), routing key, acknowledgement, dead-letter queue। *প্রতিটাকে "Laravel queue দিয়ে কীভাবে করতাম?"-এর সাথে মেলাও।*

**ফ্রি রিসোর্স:**
- **Official RabbitMQ tutorials** — `rabbitmq.com/tutorials` (সব ৬টার **Go version** আছে — ছয়টাই করো)
- **CloudAMQP blog** — exchange, queue, routing-এর পরিষ্কার ব্যাখ্যা

**বানাবে:** order/notification system — একটা Go service event publish করে, আরেকটা consume করে "process" করে। retry + dead-letter flow যোগ করো।

---

## 🌊 Kafka (Weeks 12–14)

👉 [Kafka lessons](kafka/00-index.md)

**যে concept গুলো নিখুঁত করতে হবে:** topic, partition, offset, consumer group, replication, এবং কেন Kafka message রেখে দেয় (log) আর RabbitMQ মুছে ফেলে। **এই partition/consumer-group model একটা top interview topic।**

**ফ্রি রিসোর্স:**
- **Confluent Developer** — `developer.confluent.io` ("Apache Kafka 101" সেরা intro)
- **Apache Kafka Quickstart** — `kafka.apache.org/quickstart`
- Go client: `segmentio/kafka-go` বা `confluent-kafka-go`

**বানাবে:** একটা Go producer Kafka topic-এ event পাঠাবে + ২+ consumer-এর একটা consumer group, যাতে partition rebalancing **চোখে দেখতে** পারো।

---

## 🎯 Milestone
সহজ ভাষায় বলতে পারবে কখন RabbitMQ আর কখন Kafka বেছে নেবে (task queue vs event stream)।

---

পরের phase 👉 [Phase 4 — Docker + Kubernetes](../phase-4-docker-kubernetes/00-index.md)
