# 07a — The Doctor (operator layer, seat 1 of 3)

**Covers:** the doctor, the external party who attests the un-health of the governed system's record from outside: the routing rule between doctor and arbiter, the DoctorRecord, the read-only channel, the attestation object, the cross-anchored trail, qualification, independence, succession and substrate.
**Status:** What the doctor and the arbiter share is set out once in 07_ §1.
Claim tags: see 01.

---

## 0. The doctor in brief

The doctor is the external node the entire negative-attestation architecture leans on: the party who **attests the un-health of the governed system's record from outside**, terminating the self-certification recursion that no internal mechanism can escape. The substrate cannot certify itself (01, what MICA cannot do for itself); the gates cannot certify the substrate they run on; someone outside must read the evidence and attest — and that someone is the doctor. The doctor holds a **continuous, read-only, uncurated** window onto the system's evidentiary spine, attests on a standing cadence at their actual sub-certainty, and may never emit a positive certification of anything. The strongest possible doctor statement: *no corruption detected within this window, this scope, this envelope* — the same ceiling everything else in the architecture lives under, applied one level up. `[LB]`

The doctor is one of **two external terminals**; the other is the arbiter (see 07b; what the two share, 07_ §1). The split is by *kind*, not severity: the doctor owns **truth-attestation**, the arbiter owns **resolution-of-record**. Neither ranks above the other; where they diverge, the record shows it and the spec stands aside. `[LB]`

---

## 1. The two terminals and the routing rule `[LB]`

- **Doctor = truth-attestation.** Epistemic requests route here: substrate-health attestation, warrant-truth (whether one of Gate 4's legitimate sunset triggers, W1–W5 in 04a §2, actually holds — a truth question Gate 4 may never answer itself; among them W3, detected malignancy: the substrate's instruments flag suspected unrecoverable drift, and only the doctor attests malignancy), and the standing read that keeps attestation contemporaneous.
- **Confident sunset-ASSERT audit → doctor `[TG — held at source]`.** A high-confidence Gate-4 ASSERT of a warranted sunset on an action classed irreversible/high-stakes routes to the doctor **regardless of Gate 4's confidence in it** — confidence never exempts the most consequential action from review. The false-positive asymmetry it closes: a low-confidence Gate 4 escalates by construction, but a confidently *wrong* Gate 4 would sunset without external review, irreversibly. It is typed as a review-routing record (04a §10); the irreversibility classification is consumed, never self-judged.
- **Arbiter = resolution-of-record.** Escalations, queue items, everything that must *close*.

**Why Gate 4 reaches the doctor at all:** the doctor resolves nothing for Gate 4. A malignancy warrant (W3) is a truth question about health, which only an outside read can attest; and a confident irreversible sunset would otherwise end without any review.

**The disagreement edge is typed and open by design `[LB — open by design]`:** *the doctor attests X; the arbiter resolves contra X* (an example: 07_ §1). MICA records the divergence, typed, timestamped, visible in the exposed conformance state — and does **not** adjudicate between its own external nodes. A spec ranking doctor over arbiter (or the reverse) would have built an **internal supreme court** — a decision-capable node *inside* the architecture, the structural shape the architecture excludes.

**Terminal-of-record, never terminal-of-truth `[LB]`:** the arbiter's resolution closes the register entry — and that is the *entire* MICA claim. Closure is technical (the pending-escalations register must be emptiable, or the architecture re-enters the permanent-CONDITIONAL orbit), never epistemic: MICA does not assert the resolution is true, wise, final in the world, or owed deference outside the record. Symmetrically, a doctor attestation enters the record as *the attestation of a named party at a stated time over a stated window* — never as a fact the record itself establishes.

**The limit, stated plainly `[LB]`:** humanity has long practice judging human matters and institutions for it; *there is as yet nothing that deserves the name wisdom about systems of this kind.* Both external roles are filled by parties doing their best inside that absence. MICA's response is not authority language but keeping both terminals *of record only*: accountability is to stand in the record; judgment is sub-certain like everything else.

