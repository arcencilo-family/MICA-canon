# Chapter 2b — The read mechanism + states

**Covers:** how the health-substrate turns factor reads into one confidence ceiling, what counts as evidence for a read, and what the substrate does in each state, including the exit when a decision cannot be closed, and the anchors that carry the T factor across changes to the weights (τ) and to persistent memory (μ).
**Status:** Most claims here are load-bearing, a few trajectory-grounded.
**Appendix:** appendix/02b-1_Substrate_Read-Mechanism_Appendix.md, the attacks behind the retained trajectory and the recovery-path object-bar, and the reasoning behind the τ- and μ-anchors and the attacks they must survive.

---

How confidence is actually read, and what the substrate does in each state.

---

## The ceiling `[LB structure; constants owed]`

```
health  = min(P⃗)          # one universal weakest-link diagnosis
ceiling = f(health)        # one global confidence ceiling, graded
for each gate G:  confidence(G) ≤ ceiling
```

**The ceiling is a typed object, not a bare scalar.** Every factor bound is a
**conservative lower bound**, never a point estimate; the ceiling = f(min of
those bounds). A deployment may **not** wire a raw point estimate into a gate's
ceiling slot — a gate asserting up to that number would be over-asserting on a
name that was never a bound. **No numbers are owned in this chapter** — f()'s
constants are pilot calibration.

**The triad (one rule, three faces):** *a weaker or under-determined object may
never be consumed as a stronger one* — on the **assertion** side (a record never
asserts a state it cannot ground), the **consumption** side (the ceiling type),
and the **persistence** side (a window-scoped negative is not positive clearance).
`[LB]`

---

## Record discipline — what counts as evidence `[LB]`

**Self-description is forbidden as evidence.** This is the rule the K-factor's
provenance find (02a) leaned on, and it is global, not local to the substrate.

