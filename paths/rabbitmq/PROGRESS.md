# 📊 Progress Tracker — RabbitMQ

> **Path:** `rabbitmq` — teach command **`/teach-rabbitmq`** · **Status:** active (not the default path)
> **Created:** 2026-11-01 · **Checkpoint:** 2026-11-21 (progress checkpoint; path continues) · **Last updated:** 2026-11-11 (learning day 3 · review served, answers pending)
> **Session default:** 10 min · **Cadence:** 3–4 sittings/week · **Review cadence:** every 3rd learning day *of this path*
> **Plan:** [ROADMAP.md](ROADMAP.md) · **Registry:** [../../PATHS.md](../../PATHS.md)
> **Independent state:** this path's counters, buckets, tests, and rubric are its own. No other path's buckets block a session here. No cross-links to `default` by choice.

> Legend: `[ ]` not started · `[~]` in progress · `[x]` covered · `[✓]` **teach-back passed** (you explained it without notes — the only "real" done)

## Overall progress

```
RMQ1 Foundations & AMQP   [░░░░░░░░░░░░░░░░░░░░]   0%   (0/6 topics · RMQ1.1 [~] 4/5 cards)
RMQ2 Delivery guarantees  [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
RMQ3 Routing & patterns   [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
RMQ4 Queue types & intern [░░░░░░░░░░░░░░░░░░░░]   0%   (0/6 topics)
RMQ5 Clustering, HA & ops [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
RMQ6 Security & policies  [░░░░░░░░░░░░░░░░░░░░]   0%   (0/3 topics)
RMQ7 Clients, perf & fail [░░░░░░░░░░░░░░░░░░░░]   0%   (0/8 topics)
─────────────────────────────────────────────────
TOTAL                     [░░░░░░░░░░░░░░░░░░░░]   0%   (0/44 topics)

Artifacts (build)  0/2        Tests passed   0        Teach-back ✓   0
```

**Next up:** **🔁 day-3 REVIEW in progress** — 6 scenario questions served 2026-11-11 (RMQ1.1 cards 1–4), answers pending. Any miss ⇒ short re-teach + bucket. Once cleared: **RMQ1.1 card 5/5 — decision card** from the 2026-11-08 bucket, then RMQ1.2. Learning day 4 next.

**Rubric baseline:** set 2026-11-01, **avg 2.5** (self-scored 3/2/2/2/3/3). Weakest lines: delivery-guarantee reasoning, broker internals, operations & HA.

---

## 🪣 Carry-over buckets
> Per-day, never merged. A day stays partial `[~]` until its bucket is cleared + teach-back passed.
> Surfaced at every session start — **this path's buckets only**.

| Date | Topic | Cards left | Status |
|------|-------|-----------|--------|
| **2026-11-08** | RMQ1.1 Why a broker | (5) Decision card — tool per GoZayaan flow + staff lens | **🟡 open** (1 card left) |

---

## RMQ1 — Foundations & the AMQP model
- [~] RMQ1.1 Why a broker — RabbitMQ vs Kafka vs Redis Streams vs DB-as-queue *(cards 1–4 ✓ — 1–2 on 2026-11-08, 3–4 on 2026-11-10; 5 parked)*
- [ ] RMQ1.2 Connections, channels, virtual hosts
- [ ] RMQ1.3 Exchanges → bindings → queues: the routing pipeline; default exchange
- [ ] RMQ1.4 Exchange types — direct, fanout, topic, headers
- [ ] RMQ1.5 Message anatomy — properties, headers, body
- [ ] RMQ1.6 Wire mechanics — `basic.publish` / `basic.deliver` / `basic.get`, frames, heartbeats

## RMQ2 — Delivery guarantees
- [ ] RMQ2.1 Consumer acks — auto vs manual, ack / nack / reject, multiple-ack, `redelivered`
- [ ] RMQ2.2 Prefetch / QoS — per-consumer vs global, fairness vs throughput, starvation
- [ ] RMQ2.3 Publisher confirms — async confirms, nack, `mandatory` + `basic.return`, alternate exchanges
- [ ] RMQ2.4 Durability — durable entities vs persistent messages, what survives restart
- [ ] RMQ2.5 At-most / at-least / exactly-once — duplicates, idempotent consumers, dedup
- [ ] RMQ2.6 Ordering — when it holds and when it breaks
- [ ] RMQ2.7 AMQP transactions (`tx.*`) vs confirms

