# Phase 1 — Go Fundamentals (Weeks 1–5)

> **লক্ষ্য:** Idiomatic Go পড়া ও লেখা, এবং goroutine ও channel সত্যিকারভাবে বোঝা (infra-কাজে Go-এর মূল শক্তি এটাই)।

[👈 মূল study plan-এ ফিরে যাও](../infrastructure-architect-study-plan.md)

---

## 📚 Lesson তালিকা (আসছে 🔜)

| # | Lesson | কী শিখবে |
|---|--------|----------|
| 01 | Go কী ও setup | install, `go run`, `go build`, প্রথম program |
| 02 | Variable ও type | `var`, `:=`, int/string/bool, type system |
| 03 | Function ও package | function, return, package, import |
| 04 | Condition ও loop | `if`, `for`, `switch` |
| 05 | Slice ও Map | array, slice, map — data রাখা |
| 06 | Struct ও Method | নিজের type বানানো |
| 07 | Error handling | Go-তে কেন exception নেই, `error` ফেরত দেওয়া |
| 08 | Goroutine ও Channel ⭐ | concurrency — Go-এর আসল শক্তি |
| 09 | `defer`, `sync.WaitGroup` | সঠিকভাবে concurrent code লেখা |

---

## 🔗 ফ্রি রিসোর্স (ক্রম অনুযায়ী)
1. **A Tour of Go** — `go.dev/tour` (official, interactive — এটা প্রথমে করো)
2. **Go by Example** — `gobyexample.com` ("কীভাবে X করব"-এর রেফারেন্স)
3. **Learn Go with Tests** — `quii.gitbook.io/learn-go-with-tests` (Go + testing একসাথে)
4. **freeCodeCamp Go course** (YouTube, ~7 ঘণ্টা)
5. **Boot.dev "Learn Go"** — in-browser exercise

---

## 🛠️ যা যা বানাবে (এগুলো বাদ দিও না)
- **Week 1–2:** একটা CLI tool — যেমন "todo" বা "expense tracker" যা JSON file পড়ে/লেখে
- **Week 3:** number-guessing game বা URL-status checker (error handling শেখা)
- **Week 4 (concurrency week):** goroutine + channel + `sync.WaitGroup` দিয়ে "১০০ URL একসাথে ping" tool। **এখানে সত্যিকার সময় দাও।**
- **Week 5:** শুধু standard library `net/http` দিয়ে একটা সাধারণ REST API (এখনো framework নয়)

---

## 🎯 Milestone
goroutine ও OS thread-এর পার্থক্য, এবং shared memory-র বদলে channel কেন ভালো — ব্যাখ্যা করতে পারবে।

> 💡 **তোমার সুবিধা:** Laravel-এ queue worker, scheduler চালানোর অভিজ্ঞতা আছে। নতুন concept পেলেই ভাবো "এর Laravel সমতুল্য কী?" — ২x দ্রুত শিখবে।

---

পরের phase 👉 [Phase 2 — Backend Services in Go](../phase-2-backend/00-index.md)
