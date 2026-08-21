# 🚀 3-Month Staff Engineer Roadmap (Revised)

> **Path:** `default` — **the DEFAULT path** (bare `/teach` resolves here) · registry: [../index.md](../index.md)
> **Owner:** Masudur Rahman — Senior Backend / Platform Engineer @ GoZayaan
> **Goal:** Senior → **Staff-level Platform & Backend Architect**
> **Start date:** 2026-06-19 · **Target review date:** 2026-09-19
> **Coach:** Claude (this assistant) — teaches daily, tracks progress, runs your tests, reviews you.

---

## How this works (read once)

This is not a reading list. It's a coached program. Here's the loop:

1. **You poke me daily** — say *"teach me"* (or name a topic). I serve that day's lesson.
2. **Lesson = 4–6 cards**, each ~4–5 min, with a 1-min break between them. Each card has:
   - **Concept** — plain language, no fluff
   - **Real example** — usually framed around GoZayaan (flights, hotels, bookings, payments, search)
   - **Staff lens** — why this matters when you're the one making the call
   - **🔧 Hands-on note** — *only* if I think doing-it-yourself is essential
   - **Self-check** — one question to prove you got it
3. **I update [PROGRESS.md](PROGRESS.md)** after every session — what's done, what's left, progress bars.
4. **Tests on cadence** — a checkpoint quiz after each topic cluster, a bigger test at month-end. Scores logged.
5. **You can change scope anytime** — *"add Redis internals"*, *"skip CPython bytecode"*, *"go deeper on Kafka"*. I re-slot the plan and adjust the trackers.

### Commands you can use
| You say | I do |
|---|---|
| `teach me` | Serve the next lesson in sequence |
| `teach me <topic>` | Jump to / inject a specific topic |
| `where am I?` | Show progress bars + what's next |
| `test me` | Run a checkpoint quiz on what you've covered |
| `review me` | Assess your explanations / artifact against the staff rubric |
| `add <topic>` / `drop <topic>` | Re-shape the roadmap |
| `I have N minutes` | I size the lesson to your time |

---

## What changed vs. the original plan (and why)

The original was a strong **syllabus** but a weak **transformation plan**. Five fixes:

1. **Artifacts per month** — you *build/produce* something, not just read. Recognition ≠ ability.
2. **A parallel leadership/influence track** — Staff is ~60% judgment & influence. See [SOFT_SKILLS.md](SOFT_SKILLS.md).
3. **A self-assessment rubric** — you grade against *staff competencies*, not "topics covered".
4. **"Prove it at work" hooks** — every cluster ties to something real at GoZayaan.
5. **System design as a first-class track** — 4 practice modes, all 3 months. See [SYSTEM_DESIGN.md](SYSTEM_DESIGN.md).

---

## The exponential engine (how this compounds, not just accumulates)

More topics = linear (and shallower). **These four mechanisms are what make growth compound.** I enforce them in how I teach and track:

1. **Teach-back gate.** A topic is only marked `✓` once you explain it back to me *without notes* (the Feynman test). `[x]` = covered; `[✓]` = you can actually wield it. Recognition is the #1 illusion of learning — this kills it.
2. **Connection web.** Every new concept gets tied to prior ones. `WAL → replication → Kafka's log → outbox → event sourcing` is **one idea seen five ways.** Connected knowledge lets you *reason*, not *recall* — that's the exponential part. I maintain these links as we go.
3. **Spaced resurfacing.** Old topics reappear in later tests so they stick instead of decaying. You'll get hit with a Month 1 question during a Month 3 quiz — on purpose.
4. **Build-in-public output.** Strong learnings become short internal notes / blog posts. Doubles retention *and* builds your staff reputation — one action, two returns.

---

## How testing works (5 layers)

You're tested continuously — not to grade you, but to convert recognition into real ability and beat the forgetting curve.

| Layer | When | What | Logged |
|---|---|---|---|
| **1. Self-check** | every card | one quick "what if…?" question | no |
| **2. Teach-back gate** | every topic | explain it back without notes → earns `✓` (else stays `[x]`, we revisit) | yes |
| **3. Checkpoint quiz** | end of each cluster (~4–6 topics) | 5–8 mixed/applied questions, scored | yes |
| **4. Month-end test** | end of each month | broad test + **spaced resurfacing** of earlier months → feeds rubric re-score | yes |
| **5. Capstone** | end of program | everything + artifact review + full rubric re-score → writes Phase 2 | yes |

