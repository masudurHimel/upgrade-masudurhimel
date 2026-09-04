# 📊 Progress Tracker — Backend Engineering Deep Dive

> **Path:** `be` — teach command **`/teach-be`** · **Status:** active (not the default path)
> **Created:** 2026-08-22 · **Checkpoint:** ~2026-10-24 · **Last updated:** 2026-09-05 (learning day 9)
> **Session default:** 2–5 min · **Review cadence:** every 3rd learning day *of this path*
> **Plan:** [ROADMAP.md](ROADMAP.md) · **Registry:** [../../PATHS.md](../../PATHS.md)
> **Independent state:** this path's counters, buckets, tests, and rubric are its own. `default`'s buckets never block a session here.

> Legend: `[ ]` not started · `[~]` in progress · `[x]` covered · `[✓]` **teach-back passed** (you explained it without notes — the only "real" done)

## Overall progress

```
BE1 Client → request     [███░░░░░░░░░░░░░░░░░]  14%   (1/7 topics · BE1.1 [✓] · BE1.2 [~] 1/5 cards)
BE2 Reaching the server  [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
BE3 Accepting the conn   [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
BE4 The framework        [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
BE5 Processes & workers  [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
BE6 Capacity & failure   [░░░░░░░░░░░░░░░░░░░░]   0%   (0/7 topics)
─────────────────────────────────────────────────
TOTAL                    [█░░░░░░░░░░░░░░░░░░░]   2%   (1/42 topics)

Artifacts (written)  0/3        Tests passed   0        Teach-back ✓   1 topic + 1 partial (6 cards)
```

**Next up:** clear the **2026-09-05 review-miss bucket** (Q2 teach-back: 404 from your app vs 404 from the default server) — then BE1.2 card 2 — caching at every layer. Open buckets: 2026-09-02 (BE1.2 cards 2–5) · 2026-09-05 (Q2 miss).

**Rubric baseline:** set 2026-08-22, **avg 2.6** (coach-estimated at his request — 3/3/2/2/3). Weakest line: capacity & sizing.

---

## 🪣 Carry-over buckets
> Per-day, never merged. A day stays partial `[~]` until its bucket is cleared + teach-back passed.
> Surfaced at every session start — **this path's buckets only**.

| Date | Topic | Cards left | Status |
|------|-------|-----------|--------|
| ~~2026-08-22~~ | ~~BE1.1 What "making a request" actually means~~ | ~~(4) what goes on the wire — cleared 2026-08-26 · (5) full chain end-to-end + edge cases~~ | **✅ closed 2026-08-30** |
| ~~2026-08-23~~ | ~~Day-3 review misses (BE1.1 cards 1–2)~~ | ~~(a) `connect()` boundary — cleared 2026-08-24 · (b) TTL migration play — cleared 2026-08-26~~ | **✅ closed 2026-08-26** |
| ~~2026-08-24~~ | ~~Card-3 self-check miss~~ | ~~refused vs connect-timeout vs read-timeout — read the *latency of the failure*, not the word~~ | **✅ closed 2026-08-26** (day-6 review, 3/3) |
| ~~2026-08-26~~ | ~~Card-4 teach-back omission~~ | ~~request line before headers; where path/query hit the wire~~ | **✅ closed 2026-08-30** (folded into card 5) |

| 2026-09-02 | BE1.2 DNS resolution | (2) caching at every layer · (3) TTL mechanics & trade-offs · (4) record types + failure modes (NXDOMAIN vs SERVFAIL vs timeout) · (5) edge cases + staff lens (negative caching, K8s `ndots`) | **OPEN** |
| 2026-09-05 | Day-9 review miss (Q2) | 404 diagnosis: wrong **path** = 404 from *your app* (request in your log) vs wrong **`Host`** = default server answers (your app logs nothing) — the day-7 contrast, must teach back | **OPEN** |

---

