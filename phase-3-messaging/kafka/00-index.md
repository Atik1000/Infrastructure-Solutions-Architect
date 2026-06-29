# Kafka (বাংলা)

> **লক্ষ্য:** topic, partition, offset, consumer group বোঝা — Go দিয়ে।

[👈 Phase 3-এ ফিরে যাও](../00-index.md)

---

## 📚 Lesson তালিকা (আসছে 🔜)

| # | Lesson | কী শিখবে |
|---|--------|----------|
| 01 | Kafka কী, RabbitMQ থেকে আলাদা কেন | queue vs log/stream |
| 02 | Kafka setup | Docker দিয়ে চালানো |
| 03 | Topic ও Partition | data কীভাবে ভাগ হয়ে থাকে |
| 04 | Producer (Go) | topic-এ event পাঠানো |
| 05 | Consumer ও Consumer Group | partition rebalancing চোখে দেখা |
| 06 | Offset | কোথা থেকে পড়া শুরু |
| 07 | Replication | data হারানো ঠেকানো |

---

## 🔗 ফ্রি রিসোর্স
- **Confluent Developer** — `developer.confluent.io` ("Apache Kafka 101")
- **Apache Kafka Quickstart** — `kafka.apache.org/quickstart`
- Go client: `segmentio/kafka-go` বা `confluent-kafka-go`

---

## 🎯 মনে রাখো
RabbitMQ message process হলে মুছে ফেলে; Kafka সব message **log হিসেবে রেখে দেয়** — তাই একই data অনেক consumer বারবার পড়তে পারে। এটাই মূল পার্থক্য।

---

পরের phase 👉 [Phase 4 — Docker + Kubernetes](../../phase-4-docker-kubernetes/00-index.md)
