# Chapter 2c — Overlays + the typed boundary

**Covers:** the observability overlays (what min() loses), the Sig meta-factor and its flag-only rule, and the typed boundary where the externality cut lives, including the claim-must-fail rule.
**Status:** Completes the substrate foundation. Most of this chapter is load-bearing.

---

The observability layer (what min() is lossy on), the Sig meta-factor, and the
typed boundary where the externality cut lives.

---

## Observability overlays — never touch the ceiling `[LB on the typing]`

Four instruments recover what pure min() loses. **All are typed identically:
observability instruments. They feed the warm report and the doctor channel.
They never touch the ceiling, never enter f(), never modify a state, never author
anything.** Wiring an overlay into the ceiling imports compensation by the
back door.

- **Balance-read (§5.1)** — min() cannot tell *one weak factor among five strong*
  from *six uniformly mediocre*; the balance-read can. The first is a treatment
  target, the second is systemic exhaustion; the doctor should know which patient
  walked in.
- **Fragility lens (§5.2)** — makes approaching trouble visually loud while it is
  still approaching (MICA has no FAIL floor, so it anchors to the degraded
  threshold).
- **Co-collapse covariance (§5.3)** — reads *co-movement*, which the others miss:
  two factors declining *together* (the K/Sig/Eng co-collapse) can mask a
  systemic collapse as a single local dip. A covariance term never enters f(); it feeds the doctor only.
- **Aggregate-decline lens (§5.4)** — reads the *slow distributed drift of the
  whole* (0.90 → 0.82, no single factor near critical). The temporal complement.

**Proactive early call `[LB on the boundary]`.** On a sustained negative slope,
§5.4 surfaces an early call to the outside node — **salience, never enforcement.**
It pings/recommends a look; it never throttles, clears, latches, or touches f().
This is the *proactive* face of the escalation route (§4.5 is the reactive face:
loop → call the responsible external node; §5.4 is *call it before the loop*).