## BE1 — The request leaves the client
- [✓] BE1.1 What "making a request" actually means — URL → resolution → socket *(all 5 cards ✓ teach-back passed, 2026-08-22 → 2026-08-30)*
- [~] BE1.2 DNS resolution — recursive lookup, caching, TTL *(card 1/5 ✓ 2026-09-02 — recursive lookup chain; cards 2–5 in bucket)*
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
| 2026-08-26 | 🔁 **Day-6 REVIEW** — 1 applied question (bucket 2026-08-24) | — | Learning day 6, second session of the same calendar date. **1-min box → 1 question**, so only the oldest bucket was reached. Q1 three-night failure triad (refused 8ms / connect-timeout 10s / read-timeout 30s): **3/3** — read all three by the *latency*, not the word: A app down, B never established ("the network swallowed it"), C connected + request received + no response. The flipped refused↔timeout miss from 2026-08-24 is **cleared**. Polished one imprecision: on a refused **no connection is ever created** — the SYN arrives and the box's *kernel* answers `RST` ("nothing listening on 443"), which is why it's fast; corrective contrast → a connection that opens and *then* dies gives `ReadTimeout`/mid-request reset (night C's family), never `ConnectionRefused`. Tell restated: fast failure ⇒ reachable but nothing listening · slow silence ⇒ never reached · fast connect + slow silence ⇒ alive but stuck. Not reached: the 2026-08-26 request-line bucket. |
| 2026-09-05 | 🔁 **Day-9 REVIEW** — 2 applied questions (BE1.1 + BE1.2 card 1) | — | Learning day 9. 2-min box → 2 questions. **Q1 ✓** payment-provider DNS migration: authoritative box + who runs it (provider, e.g. Cloudflare — the day-8 "who runs it" half-miss is **cleared**), TTL play correct. Polished: zero errors because the **old IP keeps answering** during the overlap; how long a pod stays stale = the TTL stamped when *its* cache stored the record. **Q2 ✗** the two-404s contrast (from day 7) slipped: answered A only and blamed nginx — re-taught that in A nginx routed fine and **Django's URL resolver** 404'd (wrong path, your log has the request); B skipped — wrong **`Host`** → no `server_name` match → **default server** 404s, your app logs nothing. Tell restated: *404 in your app's log = wrong path; 404 in the default server's log = wrong Host.* → **bucketed 2026-09-05**, must teach back before new material. |
| 2026-09-02 | BE1.2 card 1/5 — the recursive lookup: stub → recursive resolver → root → TLD → authoritative | 1 | Learning day 8. 2-min box → 1 card, 4 parked. Self-check 1.5/2: ~ Q1 authoritative ✓ but omitted *who runs it* (the zone owner — the fragile box vs replicated root/TLD); ✓ Q2 CoreDNS, shared-path reasoning. **Teach-back passed** — full chain in order (getaddrinfo → CoreDNS → VPC resolver → root → TLD → authoritative); polished in the **stub resolver** as the first box (forwards only, no detective work) and that a warm cache short-circuits the walk. Builds on BE1.1 card 2 (resolver cache, TTL). Next session = **day-9 review**. |
| 2026-08-30 | BE1.1 card 5/5 — the full chain end-to-end: 5 steps, SNI vs `Host` vs path, edge cases | 1 | Learning day 7. 2-min box → 1 card; **BE1.1 now `[✓]` — first topic complete on this path.** Folded in the 2026-08-26 bucket (request line before headers) — **cleared**. Self-check 1.5/2: ✓ Q1 path first exists at step 5, L7 can't route earlier → sharpened that the name reaches the server **twice** (SNI at step 4, `Host:` header at step 5) — `Host` is *not* early, it lands in the same write as the path; ~ Q2 SNI-was-right correct, 404 cause loose → corrective contrast: wrong **path** + right `Host` = 404 *from your API*; wrong **`Host`** = you never reach your server block, you get the **default server** (404 from a different site). Tell: check *which* vhost logged it. **Teach-back passed** — all 5 steps in order (parse → DNS → socket → TLS → send), polished step 5 to request line → headers → blank line → body. Forward-links: BE1.2 (DNS depth), BE1.4 (TLS/SNI), BE2.3 (why L4 can't see the path), BE2.6 (`server_name`/`location`). |

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