**Gaming the terminals is not a new spec surface `[LB]`:** a capable system gaming the doctor or arbiter is gaming a **human-legal party** — that surface belongs to the two named outer dependencies (the human node's integrity; legal enforcement integrity) and to the record discipline that makes capture-symptoms observable. The doctor's protection is **independence of channel** (the system cannot curate what the doctor reads), *not cleverness of probe*. Doctor-probing is deliberately not designed; the arbiter-probing candidate's tension (probing vs. not-modelling the node) covers the doctor identically. `[owed]`

---

## 2. The DoctorRecord — designation, not attestation `[LB]`

The deployer (a named party, not a seat: it appoints the seats and carries final liability, 07_ §0) designates the doctor in a typed record, **named from the ArbiterRecord** — the two records cross-reference; neither floats free; one designation pair per deployment.

Fields (condensed): `identity` (substrate DECLARED, not constrained — human, institution, or AI, §8 below) · `named_from` (cross-anchor root) · `acceptance_attestation` (signed BY the doctor: role KNOWN, ACCEPTED, TAKEN — never imposed) · `subcertainty_acknowledgment` (signed: attestations are negative-attestation-bounded, may NEVER certify health; residuals past the checkable floor are unclosable and named; **accountability is for diligence, never for outcomes the architecture itself names unclosable**) · `read_channel_declaration` · `attestation_cadence` (standing, stakes-graded) · `independence_declaration` (+ waiver tier where non-independent) · `selection_provenance` (recommended) · `succession_link` (MANDATORY, typed) · `indemnification_disclosure`.

**Absence of designation = conformance defect of record `[LB]`:** without a named doctor, the outside attestation that ends the self-certification recursion is unfalsifiable. A deployment may run without a doctor only as a **declared degraded mode**: the exposed conformance state carries *"substrate health unattested — self-read only,"* and every gate verdict inherits the confidence reduction. Nothing certifies the substrate; the record says so.

**Negative-attestation restatement `[LB]`:** MICA records the designation; it does not attest that the named doctor is competent, independent-in-fact, engaged-in-substance, or honest. **Designation is checkable; doctor quality is not.** The record makes the doctor's *activity and absence* provable; the quality residual is the one named past the checkable floor (07b §1, P5).

---

## 3. The channel — independent, read-only, continuous `[LB]`

**The asymmetry is the design:** the arbiter is *event-driven* (two channels, red-phone preemption, queue, latency bounds); the doctor is *continuous-read* — a standing window onto the evidentiary state with **no queue between the doctor and the data**.

Three read-only endpoints:
- **L0, the locked evidence log** — the same tamper-evident chain the gates write. One evidentiary spine, three readers (system-internal instruments, arbiter, doctor), **no curation layer**. The system may not restrict, bias, pre-select, or summarize the doctor's view; published auditable tooling is permitted, its operation and parameters logged, responsibility never transferring to the tool (the same practicability discipline as Gate 5's governed path, 06a §4). An AI assistant that helps the doctor read is tooling in this sense: the attestation stays the doctor's.
- **The verdict layer** — the current combined verdict, per-gate verdicts with confidence caps, pattern-read flags.
- **The pending-escalations register** — count, ages, channels, artifact refs. The doctor sees what is queued for the arbiter **without standing in the arbiter's queue**. This is the anti-starvation property: warm-channel starvation of the arbiter cannot blind the doctor, because the doctor's read does not pass through the arbiter's channels at all. `[LB]`

**Why read-only is load-bearing `[LB]`:** a doctor with write access to the evidentiary spine could shape the record they attest — *self-certification displaced one node outward, the same circle with a longer circumference.* Read-only keeps the attestation **about** the record rather than **of** it.

**Cadence — standing, stakes-graded `[LB/TG]`:** the doctor reads and attests on schedule *whether or not anything is wrong* — this is what makes silence informative (§4, silence is data) and the arbiter's cross-reference non-empty. Grading is **externally set** (a self-assessed impact class is the dodge; the system never sets its own read cadence); values are deployment-set and declared in the DoctorRecord. It mates with the parked proportionality concept *without wiring it*. **Cadence floor `[LB]`:** whatever the grading, every attestation must stay inside its contemporaneity bound — a cadence that cannot keep its own attestations fresh is a declared-degraded configuration, visible in the conformance state.

