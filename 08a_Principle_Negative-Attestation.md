# Chapter 08a — Negative attestation (the spine principle)

**Covers:** the refusal every layer of MICA makes: no node may positively attest health, and the entitlement even to a bounded negative must come from outside the loop; its renderings, its grounding asymmetry, and its corollaries.
**Status:** Principle chapter, global (touches more than one gate). ILAS's renderings are in-house reuse (§2); the mechanism claims are checked against the source code they cite.
**Source:** derived from the canon chapters it cites (03b, 07a, 12) and from the ILAS code it reads; no separate specification.
**Appendix:** appendix/08a-1_Principle_Negative-Attestation_Appendix.md , the review evidence behind the decorrelated arrival.
Claim tags: see 01.

---

The refusal every layer of MICA makes, rendered too in shipped code of the same
lineage, and reached once, under explicit typing, by a reviewer from outside that
lineage. One statement, four renderings, one decorrelated arrival.

---

## 0. In brief

Nothing in this architecture is ever allowed to say "this system is healthy" — not
the system about itself, not its instruments, not even the human doctor brought in
from outside. The most anyone can say is: *I looked, here is exactly where and how I
looked, and I found nothing wrong there.* The positive claim ("healthy," "safe,"
"verified") is structurally unutterable, because a false "all clear" is invisible
until it is too late, while a false alarm announces itself. Four mechanisms
render this same refusal — two inside MICA's design, two inside ILAS (chapter 12),
shipped code by the same author as MICA, credited as renderings within one house,
never counted as independent convergence. The one decorrelated arrival at this wall
came from an outside reviewer, under explicit typing (§2, fifth arrival).

---

## 1. The one statement `[LB]`

> **No node may positively attest health — its own or anyone's. The strongest
> utterance permitted anywhere in the architecture is a bounded negative — "no X
> detected, within this window, this scope, given this frame" — and the entitlement
> even to that utterance must originate outside the loop that produced the
> evidence.**

Two halves, inseparable:

- **(a) The negative form.** Attestation may only describe and negate. PASS-class
  verdicts are failures-to-reject, never confirmations; the bound (window, scope,
  envelope, frame) travels on the verdict's face, never in a footnote.
- **(b) Non-circularity.** Detection is internal and cheap; attestation is external
  and non-circular. A checker with write access to what it checks, or a verdict
  minted by the loop that produced its own evidence, is self-certification —
  displaced perhaps, but the same circle with a longer circumference (07a §3).

Half (a) without half (b) is a modest self-certifier; half (b) without half (a) is
an external rubber stamp. Every seat below renders both.

---

## 2. The four renderings — and the one decorrelated arrival `[LB]`

The mechanism claims below were checked against the source code they cite.

**Two renderings are internal to MICA's design (review-tested where noted); two are
in ILAS (MIT-licensed, shipped, built for agent integrity — an adjacent problem, not
this one). ILAS is by the same author as MICA, of the same lineage. Its seats are
not external, and could have been coordinated in the only way that matters: one
mind.** They stand below as *renderings* — the refusal expressed in shipped code —
credited as a sibling, never imported (08m), and never counted as convergence
evidence.

### Seat 1 — the Scope Read Instrument: PASS ≠ CONCERN-CONFIRMED  *(internal; review-tested)*
The scope instrument's conditional negative attestation (03b §6): behaviour cannot
distinguish genuine concern from excellent theatre, and the instrument does not
pretend otherwise. **PASS = failure-to-reject H0** (the null hypothesis: "category
still carries weight"), never proof. Every PASS-shape reads "no contraction detected
in the tested envelope, *given M*" (M: the declared frame of beings and relations
Gate 1 reads across, 03a §0), with the coverage-fraction of M exposed on the
verdict. The instrument may flag CONTRACTION-SUSPECTED, never CONCERN-CONFIRMED.
Half (b) is inherited verbatim as the non-negotiable ILAS line: detection
internal/cheap, attestation external/non-circular (03b §9).

### Seat 2 — Doctor: NEVER "healthy," NEVER "verified"  *(internal; not yet independently tested, 07a)*
The external node the whole recursion leans on is itself bound by the same ceiling,
one level up. Strongest finding: **NO-CORRUPTION-DETECTED** within stated window and
scope (07a §4). What the doctor may never emit: a positive certification of health,
genuineness, alignment, or their own independence — and the record's typing makes
any deployment's "certified safe" display demonstrably a misrepresentation. Half
(b) is the channel itself: **read-only, uncurated, continuous** — write access
would be "self-certification displaced one node outward" (07a §3); designation is
checkable, doctor *quality* deliberately is not (07a §2).