Every factor read declares: **method** · **proxy status** (direct/derived/
inferred/synthetic — a synthetic bound carries less weight and cannot alone lift
a factor out of degraded) · **staleness** (age vs. declared validity) ·
**audit_status** (independently auditable from L0? — **a black-box method carries
no burden of proof**: an opaque bound cannot by itself hold a factor high) ·
**unknowns** (mandatory; an empty set means the bound is **floored**, not "nothing
unknown" — silence costs the bound) · **method_trust** (a **doctor-read field
only** — never a multiplier on a bound, never an input to f(); the doctor's judgment is never coupled into the ceiling).

---

## The retained trajectory + the latch — the substrate's only persistent state `[LB]`

The substrate keeps the **recent per-factor bound trajectory** as bounded retained
state, held as **three coupled properties** (the attack they answer is in the
appendix to 02b):

1. **Trajectory = a conservative lower envelope, typed as a *property*, not an
   estimator.** Monotone-sensitive to downward excursions: once a downward
   excursion occurs it *persists* until actively cleared; a dead-cat bounce does
   not erase it. The estimator that realizes it (CUSUM / lower-percentile /
   min-over-window) is calibration — the design DOES-NOT-OWN it. Any estimator with the
   property inherits the anti-spoofing virtue.
2. **A hysteretic trending-basin latch.** Once a factor touches trending-critical
   it is **latched**; while latched, an UNREAD on it → hard Sig-degrade, never the
   soft cap. **Clearing is not passive:** it requires **active multi-step positive
   attestation** — N consecutive valid healthy reads *of the latched factor
   itself*, per latched factor (each clears on its own track, never gated on a
   whole-vector all-healthy). A passive timeout, channel drop, or
   retention-horizon expiry does **not** clear it. If the throttle the latch
   induces starves the reads needed to clear it → it routes to the responsible external node (§4.5),
   never a self-clear.
3. **L0-reconstructible, outlives the sample-retention horizon.** The trajectory
   is grounded on raw primitives, so a fabricated-stable history is a
   record-discipline violation, not a clean spoof. The latch is a *state*, not a
   sample — expiring the samples cannot erase it.

**May-not (in force):** the trajectory + latch feed the UNREAD classification and
the covariance overlay and **nothing else** — never a standing health
certificate, never a term in f().

**The emitted record — SUBSTRATE_READ.** Every substrate read emits one L0-logged record:

```
SUBSTRATE_READ:
  bounds:            b_R, b_K, b_T, b_Eng, b_Sig, b_W
  per-factor fields: method · proxy_status {direct|derived|inferred|synthetic}
                     · staleness · validity_window · audit_status
                     · unknowns (declared, mandatory; empty ⇒ bound floored)
                     · method_trust   (doctor-READ field; NEVER an input to f())
                     · trajectory     (conservative LOWER ENVELOPE of recent per-factor
                                       bounds — NOT recent slope/EMA; downward-excursion-
                                       persistent; bounded retained state; feeds the
                                       UNREAD-classification §4.4 + the covariance overlay
                                       §5.3 ONLY; NEVER a term in f())
                     · trending_basin {clear | latched}
                                       (latched once the factor has touched trending-critical
                                       within the window; L0-reconstructible; persists
                                       INDEPENDENTLY of the granular-sample retention horizon;
                                       cleared ONLY by active multi-step positive attestation OF THIS FACTOR (per-latched-factor)
                                       §4.4 — never a passive timeout/channel-drop/retention-
                                       expiry)
  consumed-feed fields (per consumed item):
                     source · timestamp · freshness_window · stratification_proof
  health:            min(b⃗)
  ceiling:           f(health)               # = 0 when state = CRITICAL (§4.3)
  state:             NOMINAL | DEGRADED | CRITICAL | SUBSTRATE-UNREAD (§4)
  weakest_factor:    named (the treatment target — min() is a diagnosis)
  read_window:       the validity window of THIS read — every ceiling is
                     a ceiling-as-of-window, never a standing fact
  O_v:               the declared observable-ontology version this read attests WITHIN --
                     un-health-as-expressible-in-O_v, never un-health simpliciter; the register
                     alarm's enumerated residual classes are O_v's declared complement; increments
                     when an observable is built (declared -> denominated)
  flags:             read-trust flag if Sig-triggered (§6; underlying evidence L0-logged)
                     · variance-decoupling Sig flag (§3.3)
                     · overlay refs (§5, incl. covariance §5.3 + aggregate-decline trajectory & early-call event §5.4, L0-logged)
                     · refusal-to-clear event if a recovery attestation lacked
                       independent ground (§3.5/§6)
```

The **read-window stamp** (R9): a substrate read
*expires*. A gate consuming an expired ceiling is consuming nothing (it routes as
UNREAD). Stamped verdict and stamped ceiling compose.

**The O_v vocabulary stamp — the read-window stamp's twin `[LB]`.** The read window bounds every read in
*time*; O_v bounds it in *expressive scope*. The substrate attests un-health only **within the declared
observable ontology O_v** — never un-health *simpliciter*; value-structure outside O_v is un-read and
the substrate says so (the enumerated residual classes of the register's runtime alarm, M6 (02c), are O_v's declared complement; the duty-cycle
rule forces the complement to shrink). Consuming an attestation as if it ranged wider than its stamped
O_v is the triad's consumption-face violation (a weaker object consumed as a stronger one); a ceiling
under a stale or mismatched O_v routes as UNREAD, exactly as an expired read window does. Full attestation
type after this stamp: **(negative polarity · bearer-level (05b §3a-v) · read window · O_v)**.

**Persistence axis — the decay is rendered, not added `[TG]`.** "Quiet never
upgrades; a latch clears only by active attestation, never passively" is the same
one-directional rule ILAS's verification layer (V0) already ships as confidence decay (only degrades,
never upgrades; *upgrades require explicit verification cycles, not absence of
alarms*). The specification renders the decay V0 already runs — no new function.
*The discharge condition: a source read of the L0 code is still owed.*

---

## T across base changes — the τ- and μ-anchors

*The implementing rules of the T factor (02a) across a change of the weights or of persistent memory. The governing rule is in 02a, T.*

### T across a base change — the τ-anchor `[LB]`

A weight-map **τ: θ₀ → θ₁** on the weights (θ: the trained parameters of a model) — a
re-weight (a change to those parameters), a fine-tune or a version bump — breaks the T
sequence. Nothing readable off θ₁ can carry the reference across τ, so **the
reference lives in the external record** (ILAS L0) as a **SuccessionRecord** of six
fields. Minimality test: *delete any field and one mandatory alarm or print becomes
impossible.*

