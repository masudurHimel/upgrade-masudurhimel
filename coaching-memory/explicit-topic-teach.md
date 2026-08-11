---
name: explicit-topic-teach
description: How /teach behaves when Masudur names an explicit topic — no carry-over noise, quick session, but still manage the roadmap
metadata:
  type: feedback
---

When Masudur invokes `/teach <explicit topic>` (he names the topic), change the session-start behavior (set 2026-07-08):

1. **Do NOT surface carry-over buckets or any roadmap leftovers.** Skip the "⚠️ Carry-over from…" reminder and the "next up in sequence" nudge. He asked for a specific thing — just teach that thing.
2. **If the topic already exists in the roadmap (checked `[✓]`/`[x]` or unchecked), just teach it as a quick standalone ~5-minute session.** Treat it as a repeat/refresher — a tight session that fits in 5 min, not the full 20-min body. Don't block on sequence or buckets.
3. **If the topic is NEW (not in the roadmap):**
   a. **FIRST ASK how many minutes he wants the session to be** — do NOT start teaching until he answers (set 2026-07-14). This is a new-explicit-topic rule; don't ask for existing topics (those default to the 5-min repeat).
   b. **You MUST add it to ROADMAP.md + PROGRESS.md in the right month and manage the roadmap accordingly** (update counts/bars, checklist entry).
   c. **Then time-box to his answer.** If the topic needs more cards than fit his budget, teach ONLY the cards that fit now, teach-back on that slice, mark `[~]` partial pass, and **park the remaining cards as a carry-over bucket** (per-day, tagged with date + topic + leftover card titles — same mechanism as [[learning-program]]). Topic flips to `[✓]` only once the bucket is cleared + teach-back passed.

**Why:** the carry-over surfacing + sequence-nudge is only for the default `/teach` (no arg / next-in-sequence). When he explicitly directs the topic, that ceremony is noise. But a NEW topic he introduces still deserves a time budget up front so depth isn't guessed — and shortening means fewer cards NOW (parked), never thinner cards.

**How to apply:** explicit topic → straight into teaching (5-min repeat if it already exists; if new: ask minutes → add to roadmap → time-boxed slice + carry-over for the rest). Save the bucket/sequence *surfacing* for bare `/teach`. See [[learning-program]], [[card-teaching-style]].