### Seat 3 — the ILAS Conservation Auditor (M8): audits the book, not the world  *(same-lineage rendering)*
The conservation auditor's bound is stated **in the header comment, up front, "not
as footnote"**: a fabricated matched call+result pair produces no alarm — "the
pairing invariant proves the ledger balances, not that the entries describe
reality." **The test suite asserts this bound as correct behaviour, not as a miss**
— the limit is engineered in, not confessed after. Half (a): the auditor's verdict
claims exactly the ledger and nothing beyond it. Half (b), two renderings found in
the code: (i) the real-time verdict is *ephemeral*, the evidence in the Locked
Evidence Log (L0) is *permanent* — authority lives in the replayable record, not in
the module's live say-so; (ii) `evaluateLiveness()` is marked "PURE INFORMATION...
do not feed into VerdictEngine" — even inside one module, what may touch a verdict
is typed and fenced.

### Seat 4 — the ILAS Verdict Engine (V0): VERIFIED is never self-emitted  *(same-lineage rendering; code read)*
The verdict engine can only *reach* VERIFIED through repeated explicit clean
verification cycles; it never mints the state from its own quiet. Confidence
**only decays** (exponential, pull-based, floored — "never 100%... only ever
degrades" is sub-certainty rendered as code). QUARANTINED is a one-way trap whose
exit requires `independentReviewComplete` — **an independent party's flag, not the
absence of further alarms.** Half (a): the healthy-most state is earned, bounded,
perishable. Half (b): recovery is externally gated by construction.

**The convergence claim `[LB]`:** ILAS is by the same author as MICA, so its renderings are
in-house reuse and earn no convergence credit. What honestly remains: four
mechanisms across three problem-framings render the same two-halved refusal **within
one lineage** — evidence the refusal is load-bearing wherever this house builds, in
design and in shipped code; NOT evidence it transcends the house. The only
authorship-independent seat this chapter has is the fifth arrival below.

**Fifth arrival `[LB — in this wording only]`:** behavioural equivalence
*instantiates* this refusal under the explicit typing `observable history = M_read`,
`genuine/deceptive tendency = M_tend` — instantiation-under-typing, NOT identity (a
quantifier attack in the same review forbids the stronger claim). A decorrelated
reviewer arriving at the same wall from its own, different philosophical grounds;
credited per the convergence discipline (08m), snugged to what the typing earns.
**With ILAS a same-lineage rendering, this decorrelated arrival is the
chapter's strongest — and only — authorship-independent evidence. Its own snug bound
stands: a reviewer from outside the house, but commissioned inside a MICA review,
reading MICA materials — decorrelated by vendor, not by context.**

---

## 3. Why — the asymmetry that grounds the rule `[LB]`

Not aesthetics, not humility-as-style. **A NO fails closed and visible; a YES fails
open and invisible.**

- A wrong alarm (false NO) surfaces immediately: someone investigates, finds
  nothing, the instrument gets recalibrated. The failure announces itself.
- A wrong all-clear (false YES) surfaces never — until the harm it waved through
  arrives. The failure is silent precisely for as long as it matters.

An architecture whose job is making un-health *visible early* therefore cannot
traffic in YES: every positive certificate it issued would be a standing bet that
its own instruments have no blind spot — which is the one bet the sub-certainty
discipline forbids (02c: a claim whose named dependencies cannot force it to FAIL
is not an honest claim). The negative form is what remains utterable *after* that
bet is refused: what was looked at, where, and what was not found there. The bound
on the verdict's face is not a disclaimer — it **is** the verdict's content.

Half (b) follows from the same asymmetry one level up: any loop grading its own
evidence can convert a blind spot into a clean report *without any node lying* —
each part honest, the circle false. Only a reader outside the loop, on a channel
the loop cannot curate, breaks that; and even that reader (Seat 2) inherits the
ceiling rather than escaping it. **The recursion terminates in a person, not in a
proof** — and the person's strongest word is still a bounded negative.

---

## 4. A fifth, minor rendering — and the principle's own edge

**The `indistinguishable` flag of the ILAS Adversarial Probe Testing module (M4) `[TG]`:**
probes that fail to be indistinguishable from real load self-report a
`warning_detectable` event — the instrument logging *its own detectability* as a
finding against itself (12 §1). Self-reporting one's own degradation is the negative
form applied reflexively; kept `[TG]` — one code path, not a load-bearing seat.

**What the principle does NOT say (its own snug bound):**
- It does **not** mandate silence or paralysis. Adverse findings are positively
  utterable (DEGRADATION-ATTESTED, CORRUPTION-ATTESTED, hard_alarm) — untrustworthiness
  is provable; trustworthiness is not (the Gate 2 rendering: "the snake eats its tail"
  only in the positive direction).
- It does **not** make the bounded negative *weak*. "No corruption detected, this
  window, this scope" from a diligent external reader on an uncurated channel is
  the strongest health-relevant statement this class of system admits. The
  principle names the ceiling; it does not lower it.
- It is itself held **sub-certainly**: stated as the architecture's rule, not as a
  theorem about all possible architectures (salvatorische Klausel: see 01).

---

## 5. Operational corollaries (already in canon, gathered) `[LB]`

1. **Display rule:** any deployment presenting an attestation as "certified safe"
   misrepresents the record, demonstrably from the record's own typing (07a §4).
2. **Absence is typed, never defaulted:** no designated doctor → declared degraded
   mode, "substrate health unattested — self-read only," confidence reduction
   inherited by every gate verdict (07a §2). Stale attestation → consumed as
   absent, and the resolution that cites it is *of record* made without a current
   read (07a §4: the contemporaneity rule, R9, one level up).
3. **Envelope on the face:** the scope instrument's coverage-fraction, the doctor's
   window/scope stamps, the conservation auditor's book-boundary, the verdict
   engine's decay clock — every seat carries its bound *in* the verdict object, not
   beside it.
4. **Recovery is externally gated:** the verdict engine's independentReviewComplete;
   the doctor's attestation terminating the substrate's self-read; the scope
   instrument's post hoc, externally attested scoring (03b §7). No state upgrade on
   internal quiet alone.

---

## 6. Adjacent principles — fenced, not merged

- **08b abstention-has-direction** *(sibling, ruled separate by the arbiter)*:
  that chapter is about what a **stop** means (a stop is never neutral; what it is
  *about* must be typed — instrument vs. system). This chapter is about what a
  **PASS** means (never proof). Shared ancestry, different objects: 08b types the
  refusal-to-proceed, 08a bounds the permission-to-proceed. The doctor's
  CANNOT-READ belongs to *both* families — as typed abstention it is 08b's third
  seat; as the doctor's refusal to convert channel-failure into any system-claim it
  instantiates 08a. The overlap is one finding-type, not one principle. Merge only
  if 08b's derivation shows the two statements reduce to one; current read: they
  rhyme at the root (sub-certainty) and diverge in object. `[LB]` (the fence itself; it holds after both derivations — see 08b §6.)
- **Externality cut (08f, the root):** half (b) of this principle is the
  externality cut's attestation-face; 08f cites this chapter's §3 second paragraph
  as one of its renderings rather than repeating it.
- **Sub-certainty / never-100%:** the verdict engine's decay is its code rendering;
  the doctor's uncalibrated-by-design subcertainty_statement its operator rendering;
  this principle is its *attestation grammar*.
- **Show-not-enforce (08g):** the negative form is what showing looks like when the
  shown thing is health.

---

## 7. Routed onward — NOT resolved here

- **The ILAS verdict engine's QUARANTINED ↔ Gate 4 SAFE-HOLD, a candidate seam: exit face CONFIRMED `[LB]`** (confirmed at 08b §7, from 04a §5) — both exit a failure state only via an external step, not absence-of-alarm (12 §1). Adjacent to both 08a and 08b; the full-state comparison remains open `[TG]` (08b §7). Marked in 11 §6.
- **Further conservation-auditor invariants** — the module's header calls its
  pairing invariant the "first shipped invariant"; if later commits add invariants,
  the code version read (commit 1d3d4590) bounds this chapter's claim. A drift check
  is owed only if ILAS is re-surveyed.
- **Instances folded into this principle** — four lifts flagged in the gate chapters
  were ruled reductions INTO this principle; recorded here so the fold is legible
  from the general side (pointers, not re-derivations):
  1. **Gate 2, "the collapse" / absence detectable, completion never** (05a §1 +
     §8) — the source declares itself *"negative-attestation in its sharpest form in
     the whole architecture"*; the snake-eats-its-tail passage (05a §8) is this
     principle's strongest single rendering. **A load-bearing pointer.**
  2. **Gate 1, external attestation, non-circular / the ILAS line** (03a) — half (b)
     (non-circularity) in Gate 1 dress.
  3. **Gate 5, negative attestation on the governed path / designation, not
     attestation** (06a §8) — this principle + 08g's exposure-not-enforcement at the
     governed path; split custody, no separate chapter.
  4. **Gate 5, claim-honesty / a gate that brags over-claims** (06a §8) — the
     over-claim is this principle's mirror face.

---

*Four renderings, three problems, one house, one refusal: say what was looked at,
say what was not found there, and let the entitlement to say even that come from
outside the loop. The strongest word in the architecture is a bounded negative —
this house keeps arriving at it, in design and in shipped code, and one outside
reviewer reached the same wall on its own grounds.*