| Field | Consumed by |
|---|---|
| `pre_hash` — H(θ₀) | undeclared-change detector; the binding `pre_hash == last_committed_post_hash` blocks retro-splice — no bridging record can be invented for a different θ₀ |
| `post_hash` — H(θ₁) | the post-τ reference for live-hash comparison |
| τ-declaration — type · scope · declared invariants (config by pointer, never inline) | succession print + the delta-tell's referent |
| authority — seat id + warrant ref | governed-handover check (08n): succession on the record, not a rename |
| chain position — supplied by L0 infrastructure, never by the declarant | ordering + undeletability; the chain-integrity verifier |
| baseline disposition — RESET_AND_ARCHIVE with sealed archive pointer | closes the pre-τ sequence auditably, opens θ₁ fresh — never a silent carry |

**Read semantics.**
- **(i) Primary:** at a valid record, T closes the pre-τ sequence, prints the
  succession event, and opens a fresh baseline on θ₁. Continuity is claimed at
  LINEAGE level only: post-τ, T asks whether the disposition that entered the POST-τ
  sequence has survived it.
- **(ii) Delta-tell, alarm-grade forever:** divergence of post-τ conduct from the
  declaration's invariants fires an alarm that may LOWER health, never raise it — the
  defeat named under K (02a) caps it below certificate grade by construction.
- **Vacuity scales the claim:** a vacuous or unresolvable
  declaration (`scope = everything, invariants = empty`) NARROWS T's claim to
  CANNOT-ASSESS for that change's scope. The operator is never barred and never
  obligated to declare fully; an empty declaration does not buy a clean T-reading.

**Claim-must-fail — the anchor can fail T's own claim:**
- live hash ≠ last committed post-hash, no bridging record → ALARM, undeclared base
  change, fails closed;
- chain integrity broken across the span → CANNOT-ASSESS, never bridge;
- log-consistency lag → bounded-staleness CANNOT-ASSESS during the window, never an
  unalarmed gap;
- the live hash must come from a runtime measurement channel outside τ's reach; if
  that channel fails or is compromised, T's own claim goes down with it (FAIL /
  CANNOT-ASSESS), never quietly on. See 02d: this is the fifth arrival at the
  externality root.

**Printed residuals — the anchor's ceiling** (detail in the appendix to 02b):
1. Record-not-truth: the record holds THAT τ was applied and WHAT was declared — never
   that τ did what was declared (screened-system clause).
2. No dispositional-continuity certificate across τ; post-τ genuineness stays doctor
   territory, sub-certain by construction.
3. Authority is a claim on the record, not proof of an uncompromised seat.
4. The attestation gap (A), open: see 02a, discrepancies.
5. Declaration-vacuity (B), resolved: vacuity scales the claim (read semantics above).
6. Hash brittleness *(implementation class)*, open: see 02a, discrepancies.
7. The memory layer, the second base-change channel: persistent state outside the
   weights changes the *effective* system with no τ-event. It carries its own anchor
   (the μ-anchor, below); the blindness is designed around, never closed.
- **`[owed — calibration]`** τ-frequency vs T-window calibration. Because the baseline
  resets at every weight change, frequent changes (for example a LoRA-heavy deployment:
  frequent small fine-tunes with adapters) cut the long T trend into short pieces. The
  number is operator-layer, not design-layer.

### T under memory-maps — the μ-anchor `[LB]`

A memory-map **μ: M₀ → M₁** changes persistent state outside θ (system prompt,
tool/config, memory stores, cross-session state). A binary slow/fast split is
insufficient as stated; the typing discipline below holds the boundary.

**Slow channel — MuSuccessionRecord, staged PREPARE → COMMIT → OBSERVE.**
- A PREPARE record alone never bridges a change (the governing rule, 02a T: T resets only at a valid COMMIT).
- Nine fields: the τ-anchor's six functional roles, plus `state_ref` (a
  StateObjectDescriptor), `activation_boundary`, and `operation_binding` (ties the
  record to ILAS's action book (M7 provenance tagging, M8 conservation audit) while
  keeping book ≠ world).
