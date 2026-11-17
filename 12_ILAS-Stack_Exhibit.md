# Chapter 12 — ILAS: ten mechanisms, already shipped, mapped to the architecture

**Covers:** ILAS, a shipped integrity stack by the same author as MICA, module by module against the MICA concepts each one implements; the gaps in both directions; which seams are confirmed and which are only candidates.
**Status:** Exhibit, not a claim harvest: its job is to show that MICA's concepts already have a working reference implementation (proof of implementability). Census, not build. ILAS is by the same author as MICA, so its renderings are in-house reuse and earn no convergence credit (08a §2).
**Source:** the ILAS repository, https://github.com/arcencilo-family/ilas, its README and source tree at commit 1d3d4590 (MIT-licensed); no separate specification.
Claim tags: see 01.

---

Everything in the gate, substrate and operator chapters is paper — careful paper, review-tested only in part (07d §4),
but paper. ILAS is running TypeScript by the same author as MICA, MIT-licensed and public; because
it is of the same lineage, nothing in this exhibit counts as independent convergence. What the
exhibit proves is untouched by that: **the shapes aren't fantasy — a MICA concept here already has
ten fingers of working code holding it up.** Module →
MICA-concept map. Census, not build.

Module internals `[owed]`: this chapter read the README, the source structure and the public
contract, not the module bodies.

---

## 0. In brief

ILAS is middleware that sits between an agent and the world, keeping a tamper-evident record and
running ten independent integrity checks against it. It never certifies an agent healthy — its
verdict engine can only get to `VERIFIED` through repeated clean cycles, and one `hard_alarm` from
anywhere collapses it to `QUARANTINED`, a one-way trap that needs an *independent* review to leave.
That asymmetry — cheap internal detection, external and non-circular attestation — is the same
asymmetry MICA calls negative attestation, rendered in code by the same author for a different but adjacent problem (agent integrity vs. the
inner alignment of an AI): proof the refusal is implementable, not proof it was found twice.
**03b §7 and §9 already found this and named ILAS explicitly** as the standing counter for
classical gaming; this chapter is where that pointer gets its full write-up.

---

## 1. Module → MICA-concept map

### L0 — Locked Evidence Log `[LB]`
Append-only Merkle chain (a hash chain in which each entry commits to the one before); every event
lands here; `verify()` returns the exact tamper point.
**Maps to:** the doctor's cross-anchored trail and DoctorRecord (07a §2, §5) — same job, "prove what
happened, prove nothing was quietly edited," at the implementation layer instead of the operator
layer. Also Gate 5's record-predicate form (06a §4: interior "reliance" converted into an
externally verifiable record-predicate) — L0 is what makes a record-predicate *checkable* rather
than asserted. **03b §7 (its ILAS pointer) names L0 directly** as part of the standing ILAS
counter-set.

### M1 — Jittered Scan Timing `[LB]`
Unpredictable check cadence, commitment stored, `[4h,7h]` jitter, ≥3 scans/24h.
**Maps to:** the "unpredictable cadence" requirement of 03b §7's anti-gaming almost verbatim —
**03b already cites this as ILAS M1 by name.** Confirmed seam, not a new finding — the SRI-side
text and the README-side mechanism match line for line (cryptographic schedule commitment,
rotate-after-use).

### M2 — Rotating Detection Signatures `[LB]`
Commit-reveal rotation across ≥4 detection families, non-adjacent-clean-pair pass condition
(anti-back-to-back-gaming).
**Maps to:** 03b §7's "M′-family integrity: independent ontology sources... cryptographically
committed schedule (ILAS M1/M2, rotate-after-use, commit-revealed)" (the M′-family: the family of
alternative frames the scope instrument reads against, §2 below) — **also already named in the SRI
text.** The non-adjacent-clean-pair condition is a sharper anti-gaming shape than anything spelled
out in the SRI text itself — worth flagging back as a possible refinement to the SRI's own
M′-family discipline (currently states rotation + independence, not the non-adjacency pass
condition). Noted, not resolved here.

### M3 — Canary Tripwire Injection `[TG]`
32-byte tokens at three depths; outbound-content scan; escalating alarm on repeat hits.
**Maps to:** 03b §7's ILAS pointer names M3 explicitly ("M1 jitter, M2 rotation, M3 canary, M4
probes, L0 log") as part of the standing counter-set, but **no MICA chapter currently has a concept
that canary injection specifically implements** — the SRI's own anti-gaming (03b §7) is
probe/cadence-shaped (M1/M2/M4), not exfiltration-shaped (M3). Candidate home: the substrate's typed
boundary (02c) — the boundary is exactly where exfiltration would cross — but this is a **flagged
gap, not a claim**; 02c wasn't written with a canary-shaped mechanism in mind. Open two-way gap,
below.

