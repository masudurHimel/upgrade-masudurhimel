# 📊 Progress Tracker — Backend Engineering Deep Dive

> **Path:** `be` — teach command **`/teach-be`** · **Status:** active (not the default path)
> **Created:** 2026-08-22 · **Checkpoint:** ~2026-10-24 · **Last updated:** 2026-08-26 (learning day 5)
> **Session default:** 2–5 min · **Review cadence:** every 3rd learning day *of this path*
> **Plan:** [ROADMAP.md](ROADMAP.md) · **Registry:** [../../PATHS.md](../../PATHS.md)
> **Independent state:** this path's counters, buckets, tests, and rubric are its own. `default`'s buckets never block a session here.

> Legend: `[ ]` not started · `[~]` in progress · `[x]` covered · `[✓]` **teach-back passed** (you explained it without notes — the only "real" done)

## Overall progress

```
BE1 Client → request     [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics · BE1.1 [~] 4/5 cards)
BE2 Reaching the server  [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
BE3 Accepting the conn   [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
BE4 The framework        [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
BE5 Processes & workers  [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
BE6 Capacity & failure   [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
─────────────────────────────────────────────────
TOTAL                    [░░░░░░░░░░░░░░░░░░░░]   0%   (0/42 topics)

Artifacts (written)  0/3        Tests passed   0        Teach-back ✓   0 topics (4 cards)
```

**Next up:** BE1.1 card 5/5 — the full chain end-to-end + edge cases (last parked card; clears the 2026-08-22 bucket and flips BE1.1 to `[✓]`). Learning day 5 done; **next session (day 6) = REVIEW day**.

**Rubric baseline:** set 2026-08-22, **avg 2.6** (coach-estimated at his request — 3/3/2/2/3). Weakest line: capacity & sizing.

---

## 🪣 Carry-over buckets
> Per-day, never merged. A day stays partial `[~]` until its bucket is cleared + teach-back passed.
> Surfaced at every session start — **this path's buckets only**.

| Date | Topic | Cards left | Status |
|------|-------|-----------|--------|
| 2026-08-22 | BE1.1 What "making a request" actually means | 1 — ~~(4) what actually goes on the wire (request line + headers)~~ **cleared 2026-08-26** · (5) full chain end-to-end + edge cases | **open** |
| ~~2026-08-23~~ | ~~Day-3 review misses (BE1.1 cards 1–2)~~ | ~~(a) `connect()` boundary — cleared 2026-08-24 · (b) TTL migration play — cleared 2026-08-26~~ | **✅ closed 2026-08-26** |
| 2026-08-24 | Card-3 self-check miss | 1 — refused vs connect-timeout vs read-timeout: read the *latency of the failure*, not the word (fast reply ⇒ network fine, app dead; silence ⇒ never connected; connect fast + slow response ⇒ app slow) | **open** — resurface day-6 review |
| 2026-08-26 | Card-4 teach-back omission | 1 — the **request line** (`METHOD path?query HTTP/1.1`) is written *before* the headers; it is where path/query finally hit the wire. `Host` → server block, path → location/upstream | **open** — resurface day-6 review |

---

