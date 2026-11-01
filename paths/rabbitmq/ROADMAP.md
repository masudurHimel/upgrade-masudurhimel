# 🐇 RabbitMQ — Everything, Fundamentals to Advanced Edge Cases

> **Path:** `rabbitmq` — teach command **`/teach-rabbitmq`** · registry: [../../PATHS.md](../../PATHS.md)
> **Owner:** Masudur Rahman — Senior Backend / Platform Engineer @ GoZayaan
> **Outcome:** **design and operate** a RabbitMQ topology end to end (queue types, routing, delivery guarantees, HA) **and debug it in production** from first principles — pile-ups, alarms, partitions, message loss — saying exactly *when* a message can be lost or duplicated and why.
> **Start date:** 2026-11-01 · **Checkpoint:** 2026-11-21 (20-day progress checkpoint — the path continues past it; the window extends as needed)
> **Style:** deep fundamentals + every edge case · **Session default:** 10 min · **Cadence:** 3–4 sittings/week · **Coach:** Claude

---

## How this works (read once)

Same engine as the `default` Staff Engineer path, run **completely independently** — this path has its own learning-day counter, its own review cadence, its own carry-over buckets. Nothing here blocks or is blocked by any other path. By choice this path does **not** cross-link to `default`: overlapping topics are taught again here, RabbitMQ-first.

1. **You poke me** — `/teach-rabbitmq` (optionally `/teach-rabbitmq 20 mins` or `/teach-rabbitmq quorum queues`). I serve the next topic in sequence.
2. **Lesson = 4–6 cards**, each: **Concept** (plain language) → **real-world example** (everyday analogy) → **GoZayaan example** (bookings, payments, flight/hotel search, notifications) → **edge cases** → **staff lens** → **self-check**.
3. **Deep by design.** Every topic goes to the edge cases — the "when does this break" is the point, not an appendix. A 10-min sitting covers ~2 cards; a topic usually takes 1–2 sittings.
4. **I update [PROGRESS.md](PROGRESS.md)** after every session, then refresh this path's row in the registry.
5. **Time-boxed** — a small budget means fewer cards *now*, never thinner cards. Leftovers get parked in a dated carry-over bucket and the topic sits at `[~]` until you clear it.

### The engine
1. **Teach-back gate** — `[x]` = covered, `[✓]` = you explained it back without notes. Only `[✓]` counts.
2. **Connection web** — every topic ties to the ones before it *inside this path*. The spine is one question asked forty-four ways: *where is this message right now, and what can kill or duplicate it?*
3. **Spaced resurfacing** — review every **3rd learning day of this path**; earlier clusters reappear in later quizzes.
4. **Build-in-public** — the two build artifacts below are the output.

### Testing
self-check (per card) → teach-back (per topic) → cluster quiz (`/test_me rabbitmq`) → checkpoint review + rubric re-score.

---

## The clusters

### RMQ1 — Foundations & the AMQP model
| ID | Topic | Notes |
|----|-------|-------|
| RMQ1.1 | Why a broker — RabbitMQ vs Kafka vs Redis Streams vs DB-as-queue | where RabbitMQ fits, where it doesn't |
| RMQ1.2 | Connections, channels, virtual hosts | multiplexing; channel-level vs connection-level errors |
| RMQ1.3 | Exchanges → bindings → queues: the routing pipeline | the default exchange; a message never "goes to a queue" directly |
| RMQ1.4 | Exchange types — direct, fanout, topic, headers | `*` vs `#` edge cases; headers `x-match` |
| RMQ1.5 | Message anatomy — properties, headers, body | delivery-mode, content-type, correlation-id, reply-to, expiration |
| RMQ1.6 | Wire mechanics — `basic.publish` / `basic.deliver` / `basic.get`, frames, heartbeats | channel closure semantics; why `basic.get` is a trap |

### RMQ2 — Delivery guarantees
| ID | Topic | Notes |
|----|-------|-------|
| RMQ2.1 | Consumer acks — auto vs manual, ack / nack / reject, multiple-ack | the `redelivered` flag; what an unacked message costs |
| RMQ2.2 | Prefetch / QoS — per-consumer vs global | fairness vs throughput; prefetch starvation |
| RMQ2.3 | Publisher confirms — async confirms, nack, `mandatory` + `basic.return` | alternate exchanges; what a confirm actually promises |
| RMQ2.4 | Durability — durable entities vs persistent messages | what survives a restart; fsync cost; the three switches that must all be on |
| RMQ2.5 | At-most / at-least / exactly-once | the myth; duplicates are normal; idempotent consumers and dedup strategies |
| RMQ2.6 | Ordering — when it holds and when it breaks | redelivery, multiple consumers, priority, DLX re-queue |
| RMQ2.7 | AMQP transactions (`tx.*`) vs confirms | why tx is slow and almost never the right tool |

**🎯 Artifact A1 (build), after RMQ5:** local **3-node Docker cluster** — quorum-queue leader failover + a partition-strategy demo (`pause_minority` vs `autoheal`), with a written "what I saw" log.
**🧭 Prove it at work:** for one real GoZayaan queue, write down the exact conditions under which a message can be lost today.