**Principles:** applied scenarios > definitions · spaced resurfacing is automatic (Month-1 topics reappear in Month-3 quizzes) · failing → re-teach from a new angle, then re-test (we never move on with a hole) · trigger anytime with `test me` / `test me M2`, and I'll proactively offer checkpoints.

## Weekly cadence

- **5 learning days** (the daily loop above)
- **1 review day** — no new material. Re-explain the week from memory, refine notes, do the week's self-check.
- **1 rest day** — actually rest. Retention needs it.

---

## Month 1 — Foundations: Python, DSA & Networking

**Theme:** Be the person who knows *why* Python behaves the way it does, and understands the wire your services talk over.

### Topics
| ID | Topic | Notes |
|----|-------|-------|
| M1.1 | Python data model & object identity (`is` vs `==`, `id()`) | |
| M1.2 | Mutable vs immutable · `__dict__` vs `__slots__` | |
| M1.3 | MRO & method resolution (C3 linearization) | |
| M1.4 | Dunder methods & operator overloading | |
| M1.5 | Descriptors & properties | the magic behind `@property`, ORMs |
| M1.6 | Closures & scope (LEGB), late binding | |
| M1.7 | Decorators (incl. parametrized, stacked) | |
| M1.8 | Iterators & generators (`yield`, lazy pipelines) | |
| M1.9 | Context managers (`with`, `__enter__/__exit__`, `contextlib`) | |
| M1.10 | AsyncIO: event loop, coroutines, tasks | 🔧 likely hands-on |
| M1.11 | Concurrency patterns (gather, semaphores, queues) | |
| M1.12 | GIL · threading vs multiprocessing vs async | |
| M1.13 | Memory management, refcounting & GC | |
| M1.14 | CPython internals (bytecode, object layout) | |
| M1.15 | DSA: hash tables | concepts only (no LeetCode grind) |
| M1.16 | DSA: trees | |
| M1.17 | DSA: heaps | |
| M1.18 | DSA: graph basics | |
| M1.19 | Networking: TCP/IP & the life of a request | |
| M1.20 | TLS/HTTPS — handshake, certs, what "secure" means | |
| M1.21 | HTTP/1.1 vs HTTP/2 vs HTTP/3 | |
| M1.22 | Connection pooling & keep-alive | why your DB/HTTP clients pool |
| M1.23 | Git: merge vs rebase, worktrees | history hygiene; rewriting vs preserving history, isolated checkouts |

**🎯 Month 1 Artifact:** Build a small but real **async rate limiter** (token-bucket) *or* a **mini async task queue** — something you'd actually drop into a service. (~2–3 short sessions when you're ready.)

**🧭 Prove it at work:** Find one place in a GoZayaan service where `__slots__`, a generator, or an async pattern would help. Note it.

---

## Month 2 — Data, APIs, Performance & System Design Core

**Theme:** Be the person who reads an `EXPLAIN ANALYZE` and knows what to do, designs an API others build on for years, and can defend an architecture decision.

