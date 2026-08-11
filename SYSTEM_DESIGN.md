# 🏛️ System Design Track

> Your heavy-interest area. This runs **across all 3 months**, in parallel with the main roadmap.
> You picked **all four practice modes** — so we cycle through them.

The four modes, and how we use each:

| Mode | What it is | Cadence |
|------|-----------|---------|
| **1. Build real components** | Implement scaled-down versions of real building blocks | ~1 per month (it's an artifact) |
| **2. Design real systems** | Write design docs / RFCs for GoZayaan-scale problems | ~1 doc/month |
| **3. Interview drills** | Classic "design X" prompts, timed, then I critique | 1 short drill/week (review day) |
| **4. Study famous systems** | Read how real systems work + why they chose their tradeoffs | woven into daily cards |

---

## Mode 1 — Build real components (pick one per month)

These map to your monthly artifacts. Small enough for a few short sessions, real enough to matter.

- **Month 1:** Token-bucket **rate limiter** (async) — teaches concurrency, time, fairness.
- **Month 2:** A **read-through cache** with stampede protection (single-flight) — teaches caching pitfalls.
- **Month 3:** **Outbox pattern** publisher *or* a toy **leader election** over a lock — teaches reliability primitives.

> Build is optional-but-recommended. If you'd rather stay theory + design, tell me and I'll swap build slots for extra design docs.

## Mode 2 — Design real systems (GoZayaan-flavored prompts)

Pick one per month, write a 1–2 page design doc, I review it against a real RFC bar (problem → constraints → options → decision → tradeoffs → failure modes → rollout).

Candidate prompts (travel-platform realistic):
1. **Flight search + caching** under bursty traffic and volatile fares.
2. **Booking & seat/inventory hold** with no double-booking (idempotency + locking).
3. **Payment flow** with retries, idempotency keys, and an outbox to a ledger.
4. **Price/availability fan-out** to many suppliers with timeouts & circuit breakers.
5. **Notifications** (email/SMS/push) — at-least-once delivery, dedup, ordering.
6. **Audit/event log** — event-driven, replayable, schema evolution.

## Mode 3 — Interview drills (weekly, ~15 min, on review day)

Timed prompt → you sketch → I critique like an interviewer (probing scale numbers, bottlenecks, failure modes). Rotating classics + travel twists:
URL shortener · rate limiter · news feed · ticketing/seat booking · chat · nearby-search (geo) · distributed ID generator · notification system · ride-matching · object storage.

## Mode 4 — Study famous systems (woven into daily cards)

When a topic has a great real-world exemplar, I'll point you at it and summarize the tradeoff:
- **Postgres MVCC**, **Kafka's log**, **Cassandra/Dynamo quorums**, **Stripe idempotency**, **Google's SRE error budgets**, **Amazon's distributed-systems patterns**, **Redis**, **Raft (raft.github.io visualization)**.

---

## Anchor resources (free / canonical)
- **System Design Primer** (github.com/donnemartin/system-design-primer) — breadth map
- **Designing Data-Intensive Applications** (Kleppmann) — *the* book; we'll pull chapters as topics align
- **The Architecture of Open Source Applications** (aosabook.org) — how real systems are built
- **High Scalability** (highscalability.com) — real architecture case studies
- **Raft visualization** (raft.github.io) — consensus, made clickable

> I'll keep a running list here of which prompts you've done and how the review went, mirrored in PROGRESS.md.

## System design log
| Date | Mode | Prompt / component | Outcome / my critique |
|------|------|--------------------|------------------------|
| — | — | — | Not started |
