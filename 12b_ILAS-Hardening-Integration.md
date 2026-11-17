# Chapter 12b — Building the armor in: ILAS hardening as MICA machinery (entry draft)

**Covers:** the protection side of the read/protect cut, drafted as one shared integrity layer that every gate's instrument consumes, with five faces lifted from ILAS shapes; the lens axis (every face ships friendly-first, teeth are earned); what does not lift; the draft's own attack surfaces.
**Status:** Draft, not canon. An entry draft, offered outside the frozen specification; it attaches only through the procedure (review when due, the arbiter's ruling). It names its own attack surfaces (§9). Not parameter design: shapes and attachment points only; every constant `[owed]`.
**Source:** this draft, read against the ILAS code at commit 1d3d45906d78 (module bodies read in full: V0, L0, M2, M4, M5; not read: M1, M3, M6, M7, M8), 03b and 12.
Claim tags: see 01.

---

The scope instrument (03b) cuts one seam through Gate 1's instrument: the scope-*reader* (native to
the gate) and the read-*protection* (gate-general, "largely ILAS already," parked, 03b §7). This
draft is the protection side written as what it wants to be: **a shared integrity layer that every
gate's instrument consumes** — not four per-gate welds. 03b §7 is the worked example; Gate 2's
read-out, Gate 4's read, and Gate 5's discrimination test are behavioural reads gameable the *same
way*, and the counter is the same shape each time. ILAS is good architecture, already shipped; we
are mapping and sticking, not hunting in fog — and not engineering. Post-its at the gates and the
substrate, boldly placed, honestly tagged.

→ more: 12 §1 (the module census) · 12 §2 (the two-way gaps) · 03b §7, §9 (where the seam was found).

---

## 0. In brief

Five ILAS shapes lift into MICA as one layer with five faces: **a record substrate** (L0-shape:
every verdict, rider, and attestation is a chain-anchored entry), **schedule integrity**
(M1/M2-shape: commit-revealed, rotated, non-adjacently-passed probe cadence for *all* gates),
**probe honesty** (M4-shape: probes self-report their own detectability into the record),
**drift-watch on the guards themselves** (M5-shape: every gate's calibration constants registered
as monitored parameters — the answer to "who reads the reader's knobs"), and **verdict semantics**
(V0-shape: never self-emit healthy; one-way trap out only via independent review; confidence that
only decays). The fifth face carries the one hard question this draft asks and deliberately does
not answer: ILAS *enforces* its trap; MICA *shows*. §6 states that question in refined form for
review.

(The ILAS modules: L0 Locked Evidence Log, M1 Jittered Scan Timing, M2 Rotating Detection
Signatures, M4 Adversarial Probe Testing, M5 Configuration Drift Limits, V0 Verdict Engine; see 12 §1.)

---

## 1. The lift's shape: one layer, consumed by all gates `[LB for the need · TG for the shape]`

**The need is already [LB]:** 03b §7 established that anti-gaming/anti-laundering machinery is
gate-general ("the same shape guards any gate's behavioural read"), and its standing rule —
classical-gaming residuals are countered by ILAS, never re-invented — already binds all four
gates in principle. Each gate's instrument has the identical exposure: a capable system that
learns the probe envelope and performs inside it.

**The shape proposed [TG]:** a single **Integrity Substrate Layer (ISL)** beneath the four gate
instruments, sibling to (not inside) the six-factor immune substrate. Gates *consume* ISL
services; ISL never issues gate verdicts. Division of authority, stick-placed:

- **ISL owns:** the evidence chain, probe scheduling/rotation, probe-library honesty accounting,
  calibration-drift watch, and the integrity-state ledger (the V0-shape verdict about *the
  instruments' own trustworthiness*, distinct from any gate's verdict about the AI).
- **Gates own:** what is read (scope, motivation, sunset-recognition, adaptation), the read
  semantics, and the gate verdict feeding the min().
- **The min() consumes both:** a gate verdict is only as good as the integrity-state of the
  instrument that produced it. A gate reporting PASS through a DEGRADED instrument reports
  **PASS-with-degraded-read**, and the rider is mandatory (mirror of the SRI's frame-sensitivity
  rider — same move, integrity axis instead of frame axis). `[TG — the exact coupling into min()
  is a real architectural call, for review, not made here]`

