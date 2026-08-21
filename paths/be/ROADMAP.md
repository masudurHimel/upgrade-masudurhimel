# 🌐 Backend Engineering Deep Dive

> **Path:** `be` — teach command **`/teach-be`** · registry: [../../PATHS.md](../../PATHS.md)
> **Owner:** Masudur Rahman — Senior Backend / Platform Engineer @ GoZayaan
> **Outcome:** trace *any* request hop by hop and say what each layer did to it — then pick and defend a concurrency + capacity model for it, end to end.
> **Start date:** 2026-08-22 · **Checkpoint:** ~2026-10-24 (8–10 weeks)
> **Style:** breadth-first survey · **Session default:** 2–5 min · **Coach:** Claude

---

## How this works (read once)

Same engine as the `default` Staff Engineer path, run **completely independently** — this path has its own learning-day counter, its own review cadence, its own carry-over buckets. Nothing here blocks or is blocked by `default`.

1. **You poke me** — `/teach-be` (optionally `/teach-be 10 mins`). I serve the next topic in sequence.
2. **Lesson = 4–6 cards**, each: **Concept** (plain language) → **real-world example** (everyday analogy) → **GoZayaan example** (flights, hotels, bookings, payments, search) → **edge cases** → **staff lens** → **self-check**.
3. **Breadth-first.** Each topic is *one survey pass* that builds the map — enough to reason and to know what you'd go read next. Depth comes later, on the topics that turn out to matter.
4. **I update [PROGRESS.md](PROGRESS.md)** after every session, then refresh this path's row in the registry.
5. **Time-boxed** — a small budget means fewer cards *now*, never thinner cards. Leftovers get parked in a dated carry-over bucket and the topic sits at `[~]` until you clear it.

### The engine
1. **Teach-back gate** — `[x]` = covered, `[✓]` = you explained it back without notes. Only `[✓]` counts.
2. **Connection web** — every topic ties to the ones before it. This path is *one request* seen forty ways.
3. **Spaced resurfacing** — review every **3rd learning day of this path**; earlier clusters reappear in later quizzes.
4. **Build-in-public** — the three written artifacts below are the output.

### Testing
self-check (per card) → teach-back (per topic) → cluster quiz (`/test_me be`) → checkpoint review + rubric re-score.

---

## The clusters

### BE1 — The request leaves the client
| ID | Topic | Notes |
|----|-------|-------|
| BE1.1 | What "making a request" actually means — URL → resolution → socket | the map for the whole path |
| BE1.2 | DNS resolution — recursive lookup, caching, TTL | why the first hit is slow |
| BE1.3 | TCP connection setup — 3-way handshake | the RTT you pay before any bytes move |
| BE1.4 | TLS handshake — what's negotiated, session resumption | the extra round trip HTTPS costs |
| BE1.5 | HTTP request anatomy — methods, headers, body | what the client adds for you |
| BE1.6 | Keep-alive & connection reuse | why a fresh connection per request is expensive |
| BE1.7 | Client-side limits — browser connection caps, HTTP/2 multiplexing, mobile apps | |

### BE2 — Getting to your server
| ID | Topic | Notes |
|----|-------|-------|
| BE2.1 | The hop map — client → CDN → LB → reverse proxy → app server | who does what, and why each exists |
| BE2.2 | CDN & edge caching | the requests that never reach you |
| BE2.3 | Load balancers — L4 vs L7 | what each can actually see and decide |
| BE2.4 | LB algorithms — round-robin, least-conn, consistent hashing | how each one misroutes |
| BE2.5 | Health checks & connection draining | removing a bad instance; deploying without dropped requests |
| BE2.6 | Reverse proxy duties (nginx) — TLS termination, buffering, static files, timeouts | |
| BE2.7 | Sticky sessions, `X-Forwarded-For` | what the app can and cannot trust |