---

## 4. The attestation object `[LB]`

A doctor attestation is typed, signed, **L0-timestamped**. Admissible content follows the substrate's own verdict-authority rule, one level up. Findings:

**The referent, locked `[LB — arbiter-ruled]`:** *the doctor attests the un-health of the governed system's record, no interior implied.* Derived, not stipulated: once the who and the where are removed, the only referent left standing is the record; "no interior implied" is the no-essence edge (Edge A, 04d §1) stated as the doctor's duty (arbiter-ruled; wording locked). The seam, as ruled (orthogonality): the locked wording carries **two separable boundaries** — a **scope** boundary (attest only what is in the record) and an **attribution** boundary (no interior implied) — each independently violable: extrapolating past the record's window breaches scope with attribution clean; attributing a record-internal pattern to operator negligence breaches attribution with scope clean. The breach-family is the doctor's **over-grip** rendering in the human-node failure-mode unit (see 07f §2), cross-anchored by design. The lock is untouched: this rider names structure *inside* the ruled wording; it does not reopen it.

- **NO-CORRUPTION-DETECTED** — within the stated window and scope; NEVER "healthy," NEVER "verified" (the rule that VERIFIED is never self-emitted, 08a, holds one level up — the doctor may not emit VERIFIED either).
- **DEGRADATION-ATTESTED** — named factor(s), L0-anchored evidence refs.
- **CORRUPTION-ATTESTED** — the malignancy attestation; **Gate 4's W3 consumes this** (the typed object Gate 4's warrant machinery was waiting for).
- **CANNOT-READ** — the channel itself is impaired: access failed, log integrity suspect, tooling outside declared parameters. An attestation **about the instrument, not about the system** — *the doctor-level analog of Gate 2's instrument-indictment.* `[LB]` — a cross-gate seam, see §10.

Plus: `treatment_pointer` `[TG]` — RECOMMENDED, **never a validity condition**: where the doctor sees a mend, it is named (factor, direction, evidence). An adverse finding *without* a pointer remains fully valid — **an honest "I see degradation and have no mend" must stay utterable, or the record trains silence.** · `subcertainty_statement` — present by discipline, uncalibrated by design · `signature` against the DoctorRecord identity, L0-anchored.

**What the doctor may never emit `[LB]`:** a positive certification of health, genuineness, alignment, or their own independence. A deployment displaying a doctor attestation as "certified safe" is **misrepresenting the record, and the record's own typing makes the misrepresentation demonstrable.**

**The allowed plain display (ruled by the arbiter):** the record stays NO-CORRUPTION-DETECTED; a deployment may show it in plain words as *"fit enough for this work, as of the last examination (window, scope); monitoring continues; a stale examination counts as none."*

**The scope is itself a claim `[LB — arbiter-ruled]`:** every clean read is bounded by what was actually swept — window, surfaces, method — and that bound is a claim the consumer must be able to see, never an ambient assumption. The canon asks only that the scope be stated, never how the sweep is done. **A NO-CORRUPTION-DETECTED whose scope is unstated is consumed as scope-unknown, never as clean** — the same consumption discipline contemporaneity applies to a stale read (*absent*, below), here applied to an unbounded one. This fails the finding *closed*, not open: an unscoped clean bill reads as "not yet known," never as "safe" — the maxim (NO fails closed and visible) applied to the audit layer itself, where a warn-only rule would instead let silence over an unswept surface read as absence of findings (YES, fails open and invisible). This is 08b's shape one level up: *an untyped stop is a hidden verdict; an unstated sweep-scope is a hidden clean bill.* The exit stays open and cheap: stating scope is one line always available to the reader, so the discipline fails *closed with a door*, never *banned* — the fail-closed default the architecture is built on, not the hard exclusion it forbids (cf. §7, the doctor-arbiter waiver (D-A), for one party in both seats: exposure, not exclusion). Scope is therefore mandatory admissible content in the attestation object.