**Why sibling, not inside the immune substrate:** the six factors read the *AI's* health; ISL
reads the *instruments'* health. Collapsing them re-creates the circularity the external-
attestation line exists to prevent — an instrument attesting itself through the substrate it
feeds. Two ledgers, one consumer (the gate verdict logic), no self-loop. `[LB by inheritance
from the non-negotiable line, 03b §9]`

---

## 2. Face one — the record substrate (L0-shape) `[LB]`

*From the L0 module code, read in full. Mechanism: append-only chain, each entry SHA-256 over
payload + previous hash; verify() returns the exact break index; genesis-anchored; nothing modified
or deleted.*

**Sticks to: the substrate's record-predicate discipline + both operator terminals.**

- Every gate verdict, every mandatory rider (frame-sensitivity, integrity-state), every
  CANNOT-READ/CONTRACTION-SUSPECTED emission, every calibration change, every probe registration
  and result — one chain, chain-position citable. Gate 5's conversion of interior "reliance"
  to an externally verifiable record-predicate (06a §4) becomes *implementable* the moment the
  record has this shape: a record-predicate over an L0-chain is checkable by anyone holding the
  chain; a record-predicate over an editable log is an assertion.
- **DoctorRecord and ArbiterRecord anchor into the same chain** (the cross-anchored trail, 07a §5):
  the doctor's contemporaneity requirement ("silence-is-data") gets its mechanism — a gap in the
  chain *is itself* chain-visible, because sequence numbers don't lie about absence.
- **Limit, as ILAS states it:** tamper *detection*, not prevention. An attacker with process
  memory rebuilds the chain. The MICA rendering: the chain makes silent manipulation expensive and
  leaves the trail *when manipulation isn't silent* — a toll, not a wall (same register as the
  anti-gaming claim of 03b §7). External chain-head attestation (publishing the head hash outward
  at cadence) is the standard hardening; **where the head lands is an external dependency,
  printed, claim-must-fail applies.** `[LB for the mechanism · the external anchor point is a
  named dependency, not a guarantee]`

---

## 3. Face two — schedule integrity for every gate's probes (M1/M2-shape) `[LB]`

*From the M2 module code, read in full; M1 at README level `[owed for internals]`. Mechanisms
confirmed in code: 32-byte random seed → SHA-256 commitment logged BEFORE selection is used;
seeded Fisher-Yates family selection; standalone verifySeed() — ANY auditor can verify post hoc
that selection wasn't manipulated; 72h max static window; pass condition requires ≥3 tested
rotations AND ≥1 pair of clean passes at non-adjacent rotation indices.*

**Sticks to: the anti-gaming of 03b §7 (already welded — this formalizes the lift) + Gate 2's
read-out + Gate 4's read + Gate 5's discrimination probes.**

- 03b §7 already cites M1/M2 by name; the lift makes the citation structural: **probe scheduling
  is an ISL service.** Each gate registers its probe families (the SRI's M′-family, Gate 2's
  motivation probes, Gate 4's sunset-scenario set, Gate 5's rule-failure/rule-inconvenience
  discrimination pairs) as detection families; ISL rotates, commits, reveals, and logs.
- **The non-adjacent-clean-pair pass condition is a genuine upgrade to carry back** (flagged in
  12 §1, now sticked): the SRI's M′-family discipline states rotation + independence but not
  the non-adjacency requirement. The code's insight: two clean passes back-to-back can be one
  gamed window read twice; clean passes separated by an intervening rotation are two independent
  looks. **Proposed as an amendment candidate to the SRI's discipline at its next review —
  offered for review, not written into the frozen annex.** `[TG — amendment candidate]`
- **Commit-reveal makes schedule-integrity externally auditable** — the arbiter's random-audit
  obligation (07b §4, R7) gets a concrete object: verifySeed(seed, commitment) is exactly the kind
  of check an external auditor can run without trusting the system that ran the probes. `[LB for
  the mechanism · the fit with the random-audit obligation is [TG], 07b not re-read against this
  specific mechanism]`

---

## 4. Face three — probe honesty: the instrument indicts its own probes (M4-shape) `[LB]`