## BE1 — The request leaves the client
- [~] BE1.1 What "making a request" actually means — URL → resolution → socket *(cards 1–4/5 ✓ teach-back passed 2026-08-22 → 2026-08-26; card 5 parked)*
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
| 2026-08-22 | BE1.1 card 1/5 — a URL is four instructions for four layers; network needs only IP + port | 1 | Learning day 1. 2-min box → partial `[~]`, 4 cards parked. Teach-back **passed** — got IP + port correct; added the *why* (names resolve in userspace via `getaddrinfo`; `connect()` takes 4-byte IP + 2-byte port). Rubric baseline still awaited. |
| 2026-08-23 | BE1.1 card 2/5 — DNS: name → address (`getaddrinfo`, resolver, TTL, caching) | 1 | Learning day 2. 2-min box → 1 card, 3 still parked. Self-check 2/3: ✓ lookup happens in-process; ✓ first call slow (worded as "no caching" → corrected to **cold cache**); ✗ stale-IP cause answered "TTL" → corrected with contrast (same TTL, one client re-resolves and recovers, one cached the IP at startup and needs a restart). **Teach-back passed** — derived DNS necessity from card 1 (`connect()` takes 4-byte IP + 2-byte port, knows no names) and named the cache path. ⚠️ Resurface on day 3 review: *client-side IP caching vs TTL*. |
| 2026-08-23 | 🔁 **Day-3 REVIEW** — BE1.1 cards 1–2, 4 applied questions | — | Second session of the same calendar date (learning day 3). **2 clean / 2 incomplete.** ✓ Q1 stale-IP: diagnosed cached IP, correctly rejected the TTL bait (the flagged day-2 miss is **cleared**) — re-taught the *tell* (a restart fixes it). ✓ Q2: DNS time hides inside the supplier span. ~ Q3: said `connect()` uses the hostname as 4 bytes → re-taught that the name dies in userspace after `getaddrinfo`; skipped where path/query go → **bucketed**. ~ Q4: trade-off right, action missing → re-taught *lower TTL in advance, raise after* → **bucketed**. Closing teach-back **passed**: 1 DNS lookup + 2 `connect()` (correct for scope; forward-linked to BE1.6 keep-alive where the minimum is 1). Fixed "connect gets IP from cache" → the resolver cache serves *names*. |
| 2026-08-24 | BE1.1 card 3/5 — opening the socket: `connect(fd, IP, port)`, the fd, the 4-tuple, ephemeral ports | 1 | Learning day 4. 2-min box → 1 card, 2 still parked. Folded in review miss (a): `connect()` carries **only** 4-byte IP + 2-byte port — path/query/headers/TLS are bytes written *after* → **cleared**. Side-questions he raised (both good): source port is the random/ephemeral one (dest stays 443) → `TIME_WAIT` + ~28k range ⇒ port exhaustion, fix is keep-alive/pooling (forward-link BE1.6); and asked whether TLS is covered later → yes, BE1.4 + BE2.6. Self-check 2/3: ✓ Q1 only IP+443; ✗ Q2 **flipped** refused↔timeout (called refused a "network issue" and timeout "connected but slow") → re-taught with the three-state contrast, **bucketed**; ✓ Q3 L4 can't read the path. **Teach-back passed** — `connect(fd,ip,port)`, nginx accepts blind with no application data, path arrives as bytes after. Polished: nginx *accepts* not connects; it does see the 4-tuple (→ BE2.7 `X-Forwarded-For`); first bytes on 443 are TLS (→ BE1.4). |
| 2026-08-26 | BE1.1 card 4/5 — what actually goes on the wire: request line, headers, `Host`, SNI | 1 | Learning day 5. 2-min box → 1 card, 1 still parked. Folded in review miss (b): **TTL migration play** — lower TTL days *in advance*, flip, settle, restore; safe because only the IP moves while `Host:` stays identical → **cleared**, closing the 2026-08-23 bucket. Self-check **3/3**: ✓ Q1 `Host` (sharpened → matched against `server_name`); ✓ Q2 TTL play *with* the why ("old value is already cached"); ✓ Q3 SNI picks the cert, `Host` picks the route. **Teach-back passed** — pipe → client writes → blank line → body → routes on `Host`. Polished: the **request line comes first**, before any header, and is where path/query reach the wire → **bucketed** for day-6. Forward-links: BE1.4 (TLS/SNI), BE2.6 (nginx server blocks), BE2.7 (`X-Forwarded-For`). |

---

## Path rubric (score 1–5, re-score monthly)

Five competencies specific to this path — **not** the 7 staff competencies used by `default`.

| Competency | What a 5 looks like | Baseline (Aug) | Sep | Oct |
|------------|---------------------|:---:|:---:|:---:|
| **Request-path fluency** | Traces any request hop by hop and says what each layer did to it | 3 | | |
| **Concurrency-model judgment** | Picks process/thread/async/worker model from the workload and defends it | 3 | | |
| **Capacity & sizing** | Turns traffic numbers into worker/pool/instance counts with math | 2 | | |
| **Failure-mode reasoning** | Predicts where load or a slow dependency breaks the chain, and why | 2 | | |
| **Diagnostic instinct** | Given 502s / a p99 spike / pool exhaustion, narrows to the layer fast | 3 | | |

> **Baseline set 2026-08-22 — coach-estimated at his request** ("fill this what you think best"), not self-scored. Avg **2.6**.
> Basis: `default`-path asyncio depth (M1.10/M1.11 ✓ — Semaphore, `asyncio.Queue` pool, `gather(return_exceptions=True)`) → concurrency 3; daily nginx/gunicorn/Django operation but no hop-by-hop mechanism → request-path 3; no evidence of capacity math (Little's Law / pool sizing unlearned) → 2; production exposure to failures but no predictive reasoning shown → 2; senior on-call instinct + clean BE1.1 teach-back → diagnostic 3.
> **Weakest + highest-leverage line: Capacity & sizing (2).** Overridable by his own self-score at any time.
> The gap between your baseline and 4–5 is the real curriculum inside this path.
