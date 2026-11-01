# 📊 Progress Tracker — RabbitMQ

> **Path:** `rabbitmq` — teach command **`/teach-rabbitmq`** · **Status:** active (not the default path)
> **Created:** 2026-11-01 · **Checkpoint:** 2026-11-21 (progress checkpoint; path continues) · **Last updated:** 2026-11-01 (learning day 0)
> **Session default:** 10 min · **Cadence:** 3–4 sittings/week · **Review cadence:** every 3rd learning day *of this path*
> **Plan:** [ROADMAP.md](ROADMAP.md) · **Registry:** [../../PATHS.md](../../PATHS.md)
> **Independent state:** this path's counters, buckets, tests, and rubric are its own. No other path's buckets block a session here. No cross-links to `default` by choice.

> Legend: `[ ]` not started · `[~]` in progress · `[x]` covered · `[✓]` **teach-back passed** (you explained it without notes — the only "real" done)

## Overall progress

```
RMQ1 Foundations & AMQP   [░░░░░░░░░░░░░░░░░░░░]   0%   (0/6 topics)
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

**Next up:** **RMQ1.1 Why a broker — RabbitMQ vs Kafka vs Redis Streams vs DB-as-queue.** First session = learning day 1 of this path.

**Rubric baseline:** set 2026-11-01, **avg 2.5** (self-scored 3/2/2/2/3/3). Weakest lines: delivery-guarantee reasoning, broker internals, operations & HA.

---

## 🪣 Carry-over buckets
> Per-day, never merged. A day stays partial `[~]` until its bucket is cleared + teach-back passed.
> Surfaced at every session start — **this path's buckets only**.

| Date | Topic | Cards left | Status |
|------|-------|-----------|--------|
| — | — | — | none open |

---

## RMQ1 — Foundations & the AMQP model
- [ ] RMQ1.1 Why a broker — RabbitMQ vs Kafka vs Redis Streams vs DB-as-queue
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