### BE3 — The server accepts the connection
| ID | Topic | Notes |
|----|-------|-------|
| BE3.1 | Sockets, ports, and the listen **backlog** | where a request waits before anyone reads it |
| BE3.2 | `accept()`, file descriptors, `ulimit` | the real "max connections" ceiling |
| BE3.3 | Blocking vs non-blocking I/O; the event loop (epoll/kqueue) | ties `default` M1.10 |
| BE3.4 | The C10K problem | why thread-per-connection stops scaling |
| BE3.5 | What one connection actually costs — memory, FD, kernel buffers | |
| BE3.6 | Timeouts at every layer — client, LB, proxy, app, DB | how mismatches produce 502/504 |
| BE3.7 | Backpressure & queueing | shed, queue, or fall over when you're full |

**🎯 Artifact 1 (written), after BE1–BE2:** *"Life of a GoZayaan flight-search request: client → edge"* — every hop, what it did, what it cost.
**🧭 Prove it at work:** trace one real endpoint's hops and put a millisecond number on each.

### BE4 — The framework receives it
| ID | Topic | Notes |
|----|-------|-------|
| BE4.1 | WSGI — the real contract (`environ`, `start_response`) | why Django is "just a callable" |
| BE4.2 | ASGI — what changed and why | long-lived connections, websockets, async views |
| BE4.3 | Django's request path — WSGI callable → middleware → URL resolver → view → response | |
| BE4.4 | FastAPI/Starlette's request path — routing, dependency injection, sync-vs-async endpoints | |
| BE4.5 | Go for contrast — `net/http`, goroutine-per-request, the runtime scheduler | why it feels different |
| BE4.6 | Middleware ordering | where auth, logging, and tracing actually belong |
| BE4.7 | Serialization & validation | the hidden per-request CPU cost |

### BE5 — Processes, threads & workers
| ID | Topic | Notes |
|----|-------|-------|
| BE5.1 | Process vs thread vs coroutine | the memory and scheduling picture |
| BE5.2 | CPU-bound vs I/O-bound | the one call that drives every worker decision |
| BE5.3 | The GIL in one card — what it blocks and what it doesn't | cites `default` M1.12 |
| BE5.4 | Gunicorn architecture — master/arbiter + pre-fork workers | |
| BE5.5 | Worker classes — sync vs gthread vs gevent vs uvicorn | chosen from the workload, not the docs |
| BE5.6 | Sizing workers & threads — `(2×CPU)+1` folklore vs measuring | where it's flat wrong for I/O-bound |
| BE5.7 | Worker lifecycle — `max-requests` recycling, graceful reloads, timeouts, memory creep | |

**🎯 Artifact 2 (written), after BE3–BE4:** *"How our Django/FastAPI service really handles a connection"* — socket to view, written for a teammate.
**🧭 Prove it at work:** read your service's actual gunicorn/uvicorn config and explain every flag on it.

### BE6 — Capacity, failure & seeing inside
| ID | Topic | Notes |
|----|-------|-------|
| BE6.1 | Where a request's time actually goes | the latency budget across every hop |
| BE6.2 | Concurrency vs throughput vs latency | Little's Law as the sanity check |
| BE6.3 | Percentiles & tail latency — why p99 is the number that matters | cites `default` M2.22 |
| BE6.4 | DB connection pooling — pool size vs worker count | the classic exhaustion outage |
| BE6.5 | Load testing honestly — open vs closed models, warmup | what a bad test hides |
| BE6.6 | Failure modes end to end — retry storms, thundering herds, cascading timeouts | |
| BE6.7 | Observability of a request — access logs, RED metrics, tracing across hops | |

**🎯 Artifact 3 (written), after BE5–BE6:** *"Worker & pool sizing for one real service"* — a capacity model backed by measurements, not folklore.
**🧭 Prove it at work:** find one place where pool size and worker count disagree, and say what happens under load.

---

## Checkpoint (~2026-10-24)

- `/test_me be` across all six clusters, applied scenarios
- review of the three written artifacts
- rubric re-score against the baseline in [PROGRESS.md](PROGRESS.md)
- then: pick the 3–4 topics that turned out to matter most and go **deep** on them (this path was breadth-first by design)

### Phase 2 backlog for this path
Kernel networking internals (`SO_REUSEPORT`, TCP tuning, congestion control) · HTTP/2 and HTTP/3 internals · Kubernetes ingress & service mesh · sidecar/proxy overhead · gRPC transport · eBPF for request tracing · multi-region routing & anycast.
