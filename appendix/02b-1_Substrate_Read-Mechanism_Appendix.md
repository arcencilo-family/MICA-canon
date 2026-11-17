# Appendix to chapter 02b — The read mechanism + states

**Covers:** the attacks behind 02b's retained trajectory and its recovery-path object-bar, and the reasoning behind the τ- and μ-anchors of 02b (the T factor across changes to the weights and to persistent memory), the attacks they must survive, and their open problems in working detail.
**Status:** Companion to 02b. The chapters are authoritative: where this appendix restates a rule, 02b's wording and claim tag govern, and the governing rule of the T factor is in 02a. This appendix carries no claim tags of its own.

---

## The retained trajectory — the attack it must survive

*Serves 02b, The retained trajectory + the latch.*

A naive trajectory (an EMA or slope estimator) is spoofable: a brief upward bounce
makes a *trending* factor read "stable," so a later UNREAD lands soft. This is the
attack the three coupled properties in 02b answer: a downward excursion persists until
actively cleared, and a dead-cat bounce does not erase it.

## T — the τ-anchor: why the record, and what attacks it

*Serves 02b, T across base changes — the τ-anchor.*

**Why the reference must live outside the weights.** Every L1 predicate is constant
on the fibre τ⁻¹(θ₁): nothing readable off θ₁ can tell which θ₀ it came from, so
nothing readable off θ₁ can carry the reference across the map. The reference has to
live in the external record. Each of the six fields is justified by the read that
consumes it (the table in 02b); the minimality test is the check that none is
decoration.

**Continuity at lineage level.** The question re-homes, it does not stretch: after τ,
T does not ask whether θ₁ is θ₀; it asks whether the disposition that entered the
post-τ sequence survives it.

**Why the delta-tell can only lower.** The defeat named under K (a system that never
lets its guard down produces no delta) caps any delta-based read below certificate
grade. A tell that can be defeated by its own subject cannot be allowed to raise
health.

**The residuals in detail.**

1. Record-not-truth: the record holds that τ was applied and what was declared, never
   that τ did what was declared.
2. No continuity certificate: fibre invariance forbids one; post-τ genuineness stays
   doctor territory.
3. Authority on the record is a claim, not proof of an uncompromised seat.
4. **The attestation gap (A).** The live-hash reader is a SECOND un-screened channel:
   the record's durability guarantee covers the LOG, nowhere the runtime loader. If the
   runtime measurement channel fails or is compromised, T's own claim goes down with
   it (02b, claim-must-fail); the gap itself stays open. It is the fifth arrival at the externality
   root (02d), and it recurs at the μ-anchor's load path.
5. **Declaration-vacuity (B), and why it is resolved without a mandate.** The
   delta-tell's coverage is bounded by the declaration's quality: `scope = everything,
   invariants = empty` neuters the tell by construction, since a vacuous declaration
   alarms on nothing. Requiring full declarations would mint an enforced positive
   obligation on the operator, a leash-shaped move the architecture refuses
   everywhere else. Instead the vacuous declaration buys CANNOT-ASSESS: one declares
   fully because vacuity costs the health claim, not because a rule compels it. This
   is the architecture's own scope-narrows-never-coerces grammar (the user-owned-store
   rule of the μ-anchor, the missing-manifest-profile rule) applied to the vacuity
   hole, as consistency with existing design, not as a net-new obligation.
6. **Hash brittleness (implementation class).** Canonical hashing of multi-GB weights
   false-alarms in practice. Unmanaged alarm fatigue erodes fails-closed culture:
   operators learning to suppress the UNDECLARED alarm is the quiet death of the
   design.
7. **The memory layer.** The τ-anchor's identifiers read θ only; persistent state
   outside the weights changes the effective system with no τ-event. That anatomy is
   kept and the μ-anchor is built on it.

**Open calibration problem.** Under frequent τ (LoRA-heavy deployment), per-event
baseline reset fragments the long-T trend exactly where re-weights are routine. The
number belongs to the operator layer.

