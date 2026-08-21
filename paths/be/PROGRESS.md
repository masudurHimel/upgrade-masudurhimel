# 📊 Progress Tracker — Backend Engineering Deep Dive

> **Path:** `be` — teach command **`/teach-be`** · **Status:** active (not the default path)
> **Created:** 2026-08-22 · **Checkpoint:** ~2026-10-24 · **Last updated:** 2026-08-22
> **Session default:** 2–5 min · **Review cadence:** every 3rd learning day *of this path*
> **Plan:** [ROADMAP.md](ROADMAP.md) · **Registry:** [../../PATHS.md](../../PATHS.md)
> **Independent state:** this path's counters, buckets, tests, and rubric are its own. `default`'s buckets never block a session here.

> Legend: `[ ]` not started · `[~]` in progress · `[x]` covered · `[✓]` **teach-back passed** (you explained it without notes — the only "real" done)

## Overall progress

```
BE1 Client → request     [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
BE2 Reaching the server  [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
BE3 Accepting the conn   [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
BE4 The framework        [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
BE5 Processes & workers  [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
BE6 Capacity & failure   [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
─────────────────────────────────────────────────
TOTAL                    [░░░░░░░░░░░░░░░░░░░░]   0%   (0/42 topics)

Artifacts (written)  0/3        Tests passed   0        Teach-back ✓   0
```

**Next up:** BE1.1 — what "making a request" actually means (URL → resolution → socket). First session is **learning day 1** of this path.

**Pending:** rubric baseline not yet set — collect the five 1–5 self-scores at the top of the first session and stamp them dated.

---

## 🪣 Carry-over buckets
> Per-day, never merged. A day stays partial `[~]` until its bucket is cleared + teach-back passed.
> Surfaced at every session start — **this path's buckets only**.

> None open.

---

## BE1 — The request leaves the client
- [ ] BE1.1 What "making a request" actually means — URL → resolution → socket
- [ ] BE1.2 DNS resolution — recursive lookup, caching, TTL
- [ ] BE1.3 TCP connection setup — 3-way handshake
- [ ] BE1.4 TLS handshake — what's negotiated, session resumption
- [ ] BE1.5 HTTP request anatomy — methods, headers, body
- [ ] BE1.6 Keep-alive & connection reuse
- [ ] BE1.7 Client-side limits — browser caps, HTTP/2 multiplexing, mobile apps

## BE2 — Getting to your server
- [ ] BE2.1 The hop map — client → CDN → LB → reverse proxy → app server
- [ ] BE2.2 CDN & edge caching
- [ ] BE2.3 Load balancers — L4 vs L7
- [ ] BE2.4 LB algorithms — round-robin, least-conn, consistent hashing
- [ ] BE2.5 Health checks & connection draining
- [ ] BE2.6 Reverse proxy duties (nginx) — TLS termination, buffering, static files, timeouts
- [ ] BE2.7 Sticky sessions, `X-Forwarded-For`, and what the app can trust
- [ ] 🎯 Artifact 1 (written): "Life of a GoZayaan flight-search request: client → edge"

## BE3 — The server accepts the connection
- [ ] BE3.1 Sockets, ports, and the listen backlog
- [ ] BE3.2 `accept()`, file descriptors, `ulimit` — the real max-connections ceiling
- [ ] BE3.3 Blocking vs non-blocking I/O; the event loop (epoll/kqueue)
- [ ] BE3.4 The C10K problem
- [ ] BE3.5 What one connection actually costs — memory, FD, kernel buffers
- [ ] BE3.6 Timeouts at every layer — and how mismatches produce 502/504
- [ ] BE3.7 Backpressure & queueing

## BE4 — The framework receives it
- [ ] BE4.1 WSGI — the real contract (`environ`, `start_response`)
- [ ] BE4.2 ASGI — what changed and why
- [ ] BE4.3 Django's request path — middleware → URL resolver → view → response
- [ ] BE4.4 FastAPI/Starlette's request path — routing, DI, sync-vs-async endpoints
- [ ] BE4.5 Go for contrast — `net/http`, goroutine-per-request, the scheduler
- [ ] BE4.6 Middleware ordering — where auth, logging, tracing belong
- [ ] BE4.7 Serialization & validation — the hidden per-request CPU cost
- [ ] 🎯 Artifact 2 (written): "How our Django/FastAPI service really handles a connection"

## BE5 — Processes, threads & workers
- [ ] BE5.1 Process vs thread vs coroutine
- [ ] BE5.2 CPU-bound vs I/O-bound — the decision that drives everything
- [ ] BE5.3 The GIL in one card — what it blocks and what it doesn't
- [ ] BE5.4 Gunicorn architecture — master/arbiter + pre-fork workers
- [ ] BE5.5 Worker classes — sync vs gthread vs gevent vs uvicorn
- [ ] BE5.6 Sizing workers & threads — `(2×CPU)+1` folklore vs measuring
- [ ] BE5.7 Worker lifecycle — `max-requests`, graceful reloads, timeouts, memory creep

## BE6 — Capacity, failure & seeing inside
- [ ] BE6.1 Where a request's time actually goes — the latency budget
- [ ] BE6.2 Concurrency vs throughput vs latency — Little's Law
- [ ] BE6.3 Percentiles & tail latency — why p99 matters
- [ ] BE6.4 DB connection pooling — pool size vs worker count
- [ ] BE6.5 Load testing honestly — open vs closed models, warmup
- [ ] BE6.6 Failure modes end to end — retry storms, thundering herds, cascading timeouts
- [ ] BE6.7 Observability of a request — access logs, RED metrics, tracing
- [ ] 🎯 Artifact 3 (written): "Worker & pool sizing for one real service"

---

## Test log
| Date | Topic(s) | Type | Score | Notes |
|------|----------|------|-------|-------|
| — | — | — | — | No tests yet |

---

## Session log
| Date | Topics covered | Cards | Notes |
|------|----------------|-------|-------|
| — | — | — | No sessions yet |

---

## Path rubric (score 1–5, re-score monthly)

Five competencies specific to this path — **not** the 7 staff competencies used by `default`.

| Competency | What a 5 looks like | Baseline (Aug) | Sep | Oct |
|------------|---------------------|:---:|:---:|:---:|
| **Request-path fluency** | Traces any request hop by hop and says what each layer did to it | | | |
| **Concurrency-model judgment** | Picks process/thread/async/worker model from the workload and defends it | | | |
| **Capacity & sizing** | Turns traffic numbers into worker/pool/instance counts with math | | | |
| **Failure-mode reasoning** | Predicts where load or a slow dependency breaks the chain, and why | | | |
| **Diagnostic instinct** | Given 502s / a p99 spike / pool exhaustion, narrows to the layer fast | | | |

> **Baseline pending** — to be self-scored at the top of the first session and stamped with the date.
> The gap between your baseline and 4–5 is the real curriculum inside this path.
