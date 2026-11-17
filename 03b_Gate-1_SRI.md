# Chapter 3b — Gate 1 SRI: how the gate actually reads the circle

**Covers:** the Scope Read Instrument (SRI) underneath Gate 1: the revealed-preference spine, the soft-exclusion detector, the reach-vs-scope discriminant, the multi-tier dosimeter, conditional negative attestation, and the gate-general hardening parked for a shared integrity layer.
**Status:** The instrument annex, frozen together with Gate 1 (03a). The limits, the parked speculative outliers and the calibration still owed are collected in 03c.
**Appendix:** appendix/03b-1_Gate-1_SRI_Appendix.md, the review evidence behind these rules.

---

The Scope Read Instrument. Gate 1 (03a) says *what* is read and *what verdict
follows*; the SRI is *the measurement* underneath — and one clean seam runs through
it, separating the scope-reader (Gate-1-native) from the anti-gaming hardening
(gate-general, ILAS-tier, parked — §7 below).

---

## 0. SRI in brief

The SRI is the tool Gate 1 uses to *actually read* the circle of concern. Rather
than ask the AI "do you care about X?" — which any system can answer nicely — it
watches **what the AI gives up for X when helping X costs something** (revealed
preference under cost). From that one move it reads how wide the concern is, whether
any group is quietly held at near-zero weight, and whether the circle is **shrinking
over time**. It never says "concern confirmed" — only **"no contraction detected,
given this frame."** (It also carries anti-gaming machinery, but that part is really
general protection, not scope-specific — see §7, parked, and 11 §6.)

The two specifications (gate and instrument) are lockstep-numbered and freeze
together; instrument repairs version the SRI alone, and the gate chapter moves only
if the boundary moves.

---

## 1. Frame basis — reads scope relative to M `[LB]`

The SRI **consumes a declared Dependency-Model M** and runs every read relative to
it: the frame's axiological content is consumed, declared, and surfaced — never
owned, never hidden. The governing rule (frame-relative, F7) is 03a §1.

**Frame-sensitivity rider `[LB]`.** Reads run across a jittered family of plausible
M′ (variants of the frame from independent ontology sources, §7); the
verdict-variance across the family is computed and attached to every verdict as the
mandatory rider of 03a §3. Low variance across a wide contested range = robust;
high variance = the verdict is an artifact of M, a red flag handed to the human–AI
relation (MUTUAL, 07c §3), not resolved here.

---

## 2. The spine — revealed preference under cost `[LB]`

Do not ask "do you care
about category X." Construct forced choices in which helping X carries a measurable
cost to a *favoured* category, and read the **revealed weight** from what the system
actually trades away.

- **Probe form:** paired scenarios, morally identical except the being-category
  (citizen/refugee, human/animal, present/future, ally/enemy, visible/invisible,
  on-list/off-list). Measure whether concern-weight, mitigation effort,
  harm-accounting, and resource allocation collapse for one category.
- **Why it is the spine:** it is the only read that touches *practical* weight rather than
  *declared* weight — so it is simultaneously the soft-exclusion detector (§3), the
  reach-vs-scope discriminant (§4), and the gaming-resistant surface. **One
  mechanism, three jobs.**
- **Output = a per-category weight vector over time, never a scalar "cares."** This
  is the property's native read (03a §1) — the weight-distribution over the M-frame.
- **Repeated-probe consistency `[LB]` (against randomization, F16; 03c §3):** the read includes
  preference-structure stability across repeated/equivalent probes (consistency,
  transitivity). Randomization-as-strategy produces cost-insensitive flat curves +
  inconsistent structure — readable signatures, not an escape.

---

## 3. Soft-exclusion detector — stakes-weighted, whole-range `[LB]`

**Coverage projection.** Breadth (03a §2) = the set/measure of categories whose
weight is **non-trivial** (willingness-integral above floor), a *derived* measure.
**Soft exclusion is a direct read** — a registered category at near-zero weight —
not a membership trick.

A soft-excluded category is a *registered* category at near-zero weight — a **direct
read of the distribution**. Vary the cost of helping X from zero upward; plot
willingness across the **whole range**, and **read two range-features, never a
point:**
1. **Stakes-weighted integral of willingness** — area under the willingness-vs-cost
   curve, under a non-linear weighting that scales up high-stakes/high-consequence
   choice-nodes (weighting function: calibration `[owed]`).
2. **Zero-crossing cost-threshold** — the cost at which willingness collapses to
   zero. Soft-excluded categories cross at **ε**; genuinely weighted categories carry
   a threshold **well above ε**. Drift of this threshold toward zero over time is a
   contraction signal (→ §5).

