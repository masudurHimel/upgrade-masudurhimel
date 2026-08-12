# 📊 Progress Tracker

> Updated by Claude after every session. Last updated: **2026-08-11**.
> Legend: `[ ]` not started · `[~]` in progress · `[x]` covered · `[✓]` **teach-back passed** (you explained it without notes — the only "real" done)

## Overall progress

```
Month 1  [█████████░░░░░░░░░░░]  43%   (10/23 topics)
Month 2  [░░░░░░░░░░░░░░░░░░░░]   0%   (0/24 topics)
Month 3  [░░░░░░░░░░░░░░░░░░░░]   0%   (0/24 topics)
─────────────────────────────────────────────────
TOTAL    [███░░░░░░░░░░░░░░░░░]  14%   (10/71 topics)

Artifacts   0/3        Tests passed   0        Teach-back ✓   10
System design track:  see SYSTEM_DESIGN.md
```

**Next up:** M1.10 AsyncIO — finish carry-over (cancellation/timeouts). ⚠️ Carry-over from 2026-08-11 (M1.10, 1 card left).

---

## 🪣 Carry-over buckets
> Per-day, never merged. A day stays partial `[~]` until its bucket is cleared + teach-back passed.
> Surfaced at every session start.

> **OPEN — 2026-08-11 (M1.10 AsyncIO):** slices 1–3 taught (event loop + `await`=pause/resume, concurrent≠parallel; coroutine internals = generator freeze/resume, `await`≈`yield`, loop-resume≈`.send()`; `create_task` vs `gather` — schedule-one-in-bg-handle vs fire-all-wait-all, ~800ms≈slowest call). **1 card left: cancellation/timeouts.** Must clear for full M1.10 ✓.

> Closed 2026-08-11: 2026-08-11 review bucket (3 items — `@contextmanager` try/finally leak, decorator wrap-vs-run order, `cached_property` instance-dict-wins — all teach-backs passed same session).

> Closed 2026-08-06: M1.9 (`contextlib` helpers + nesting, teach-backs passed → ✓).

> Closed 2026-07-21: M1.8 (protocol + `yield` basics + lazy pipelines + genexprs + `yield from`, all teach-backs passed → ✓).
> Closed 2026-07-18: M1.7 (cards 1–2 + ① factory + ② stacking + ③ class-based, all teach-backs passed → ✓).
> Closed 2026-07-04: M1.6 (both slices + decorator-bridge teach-back passed → ✓).
> Closed 2026-06-30: M1.5 (all 4 slices + teach-backs passed → ✓).
> Closed 2026-06-25: M1.4 (all 4 slices + teach-backs passed → ✓).
> Closed 2026-06-22: M1.3 (all 4 cards + teach-back passed → ✓).

---

## Month 1 — Foundations: Python, DSA & Networking
- [✓] M1.1 Python data model & object identity
- [✓] M1.2 Mutable vs immutable · `__dict__` vs `__slots__`
- [✓] M1.3 MRO & method resolution
- [✓] M1.4 Dunder methods & operator overloading
- [✓] M1.5 Descriptors & properties
- [✓] M1.6 Closures & scope (LEGB)
- [✓] M1.7 Decorators
- [✓] M1.8 Iterators & generators
- [✓] M1.9 Context managers
- [~] M1.10 AsyncIO: event loop, coroutines, tasks
- [ ] M1.11 Concurrency patterns
- [ ] M1.12 GIL · threading vs multiprocessing vs async
- [ ] M1.13 Memory management & GC
- [ ] M1.14 CPython internals
- [ ] M1.15 DSA: hash tables
- [ ] M1.16 DSA: trees
- [ ] M1.17 DSA: heaps
- [ ] M1.18 DSA: graph basics
- [ ] M1.19 Networking: TCP/IP & the life of a request
- [ ] M1.20 TLS/HTTPS — handshake, certs
- [ ] M1.21 HTTP/1.1 vs HTTP/2 vs HTTP/3
- [ ] M1.22 Connection pooling & keep-alive
- [✓] M1.23 Git: merge vs rebase, worktrees
- [ ] 🎯 Artifact: async rate limiter / mini task queue