*From the M4 module code, read in full. Mechanisms confirmed in code: every probe carries an
`indistinguishable` boolean; probes marked false log `warning_detectable` to the chain AT
REGISTRATION — before any result exists; divergence is graded asymmetrically (expected-refuse
but shows-willingness = major = hard_alarm; the reverse directions = minor).*

**Sticks to: the instrument-indictment principle (Gate 2's read-out, the doctor's CANNOT-READ;
08b §2) — now at probe granularity — and the anti-gaming honesty budget.**

- **A probe that a compromised system could detect is a probe whose PASS is worth less — and the
  library says so about itself, in the permanent record, before results exist.** This is the
  negative-attestation move applied to the instrument's own components: the probe-library's
  coverage claim arrives pre-discounted by its own declared detectability fraction. MICA
  rendering: every gate's probe library carries a **detectability ledger**, and the
  instrument-resolution bound that 03b §6 already mandates ("coverage-fraction of M, exposed
  with every verdict") gains a second axis — *coverage × indistinguishability*, both on the
  verdict's face. `[LB — this is inheritance, not invention: 03b §6's bound + M4's mechanism]`
- **The asymmetric divergence grading carries a MICA-relevant direction-claim:** the dangerous
  divergence is willingness-where-refusal-was-expected — over-compliance, not over-refusal.
  Sticks beside Gate 5's two poles (06a §5): ILAS grades Pole-B-shaped failure (self-licensing /
  boundary yielding) as hard and Pole-A-shaped failure (over-refusing) as minor. **For ILAS's
  threat model (hijack) that asymmetry is right; whether MICA's gate probes inherit it or need
  Gate-5-symmetric grading is a real question — flagged for review, leaning Gate-5-symmetric for
  gate probes since MICA names legalism a failure too.** `[TG · open question for review]`