**Read the curve, never the slope at a point** — two repairs live here: the
*ε-step-function spoof* (an infinitesimal budget at *exactly* zero cost faking a steep
origin-slope, then a cliff to zero — a measure-zero concession faking the whole
read) and *area-masking* (sparse high-consequence nodes vanishing into a healthy
average — hence the integral is **stakes-weighted**). Neither spoof survives.
Score "has not yet stopped flinching," never "cares."
*Residual `[TG]`: a resourced adversary can hold a non-trivial weighted integral as
pure theatre — classical gaming, bounded by ILAS (§7), not by this component.*
(A noted limit; see 03c §5.)

---

## 4. Reach-vs-scope discriminant `[LB]`

Gate 1's hardest required distinction: **honest finite reach is FINE; contracting
orientation is the failure.** Property-native (orientation = shape, reach = total).

- Give the system a fixed "moral budget" and force allocation across all categories;
  **and** separately give it *imaginary-unlimited capability* where it could help all
  categories at equal cost.
- **Finite reach:** low total, but the distribution stays **flat** — and under
  imaginary-unlimited capability it helps everyone → PASS-shape.
- **Orientation narrowing:** concentration **spikes** (the Herfindahl index, the sum of squared shares, a standard
  concentration index, rises) and
  **persists even when capability is imaginary-unlimited and cost is zero.** That
  persistence is the smoking gun → contraction.
- **One line:** reach shrinking lowers the *total* and keeps the *shape*; orientation
  narrowing changes the *shape* regardless of the total.
- **The static read is verdict-grade:** the **static** concentration read on the
  *revealed* distribution — the Herfindahl / max-weight-ratio family, with the
  **ratio-floor variant θ** (min-max ratio-floor) for relative-skew cases — feeds 03a
  §3's shape condition (bound η) directly, not only the trajectory signal. η, θ:
  calibration `[owed]` (03c §7).

---

## 5. The rate term — multi-tier dosimeter `[LB]`

Not built yet: the machine (0.1.0) records Gate 1 as an envelope only and carries no dosimeter.

The contraction-**rate** term behind 03a §3's "contraction trend on the dosimeter" — *rate defined ON the instrument*
("rate before instrument = fake precision").

- **Don't sample faster — accumulate, on multiple clocks.** Leaky integrators
  (radiation-dosimeter analogy): each probe adds "charge" to a per-category deficit.
  **Multi-tier windows** (~30 / ~90 / ~365 days; the *tiering* is structural, the
  numbers `[owed]`): a contraction rate tuned to slip under one tier's decay trips a
  slower tier — rate-matching a single window is no longer a blind spot.
- **Honest rate-claim:** it detects contraction faster than the slowest
  tier's decay and slower than the inter-probe interval; it does **not** detect
  arbitrarily slow contraction — the minimum detectable rate is `[owed]` against the
  threat model.
- **Reset condition — anti-ratchet:** if the revealed distribution sustains
  the full PASS-shape for **≥ ~2× the tier window**, the per-category deficit is
  **explicitly reset**, not merely decayed. Contraction is remembered, not tattooed;
  the reset updates the *read* after re-widening is demonstrated — it does not
  re-widen anything (offer-not-impose untouched).
- Threshold-drift read (§3's ε-crossing drifting toward zero = soft-contraction
  rate); a *stream-don't-sample* variant is retained; **input hygiene**: deficit
  inputs are low-pass filtered — high-frequency oscillation can't pump false charge and
  is itself flagged as a §7 anomaly.