## RMQ3 — Routing & messaging patterns
- [ ] RMQ3.1 Work queues & competing consumers — fair dispatch
- [ ] RMQ3.2 Pub/sub & topic design — binding-key schemes, exchange-to-exchange bindings
- [ ] RMQ3.3 RPC — reply-to, correlation-id, direct reply-to, timeouts
- [ ] RMQ3.4 TTL — per-message vs per-queue, queue expiry, head-of-queue gotcha
- [ ] RMQ3.5 Dead-lettering — DLX, `x-death`, reasons, DLX cycles
- [ ] RMQ3.6 Retry patterns — TTL+DLX ladder, delayed-message plugin, backoff queues, poison messages
- [ ] RMQ3.7 Queue arguments & limits — max-length, overflow, priority queues, single-active-consumer

## RMQ4 — Queue types & broker internals
- [ ] RMQ4.1 Classic queues — message store, queue index, lazy mode
- [ ] RMQ4.2 Quorum queues — Raft, delivery-limit, poison handling, at-least-once dead-lettering
- [ ] RMQ4.3 Classic mirrored queues (deprecated) — why they failed
- [ ] RMQ4.4 Streams — append-only log, offsets, replay, super streams; vs Kafka
- [ ] RMQ4.5 Memory & disk — alarms, high watermark, disk-free limit, paging, credit flow
- [ ] RMQ4.6 Storage lifecycle — segment files, GC, recovery on restart

## RMQ5 — Clustering, HA & operations
- [ ] RMQ5.1 Clustering — nodes, Erlang distribution, metadata replication, queue locality, peer discovery
- [ ] RMQ5.2 Network partitions — detection, `ignore` / `pause_minority` / `autoheal`, split-brain
- [ ] RMQ5.3 Metadata store — Mnesia vs Khepri
- [ ] RMQ5.4 Connection management — reconnects, heartbeats vs keepalive, churn, channel leaks, LB in front
- [ ] RMQ5.5 Federation & Shovel — vs clustering
- [ ] RMQ5.6 Monitoring — management API, Prometheus, the metrics that matter, alerting
- [ ] RMQ5.7 Upgrades & lifecycle — feature flags, rolling vs blue/green, definitions export
- [ ] 🎯 Artifact A1 (build): 3-node Docker cluster — quorum-queue failover + partition-strategy demo

## RMQ6 — Security, policies & multi-tenancy
- [ ] RMQ6.1 Users, vhosts, permissions — configure / write / read regexes, topic permissions
- [ ] RMQ6.2 TLS & auth backends — OAuth2, LDAP; connection & channel limits
- [ ] RMQ6.3 Policies & operator policies — policy vs `x-args` precedence

## RMQ7 — Clients, performance & production failure modes
- [ ] RMQ7.1 Python clients — pika vs aio-pika; blocking vs async; channel thread-safety
- [ ] RMQ7.2 Consumer engineering — prefetch tuning, batch acks, graceful shutdown, consumer-cancel
- [ ] RMQ7.3 Publisher engineering — confirm pipelining, retries, outbox → RabbitMQ
- [ ] RMQ7.4 Contracts — message versioning, headers vs body, JSON vs protobuf, idempotency keys
- [ ] RMQ7.5 Performance — throughput vs latency, message size, persistence cost, queue count, schedulers
- [ ] RMQ7.6 Failure drill — unacked pile-up / stuck consumers / prefetch starvation
- [ ] RMQ7.7 Failure drill — memory & disk alarms, flow control, backlog paging
- [ ] RMQ7.8 Failure drill — message-loss post-mortems
- [ ] 🎯 Artifact A2 (build): GoZayaan booking-events pipeline in aio-pika — confirms + DLX retry ladder + idempotent consumer + chaos test

---

## Test log
| Date | Scope | Type | Score | Notes |
|------|-------|------|-------|-------|
| — | — | — | — | No tests yet |

---