### Topics
| ID | Topic | Notes |
|----|-------|-------|
| M2.1 | Transactions & ACID | |
| M2.2 | MVCC (how Postgres avoids read locks) | |
| M2.3 | WAL (write-ahead log, durability, replication basis) | |
| M2.4 | Isolation levels (RC, RR, Serializable) & anomalies | |
| M2.5 | Locks & lock types (row, table, advisory) | |
| M2.6 | Deadlocks — cause, detection, avoidance | |
| M2.7 | Query planner & statistics | |
| M2.8 | EXPLAIN / EXPLAIN ANALYZE — reading plans | 🔧 likely hands-on |
| M2.9 | Index internals: B-Tree | |
| M2.10 | GIN / GiST / BRIN — when each wins | |
| M2.11 | Scalability fundamentals (vertical/horizontal, sharding) | |
| M2.12 | Consistency models (strong, eventual, causal) | |
| M2.13 | Caching architecture (patterns, invalidation, stampede) | |
| M2.14 | Event-driven architecture | |
| M2.15 | Build vs buy | |
| M2.16 | Monolith vs microservices | |
| M2.17 | Database-per-service & shared-DB pitfalls | |
| M2.18 | REST API design (resources, status codes, idempotency) | |
| M2.19 | Versioning & backward/forward compatibility | the staff skill: not breaking callers |
| M2.20 | gRPC vs REST · protobuf & contracts | |
| M2.21 | Profiling (CPU/memory, flame graphs) | 🔧 likely hands-on |
| M2.22 | Latency & percentiles (p50/p95/p99, tail latency) | |
| M2.23 | Load testing & capacity (throughput, Little's Law) | |
| M2.24 | Finding bottlenecks (USE / RED method) | |

**🎯 Month 2 Artifact (2 parts):**
1. Take a **real slow query** (GoZayaan or a seeded dataset), `EXPLAIN ANALYZE` it, fix it, write a before/after note.
2. Write **one short design doc / RFC** for a real-ish problem (see [SYSTEM_DESIGN.md](SYSTEM_DESIGN.md)).

**🧭 Prove it at work:** Bring a real query plan to a session; we'll dissect it together.

---

## Month 3 — Distributed Systems, Messaging, SRE & Security

**Theme:** Be the person trusted to design the system that *stays up*, *stays secure*, and the one who runs the incident.

### Topics
| ID | Topic | Notes |
|----|-------|-------|
| M3.1 | CAP theorem (what it really says) | |
| M3.2 | PACELC (the part CAP leaves out) | |
| M3.3 | Replication (sync/async, leader-follower) | |
| M3.4 | Consensus & Raft (intuition, not the paper) | |
| M3.5 | Quorums (R + W > N) | |
| M3.6 | Leader election | |
| M3.7 | Idempotency (keys, dedup) | |
| M3.8 | Retries, backoff, jitter | |
| M3.9 | Circuit breakers & bulkheads | |
| M3.10 | Distributed transactions (2PC and why it hurts) | |
| M3.11 | Sagas (orchestration vs choreography) | |
| M3.12 | Outbox pattern | 🔧 likely hands-on |
| M3.13 | RabbitMQ internals & quorum queues | |
| M3.14 | RabbitMQ streams | |
| M3.15 | Kafka partitions & consumer groups | |
| M3.16 | Kafka ISR & rebalancing | |
| M3.17 | SLI / SLO / SLA & error budgets | |
| M3.18 | Incident management & blameless postmortems | |
| M3.19 | Capacity planning | |
| M3.20 | Observability: metrics, logs, traces, OpenTelemetry | |
| M3.21 | AuthN vs AuthZ (sessions, tokens, scopes) | |
| M3.22 | OAuth2 / OIDC / JWT | how real auth flows work |
| M3.23 | Secrets management & encryption (at rest / in transit) | |
| M3.24 | Common backend vulns (OWASP: injection, SSRF, IDOR…) | |

**🎯 Month 3 Artifact:** Implement the **outbox pattern** *or* a toy **leader election**, *or* write a full **event-driven design** for a GoZayaan booking flow (your pick — sys-design lovers may prefer the design).

**🧭 Prove it at work:** Map one real GoZayaan failure/retry path to circuit-breaker + idempotency + outbox thinking.

---

## End-of-3-month checkpoint

> **Pacing note (be honest with yourself):** with the added clusters this is now ~70 topics — realistically **~14 weeks** of material at 20–30 min/day, not a clean 12. That's fine. **2026-09-19 is a checkpoint, not a deadline.** We pace by *understanding* (the teach-back gate), not by calendar. If we're at topic 55 of 70 on that date, we still run the assessment, measure growth, and write Phase 2 around where you actually are.

At 2026-09-19 we run a **capstone assessment**:
- A mixed test across all 3 months
- Review of your 3 artifacts
- Self-score against the **Staff rubric** (in [PROGRESS.md](PROGRESS.md))
- **Then we write Phase 2** based on your *actual* performance — strong areas accelerate, weak areas get reinforced.

### Phase 2 backlog (after completion)
Kubernetes · Terraform/OpenTofu · Platform Engineering · Advanced Kafka · Nginx internals · Networking deep-dive · AI Engineering · Staff+ architecture · Cost engineering.

---

## Files in this program
- **[ROADMAP.md](ROADMAP.md)** — this file (the plan)
- **[PROGRESS.md](PROGRESS.md)** — living tracker: progress bars, checklists, test scores, session log
- **[SYSTEM_DESIGN.md](SYSTEM_DESIGN.md)** — your 4-mode system design track
- **[SOFT_SKILLS.md](SOFT_SKILLS.md)** — curated leadership/influence resources (blogs, books, talks)