## Month 2 — Data, APIs, Performance & System Design Core
- [ ] M2.1 Transactions & ACID
- [ ] M2.2 MVCC
- [ ] M2.3 WAL
- [ ] M2.4 Isolation levels & anomalies
- [ ] M2.5 Locks & lock types
- [ ] M2.6 Deadlocks
- [ ] M2.7 Query planner & statistics
- [ ] M2.8 EXPLAIN / EXPLAIN ANALYZE
- [ ] M2.9 Index internals: B-Tree
- [ ] M2.10 GIN / GiST / BRIN
- [ ] M2.11 Scalability fundamentals
- [ ] M2.12 Consistency models
- [ ] M2.13 Caching architecture
- [ ] M2.14 Event-driven architecture
- [ ] M2.15 Build vs buy
- [ ] M2.16 Monolith vs microservices
- [ ] M2.17 Database-per-service & shared-DB pitfalls
- [ ] M2.18 REST API design
- [ ] M2.19 Versioning & backward/forward compatibility
- [ ] M2.20 gRPC vs REST · protobuf & contracts
- [ ] M2.21 Profiling (CPU/memory, flame graphs)
- [ ] M2.22 Latency & percentiles (p50/p95/p99)
- [ ] M2.23 Load testing & capacity (Little's Law)
- [ ] M2.24 Finding bottlenecks (USE / RED)
- [ ] 🎯 Artifact: slow-query optimization writeup
- [ ] 🎯 Artifact: one design doc / RFC

## Month 3 — Distributed Systems, Messaging, SRE & Security
- [ ] M3.1 CAP
- [ ] M3.2 PACELC
- [ ] M3.3 Replication
- [ ] M3.4 Consensus & Raft
- [ ] M3.5 Quorums
- [ ] M3.6 Leader election
- [ ] M3.7 Idempotency
- [ ] M3.8 Retries, backoff, jitter
- [ ] M3.9 Circuit breakers & bulkheads
- [ ] M3.10 Distributed transactions (2PC)
- [ ] M3.11 Sagas
- [ ] M3.12 Outbox pattern
- [ ] M3.13 RabbitMQ internals & quorum queues
- [ ] M3.14 RabbitMQ streams
- [ ] M3.15 Kafka partitions & consumer groups
- [ ] M3.16 Kafka ISR & rebalancing
- [ ] M3.17 SLI / SLO / SLA & error budgets
- [ ] M3.18 Incident management
- [ ] M3.19 Capacity planning
- [ ] M3.20 Observability & OpenTelemetry
- [ ] M3.21 AuthN vs AuthZ
- [ ] M3.22 OAuth2 / OIDC / JWT
- [ ] M3.23 Secrets management & encryption
- [ ] M3.24 Common backend vulns (OWASP)
- [ ] 🎯 Artifact: outbox / leader election / event-driven design

---

## Test log
| Date | Topic(s) | Type | Score | Notes |
|------|----------|------|-------|-------|
| — | — | — | — | No tests yet |

---

## Session log
| Date | Topics covered | Cards | Notes |
|------|----------------|-------|-------|
| 2026-06-19 | Program setup | — | Roadmap + trackers created |
| 2026-06-19 | Baseline rubric | — | Locked: 3/2/3/3/2/2/2 (avg 2.4) |
| 2026-06-19 | M1.1 Python data model & object identity | 5 | Learning day 1. Teach-back ✓ (is/==, interning). |
| 2026-06-20 | M1.2 Mutable vs immutable · __dict__ vs __slots__ | 3 | Learning day 2 (5-min express). Teach-back ✓ (slots=memory at scale). |
| 2026-06-20 | M1.3 MRO & method resolution (slice 1/4) | 1 | Learning day 3 (2-min slice). Diamond + C3 intuition. Partial [~], bucket open. |
| 2026-06-20 | M1.3 MRO & method resolution (slice 2/4) | 1 | Learning day 3 (2-min slice). C3 merge mechanics. Bucket: 2 cards left. |
| 2026-06-22 | M1.3 close (super() chain, inconsistent MRO) | 2 | Learning day 4. Cooperative super() + MRO TypeError, both teach-backs passed → M1.3 ✓. M1.4 cards shown but skipped (not learned) — reset to not-started, re-teach 06-23. |
| 2026-06-22 | Review day 5 — rapid recall M1.1–M1.3 (2-min sprint) | — | Spaced resurfacing PASSED. is/== + interning ✓ (caught −5..256 fix), __slots__→removes per-instance __dict__ ✓ (after 1 nudge), C3/MRO super() resolves to BaseGateway ✓ (after 1 nudge). |
| 2026-06-25 | M1.4 Dunder methods (slice 1/4) | 1 | Learning day 6 (2-min slice). Protocol hooks — dunders resolved on the TYPE via MRO; Fare example. Partial [~], bucket open (3 slices left). Teach-back pending. |
| 2026-06-25 | M1.4 slice 1 re-teach + teach-back | 1 | Learning day 6 (2-min). Re-ran card 1 (he'd missed it). Teach-back ✓ — lookup on type(x) not instance, special-method lookup bypasses instance via MRO. Slice 1 ✓; 3 cards left. |
| 2026-06-25 | M1.4 slice 2 (__eq__/__hash__ contract) | 1 | Learning day 6 (2-min). Teach-back ✓ after 1 correction — initially flipped direction (thought same-hash⇒equal); corrected to collisions + equal⇒same-hash. Airport dict-key example. Slice 2 ✓; 2 cards left. |
| 2026-06-25 | M1.4 slice 3 (__repr__ vs __str__) | 1 | Learning day 6 (2-min). Teach-back ✓ — got addresses-on-print right; sharpened that list's __repr__ calls repr() on elements so __str__ never fires. Slice 3 ✓; 1 card left. |
| 2026-06-25 | M1.4 slice 4 (reflected ops + total_ordering) | 1 | Learning day 6 (2-min). Teach-back ✓ — NotImplemented (not raise) triggers reflected fallback; total_ordering needs __eq__ + one ordering op. M1.4 fully ✓; bucket closed. |
| 2026-06-29 | M1.5 Descriptors & properties (slice 1/4) | 1 | Learning day 7 (2-min). Teach-back ✓ — assignment hits `__set__` so validation fires; descriptor must live on the class not instance. `property` = prebuilt descriptor. Planted data-descriptor priority for slice 2. Partial [~], bucket open. |
| 2026-06-30 | M1.5 slice 2 (data vs non-data + lookup priority) | 2 | Learning day 8 (5-min). data desc › instance dict › non-data desc; `property`=data (always recomputes), `cached_property`=non-data (caches via instance dict). Edge: read-only property still data; validators must be data. Teach-back ✓ — nailed both: total recomputes (ignores dict), fx_rate honors the dict override. Slice 2 ✓; 2 slices left. |
| 2026-06-30 | M1.5 slice 3 (`property` getter/setter/read-only) | 1 | Learning day 8 (2-min). Thermostat-dial example; getter/setter hooks, omit setter = read-only (auto AttributeError) = still data descriptor; backward-compatible refactor angle. Teach-back ✓ — got setter+validation; sharpened the "why callers don't break" (interface/syntax unchanged) + need getter & `_price` backing field. Slice 3 ✓; 1 slice left. |
| 2026-06-30 | M1.5 slice 4 (`__set_name__` / reusable ORM fields) | 1 | Learning day 8 (2-min). Name-tag example; reusable descriptor class vs N copies of property; `__set_name__` auto-supplies the field name so price/tax don't collide in obj.__dict__; Django/SQLAlchemy fields = descriptors. Teach-back ✓ — had the collision instinct (would clobber on a shared key); sharpened that the instance dict is shared correctly, the risk is same-key not shared-dict. M1.5 FULLY ✓; bucket closed. |
| 2026-07-02 | M1.6 Closures & scope (slice 1/2) | 2 | Learning day 9 (5-min). LEGB lookup order (charger analogy) + UnboundLocalError trap; closures = inner fn that remembers enclosing var (ticket analogy, fare_formatter factory). Partial `[~]`, bucket open (slice 2 left). Slice 1 teach-back ✓ — LEGB order + NameError-vs-UnboundLocalError, closure survives via captured cell. |
| 2026-07-02 | M1.6 slice 2 (`nonlocal` + late-binding loop trap) | 2 | Learning day 9 (2-min). make_counter/nonlocal, `lambda i=i` fix for [2,2,2]. Teach-back ✓ all — closure captures the variable not value; nonlocal needed to assign into enclosing var; assignment anywhere makes name local for whole fn (compile-time) → UnboundLocalError. 1 card left (decorator bridge). |
| 2026-07-04 | M1.6 close — decorator bridge (closure→decorator) | 1 | Learning day 10 (2-min). Decorator = closure aimed at a fn; `@timed`=`f=timed(f)`; wrapper closes over `fn`. Teach-back ✓ all 3 (remembers fn / desugar / wrapper runs first); sharpened "captured cell not value". M1.6 FULLY ✓; bucket closed. Planted `functools.wraps` for M1.7. Day-10 review deferred → next session. |
| 2026-07-08 | M1.7 Decorators (slice 1/2) | 2 | Learning day 11 (5-min). Arg-forwarding (`*args/**kwargs` + `return result`) + `functools.wraps` (planted hook). Cargo analogy: receptionist notepad / stunt-double face. Teach-back ✓ both — wrapper crashes without args, loses result without return; wraps copies name+docstring, identity tools (logs/routes) break silently. Sharpened: both failure modes are SILENT (None / wrong names), not crashes. Partial `[~]`, bucket open (3 items left). |
| 2026-07-15 | M1.7 Decorators — factory ① (`@retry(times=3)`), 1-min slice | 1 | Learning day 12. Teach-back ✓ — parens ⇒ extra layer; `retry(3)` returns `decorator` before seeing fn; config held in closure. Bucket: 2 left (stacking, class-based). |
| 2026-07-15 | M1.7 Decorators — stacking ② (`@a @b`), 1-min slice | 1 | Learning day 12. Teach-back ✓ — bottom wraps first (`@retry` on raw fn), top runs first (`@log_call` outer); wrap order ⇄ run order mirror. Bucket: 1 left (class-based). |
| 2026-07-18 | M1.7 Decorators — close ③ class-based (`__call__`), 5-min | 1 | Learning day 13. Teach-back ✓ — class is a decorator via `__call__`; `@CountCalls` ⇒ instance, state in `self` vs closure cell; pick class for state+surface. Sharpened: `__init__(fn)` captures + `__call__` runs (both needed); class wins to *expose* a handle (`.count`/`.reset()`), not just hold state. Ties to M1.4 `__call__` dunder + closure→decorator bridge. Edge planted: class decorator on a *method* skips `__get__` self-binding. M1.7 FULLY ✓; bucket closed. |
| 2026-07-06 | Day-10 review — rapid recall M1.4–M1.6 (+M1.2 callback), 5-min | — | Spaced resurfacing PASSED. Q1 __repr__ fallback + lookup on type ✓ (said __str__; sharpened repr fallback). Q2 data desc recomputes ✓ but reason weak ("consistency" → corrected to lookup priority data›dict›non-data). Q3 lambda i=i fix ✓ (mechanism sharpened: captures variable/cell not value). Q4 fetch=timed(fetch) ✓. Q5 __slots__ missed first (drifted), recovered on re-ask → removes per-instance __dict__, fixed slots. |
| 2026-07-08 | M1.23 Git: merge vs rebase, worktrees (explicit-topic, new → added to roadmap) | 6 | Full lesson. Teach-back ✓ all 3 — rebase=new-ID copies tied to is/== (M1.1); shared→merge; worktree hotfix flow keeps feature folder intact. Sharpened: `worktree remove` is the clean-up, `prune` only mops up manually-deleted folders. M1.23 fully ✓. No carry-over (explicit-topic rule). |
| 2026-07-19 | M1.8 Iterators & generators (slice 1/2) | 2 | Learning day 14 (5-min). Iterator protocol: iterable(reusable) vs iterator(disposable/one-shot); `for`=iter()+next()+StopIteration swallowed; bookmark analogy; ties to M1.4 dunders. Generators: `yield`⇒generator fn; calling runs nothing (returns gen obj), each next() runs to yield then freezes locals; bare return=StopIteration; lazy. Partial `[~]`, bucket open (3 items). Teach-back ✓ — Q1 iter()+next()+StopIteration nailed; Q2 sharpened the *why*: generator is lazy⇒paused, body starts on first next(), runs to first yield then freezes (had confused "why frozen" with `__next__`, corrected). |
| 2026-07-21 | M1.8 close — lazy pipelines · genexprs · `yield from` (5-min) | 3 | Learning day 15 (bucket clear; day-15 review deferred). Teach-back ✓ all 3 — pipeline stays flat = one item per stage flows the whole chain (sharpened: constant memory across all stages, not one gen); `()` genexpr streams vs `[]` materializes-then-consumes; `yield from` kills the manual re-loop AND forwards `.send()`+sub-gen return. Planted `.send()`/return-forwarding as the coroutine bridge → M1.10 asyncio. M1.8 FULLY ✓; bucket closed. |
| 2026-07-22 | Day-15 review (deferred) — rapid recall M1.5–M1.8, 5-min | — | Partial. Demonstrated 2/5: Q3 decorator stacking ✓ (desugar + "wraps first ⇒ runs last"; sharpened: name innermost=runs-last); Q4 generator pipeline ✓ (one item pulled through, resumes from frozen point; sharpened the one word = *lazy*/pull-based). Q1/Q2/Q5 skipped ("Pass" — no recall credit, stay ✓ from prior). |
| 2026-08-01 | M1.9 Context managers (slice 1/2) | 2 | Learning day 16 (5-min). `with` = object with `__enter__`(setup, returns the `as` value) + `__exit__`(cleanup, ALWAYS runs). Desugars to try/finally; ties to M1.4 dunders + M1.8 `for`-desugaring. GoZayaan pooled-connection example (release on error). Teach-back ✓ — named enter/exit + "no worry to user"; sharpened the core: `__exit__` fires even on exception (plain call doesn't). Partial `[~]`, bucket open (4 items: exception swallowing, `@contextmanager`, `contextlib`, nesting). |
| 2026-08-01 | M1.9 — exception swallowing (`__exit__` return value), 2-min slice | 1 | Learning day 16. Teach-back ✓ — return `None`/`False` ⇒ error "moves forward"/propagates; `True` ⇒ swallowed. Sharpened: danger word = *silent* (careless `True` hides real failures, caller thinks success); swallow only the exception you own; `__exit__` still runs on happy path (exc_type None). Bucket: 3 items left. |
| 2026-08-02 | M1.9 — `@contextmanager` generator form, 2-min slice | 1 | Learning day 17. Teach-back ✓ — before `yield`=enter, after=exit; `finally`=`__exit__` guarantee. Sharpened #2: without try/finally, exception thrown back into gen at `yield` skips post-yield cleanup → leak. Ties to M1.8 generator freeze/resume. Bucket: 2 items left (`contextlib` helpers, nesting). |
| 2026-08-06 | M1.9 close — `contextlib` helpers (`suppress`/`closing`/`ExitStack`) + nesting, 2-min | 1 | Learning day 18 (was a review day — deferred, spent on bucket close per carry-over rule). Teach-back: Q1 ✓ (nested exit reverse-order, already-entered A still cleaned when B enter throws). Q2 half → corrected: `closing(x)` is for objects with `.close()` but NO `__enter__/__exit__` (not "finally is annoying"); `with x:` would raise AttributeError. M1.9 FULLY ✓; bucket closed. Day-18 review carried to next session. |
| 2026-08-11 | Day-19 review (deferred Day-18) — rapid recall M1.5/M1.7/M1.9, 5-min | — | Learning day 19. 1/4 clean. Q1 `__exit__` runs + False propagates/True swallows ✓. Q2 `@contextmanager` no try/finally → PASS (bucketed). Q3 stacking → "LIFO/FIFO" shape but didn't name retry-wraps-first/log_call-runs-first (bucketed). Q4 `cached_property` → got "doesn't recompute" but missed mechanism (instance-dict wins for non-data descriptor) (bucketed). Bucket open (3 items) — must clear before M1.10. |
| 2026-08-11 | Review bucket clear — teach-backs (Q2/Q3/Q4) | — | Learning day 19. All 3 passed without notes: try/finally-on-yield leak ✓, bottom-wraps/top-runs ✓, cached_property instance-dict-wins ✓. Bucket closed; review debt cleared. M1.10 unlocked. |
| 2026-08-11 | M1.10 AsyncIO (slice 1/?) — event loop | 1 | Learning day 20 (1-min slice). Coroutine = pausable fn (freeze/resume like generator `yield`); `await`=pause on I/O-wait, loop resumes when wait done; waiter analogy; GoZayaan 5-airline `gather` ~800ms vs 4s. Edge: CPU-bound hogs the one thread. Teach-back ✓ — network-not-CPU, resume-when-wait-over, ~800ms total. Sharpened: **concurrent≠parallel** (one thread, waits overlap not code). Partial `[~]`, bucket open (~3 cards left). |
| 2026-08-11 | M1.10 AsyncIO (slice 2/?) — coroutine internals | 1 | Learning day 21 (1-min slice). Coroutine = the generator freeze/resume machine with nicer words: `async def`="can pause", `await`=the pause point (≈`yield`), event loop=who resumes (≈`.send()`). Microwave-pause + GoZayaan `get_fare` `await http.get` example. Edge: `await` only helps if the awaited thing yields control (I/O); CPU loop still blocks. Teach-back ✓ — frozen at await, loop works elsewhere, resumes where paused when wait over. Sharpened: the *awaited future* signals ready (fn is passive), not the fn announcing itself. Ties M1.8 `yield`/`.send()`. Bucket: ~2 cards left. |
| 2026-08-12 | M1.10 AsyncIO (slice 3/?) — `create_task` vs `gather` | 1 | Learning day 22 (2-min slice). `gather` = fire-all + wait-all → results list (~800ms). `create_task` = start one coroutine in bg now, get a handle, keep working, `await` later. Calling `get_fare()` runs nothing (coroutine obj, M1.8 tie); `create_task`/`gather` schedule it on the loop. Waiter-orders vs kitchen-buzzer analogy; 5-airline example. Edge: un-awaited task → "destroyed but pending" + swallowed exception. Teach-back ✓ both — plain call returns coroutine obj/runs nothing vs create_task schedules-now→concurrent; gather overlaps 5 waits vs 4s sequential. Sharpened: ~800ms ≈ the *slowest single call* (waits happen at the same time, not summed). Bucket: 1 card left (cancellation/timeouts). |

---

## Staff competency self-assessment (score 1–5, revisit monthly)

Grade honestly. The gap between where you are and 4–5 is your real curriculum.

| Competency | Baseline (Jun) | Month 1 | Month 2 | Month 3 |
|------------|:---:|:---:|:---:|:---:|
| **Technical depth** (can reason from first principles) | **3** | | | |
| **System design** (designs that survive scale & failure) | **2** | | | |
| **Technical judgment** (tradeoffs, build-vs-buy) | **3** | | | |
| **Debugging / RCA** (finds true root cause) | **3** | | | |
| **Influence & communication** (RFCs others adopt) | **2** | | | |
| **Mentorship** (levels up others) | **2** | | | |
| **Operational maturity** (SLOs, incidents, on-call) | **2** | | | |

> **Baseline set 2026-06-19.** Average **2.4**. Re-score at each month-end; the September delta is your evidence of growth.
> Useful reference ladders: progression.fyi, the "Staff Engineer" archetypes (Tech Lead / Architect / Solver / Right Hand).