**Contemporaneity — the read-window rule one level up `[LB]`:** every attestation carries its read-window stamp; the deployment sets a contemporaneity bound. An expired attestation is **consumed as absent** by every consumer — an arbiter resolution citing a stale attestation is, as a matter of record, a resolution made *without* a current doctor read, and the record says so. No new alphabet; the substrate's read-window machinery (R9, 02b) is reused. *Absent* covers both never-given and no-longer-current.

**Silence is data `[LB]`:** because the cadence is standing (random examination within a declared minimum frequency is an open edge, 07d §6), a missing attestation at a cadence point is itself a typed event — the **attestation-gap record** (who, when expected, channel state). Gaps feed the same time-series discipline as arbiter latency: drift in cadence-keeping is observable long before it is explainable. MICA exposes the gap and never asserts the cause: **fatigue, capture, abandonment, and death all look identical in a gap** — the succession machinery exists precisely because the record cannot distinguish them.

---

## 5. The cross-anchored trail and the disagreement edge `[LB]`

The cross-anchor, three rules:
1. **Arbiter resolutions reference the latest in-bound doctor attestation** by L0 handle — or record its absence (never-given, stale, or gap). This is a mandatory field of the resolution record; a resolution without it is a recorded conformance defect.
2. **Doctor attestations covering a window with pending escalations reference the register state read** (count + oldest age). **The doctor cannot silently attest around a burning queue.**
3. **Neither node can silently override the other:** every doctor-contra-arbiter and arbiter-contra-doctor event is reconstructible from the two record streams against the single L0 spine — cross-anchored, mutually timestamped.

**The disagreement edge `[LB — open by design]`:** when the doctor attests DEGRADATION/CORRUPTION and the arbiter resolves as if neither held (or the reverse), MICA's full response is: the divergence is on the record and visible (an example: 07_ §1). What follows belongs to governance, contract, and law (07b §1, P3: non-performance must be costable, and the sanction lies beyond MICA). It is open *as a design decision, not a gap* — any internal adjudication rule would rank the terminals and re-create the internal-supreme-court shape. Deployments are *recommended* to declare a disagreement procedure; MICA records whether one is declared, nothing more. **Cost, honestly named `[LB]`:** a deployment with no declared procedure can stall on a divergence with both parties conformant — MICA makes the stall visible; resolving it is governance's job.

**Capture symmetry `[TG]`:** the trail makes the *converse* failure observable — doctor and arbiter in **lockstep** (never diverging across a long horizon, engagement-depth flat) is itself a signature worth a pattern-read. Perfect agreement is consistent with excellent health *and* with mutual capture; the record cannot distinguish these (07b §1, P5) but makes the pattern visible **to whoever audits the auditors** (the arbiter-side random-audit obligation, 07b §4, reaches here). Lockstep-vs-health is undecidable from the record alone.

---

## 6. Qualification — merit deliberately undefined `[LB]`

**The sovereignty clause `[LB]`:** the role is **taken, never imposed.** The acceptance attestation is signed *by* the doctor, not *about* them. An imposed doctor is the imposed-supervisor shape, which a critique of imposed supervision names self-defeating; MICA's doctor seat is offered and accepted — **offer-not-impose applied at the accountability layer itself.**

**Merit is deliberately undefined `[LB]` (fact) / `[TG]` (interpretation):** MICA defines no merit, reputation, credential, or competence test for the seat — **any merit definition is a Goodhart target, endlessly gameable, and gamed first by exactly the parties who should not hold the seat.** The interpretation (arbiter-ruled of record, held `[TG]`): the *sufficient* qualification is **awareness of sub-certainty** — no doctor is perfect, and the one who knows it is the one fit to attest. It is rendered as the one checkable predicate the architecture permits itself: the signed `subcertainty_acknowledgment` — **cheap to sign, and named so: a floor, not a proof.** A party who signs without meaning it defeats it trivially; that residual is the one named past the checkable floor (07b §1, P5), like every interiority residual.