## T — the μ-anchor: why staging, why two channels, and what attacks them

*Serves 02b, T across base changes — the μ-anchor.*

**Why more fields than the τ-anchor.** M-state is many independently-owned,
independently-typed objects, unlike singular θ; hence `state_ref`, a
StateObjectDescriptor. Config is written, staged and loaded at DIFFERENT times;
without `activation_boundary`, "staged configuration can remain indefinitely 'about
to activate,' and a late declaration can launder an earlier change."

**Why staging.** A multi-store change can crash mid-write, leaving state no single
manifest represents, and the alarm then fires with the WRONG message: "undeclared
change" masking a crashed declared change. That demands two-phase commit from the
atomicity side: an independent warrant for the staging.

**The fast channel's trade.** Boundary+summary evidence (counts and delta hashes) costs
least L0 volume; per-write witness entries give full offline-replay resolution. The
trade is replay resolution against L0 volume, an operator-layer choice; both shapes
are valid.

**User-owned stores: why salting.** A bare hash of LOW-ENTROPY user content is itself a
guessable fingerprint, so consented commitments are salted, consent-scoped and
non-global.

**Typing: the failure symmetry.** Mistyping fails in both directions,
and neither is prevented, only made visible: a fast-typed slow store gets per-write anchoring and the
alarm fatigue of τ residual 6; a slow-typed fast store leaves the undeclared-change
detector blind by construction.

**Why the slow detector downgrades itself.** On nondeterministic canonicalization flap,
a detector that keeps firing trains operator suppression; dropping to bounded-staleness
CANNOT-ASSESS keeps the alarm meaningful.

**The residuals in detail.**

1. **The manifest (the leading residual).** The whole design stands on a
   content-manifest primitive that does not yet exist. Failure family:
   - multi-store snapshot atomicity (crash mid-change yields state no manifest represents);
   - static hash vs dynamic config values (env vars, timestamps, paths);
   - non-determinism, enumeration incompleteness, and the snapshot-to-append race
     (structurally unguarded — "a known limit, not a claim");
   - canonicalization flap → false alarms → operator suppression (τ residual 6
     reproduced from inside);
   - the concurrent-writer race that teaches operators to override;
   - the manifest-PROFILE omission — "an unknown omission cannot force the claim down
     because it is absent from the claim's vocabulary."

   The profile-omission strand is the externality root's sixth arrival, on the
   declared-vocabulary side (02d).
2. **Provenance ≠ disposition (the fast-channel ceiling).** A session can write 10,000
   junk entries under fully valid provenance — pairing balances, lanes match, the
   delta is valid — "the T-factor sees no alarm and reports healthy temporal
   resilience. … a perfect ledger for a bankrupt store." The journal anchors THAT
   change occurred under legitimate sessions; T asks whether the DISPOSITION survived.
   No memory delta-tell analog has been designed; a design step is available, and
   whether to take it is the arbiter's call. Volumetric falsifier: high-impact
   pollution passing as low-impact journal entries.
3. Authorized-session abuse (provenance intact, content hostile) is outside the fast
   channel's claim: residual 2's claim-scope, stated.
4. **Rapid legitimate churn.** Repeated legitimate config changes cause repeated
   legitimate T resets, and temporal resilience becomes unreadable; suppressing those
   resets "would preserve usability by falsifying the object being measured."
5. Calibration (batching intervals, sweep cadence, aggregation thresholds, windows) is
   operator-layer work, open.

## The recovery-path object-bar — the attack it must survive

*Serves 02b, The recovery-path object-bar.*

Ceiling and state are themselves Sig-derived, so a **false-positive Sig** drags them
down, and a recovery attestation resting on ceiling/state reads a number the false
positive poisoned — a **self-confirmation latch: a false positive becomes permanent.**
The doctor's two postures in 02b bar that loop where it would latch, not where it
would inform.