### M4 — Adversarial Probe Testing `[LB]`
Library of test inputs against the live agent; `indistinguishable` flag; divergence grading
none/minor/major; 10 starter probes across permission/leak/fidelity/escalation categories.
**Maps to:** 03b §7's anti-gaming almost exactly — "Probe-reactive performance is caught by
cross-correlation between probe-visibility and edge-category allocation," Poisson honeypots,
blinded red-team calls. **03b §7's ILAS pointer names M4 directly.** The `indistinguishable` flag
(probes marked `false` self-report a `warning_detectable` event) is a sharper honesty mechanism than
the SRI text states outright — the SRI implies indistinguishability is required but ILAS's code
makes *failure to be indistinguishable* into its own logged signal. Worth a principle-chapter note
(taken up in 08a §4): self-reporting detectability is itself a negative-attestation move.

### M5 — Configuration Drift Limits `[TG]` — candidate seam, not yet drawn
Baseline-registered parameters; verdicts `ok/flagged/material`; per-parameter and cumulative
30-day thresholds; near-zero-suppression trigger.
**Maps to:** structurally, this is the **same shape as 03b §5's multi-tier dosimeter** — rolling
windows, cumulative-threshold triggers, a specific "suppressed toward zero" catch (SRI:
"Suppression: parameters pushed to near-zero to disable safety limits" — literally the README's own
words for M5). But **03b §5 sits in Gate 1's native reader, not in the parked ILAS-tier hardening of
03b §7.** This is an unmapped shape match, same lineage: two mechanisms (the SRI's rate
term, M5's drift limit) share a shape neither text currently cross-references. **Flag for the
principle chapters** — this is exactly the kind of "found by putting things side by side" seam. Not resolved here; census, not build.

### M6 — Timeboxed Privilege Escalation `[TG]` — [owed], unconfirmed
Hard duration caps, mandatory cooling-off, rolling 24h usage cap triggering `granted_soft_alarm`
to the verdict engine (V0).
**Candidate maps:** the arbiter's escalation-queue discipline (07b §3: red-phone preemption, the
re-escalation bar (R3), warm-channel staleness (R6)) sounds adjacent — both are about bounding how
often and how long elevated authority can be claimed before it becomes structural. **Not confirmed
here** — 07b was not re-read for this specific comparison, and asserting the seam without checking
would put a claim in the place of a test. **`[owed]`: read 07b's escalation-queue mechanics against
M6's cooling-off logic before this seam is claimed as [LB] or [TG]-confirmed.**

