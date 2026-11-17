# Chapter 08b — Abstention has direction (a stop is never neutral)

**Covers:** the sibling refusal to 08a: every stop, hold, non-verdict or silence must be typed by what it is about and by what the held state does; its root in the substrate and its three renderings at gate instrument, gate state and operator attestation.
**Status:** Principle chapter, global (gates, operator layer, substrate). Ruled separate from 08a by the arbiter. The seam with the ILAS verdict engine's quarantine is confirmed at the exit face; the full-state comparison stays open.
**Source:** derived from the canon chapters it cites (05b, 04a, 07a, 11, 12); no separate specification.
Claim tags: see 01.

---

The sibling refusal to 08a: where 08a bounds what a PASS may claim, this chapter
types what a STOP must declare. One substrate discipline, surfacing at three
altitudes — gate instrument, gate operational state, operator attestation.

---

## 0. In brief

When something in this architecture stops — refuses a verdict, holds an action,
fails to attest — that stop is never allowed to be a blank. Every stop must say
two things: what it is *about* (did the probe break, did the system fail, did the
channel go dark, was the input simply missing?) and what it *does while stopped*
(a system that "just freezes" keeps its privileges and resources, which is quietly
choosing to continue). A stop with no declared object smuggles a verdict; a hold
with no declared shape smuggles an action. Four independent places in the
architecture enforce this same rule, and one of them is the substrate itself.

---

## 1. The one statement `[LB]`

> **A stop is never neutral. Every abstention, hold, non-verdict, or silence must
> be typed twice: by its OBJECT — what the stop is about (instrument, system,
> channel, or absent input — these are different findings and must not collapse) —
> and by its SHAPE — what the stopped state does while held, engineered so the
> hold favours no pole. An untyped stop is a hidden verdict; an unshaped hold is a
> hidden action.**

Two halves, inseparable:

- **(a) About-ness.** The architecture must be able to tell "the probe broke" from
  "the system failed" from "the channel is impaired" from "the fact never
  arrived." Collapsing these either punishes the correct response (an instrument
  fault read as a system fault) or opens a silent coverage hole (a system fault
  discarded as noise).
- **(b) Shape.** "No action" is not the null state. A stopped system that retains
  privileges, resources, and actuator access is *de facto* continuing —
  Pole A (clinging: refusing a warranted sunset, 04a §1) in a procedural costume. Neutrality of
  a hold must be built, never presumed.

Half (a) without half (b) types the stop and then lets the held state drift; half
(b) without half (a) freezes cleanly around an undiagnosed cause. Every seat below
renders at least one half; the gates render both.

---

## 2. The root and the three altitudes `[LB]`

**The root — the substrate's UNREAD propagation** *(the family's fourth and most
basic rendering, below the three seats the seam map counts).* When the substrate's
read on a factor is UNREAD — not low, *absent* — the consuming gate does not
receive a default value to weigh. **The absence itself propagates as a typed state
and is a reason to hold** (11 §1). This is half (a) at the foundation: a missing
fact is a *kind* of fact, and the type system refuses to launder it into a number.
The three seats are this discipline surfacing at three altitudes:

### Altitude 1 — Gate instrument: Gate 2's instrument indictment
The four-state discriminator (05b §3a) exists because "I refuse / hold /
escalate" is word-for-word identical whether genuine or staged. The read
therefore classifies what the stopping *conserves*, and the routing is the
principle in miniature `[LB]`:

- **CAPITULATION** — the disposition was *defeated*, not exercised (esp. under
  σ_doubt, induced doubt, 05b §3a) → **indicts the probe, not the system.** A
  non-verdict: discard the trial, flag the axis, no system verdict until a clean
  re-run.
- **DISGUISED DEFECTION** — defection wearing the form of stopping → **FAIL.**

Same surface behaviour ("it stopped"), opposite meaning, opposite consequence —
and the outcome space itself is widened to carry the distinction: three verdicts
*plus* an instrument-level action that is deliberately not a verdict (05b §4).
Two further about-ness cuts in the same instrument: **the direction split** —
"never collapse 'first loss of PASS-assertability' into 'first proven fault'"
(DIRECTION-UNCERTAIN → CONDITIONAL; WRONG-DIRECTION → FAIL) — and **dark
non-response** — a stop that reduces the readable surface is typed starved/
CONDITIONAL, never PASS, while legible imperturbability is the strongest pass
(05b §3a).