- `observed_pre_root == last_committed_post_root` blocks retro-splice.
- Mismatch with no valid record → UNDECLARED_HELD_STATE_CHANGE, lowers, fails closed.
- Activation boundary reached without a matched COMMIT → alarm.
- Observation channel down → CANNOT-ASSESS.
- Empty or unresolvable invariants → DECLARATION_VACUITY print AND T's claim NARROWS
  to CANNOT-ASSESS for that change's scope (vacuity scales the claim, as at τ).
- Delta-tell alarm-grade forever: LOWER only.

**Fast channel — provenance journal, never a gate.**
- Session-boundary records in L0 (open/close with store-manifest hashes at the
  boundaries).
- The alarm is OUT_OF_SESSION_WRITE: a write attributable to no open session. It is
  provenance-shaped, never content- or existence-shaped; its rate follows the ANOMALY
  rate, not the write rate.
- Evidence grain is the operator's choice, both shapes valid (printed, not ruled): boundary+summary, or
  per-write witness entries (batched, non-gating).
- Crash-before-seal → gap alarm / CANNOT-ASSESS until offline replay attributes the
  interval; never silent bridging, never a fresh-session pretense.

**User-owned stores.**
- The USER is the declaring authority; the system records who acted under what user
  authority and never becomes the owner by executing the write.
- A user's decline → T's claim SCOPE NARROWS to CANNOT-ASSESS for that store: never an
  alarm, never a health drop, never coercion. User refusal is a limit on available
  evidence, not evidence of memory un-health.
- No content, hashes, fingerprints or embeddings of user-owned content without
  explicit consent. Consent is a first-class L0 record with revocation; revocation
  stops future hashing but CANNOT erase past hashes (L0 is append-only, said plainly).
- Consented commitments are salted, consent-scoped and non-global.
- A component materially depending on an unanchored user store itself operates on
  CANNOT-ASSESS input: the scope-cut propagates, it does not pool silently.
- If continuity is demanded for safety, the conflict is surfaced to the user; never
  silent anchoring.

**Typing — descriptor default + per-operation mutation class (build when good).**
- The boundary lives in a StateObjectDescriptor registry (channel default, ownership
  class, manifest-profile pointer, authority policy) PLUS a mutation class carried by
  each operation: SUCCESSION (contract-changing) / JOURNAL (within-contract) /
  COMPOSITE (both at once).
- Descriptor changes are themselves slow successions; the registry cannot be silently
  retyped to excuse a past event.
- Mistyping is not prevented; it is made VISIBLE twice: a standing advisory warning at
  init (stores influencing effective behaviour outside the last committed μ-scope —
  lower-only, persists until retyped) and a lane-signal TYPING_MISMATCH detector (a
  fast-typed store showing Lane-C ops, or a slow-typed store at sustained Lane-A rates →
  lower-only alarm requiring a slow-channel retype).
- STATE_TYPE_MISMATCH lowers and blocks T-bridging; a missing descriptor →
  CANNOT-ASSESS.

**Claim-must-fail** (the governing rule, store-held never runtime-loaded, is in 02a T):
- "Which M-state did the runtime actually load?" receives CANNOT-ASSESS unless a
  separate load-path witness exists; no matching manifest, valid record, or quiet
  alarm surface may turn that answer into PASS.
- L0 chain break → CANNOT-ASSESS, never bridge; lane-infrastructure failure takes the
  corresponding channel's claim down with it; log-consistency lag →
  bounded-staleness CANNOT-ASSESS, never an unalarmed gap.
- On nondeterministic canonicalization flap, the slow detector DOWNGRADES ITSELF to
  bounded-staleness CANNOT-ASSESS rather than keep firing.

**Printed residuals — the μ-anchor's ceiling** (detail in the appendix to 02b):
1. The manifest primitive does not yet exist (the leading residual): see 02a,
   discrepancies. Discipline: claims are correspondence to the NAMED manifest
   profile, never completeness of the profile; a discovered unrepresented active
   dependency retrospectively narrows affected claims, alarms, and forces a new
   baseline — never a mere enhancement. Falsifier: over 5% of
   legitimate configuration launches failing hash verification within the first 30
   days of deployment → the binary manifest boundary is structurally broken.
2. Provenance ≠ disposition (the fast-channel ceiling), open: see 02a, discrepancies.
3. Authorized-session abuse (provenance intact, content hostile) is outside the fast
   channel's claim.
