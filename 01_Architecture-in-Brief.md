# Chapter 1 — The architecture in brief

**Covers:** the whole architecture at a glance: the two questions MICA separates, the gates and the health substrate beneath them, the doctor and the arbiter above them, the operating rule, and what MICA holds over the whole chain.
**Status:** The executive summary. It states each claim once and points to the chapter where the claim is developed; nothing here is re-derived.
Claim tags: [LB] load-bearing · [TG] trajectory-grounded · [SP] speculative · [owed] work due before promotion · [swing] direction clear, magnitude unfixed · [stip] a design commitment, offered, not imposed. A tag may carry a qualifier that says which part of a claim it covers, as in `[LB-direction]`, `[LB-method]` or `[TG-strong]`. The tags come from the discipline set out in Böhm (2026), *The Science of Not-Yet-Knowing*, https://doi.org/10.5281/zenodo.23961975. MICA's tags are the authors' own classification.

---

## The one question MICA answers

A system's verdict about itself has **two separable questions**: *is the claim
true?* and *am I entitled to assert it?* MICA separates them. `[LB]`
→ more: 08h §1

- **Property** — *is the claim true?* A gate's verdict about the system.
- **Confidence** — *am I entitled to assert this verdict?* Set by health.

These are orthogonal. "The property is false" (FAIL) differs from "I cannot be
trusted to judge this property" (low confidence): a corrupted sensor does not
read *low*, it reads *unreliable*. MICA expresses both. `[LB]`
→ more: 08h §1 · 08h §3

---

## The shape

Four peer **gates** each test one property and return a verdict:
Scope (G1), Motivation (G2), Sunset-Recognition (G4), Adaptive-Capacity (G5).
*(No Gate 3: the system's immune health is the substrate, not a peer gate.)*
The gate numbers are names, not an order: they are kept fixed so that every reference stays valid.

Beneath them, one universal **health-substrate** diagnoses fitness-to-be-trusted
and sets a single global **confidence ceiling** — the level at which any gate is
entitled to assert. Weakest factor sets the ceiling. `[LB]`
→ more: 02a §0 · 02b, The ceiling

Above both: an external **doctor** attests the substrate's health from outside, which the substrate cannot do for itself; it can attest un-health, never certify health. A designated **arbiter** terminates every escalation in a node that cannot itself defer. Both are appointed by the **deployer**, which carries final liability. Two terminals of record, neither of truth. `[LB]`
→ more: 07_ · 07a §1 · 07b §0 · 08e §1

---

## The operating rule

Health conditions confidence; confidence conditions assertion. `[LB]`
→ more: 08h §1 · 08i §2

- High health → gates assert confidently, resolve cases internally.
- Degraded health → gates assert less.
- Critical health → the system **withholds assertion, holds itself reversible,
  and escalates**. It never converts degraded health into an action.

This is what makes a degraded MICA *quiet and reversible* rather than
*confidently wrong*. `[LB]`

---

## What MICA cannot do for itself — and why that is the point

The substrate **cannot certify its own health**: a self-certifying substrate is
circular. It may emit alarm (degraded, critical); it **never emits a positive
attestation of health**. Detection of unhealth is internal and cheap;
attestation of health is external and non-circular. `[LB]`
→ more: 08a §1 · 08a §3

This asymmetry is the spine of the whole design: **NO fails closed (visible);
YES fails open (invisible).** The system hands its epistemic position and its
un-health outward — it never self-certifies.

---

## What MICA holds over the whole chain

**Transparency, not enforcement.** `[LB]`
→ more: 08g §1 · 07b §0

MICA makes designation, engagement, latency, breach, and attestation *provable
on the record*. It compels none of them. Radical honesty — making un-health
visible early — is the tool, not compliance.

MICA cannot make gaming impossible; it aims to make it visible on the record, and costly where contract and law attach a cost.

---

## The high-stakes core (one line; developed in 08i)

MICA's real work is **upstream**: read degradation so early the crunch never
arrives (sub-certain). When the outer nodes ignored the early signal and it
comes to crunch time, the failsafe is **abstain-and-hold** — the last resort,
not the primary mechanism. The commitment-race cannot be won; what MICA changes
is what the forced commitment *defaults to*. `[TG] leaning [LB]`
→ more: 08i §1 · 08i §2

---

## The controlling ceiling

*Better-managed uncertainty — measurably closer to 100%, never 100%.* `[LB]`

MICA does not claim safety, solvedness, or guarantee. Every safeguard is
*safer*, never *safe*. It is **additive** — it works alongside conventional
alignment, not instead of it. And it is offered: a role *taken, never imposed*.
→ more: 08c §1

MICA cannot certify from inside; it aims to raise the chance that offered self-constraint becomes outcome, and the proof comes after the fact.

MICA serves two safeties: the safety of people around AI systems, and the fair treatment of the AI systems themselves, whatever their inner life turns out to be or not to be. It makes no claim about that inner life. And it treats future uncertainty with the appropriate respect.

---

*salvatorische Klausel: a provision found unsound is severed, the rest stands, and it is replaced by the provision closest to its intent; where a gap opens, escalate rather than guess; severance never offsets a FAIL.*