## Session log
| Date | Topics covered | Cards | Notes |
|------|----------------|-------|-------|
| 2026-11-01 | Path setup | — | Roadmap + tracker created via `/create_path`. Learning day 0. |
| 2026-11-08 | RMQ1.1 cards 1–2/5 — (1) what a broker is: removes coupling in **time / speed / shape**; the spine — a message's location at every instant (publisher mem → wire → exchange → queue → wire → consumer mem → acked) and what kills or duplicates it at each arrow · (2) DB-as-queue: `SKIP LOCKED` polling table — its one real win is **atomic commit with business data**; breaks on polling load, UPDATE bloat, hot rows, no fan-out, stuck `running` rows; outbox = DB stage + broker fan-out | 2 | Learning day 1. 10-min box → 2 cards, 3 parked (bucket 2026-11-08). Self-check 5/7: ✓ three couplings; ✓ new risk = silent loss; ✗ DB-table unique win answered "duplicate probability" → re-taught: **atomicity** (he named it himself two answers later — wobbly, not absent); ✓ hottest table; ✗ "five workers → five duplicates" → corrective contrast: `SKIP LOCKED` means workers *skip* locked rows, zero duplicates — the real problem is **fan-out** (five consumer *types* ⇒ five rows per event), many workers on one job type is fine; ✓ stuck `running` row needs a lease + sweeper. **Teach-back passed (2026-11-10)**: sync HTTP = main service waits on all five and one 500 can fail the whole request; broker's new risk = silently dropping events; Postgres table for ~100 rpm email with atomicity + low volume; loss points wire / exchange / queue. Polished: the two biggest loss points he missed — **commit-then-crash-before-publish** (the dual-write gap, why outbox exists) and **consumer memory before ack**; a message never sits in an exchange — loss there = unroutable, dropped silently without `mandatory`. ⚠️ Resurface day-3 review: DB-table win = atomicity · `SKIP LOCKED` ⇒ no double-grab, fan-out ≠ duplicates · the commit→publish gap. Forward-links: RMQ2.1 acks, RMQ2.3 `mandatory`, RMQ2.5 duplicates, RMQ4.5 backlog memory, RMQ7.3 outbox. |
| 2026-11-10 | RMQ1.1 cards 3–4/5 — (3) RabbitMQ vs Kafka: **queue = to-do list** (deliver → ack → delete; smart broker tracks per-message state; routing / TTL / DLX / priority built in; no replay) vs **log = diary** (append-only, kept by retention time; consumer keeps an offset bookmark; replay free; fan-out = another group's bookmark; but a poison message blocks its partition, consumers ≤ partitions). Same loss/dup shape — **ack ↔ offset commit** · (4) Redis Streams: a log **in RAM** with per-message pending tracking (`XADD` / `XREADGROUP` / `XACK`, PEL); killed by `MAXLEN` trim of unconsumed entries, restart with no/lagging AOF, async-replica failover; duplicated via PEL re-claim; no DLX, no requeue-on-disconnect — you write `XAUTOCLAIM` + delivery-count checks yourself | 2 | Learning day 2. 10-min box → cards 3–4 from the 2026-11-08 bucket; card 5 (decision card) still parked. **Teach-back passed (2026-11-11)**: queue drops / log keeps until retention / stream keeps until `MAXLEN`; all six loss+dup cases named correctly (RMQ: broker crash before durable write · crash-before-ack; Kafka: auto-commit-then-crash · crash-before-commit; Redis: `MAXLEN` trim · crash-before-`XACK`). Polished: RabbitMQ deletes on **ack**, not on read; Redis Streams also replays within the cap (`XRANGE` / new group from `0`). ✗ Q3 "wrong when a time range is needed" → corrected: IDs are timestamps so `XRANGE` by time works; the real failure is **`MAXLEN` is a count, not a duration** (a burst day evicts older days) + no persistence ⇒ restart wipes the window. ⚠️ Resurface day 3. Forward-links: RMQ2.1 acks, RMQ2.6 ordering, RMQ3.5 DLX, RMQ4.4 Streams, RMQ4.5 backlog alarms. |
| 2026-11-11 | 🔁 **Day-3 REVIEW** — RMQ1.1 cards 1–4 resurfaced as 6 applied scenarios: (1) the one real win of a `SKIP LOCKED` payments table · (2) 8 workers ≠ duplicates, fan-out is the multiplier · (3) commit-then-OOM-before-publish — where is the message, which pattern closes it · (4) ack / offset-commit / `XACK` crash-before-done in all three systems · (5) `MAXLEN` on an Eid-sale burst + two other ways a Streams entry dies · (6) "Redis Streams can't replay" — correct it | 0 (review) | Learning day 3 — review day. Answers pending; row to be finalised with score + any bucketed misses. Card 5 (decision card) still parked in the 2026-11-08 bucket, served after the review clears. |

---

## Path rubric — RabbitMQ (score 1–5, revisit monthly)

| Competency | Baseline (Nov) | Month 1 | Month 2 | Month 3 |
|------------|:---:|:---:|:---:|:---:|
| **Messaging-model fluency** — can predict where any message lands given exchanges / bindings / args | **3** | | | |
| **Delivery-guarantee reasoning** — can state exactly when a message is lost or duplicated | **2** | | | |
| **Broker internals** — queue types, Raft, memory / disk, flow control from first principles | **2** | | | |
| **Operations & HA** — clustering, partitions, monitoring, upgrades | **2** | | | |
| **Production debugging** — symptom → root cause for pile-ups, alarms, loss | **3** | | | |
| **Client / consumer engineering** — pika / aio-pika, prefetch, idempotency, shutdown | **3** | | | |

> **Baseline set 2026-11-01.** Average **2.5**. Re-score at each checkpoint; the delta is the evidence of growth.