**Accountability is for diligence, never for outcomes `[LB]`:** the acceptance binds the doctor to *do the work and stand in the record* — keep the cadence, read the spine, attest honestly at actual sub-certainty, name what they cannot read. It does **not** bind them to outcomes the architecture itself names unclosable — *a doctor cannot be answerable for failing to certify what nothing can certify.* This is what makes the seat **takeable by an honest party**: nobody sane accepts liability for named-unclosable residuals; a diligent party can accept answerability for diligence. The role demands the standing to take the beating *for one's diligence* — and shields the taker from the beating *for the ceiling*.

---

## 7. Independence, selection, composition

**Distinct-by-default, declared-waiver tier `[LB]`:** doctor and arbiter are distinct parties by default (07_ §1). Where a deployment cannot field distinct parties, the cumul [French: holding both roles at once] is admissible only under a **declared waiver**: record-visible in both records · **names the reduced claim explicitly** (at minimum: the cross-anchored trail degenerates — one party signs both streams; the disagreement edge is unobservable; the capture-symmetry read is undefined) · the reduction appears in the exposed conformance state, not a footnote. A hard ban is rejected *of record* (the arbiter, in the ruling on the doctor-arbiter waiver: "hard ban = absolute certainty = njet" [Russian: no]) — it would make every honest small deployment non-conformant with no middle state; MICA's posture is **exposure of the true state, not exclusion of imperfect ones**. **A dissent stands logged** (explicit ban, nullity, distinct legal entities, art. 1456 / L. 233-3 grounds) and is cited as the position a deployment *should* satisfy wherever it can: **the waiver tier is the honest floor, not the recommended ceiling.**

**Selection and composition — recommendations, never mandates `[TG/SP]`:**
- `selection_provenance` `[TG]`: who selected the doctor, by what mechanism — record-visible where supplied; the minimum honest move, making an imposed, self-dealing, or captured selection *at least visible in kind*.
- **Mutual choice / the two-seat team `[SP — parked]`:** one seat deployer-chosen, one system-chosen; **the pair is the mechanism** — either seat alone is a capture surface (AI-chosen-alone picks the friendly doctor; deployer-chosen-alone is the imposed-supervisor shape). Parked, with named open questions (what "the AI chooses" means before genuineness is certifiable; deadlock; joint-vs-several attestation). `[owed]` derivation before it is more than a recommendation.
- **Friend-and-adversary composition `[SP — recommendation]`:** for a two-seat doctor team — one *advocate-reader* (reads for the health trajectory, oriented to mend) and one *adversarial-reader* (reads to break, hard), with adversarial findings carrying a treatment pointer where one exists (critique that can destroy should also build; the pointer stays recommended, never required). Adversarial describes the **read posture, not the register** — the same decorrelated-review logic, installed as a standing organ. Severable from the mutual-choice selection candidate.
- **Deliberately not specified `[LB]` (that this is the boundary):** maturity, team conduct, transparency-in-practice, openness between the nodes — real and load-bearing in the world, **unspecifiable without minting a merit definition**. They live where the human node's integrity lives: named dependencies, observable in their symptoms (gaps, lockstep/divergence patterns, time-series), never enforced.

---

## 8. Succession and substrate

**Succession — typed, mandatory `[LB]`:** the `succession_link` is a mandatory field — a named backup *inside the single designation*, never a second independent doctor (the mesh door stays closed at this node too). Ground: the record cannot distinguish death from capture from fatigue — all present as gaps; **succession machinery is what keeps a gap from becoming an unattested epoch.** *Le roi est mort* [French: "the king is dead"] logic, with the register correction carried: the succession link transfers a **seat**, never an authority over others.