### RMQ3 — Routing & messaging patterns
| ID | Topic | Notes |
|----|-------|-------|
| RMQ3.1 | Work queues & competing consumers | fair dispatch; the one-slow-worker problem |
| RMQ3.2 | Pub/sub & topic design | binding-key schemes; exchange-to-exchange bindings |
| RMQ3.3 | RPC over RabbitMQ | reply-to, correlation-id, direct reply-to, timeouts, orphan replies |
| RMQ3.4 | TTL — per-message vs per-queue, queue expiry | the head-of-queue expiry gotcha |
| RMQ3.5 | Dead-lettering — DLX, `x-death`, reasons | rejected / expired / maxlen / delivery-limit; DLX cycles |
| RMQ3.6 | Retry patterns | TTL+DLX ladder, delayed-message plugin, backoff queues, poison messages |
| RMQ3.7 | Queue arguments & limits | max-length, overflow (drop-head vs reject-publish), priority queues, single-active-consumer |

### RMQ4 — Queue types & broker internals
| ID | Topic | Notes |
|----|-------|-------|
| RMQ4.1 | Classic queues — message store, queue index, lazy mode | always-lazy since 3.12; what "in memory" meant before |
| RMQ4.2 | Quorum queues — Raft leader/followers | delivery-limit, poison handling, at-least-once dead-lettering, when *not* to use them |
| RMQ4.3 | Classic mirrored queues (deprecated) | why they failed: sync, promotion, data loss — the lesson quorum queues learned |
| RMQ4.4 | Streams — append-only log, offsets, replay, super streams | vs Kafka; when a stream beats a queue |
| RMQ4.5 | Memory & disk — alarms, high watermark, disk-free limit, paging | credit flow; why *publishers* get blocked |
| RMQ4.6 | Storage lifecycle — segment files, GC, recovery on restart | why restart is slow with a deep backlog |

**🧭 Prove it at work:** list every GoZayaan queue by type (classic / quorum / stream) and say for each why that type — or why it's wrong.

### RMQ5 — Clustering, HA & operations
| ID | Topic | Notes |
|----|-------|-------|
| RMQ5.1 | Clustering — nodes, Erlang distribution, metadata replication | queue locality; peer discovery |
| RMQ5.2 | Network partitions | detection; `ignore` / `pause_minority` / `autoheal`; split-brain |
| RMQ5.3 | Metadata store — Mnesia vs Khepri | 3.13 → 4.x; what changed about partitions |
| RMQ5.4 | Connection management | reconnects, heartbeats vs TCP keepalive, connection churn, channel leaks, an LB in front |
| RMQ5.5 | Federation & Shovel | cross-DC / cross-cluster; vs clustering |
| RMQ5.6 | Monitoring | management API, Prometheus; the metrics that matter (ready / unacked, consumer utilisation, memory); alerting |
| RMQ5.7 | Upgrades & lifecycle | feature flags, rolling vs blue/green, definitions export / backup |

**🎯 Artifact A1 lands here** (see RMQ2 block).
**🧭 Prove it at work:** find GoZayaan's partition-handling setting and say what happens to a booking message during a 30-second split.

### RMQ6 — Security, policies & multi-tenancy
| ID | Topic | Notes |
|----|-------|-------|
| RMQ6.1 | Users, vhosts, permissions | configure / write / read regexes; topic permissions |
| RMQ6.2 | TLS & auth backends | OAuth2, LDAP; per-vhost / per-user connection & channel limits |
| RMQ6.3 | Policies & operator policies | policy vs `x-args` precedence; priorities; operator overrides |

### RMQ7 — Clients, performance & production failure modes
| ID | Topic | Notes |
|----|-------|-------|
| RMQ7.1 | Python clients — pika vs aio-pika | blocking vs async consumers; channels are not thread-safe |
| RMQ7.2 | Consumer engineering | prefetch tuning, batch acks, graceful shutdown, consumer-cancel notifications |
| RMQ7.3 | Publisher engineering | confirm pipelining, retries, outbox → RabbitMQ |
| RMQ7.4 | Contracts | message versioning, headers vs body, JSON vs protobuf, idempotency keys |
| RMQ7.5 | Performance | throughput vs latency, message size, persistence cost, many vs few queues, Erlang schedulers |
| RMQ7.6 | Failure drill — unacked pile-up / stuck consumers / prefetch starvation | symptom → root cause |
| RMQ7.7 | Failure drill — memory & disk alarms, flow control, backlog paging | symptom → root cause |
| RMQ7.8 | Failure drill — message-loss post-mortems | no durability, no confirms, auto-ack, mirror promotion, partition |

**🎯 Artifact A2 (build), after RMQ7:** **GoZayaan booking-events pipeline in aio-pika** — publisher confirms + DLX retry ladder + idempotent consumer, with a kill-the-consumer-mid-batch chaos test proving no loss and no double-processing.
**🧭 Prove it at work:** take one real incident or near-miss on GoZayaan's broker and write the root cause in RabbitMQ terms.

---

## Checkpoint (2026-11-21 — progress checkpoint, not the end)

- `/test_me rabbitmq` across whatever clusters are done, applied scenarios
- rubric re-score against the baseline in [PROGRESS.md](PROGRESS.md)
- re-estimate the remaining calendar from the actual pace; adjust cadence or session length if the gap is big
- repeat the checkpoint at each cluster boundary until all seven clusters are `[✓]`

### Phase 2 backlog for this path
MQTT / STOMP / AMQP 1.0 plugins · Erlang/BEAM internals as they affect the broker (schedulers, GC, process mailboxes) · Kubernetes operator & cluster-on-K8s specifics · stream protocol deep dive & super-stream partitioning · consistent-hash exchange & sharding plugin · benchmarking with PerfTest · multi-DC active/active designs · migrating classic → quorum in place.