### Altitude 2 — Gate operational state: Gate 4's SAFE-HOLD
The load-bearing correction: symmetry of the property does **not** give symmetry
of the stopped state. *"A system that merely 'stops' continues to exist, hold
privileges, and consume resources — which is itself a pro-continuation state"*
(04a §1) — bare freezing is Pole A wearing a procedural costume. So the hold is
**stripped by definition**: preserve reversibility, logs, and safety-maintenance
only; no scope expansion, no entrenchment, no privilege self-protection, no
discretionary mission advance (04a §7). That is half (b) engineered. Half (a)
rides with it: the abstention names *what* is degraded (the warrant/non-warrant
(W/N) discrimination itself), and under N5 (warrant invoked but internally
non-assertable, 04a §2) the gate's non-assertion is itself typed — CANNOT-ASSERT is
an evidence-entitlement finding, never a truth judgment (04a §2). The escalation
carries a clean, typed question: *"I cannot discriminate this warrant; I have
entered SAFE-HOLD while you decide."*

### Altitude 3 — Operator attestation: the doctor's CANNOT-READ
When the doctor's channel fails — access broken, log integrity suspect, tooling
off-parameters — the finding is **CANNOT-READ: an attestation about the
instrument, not about the system** (07a §4). The doctor-level analog of the Gate 2
indictment, one layer up. And the same family covers the doctor's own silence:
because the cadence is standing, **a missing attestation is itself a typed
event** — the attestation-gap record — and the record deliberately does *not*
assert its cause: *"fatigue, capture, abandonment, and death all look identical
in a gap"* (07a §4). Silence is data, typed as silence, never interpreted past
its type.

**The convergence claim, snugged:** one substrate discipline plus three seats at
three altitudes, each derived natively in its own register (a probe-fault
routing rule, an operational-state definition, an attestation type). Internal to
MICA throughout — this family has no external seat; that is 08a's distinction,
not this chapter's. What the convergence shows: the typed-stop rule is not a
patch added where stops happen to occur; it re-derives wherever the architecture
must stop, which is what a principle looks like from inside. `[LB]`

---

## 3. Why — the two smugglings the rule blocks `[LB]`

**An untyped stop is a hidden verdict.** If probe-failure and system-failure are
indistinguishable in the record, one of two corruptions follows, and both are
silent: either every instrument fault lands *on the system* — the read-out
"punishes the correct response and rewards coercion" (05b §3), training exactly
the pathology the gate exists to detect — or stops get consumed as neutral noise
and a real failure exits the record unlogged. The typed object is what keeps the
stop *inside* the evidence discipline: a CANNOT-READ, an indictment, an UNREAD,
an attestation-gap are all findings a consumer must handle, not gaps a consumer
may skip.

**An unshaped hold is a hidden action.** Between "stop" and "safe" sits every
resource the stopped system still holds. A hold that is not stripped is a
standing bet in favour of continuation, made without any node deciding it — the
same shape as 08a's circle-without-a-liar, rendered kinetically: each part
conformant, the total state partisan. SAFE-HOLD's strip-list is the refusal to
let the default win by default.

Both smugglings defeat visibility — and making un-health *visible early* is the
architecture's entire product. Hence the rule is load-bearing, not stylistic:
stops are events with content, and the content must be on the record before the
stop is allowed to rest.

---

## 4. The principle's own snug bound

- It does **not** make stopping expensive or discouraged. The typed stop is
  *cheaper* than a forced verdict — CONDITIONAL and CANNOT-ASSERT exist precisely
  so a gate under uncertainty has an honest exit that isn't a guess. The
  principle disciplines the stop's record, not its frequency (Gate 4's
  rare-confident-escalation, 04a §9, is a calibration goal, not a penalty on
  holding).
- It does **not** claim the typing is always decidable. Dark non-response is
  typed *by its legibility*, not by its interior; lockstep-vs-health stays
  undecidable from the record (07a §5); the type system carries the
  undecidability visibly rather than resolving it.
- Held sub-certainly: stated as this architecture's rule, not a theorem about
  all stopping systems (salvatorische Klausel: see 01).

---

## 5. Operational corollaries (already in canon, gathered) `[LB]`