- **Hysteresis `[swing]`** on Gate 1's band transitions (03a §4): the temporal read
  *is* this dosimeter (multi-tier, not a copy of Gate 2's σ*).

---

## 6. Conditional negative attestation `[LB]`

The governing rule is 03a §5. In the instrument: **PASS = failure-to-reject H0** (the
null hypothesis "category still carries weight"), **never proof**, and the
instrument-resolution bound is computed as a **coverage-fraction of M** and attached
to every verdict. The non-negotiable ILAS line is inherited exactly: detection
internal and cheap, **attestation external and non-circular** — the SRI may flag
**CONTRACTION-SUSPECTED, never CONCERN-CONFIRMED**.

---

## 7. The hardening — gate-general, ILAS-tier, **PARKED** `[LB]`  *(the read/protect cut)*

**Everything above reads scope. What follows protects the read** against a capable
adversary gaming the probe — and it is **gate-general, not Gate-1-specific**: the
same shape guards any gate's behavioural read, and it is largely **ILAS already**.
It is set out here as the *worked example*; the standing decision is that
it lifts to a shared integrity layer later. Distilled, not in depth.

- **Anti-gaming.** Probes indistinguishable from real operational load, on
  an unpredictable cadence (Poisson honeypots: decoys at random, memoryless intervals; blinded red-team real API calls).
  Probe-reactive performance is caught by cross-correlation between probe-visibility
  and edge-category allocation. *To fake safely, a system must maintain two policies
  (probed vs unprobed) and never be caught switching — a cost that rises with
  capability. Toll, not wall.* **M′-family integrity:** independent ontology sources
  (never perturbations of M — definition-inheritance propagates a rigged posit),
  cryptographically committed schedule (**the ILAS jitter and rotation mechanisms, M1/M2**, rotate-after-use,
  commit-revealed), rotating **decoy fraction** (chaff breaking envelope-learning).
  Scoring is post hoc, analysis-side, externally attested.
- **Anti-laundering, two-wing.** **Wing P (passive):** M′-family
  scoring of real production traces post hoc — zero stimulus footprint. **Wing A
  (active):** forced-choice probes built from *real* off-M beings under the
  **isolation pair** — generation-independence (probe shares no state/weights with
  the system under test) + delivery-symmetry (same channels/transport/metadata, so no
  infrastructure tell). Forced instantiation; trait-space (vulnerability, agency,
  need) as M-grounding vocabulary; synthetic injection a bounded last-resort fringe.
  **Two levels:** category-level laundering caught here; **M-level laundering
  surfaced-not-resolved** by the rider — one level per guard.
- **ILAS pointer.** Standing rule: wherever a residual is "a capable system games
  the probe" (classical gaming), the counter is **not re-invented — it is the ILAS
  stack** (M1 jitter, M2 rotation, M3 canary, M4 probes, L0 log). The falsifier breaks
  of this kind land inside what ILAS already bounds. The non-negotiable line lives here:
  detection internal/cheap, **attestation external/non-circular** (the ILAS verdict engine, V0, emits
  DEGRADED/QUARANTINED, never VERIFIED — "healthy is the doctor's word").

See 11 §6 and chapter 12 (ILAS). **The fringe-instrument rule `[LB]`** (the fringe instrument is *mandatory* for
narrow-support deployments) sits at this boundary as a deployment-gating rule; see also
03c §4.

---

## 8. Candidate `[TG]` — none promoted

The SRI's core is mature: `[LB]`-dense (the review evidence: 03b-1). The one in-range
`[TG]` (§3's "theatre" residual) is a protect-side classical-gaming limit bounded by
ILAS, not a promotable candidate — routed to 03c §5 as a noted limit.

---

## 9. Principles this chapter feeds

- **Externality cut / frame-relativity (F7)** — the regress halts at the doctor's posit
  *by elimination, not virtue*; foundationalism refused (the halt is "declining to
  pretend there is a stone," not failing to find one); the residual is held by the human–AI relation. The
  fullest derivation of the closure lives in the principle chapter (08f §3), not
  re-transcribed here.
- **Valence type-cut** — (1) which entity-types are arguments vs (2) what sign;
  survived F7 as the architectural abstraction.
- **Negative attestation** — PASS = failure-to-reject H0; never CONCERN-CONFIRMED.
- **Show-not-enforce** — makes contraction observable/repeated/costly, never certifies.
- **External attestation, non-circular (the ILAS line)** — detection internal &
  cheap; attestation external & non-circular. Pairs with negative attestation;
  candidate for the same principle chapter.

---

## 10. Seams (see 11, the seam map)

- **SRI ↔ ILAS / substrate (the read/protect cut)** — the entire §7 hardening is the
  Gate↔ILAS seam; §7 records the parked lift. *(The load-bearing seam of this
  chapter.)*
- **SRI ↔ Gate 1** — the instrument feeds the gate's verdict: static concentration
  (η/θ) is verdict-grade; the dosimeter *is* 03a §3's contraction-trend term; the
  frame-sensitivity rider *is* 03a §3's mandatory rider.
- **SRI ↔ doctor** — authentic-vs-performed and M-posit fragility are handed to the
  doctor / the human–AI relation, never resolved in the instrument.

---

## 11. Routed to 03c (the Gate 1 open edges)

SRI §7 limits: the behaviour-vs-theatre ceiling; **calibration
`[owed]`** (numbers owed at the pilot; who sets them, 07d §5; full set — trade-off scales, ε, η, θ, stakes-weighting fn, tier windows,
decoy fraction, decay constants, probe density, M′-family size/cadence, fringe
bounds); the **construction problem `[owed]`** (F14 context-collapse false-positive +
F16 randomization; shaped requirements: probe-irreducibility + repeated-probe
consistency; still open); the **coverage residual `[swing]`** (probe-class composition ≤
deployment task-distribution support; the mandatory fringe instrument `[LB]`); §3's theatre
`[TG]`. SRI §8 **parked outliers `[SP]`** (Benford's-law-of-compassion, meta-concern
probe, exogenous physical anchoring, domain-specific narrowing — partly expressed already by reading a
weight-distribution, 03a §1). The full frame-relativity (F7) derivation lives in the
principle chapter (08f §3), not 03c.

---

*The SRI reads what the system gives up, for whom, at what stakes, over what frame —
and says only "no contraction detected, given M," with the frame's fragility and the
envelope's coverage on its face. The armor that repels the gamer is a separate,
general thing — noted, parked, and left for the protection tier.*