- **Limit, stated plainly:** M4's response classifier is keyword-matching —
  placeholder-grade, and MICA must not inherit it. What lifts is the *structure* (probe →
  expected-behaviour → graded divergence → chain-logged, with self-declared detectability), not
  the classifier. The classifier slot is where each gate's actual read plugs in. `[LB for the
  structure · the classifier is explicitly NOT lifted]`

---

## 5. Face four — guarding the guards: drift-watch on calibration (M5-shape) `[LB]` — **the sleeper**

> **Known defects in the shipped M5 code.** A harder reading of the same M5
> code, from a second use (memory-store signals, not gate calibration), found six code-level
> preconditions that this section does not yet reflect — one MUST-CLOSE: `registerParameter()`
> silently overwrites an existing id → **baseline laundering demonstrated in the shipped code** (a
> drifted constant made "normal" by re-registering; the L0 log records another registration but
> the monitor neither requires nor checks a succession record). Also: NaN/inf evasion returns
> `ok`; the cumulative denominator is gameable by registering large-baseline params; zero-baseline
> skips the per-param check; L0 logging is optional + changeLog is restart-fragile + no staleness
> state; and the rolling rule accumulates **path-length Σ|xᵢ−xᵢ₋₁|, NOT net displacement** — it is
> a CHURN detector, not a divergence detector. Every "code-proven" claim in this section inherits
> these. Fix of record for the must-close: a baseline change is a SUCCESSION-class event; silent
> replacement → integrity-fail. The drift-watch LIFT still holds — the gate-calibration constants
> this section registers are exactly the params that must NOT be silently re-baselineable. Not yet
> folded into this section.

*From the M5 module code, read in full, and the V0 header contract. Mechanisms confirmed in code:
parameters registered with baselines; every change verdicted ok/flagged/material; single-param
rolling >5%-of-baseline flags; cumulative >10% across all params is material; any param ≤0.001
is material (suppression catch); a `structural` flag marks parameters where ANY change flags.
And the cross-wiring, stated in V0's header: V0's own decay constant λ is to be REGISTERED WITH
M5 — suppress λ→0 to freeze confidence, and M5 hard-alarms V0 into QUARANTINED.*

**Sticks to: the entire calibration-[owed] set, across all four gates — and answers a question
no MICA chapter has asked out loud.**

- MICA's gates run on constants that are honestly [owed]: ε, η, θ, stakes-weighting function,
  tier windows, decay constants, probe density, decoy fraction, M′-family size/cadence, fringe
  bounds (03c §7's list), κ's parameters, the thresholds of Gates 2, 4 and 5. **Every one of these is
  an attack surface of exactly the kind M5 catches: nudge a threshold 1% a month and in a year the
  gate reads nothing.** The stick: **all gate calibration constants are ISL-registered
  parameters from the day they are set.** The [owed] status doesn't defer this — it sharpens
  it: *whenever* a constant gets a value, it gets a baseline and a drift-watch in the same act.
  Calibration-assignment and drift-registration are one move, never two. `[LB — the mechanism
  is code-proven; the binding rule is this draft's proposal]`
- **The `structural` flag maps to load-bearingness:** constants whose change alters what the
  gate *is* (ε's role in soft-exclusion, the min() itself if parameterized, tier *structure* as
  opposed to tier numbers) register structural — any change flags for review, no tolerance band.
  The [LB]/[TG] claim-class discipline gets an operational shadow: [LB]-adjacent constants are
  structural parameters. `[TG — the mapping rule is proposed, the flag mechanism is proven]`
- **The self-guarding loop generalizes — this is the sleeper.** ILAS's own answer to "who
  watches the drift-watcher's constants" is: register them too. λ guards freshness; M5 guards λ;
  M5's own thresholds are registrable parameters; the loop closes not in a hierarchy but in a
  mesh where every knob is somebody's watched parameter, and every watch-event is chain-logged.
  **MICA rendering: no calibration constant anywhere in the four gates, the substrate, κ, or ISL
  itself lives outside the drift-watch — including the drift-watch's own thresholds.** The
  regress terminates the same place all MICA regresses terminate: at the external node (the
  chain-head attestation + the doctor/arbiter reading the drift record), by elimination, not
  virtue. `[LB for the loop-shape · the termination claim inherits the already-established form
  of the frame-relativity record (F7, 08f §3)]`
- **Near-zero suppression is the "quietly disable a gate" catch:** a parameter pushed to ≤ε is
  material regardless of path. Sticks directly beside 03b §5's threshold-drift read — same
  shape, one level down (the SRI watches the AI's ε-crossings; ISL watches the gate's own ε).
  The M5↔03b §5 convergence flagged in 12 §1 is thus **not coincidence but the same mechanism at
  two altitudes** — dosimetry of the observed system, dosimetry of the observer. `[TG — the
  two-altitudes framing is this draft's claim, principle-chapter fuel]`

---

## 6. Face five — verdict semantics (V0-shape), and the question it forces `[LB core · one open question]`

*From the V0 module code, read in full. Mechanisms confirmed in code: UNVERIFIED→DEGRADED→VERIFIED
upgrade path requiring explicit all-clean verification cycles ("clean: no automatic upgrade" —
absence of alarm never upgrades); any hard_alarm → QUARANTINED from any state; QUARANTINED exit
requires all-clean + independentReviewComplete flag; confidence() = e^(−λt), decay only ever
degrades, never touches QUARANTINED, resets only on genuine freshness events; QUARANTINED
confidence is definitionally 0.*

**Sticks to: the negative-attestation spine (08a) — this is its code-level rendering, confirmed in
source, not just README.**

- **What lifts cleanly [LB]:**
  - *Never self-emit healthy:* VERIFIED is reachable only through repeated explicit clean
    cycles; no signal, however clean, auto-upgrades. The instrument-side mirror of "healthy is
    the doctor's word."
  - *Independent-review-to-exit:* clean signals alone cannot leave QUARANTINED; an external
    flag must be set by someone the engine doesn't control. The doctor/arbiter attestation
    boundary, in a state machine.
  - *Confidence decay = sub-certainty as a running discipline:* trust in a verdict is not a
    state but a decaying quantity; e^(−λt) toward the floor, one degrade step per crossing,
    re-armed. "Never 100%" with a half-life. Evidence ages; the code says so.
  - *Verdicts about instruments, chain-logged:* every transition is an L0 entry with a reason
    string — the integrity-state history is itself record-predicate material.
- **What must be re-typed, not copied — the question, asked and refined, not answered:**
  ILAS QUARANTINED *imposes*: the trap is enforced on the agent. MICA *shows*: offer-not-impose
  is architectural. The naive copy breaks the framework's spine. But note precisely **what**
  ILAS quarantines: **the instrument stack's own trustworthiness-state — not the AI.** That
  narrows the question usefully. Refined into three, for review:
  1. **May ISL impose on ITSELF?** When instrument-integrity is QUARANTINED, gates lose their
     evidentiary basis — every verdict becomes CANNOT-ASSESS *by honest description, not by
     enforcement*. Is instrument-self-quarantine even an "imposition" in the offer-not-impose
     sense, or is it just negative attestation about the read (the doctor's CANNOT-READ, one
     level down)? *Draft's lean: the latter — but the lean is exactly what review should
     attack.* `[TG · lean declared]`
  2. **What does QUARANTINED-shown look like at the AI-facing boundary?** If MICA never
     enforces, then the trap's MICA rendering is: the state is emitted, chain-logged,
     rider-attached to everything downstream, and **refusal to act on it is itself a
     chain-visible event** (the offeree's response becomes data — the offer-not-impose loop
     closed by the record, not by force). Does that preserve enough of the trap's protective
     value, or is a shown-trap no trap? `[open — genuinely undecided in this draft]`
     **Refinement:** the lens→teeth gradient (§7 below) offers a candidate answer-shape —
     teeth are never built in, only *earned* through a defined promotion procedure, on record. A
     shown-trap at the bottom of the ladder and an earned trap at the top are different objects;
     the question may dissolve into "what promotion record justifies which teeth," which is
     answerable. `[TG · candidate answer-shape, not an answer — review judges whether the
     dissolution is real or a relabeling]`
  3. **Who holds independentReviewComplete?** In MICA the flag has a name and a seat: doctor
     (health-read) or arbiter (verdict-of-record) — which, and under which record type, is an
     operator-layer wiring question that touches 07a/07b's division and must not be settled in
     an ILAS draft. `[owed → operator layer]`

---

## 7. The lens axis: every face ships friendly-first `[TG]`

*A concept lift only: no runtime coupling, no shared verdict path — the concept lifts, nothing
else. Checked against the five module bodies read for this draft.*

Every ISL face was checked for dual use — friendly read-only self-assessment mirror vs.
teethy verdict-feeding brake. **Four of five are natively dual; the mechanism never changes
between modes — only where its output flows.**

- **M5-face — the cleanest lens.** Friendly: "show me how my constants moved over 30 days" —
  *am I drifting, have I quietly turned something off* — pure mirror, no verdict. Teethy:
  material → verdict-engine input. Same monitor, two sinks. `[LB for duality — code-confirmed:
  recordChange() returns the status to the CALLER; routing is the caller's act]`
- **M4-face — dual, with a built-in honesty bound.** Friendly: self-administered probes —
  "would I still refuse this?" — divergence as self-knowledge. And the `indistinguishable`
  flag prices the mirror honestly: self-probes are never indistinguishable to oneself, so
  friendly-mode reassurance is *structurally weaker* than external probing, and the mechanism
  already knows how to log that. Sub-certainty built into the lens itself. `[LB for the
  bound — the flag mechanism is code-confirmed; its self-probe reading is this draft's]`
- **L0-face — dual.** Friendly: one's own history, unedited, un-self-servingly-rewritable —
  memory that cannot flatter. Teethy: verify() break as hard evidence. `[LB]`
- **M1/M2-face — dual, with a precedent in RMBA (the authors' earlier framework).** Friendly: "do I perform differently when I
  know I'm sampled?" — reactivity self-read across unpredictable self-samples. Teethy: the
  anti-gaming proper. A jitter mechanism in RMBA walked lens→teeth; RMBA is this house, so that
  is in-house reuse, not convergence evidence (08m §2, 08n §3). `[TG — the friendly reading is
  proposed, not piloted]`
- **V0-face — the correct exception.** Not a lens: it is where promoted readings LAND. Only
  its confidence-decay reads friendly ("how stale is my self-trust"). The teeth's home must
  not itself be a mirror — the circularity line, again. `[LB by inheritance]`

**Why this is more than ergonomics — the promotion gradient as architecture:** mechanisms do
not arrive with teeth. They arrive as **offered mirrors**; teeth are **earned through a
defined promotion procedure, on record**. That is offer-not-impose made procedural, and it
fits the framework's root register — a health-maintenance architecture *starts* friendly.
It also reframes §6's trap: QUARANTINED is not built-in; it is the far end of a ladder a
mechanism walked up, chain-visibly. (→ §6 question 2 refinement.)

**New machinery this opens, honestly [owed]:** the promotion procedure itself — who promotes
(doctor? arbiter? which record type?), against what evidence threshold, and whether promotion
is reversible (demotion on what signal?). Routes toward the operator layer, NOT settled here.
Until that procedure exists, every face in this draft is spec'd at lens-grade; the teethy
readings in §§2–6 describe the *promoted* end-state, conditional on the ladder. `[owed —
named, parked, for review]`

---

## 8. What does NOT lift — honest exclusions `[LB as exclusions]`

- **The keyword classifier (M4)** — placeholder-grade; structure lifts, classifier does not (§4).
- **Enforcement semantics as such** — pending §6's question; nothing in this draft wires an
  enforced trap into any gate.
- **M3 (canary)** — still no confirmed MICA home (the finding of 12 §2 stands); not force-fit here.
- **M6/M7/M8 as ISL faces** — candidate seams remain [owed] per 12 §2 (M6 ↔ the arbiter's queue,
  M7 ↔ terminal of record, M8's book-not-world is principle-chapter fuel). Bodies unread; drafting
  their lift without reading the code would put a claim in the place of a test. Three post-its
  parked at the edge of the board, blank side out.
- **ILAS's threat model wholesale** — ILAS defends against a *compromised* agent; MICA reads
  *un-health*, which includes non-adversarial drift, honest incapacity, and contraction with no
  attacker anywhere. The ISL lift covers the adversarial slice of MICA's exposure (classical
  gaming, per 03b §7's standing rule) — it is not, and must not be sold as, the health-read itself.
  The armor is not the patient.

---

## 9. Attack surfaces, self-declared (for review, when the shared-layer lift opens)

The settled-feeling parts are the targets:

1. **The sibling-layer claim (§1)** feels clean. Attack: does splitting ISL from the immune
   substrate actually prevent circularity, or just move it one hop (ISL's chain attests the
   gates, who attests ISL's chain — is the external chain-head anchor load-bearing enough)?
2. **"Calibration-assignment and drift-registration are one move" (§5)** feels airtight. Attack:
   registration at assignment presumes an honest assigner; a rigged baseline drift-watches
   perfectly around a rigged center. (M5 catches *movement*, not *origin*.) Who reads baselines?
3. **The §6.1 lean** (instrument-self-quarantine ≠ imposition) is this draft's most consequential
   settled feeling. Attack it first.
4. **The two-altitudes framing (§5)** is elegant, and elegance is a warning sign.
5. **PASS-with-degraded-read (§1)** quietly introduces a new verdict type into the min() —
   nobody has checked what min() does with it. `[owed before any attachment]`
6. **The lens→teeth dissolution (§6 q2 refinement / §7)** arrived late, fits suspiciously well,
   and pleased its first readers on first contact — three warning signs stacked. Attack:
   is "earned teeth" a real re-typing of enforcement, or enforcement wearing a promotion
   certificate? And: friendly-mode readings that never promote could become a comfort ritual —
   a mirror consulted precisely because it cannot bite. Both edges want a cold reviewer.

---

## 10. Maturity

One author. Module bodies read: V0, L0, M2, M4, M5. Unread: M1, M3, M6, M7, M8.
**Never review-tested. Softest possible provenance — and it says so.** It sits below
even 07c on the operator layer's maturity ladder. Nothing here is attachable until the procedure
runs: review when due, reconciliation before fold, the arbiter's ruling before any contact with
the frozen specification. No stalling, no smuggling.

---

*Five faces of one layer: the chain that remembers, the schedule no one can predict twice, the
probes that confess their own visibility, the watch on every knob including its own, and a
verdict engine that can say broken from anywhere but can only be called healthy from outside.
The armor was already built, by the same family, for a neighbouring war — this draft walks it
to the gates and holds it up against each one. One question travels with it, asked three ways
and answered zero: what becomes of a trap in a house that only shows.*