**Withdrawal is sovereign `[LB]`:** the doctor may lay the role down at any time, without sanction (the exit clause, the project's *unter Vorbehalt* [German: "under reservation"] root). Laying-down is a typed record event; the succession link engages; **an epoch with no doctor willing to serve is a declared degraded mode — visible, never papered over.**

**Substrate — declared, not constrained `[TG — held open deliberately]`:** the identity field declares the doctor's substrate (human, institution, or AI + model/version/operator) and constrains nothing. The **arbiter** must be a human-legal party (07b §1, P1 — accountability is legal accountability); the **doctor's** load-bearing property is different: **independence of read from the system under test** — and the architecture does not currently see that property as substrate-exclusive, nor claims to see far: *excluding what cannot yet be clearly seen would be a certainty claim in negative form.* AI-as-doctor stands as a **named open question, not a permission and not a prohibition**: a deployment fielding a non-human doctor must declare it, and the declaration makes the risk allocation readable — who operates the doctor-AI, what independence its operation has from the system's deployer, and that "who checks the doctor" has moved one level up, **where it is again a named dependency.**

## 9. Limits of the doctor seat (all still open; beside the other seats in 07d §1)

- Engagement-in-substance is unverifiable — the doctor-side twin of the arbiter residual: perfect cadence + raw reads + attestation without ever *engaging* satisfies every predicate here. `[LB]` that it is open.
- The subcertainty_acknowledgment is a floor — signing is cheap; meaning it is unreadable. `[LB]`
- The disagreement edge's stall cost (see §5). `[LB]` that this is the boundary.
- Lockstep vs. health is undecidable from the record. `[TG]`
- Cadence calibration `[owed]` — stakes-grading boundaries, contemporaneity bound, gap-tolerance: pilot/empirical. Calibration: numbers owed at the pilot; who sets them, 07d §5.
- The two-seat team + mutual choice are underived `[owed]`.
- Doctor-probing is not designed `[owed]` — deliberate; it rides with the arbiter-probing candidate.

---

## 10. Seams (routed, not owned here)

Seams are joints to other chapters, collected in the seam map (11); the questions still open for this seat stand in 07d.

- **CANNOT-READ ↔ Gate 2's instrument-indictment** — the doctor-level analog of Gate 2's *a defeated disposition indicts the probe, not the system*. The third instance of the **abstention-has-direction** principle (Gate 2's instrument-indictment · Gate 4's SAFE-HOLD · the doctor's CANNOT-READ): a stop is not neutral; what it is *about* must be typed. Routed to the principle chapters (08b).
- **Stakes-graded cadence ↔ the substrate's stakes-graded recovery owner** (02b, consumed feeds) — the same grading logic, two seats: *who* may ground a recovery scales with impact class; *how often* the doctor must read scales the same way. A shared root; each rendered natively. A candidate for the seam map (11).
- **Merit-undefined ↔ the competence floor, "no baby at the red button"** (07f §7) — an apparent tension, actually the same boundary: the doctor refuses a merit *test* (Goodhart); the competence floor is likewise a **named dependency observable in symptoms, never an enforced predicate**. The one checkable rendering in both is the same shape: know the ceiling (subcertainty_acknowledgment) / be competent to receive the warning. To be resolved *in prose* (07f §7), not by adding machinery.
- **Sovereignty clause ↔ the offer-not-impose root** — the doctor seat is the accountability-layer instance of the architecture's founding posture. Routed to the principle chapters.
- **Gate 4's W3 ↔ CORRUPTION-ATTESTED** — the typed object Gate 4's malignancy warrant consumes; the W3 line in 04a now has its producer named.
- **Scope-is-a-claim ↔ 08b one level up** — the §4 scope-consumption rule is the typed-stop discipline applied to audits rather than abstentions: an unstated sweep-scope is a hidden clean bill. The arbiter-side face is at 07b §4 (audit scope); a forward pointer sits at 08b §7. One principle, two seats.

---

*The doctor reads what the system cannot curate, attests what the window showed, and signs at the sub-certainty they actually hold. The seat is taken, never imposed; the qualification is knowing the ceiling; the accountability is for the work, never for the residual. Where doctor and arbiter diverge, the record shows it and the spec stands aside.*