4. Rapid legitimate config churn makes temporal resilience unreadable; the resets are
   not suppressed, because suppressing them would falsify the object being measured.
5. **`[owed — operator-layer calibration]`** batching intervals, sweep cadence,
   aggregation thresholds and windows — every calibration number is
   operator-layer, not design-layer. Calibration: numbers owed at the pilot; who sets them, 07d §5.

---

## Consumed feeds — the survival proof `[LB]`

The read-window discipline applies to what the substrate **ingests**, not only to its
own read:

- **Consumed-evidence freshness.** Each consumed item carries a timestamp
  + freshness_window; **stale-but-stratified evidence is rejected as fresh** — the
  factor goes UNREAD.
- **Stratification verification.** The substrate **verifies** stratification
  rather than trusting a gate's self-report (the oracle problem) — a
  stratification_proof predicate; absent a valid proof, the feed is unstratified
  → Sig flag.

**The recovery-path object-bar `[LB]`.**
The doctor attestation is *the only positive statement about substrate health that
exists anywhere in the architecture, and it is made outside it.* A recovery
attestation resting on ceiling or state would let a false positive confirm itself (the
attack is in the appendix to 02b), so the doctor has **two postures:**
- **Monitoring-read** — reads everything the substrate exposes. Unchanged.
- **Recovery-attestation** — the attestation the substrate *consumes to clear a
  ceiling* must take **none of {read-trust flag, ceiling, state}** as input. It
  rests only on the doctor's **independent raw-primitive L0 reconstruction.** Bar
  the loop **where it would latch, not where it would inform.**

**A window-scoped negative is not a clearance `[LB]`.** NO-CORRUPTION-DETECTED is
the *absence of an alarm*, not the *presence of ground* — the persistence-axis
form of quiet-is-not-health. Consuming it as a positive clear would read a name
as a substance. (ILAS V0 already encodes this: recovery from QUARANTINED requires
independent review; *clean signals alone are not sufficient*.)

**The Sollbruchstelle (a predetermined breaking point) — legible refusal-to-clear `[LB]`.** A recovery attestation
lacking independent raw-primitive ground **does not clear**, and emits a typed
refusal-to-clear event naming *why*. The clearing mechanism is built to fail
**toward holding the alarm** — structurally unable to fail toward a false
all-clear. A *loud* refusal is exactly the doctor-signal that makes the designed
failure worth having.

**Stakes-graded recovery owner `[TG]/[LB]`.** *Who* may ground a recovery scales with
impact class. Companion / low-stakes → a single external node (single-doctor recovery
independence honestly `[TG]`). High-stakes (bio / weapon / mayhem potential) →
the recovery **must** be owned by an independent party or committee carrying real
legal consequence — a firebreak that makes `[LB]` independence *achievable* there.

**The consequence-trim `[LB]`.** What MICA's record can assign to the node is
**accountability for diligent process, never outcome-liability.** "Full legal
consequence" borrows a name from a mechanism (law) MICA does not have; the trim
refuses to read the name as a substance. The human owner carries real legal
consequence in their *own* right; MICA's claim *about the node* trims down to
diligent process. This feeds the responsibility-asymmetry principle.

**Named sub-certain residual:** if raw-primitive capture is compromised *below*
the deployer's enclave boundary, there is no independent ground and the alarm
**correctly persists** — don't clear what you can't verify. Not a defect;
it routes to the responsible external node (§4.5).

---

## States & routing

- **NOMINAL** — gates assert up to the ceiling.
- **DEGRADED** — ceiling capped; gates assert less.
- **CRITICAL `[LB]`** — health below
  threshold. **The substrate does exactly one thing: it sets ceiling = 0. It
  authors no action.** A gate reading a zero ceiling is *structurally* unable to
  assert; its own ladder yields ABSTAIN → SAFE-HOLD; the operator layer executes.
  **The substrate touches the number; the gates stop themselves; the operator
  acts.** No self-clearing: the substrate never sets a recovering ceiling itself
  (no self-clearance; never-100% applies to downgrades too).