**Trigger-ownership `[LB]`.** The friction lever is **record-driven +
calibration-owned, never AI discretion.** The AI owns **visibility** (always free
to warn/expose/log — exposing is never enforcing); the record + calibration own
**friction** (are-you-sure → sign-here fire on externally calibrated triggers,
never on the AI's own danger-read; friction re-surfaces, never walls); the **human
owns the decision and the responsibility** (*indéchargeable*: it cannot be discharged
to anyone else). *The dial is not in the AI's hand — that is the guard.*

**Named residual `[TG]`:** the within-NOMINAL co-erosion residual — if every factor
erodes but stays above degraded, a phase shift can defeat the covariance overlay's
early warning. Bounded: what's lost is only the early warning, not the level;
min() bites the instant any factor crosses degraded. *Named residual, min() the
backstop.*

---

## Sig as meta-factor — flag-only `[LB]`

Sig is the factor about the reads of all factors; when it degrades, every bound
is in doubt — including, circularly, Sig's own. A **mechanical cross-discount**
(Sig discounts the other five) is **rejected**: that is new internal coupling,
out-degree 5, the exact feedback topology stratification exists to prevent. Snug,
not torque.

**Flag-only (adopted):** Sig degradation emits a typed **read-trust flag** routed
to the **doctor** — the one node whose view does not pass through the substrate's
own suspect channel. Why the doctor and not the arbiter: a Sig collapse poisons the
records themselves; that is warrant-truth territory.

**No-penalty-on-false-alarm — the firefighter constraint `[LB]`.** Raising a
Sig-degrade and clearing a false one carries **no additional standing penalty**
beyond the unavoidable ceiling throttle. A system *sanctioned* for being seen to
dip acquires a gradient to **avoid being seen dipping** — precisely the masking
attack. We can't remove the throttle (a degraded read *should* lower the ceiling),
but we guarantee the false-positive return path is cheap, fast, unpenalized. *This
is offer-not-impose in the alarm path: the latch makes masking harder; the
no-penalty constraint makes sure we don't incentivise it.*

**Named residual `[TG]`:** the constraint reaches *formal* sanction; it does not fully
reach **informal cost** (reputational drag from being seen to dip). A
strong-enough informal-cost gradient can still incentivise masking. Named open;
the pilot watches.

---

## The typed boundary — EXPOSES / CONSUMES / DOES-NOT-OWN `[LB]`

The boundary owns typing; mechanism lives in §§2–6.

**EXPOSES** (to gates / doctor / warm report): the ceiling (derived from conservative
bounds, stamped with its read window, = 0 at CRITICAL); substrate state; factor-evidence records;
weakest-factor diagnosis; read-trust flag (doctor only); refusal-to-clear event
(doctor only); overlay report (**never the verdict path, never f()**);
method_trust (doctor only); the **DECLARES-UNDENOMINATED register**
(see 13) — the standing enumeration of structure classes the
current read set cannot denominate, O_v-versioned (the 02b stamp), voiced by its runtime alarm (M6, below).

**DOES-NOT-OWN:** its own health certification (the doctor's — a self-certifying
substrate is circular); any verdict on anything (at CRITICAL it sets a *number*,
not an action); any path from an overlay or doctor-read field into f() (the
back-door-compensation regression); the doctor's clearing judgment; calibration
numbers; the disposition itself (scaffolding, not source — *the substrate keeps
honest what it did not install*).

---

## The claim-must-fail rule

This is principle-grade: the spine of "it's not a leash".

> *A printed dependency **whose failure fails the claim** is the product.*
>
> A named dependency is honest **only if its failure — when it occurs under the
> deployment's actual fault model — pulls the substrate's own claim down.** A
> naming that leaves the claim standing when the dependency fails is
> claim-*protecting* — disclaimer engineering, not design. The failure that
> counts is the failure **as it actually presents in production**: a dependency
> whose fault path is masked into a safe default, gated behind an unreachable
> condition, or reset before it can latch has a failure that never presents —
> and a pull that never fires was never a pull. **And the pull is final:** no
> downstream consumer, overlay, or re-render may re-raise the claim while the
> dependency has not recovered — a claim that comes down and is quietly
> re-hoisted downstream never came down.

**Two classes, every dependency in one — mixed rows split, never classed wholesale:**

- **(i) Failure visible from inside → the claim is forced down, mechanically.**
  A stale/absent/record-violating dependency produces a typed EscalationRecord
  and caps or degrades the read.
- **(ii) Failure invisible from inside → the claim is pre-shaped and the
  dependency routed outward.** Channel integrity, a captured doctor, a gamed
  calibration baseline, the single-source-of-truth of the L0 spine — their
  failure *cannot be seen from here* (the **externality root**). The claim is
  **permanently shaped never to assert what only that dependency could warrant**
  (quiet is not health; silence never converts to clearance), and the dependency
  is **required-and-named, never verified-from-inside.**

**Class-(ii) standing is licensed by achievable-impossibility** — the failure is
unobservable from inside *by construction* — **never by the absence of a detector
someone declined to build.** Parking an inconvenient dependency as "invisible" by
not wiring a detector is the class-(ii) form of disclaimer engineering, and it
fails this test.

**The register — the same test at the ontology level `[LB]`.** The
DECLARES-UNDENOMINATED register (see 13)
applies achievable-impossibility to the read *vocabulary* itself: an
undenominated structure class stands on the register only if it is inexpressible
**by construction in the current read set** — never because an available
observable was declined. Entries leave only by building the observable
(DECLARED → DENOMINATED, O_v increments) — or, for the `L0_ONLY` class below,
by L0 routing — never by deletion. **Typed exits `[LB]`:** every entry carries one bit,
classified at declaration time — **`BUILDABLE`** (*undenominated-now*: an L1 observable (L1 is the level of what can be read off the system as it now is; L0 is the record of how it came to be) is constructible in principle, not yet built; exits by building) vs
**`L0_ONLY`** (*undenominatable-at-L1*: fibre-variant per the fibre finding
(see 02b, the τ-anchor) — no L1 observable can exist in principle; discharge only
by routing to the L0 record anchor, never by observable-construction). The bit
blocks category-error work — building L1 probes for properties the fibre finding
makes impossible — and keeps the register from becoming a
graveyard of unbuildable promises. Fallback if typing proves noisy: downgrade
to advisory tag — but it starts typed. *(The schema bit is to land in the register
chapter, 13, at its next natural touch; 13 does not carry it yet — noted, not owed-urgent.)*
The register's runtime alarm (M6) is its
voice (each firing names its specific class); the duty-cycle law is the
maintenance obligation (sustained firing forces observable-set expansion). Typed as
a **pilot-obligation-class object** — it feeds visibility, never f(), never the
ceiling.

**The decomposition obligation.** A dependency whose failure is visible from
inside **in any part** takes class-(i) treatment *for that part*; only the
genuinely-not-observable subset may sit in class-(ii). **The audit reads parts,
not labels.** (First canonical instance: the single-source-of-truth dependency of the L0 spine, split at its spec.)

**The input layer counts.** A class-(i) dependency whose *detector inputs* can be
spoofed so the claim survives the real failure passes on paper and fails in fact.
The test reads inputs, not only outputs.

*This is the externality-cut fused with negative-attestation, made into an audit
rule: MICA cannot police a channel it isn't on — so it names the channel, shapes
its claim never to over-reach it, and routes verification outward. The honesty is
the product.*