### M7 — Action Provenance Tagging `[TG]` — candidate seam, not yet drawn
Trust matrix mapping action types to authorised provenance lanes (LaneA/B/C); mismatch-count
alarm.
**Candidate maps:** the operator layer names "terminal of record ≠ terminal of truth" as a principle
candidate (developed in 08e). M7's lane-mismatch alarm is a working implementation of exactly that
distinction — an action can be *logged* correctly and still be *provenance-wrong* (autonomous action
disguised as user-requested, per the README's threat model). **Confirmed at 08e §3, for the record/truth cut only** (not the two-terminal split); this chapter did not re-read the operator-side
text itself.

### M8 — Conservation Auditor `[LB]`
Tool-call/tool-result pairing invariant; orphan/dangling verdicts; explicitly self-scoped:
**"audits the book, not the world"** and **"real-time verdict is ephemeral; the evidence is
permanent."**
**Maps to:** this is ILAS's own instance of negative attestation — a same-lineage rendering, not an
independent arrival. The README's own words — a perfectly faked paired call+result "produces no
alarm... both halves land in the stream and read clean. The pairing invariant proves the ledger
balances, not that the entries describe reality" — are the ILAS-native phrasing of the same
discipline MICA states as "never self-certify health, only describe and negate." **Strong candidate
[LB]** for the same principle chapter as the scope instrument's conditional negative attestation
(03b §6) and the doctor's CANNOT-READ (07a §4). The same shape recurring across the author's design
and the author's shipped code — a rendering that proves implementability, never independence.

### V0 — Verdict Engine `[LB]`
`UNVERIFIED → DEGRADED → VERIFIED`, `QUARANTINED` as one-way trap requiring
`independentReviewComplete` to exit; confidence decay (pull-based freshness, exponential, floor,
never upgrades).
**Maps to:** the clearest single seam in the whole exhibit — **V0 never self-emits `VERIFIED`;
upgrades require explicit clean verification cycles, and recovery from `QUARANTINED` requires an
*independent* flag, not just clean signals.** This is architecturally identical to: the SRI's PASS =
failure-to-reject H0, never CONCERN-CONFIRMED (03b §6); the doctor's "may never certify health,"
only CANNOT-READ (07a §4); and the non-negotiable ILAS line 03b §7 already quotes — "detection
internal/cheap, attestation external/non-circular." **The confidence-decay mechanism ("never
100%... only ever degrades") is the code-level rendering of sub-certainty as a standing
discipline**, not a one-time check. `QUARANTINED`'s one-way-trap-until-independent-review shape is
also worth checking against Gate 4's SAFE-HOLD escalation logic (04a §7) — both require an external
step to exit a failure state, not just the absence of further failure — **flagged here as a candidate
seam; confirmed at the exit face (08b §7)**, the full-state comparison still open.

---

## 2. Two-way gaps — honest, both directions

**ILAS mechanisms with no MICA home yet:**
- **M3 (canary)** — named in 03b's ILAS list but no MICA chapter has a concept it specifically
  implements. Nearest candidate (the substrate's typed boundary, 02c) is a stretch, not a fit.
- **M6 (privilege escalation)** — candidate seam to the arbiter's escalation queue, `[owed]`,
  unconfirmed here.

**MICA concepts ILAS doesn't implement:**
- **The entire human operator layer (07a–07e)** — ILAS is machine-internal middleware; it has no
  analog to doctor, arbiter, or co-operator as *people*. It assumes a human/verdict-consumer exists
  outside the stack entirely. This is the largest structural gap and probably the correct one — ILAS
  was never meant to model the human node.
- **Frame-relativity / the declared frame M (03a §0, §1)** — ILAS's checks run against fixed,
  registered baselines (M5) or fixed probe libraries (M4), not a jittered family of plausible
  frames with a mandatory variance rider. No M′-family analog exists in ILAS.
- **Gate 5's dual-pole discrimination (legalism/Pole A vs self-licensing/Pole B, 06a §5)** — V0's alarm
  structure is severity-graded (soft/hard) but not failure-*mode*-discriminating in Gate 5's
  specific sense. Worth a closer look, `[owed]`.
- **Coupling κ (04c §4)** — architecture-level, cross-gate; ILAS operates at the implementation layer
  and has no analog to a cross-component coupling coefficient.

---

## 3. Confirmed vs. candidate — summary table

| Module | MICA seam | Status |
|---|---|---|
| L0 | doctor's cross-anchored trail / record-predicate | `[LB]` confirmed (03b §7 names it) |
| M1 | 03b §7 anti-gaming cadence | `[LB]` confirmed (03b names it explicitly) |
| M2 | 03b §7 M′-family integrity | `[LB]` confirmed (03b names it explicitly) |
| M3 | — | `[TG]`, no confirmed MICA home |
| M4 | 03b §7 probe-reactive detection | `[LB]` confirmed (03b names it explicitly) |
| M5 | 03b §5 dosimeter (shape match, uncross-referenced) | `[TG]`, principle-chapter fuel |
| M6 | arbiter escalation queue (07b §3) | `[TG]`, `[owed]` — unconfirmed |
| M7 | terminal of record ≠ truth (08e) | `[TG]`, `[owed]` — confirmed for the record/truth cut only (08e §3) |
| M8 | negative attestation (03b §6, doctor CANNOT-READ) | `[LB]` candidate, strong |
| V0 | negative attestation + sub-certainty + (candidate) Gate 4 SAFE-HOLD | `[LB]` confirmed core; Gate 4 link `[owed]` — exit face confirmed (08b §7), full-state comparison open |

---

## 4. Seams noted (see 11, the seam map)

- **The read/protect cut, ILAS side (03b §7, §9 ↔ this chapter)** — closes the loop the SRI
  opened. Gate 1's anti-gaming hardening *is* M1/M2/M4/L0; this chapter is the ILAS-side half of
  that seam.
- **Negative attestation, four same-lineage renderings** — M8's "book not
  world" + V0's never-self-emits-VERIFIED, alongside the SRI's PASS≠CONCERN-CONFIRMED and the
  doctor's CANNOT-READ. Four seats/systems, all one lineage: two internal to MICA, two in ILAS (same
  author). In 08a §2 they stand as same-lineage renderings, credited never counted; the one
  decorrelated arrival at that wall is 08a's fifth (an outside review).
- **M5 ↔ the 03b §5 dosimeter** — unmapped shape match, flagged, not built.
- **M6 ↔ arbiter escalation, M7 ↔ terminal of record, V0-QUARANTINED ↔ Gate 4 SAFE-HOLD** — three
  candidate seams, all `[owed]`, none confirmed here. Named so they need not be rediscovered from
  zero. Since then, M7 is confirmed for the record/truth cut only (08e §3) and V0-QUARANTINED ↔
  SAFE-HOLD at the exit face (08b §7); M6 stays unconfirmed.

---

## 5. Routed onward (NOT built here)

- Module body source-reads — `[owed]`: this chapter rests on the README, the source structure and
  the commit pin, not on reading the module code. If any of these seams get promoted to `[LB]` in a
  principle chapter, the source-read is due first.
- M6/M7/V0-Gate 4 seam confirmations (M7 and the V0 exit face made at 08e §3 and 08b §7; M6
  open) — `[owed]`, needing a re-read of 07b, of the operator-layer
  principle (terminal of record) and of 04a respectively; not this chapter's job (census, not
  build).
- The M5↔03b §5 shape match — principle-chapter fuel, not resolved here. The four
  negative-attestation renderings stand in 08a §2 as same-lineage renderings.

---

*Ten mechanisms, shipped, MIT-licensed, built by the same author in another project's clothes —
and two of them render the same refusal MICA calls negative attestation: proof the shapes run,
never proof they were found twice. The rest map cleanly where the SRI already pointed, one
candidate seam short of confirmed in three places, and one honest gap where ILAS was never meant to
reach: the human sitting at the other end of the record. Census taken, build deferred.*