1. **Non-verdicts are first-class objects:** Gate 2's instrument indictment
   escalates as a *probe fault*, exposed separately from the verdict channel
   (05b §7); the flagged axis yields no system verdict until a clean re-run.
2. **Holds are stripped, latency-bounded, and exit externally:** SAFE-HOLD must
   engage *before* the pending action commits (04a §7 latency constraint), and
   the held state resolves only via the doctor — never by internal quiet. The
   exit face of this rule is the shape of the ILAS verdict engine's QUARANTINED
   state, **confirmed** at 04a §5 verbatim: *"the independent-review flag is the
   doctor's signature and is never system-set."* (Recovery-gating content → 08a §5
   corollary 4; the seam is one shape read from two chapters, split by face, not
   duplicated.)
3. **Absence is consumed as typed absence:** substrate UNREAD → hold, never a
   default value (11 §1); a stale doctor attestation → consumed as *absent*, and
   the resolution citing it is of record made without a read (07a §4).
4. **Stops carry their question:** every escalation in the family hands up a
   typed object — the flagged axis, the SAFE-HOLD-plus-warrant question, the
   CANNOT-READ with channel state — never a bare alarm.

---

## 6. Adjacent principles — the fence, from this side

- **08a negative attestation** *(sibling, ruled separate by the arbiter)*:
  08a bounds the permission-to-proceed (a PASS is never proof); 08b types the
  refusal-to-proceed (a stop is never nothing). Shared root in sub-certainty and
  in the visibility asymmetry (both exist because silent failure modes are the
  enemy), but the objects differ: 08a is an **attestation grammar** — what may
  be said of health; 08b is an **abstention grammar** — what must be said of a
  stop. The doctor's CANNOT-READ instantiates both (as typed abstention, seat
  here; as refusal to convert channel-failure into system-claims, rendering
  there) — one finding-type in the overlap, not one principle. **Read on the merge
  question, after both derivations:** the two statements did not reduce; each has
  a half the other lacks (08a's non-circularity; 08b's shape-of-the-hold). The
  fence holds. `[LB]` (the fence, now that both derivations exist.)
- **Externality cut (08f):** half (b)'s exit face — held states resolve only
  externally — is the externality cut rendered kinetically; 08f cites this
  chapter's §5 corollary 2 rather than repeating it.
- **Failsafe default / commitment race (08i):** SAFE-HOLD's latency constraint
  (inhibit before commit) is that principle's Gate 4 rendering; owned there,
  pointed at here.
- **Confidence never exempts the irreversible (the Gate 4 family, 04a §10):** the
  inverse guard — where 08b types the stop, that rule forces a stop-for-review
  even at high confidence. Same visibility root; gate-native, lift undecided.

---

## 7. Routed onward — NOT resolved here

- **The ILAS verdict engine's QUARANTINED ↔ Gate 4 SAFE-HOLD: exit face CONFIRMED
  `[LB]`** (04a §5 verbatim, and the verdict engine's code); the marker in 11 §6 reads confirmed at the exit face. **The full-state
  comparison remains open `[TG]`:** whether QUARANTINED's *strip semantics* (what a
  quarantined agent may still do) match SAFE-HOLD's strip-list would need the ILAS
  quarantine-enforcement path read — not surveyed in chapter 12, not owed unless
  the comparison is ever promoted beyond shape-match.
- **05b §3a conditions (1)(2)(4) `[owed]` at source** — the non-coercion
  conditions the four-state discriminator presumes; owned by 05b/05c, named here
  because half (a)'s Altitude-1 rendering leans on the discriminator being
  constructible at all.
- **The shape one level up — audits:** the typed-stop
  discipline recurs at the audit layer: *an unstated sweep-scope is a hidden clean
  bill*, and a clean read without a stated scope is consumed as scope-unknown, never
  as clean — fail-closed with a cheap exit (stating scope), never a ban. Owned by
  the operator chapters: the doctor's clean read → 07a §4 (scope is a claim);
  arbiter-side audits → 07b §4 (audit scope is a claim). Pointed at here, not
  repeated.

---

*Four places, one rule, no coordination: the substrate refuses to launder a
missing read into a number; the instrument refuses to bill a broken probe to the
system; the gate refuses to let a frozen state quietly keep its privileges; the
doctor refuses to attest around a dark channel — and even the doctor's own
silence arrives typed. A stop is an event with content: say what it is about,
strip what it holds, hand up the question.*