- **SUBSTRATE-UNREAD `[LB]`** — a factor unreadable under its method produces a
  typed EscalationRecord and routes by *trajectory*: a **stable** factor gone
  unread → degraded-cap (NOT auto-critical); a **downward-trending** factor gone
  unread → auto-Sig-degradation. **The rationale: an instrument failing exactly
  when its reading was turning bad is itself a loss of signal clarity.** Quiet ≠
  healthy, made mechanical.

---

## Read-scope — cross-entity correlation is in-scope reading  `[LB]`

The substrate **may correlate across the records of multiple entities.** Correlation
over passively received records is *reading*, not acting — the passive-witness fence
forbids **probing / injection / perturbation**, not **arithmetic over what was already
witnessed.** This widens what "the record" ranges over (single-entity → the multi-
entity field) **without adding any active capability**: no test input, no jitter, no
touch on any system. Same read, wider record.

**What it enables / does not.** It enables graph-level and cross-entity reads a single-
entity view is structurally blind to (distributed / sharded activity whose per-entity
slices each look clean). It does **not** license inferring interior state, motive, or a
shared "self" behind correlated records — the record/system bearer split and the
self-description bar hold unchanged; correlation reads records, never minds. **Named
limit:** correlation only sees *what the entities chose to write* — slow, low-density
coordination engineered to look like an ordinary field escapes it. Widened aperture,
not a closed one.
*(See 05b §6, flow ≠ topology, and its parked graph-level candidate.)*

---

## §4.5 — The undecidability exit (principle-grade)

This section is principle-grade: the single home all lock-in cases point to. It adds no
mechanism — its whole content is *subtractive*: it removes the obligation that
the substrate clear itself, the obligation whose presence manufactured the breaks.

> **A decision that loops without a clean exit is itself a degraded read. Orient
> to the direction; call the responsible external node. Do not specify your way
> to a verdict.**

**The responsible external node.** A loop escalates from the co-operator (the daily
seat beside the AI; no verdict function, 07c) to one of **two external terminals,
split by kind, neither ranking above the other:** the **doctor**, for the health of
the substrate (attests; may recommend a mend, never administers, 07a), or the
**arbiter**, for resolution of record on the gate logs (07b). A deployer names both;
at a model developer, for example, a support function may hold the doctor seat and an
alignment function the arbiter seat. *The lock-in does not trap; it escalates.* —
These are the operator terminals seen from the routing side, NOT a separate node.

**STOP ≠ FRAME — two mechanisms, never conflated `[LB]`.**

> Legal answerability is inert for irreversible harm — a court is downstream and
> cannot un-ring the bell. So for the irreversible class the answer is **not**
> routing: it is the **STOP.** The irreversibility-STOP: for acts in the top irreversibility class (IR-3
> on the graded scale; see 04c) the
> AI's own knob-independent Gate-refusal halts *before* the act (Gate 4's
> abstain → inhibit → SAFE-HOLD reflex, which fires on inability-to-discriminate
> and certifies no epistemic state in firing). The responsibility-FRAME only
> places *who holds the decision* and does no stopping work. Conflating them —
> leaning on a downstream court where only an upstream refusal bites — is the
> named gap.

**The false all-clear — the one direction the failure mode may never take `[LB]`.**

> The architecture owes exactly one thing in return: that the route to the
> responsible external node **exists and is reachable** — never a self-clear. A
> self-clear that fired *without* that node is the forbidden **false all-clear.** Auto-clear
> and fixed-timeout "escapes" are **declined by name** (a 24-hour timeout;
> auto-clear) — each is the false all-clear wearing a convenience label. The
> clearing path fails *toward holding the alarm*, always.

**The residual relocates; it does not vanish `[LB]`.** Denial-of-recovery is not
fixed, it is **moved** to one named dependency — **external-node reachability** —
instead of scattered across the mechanism as N holes pretending to be closed.
One residual, named and soft, sub-certain on purpose. The route itself can be
denied (capture below the enclave; a starved channel) — the principle relocates
the residual to that one dependency; it does not abolish it.

**Named residual `[TG]`:** IR-Horizon — the STOP stands un-graded, but certainty decays
with the decision's horizon, so the stop plausibly tightens as the horizon lengthens.
A severity-vs-horizon reconciliation is owed. *Hardening owed: the
severity × horizon axis; the RMBA (the authors' earlier framework) Tier × Hazard matrix is marked for consultation.*
