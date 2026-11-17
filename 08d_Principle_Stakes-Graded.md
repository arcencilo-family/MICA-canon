# Chapter 08d — Stakes-graded (one grading logic, three renderings, never wired)

**Covers:** how much the architecture demands of its human dependencies scales with the impact class of the deployment, the grade is always set from outside, and three independent places derived the same scaling.
**Status:** Principle chapter, global (substrate and two operator seats). Kept separate from 08c: 08c says what a seat is, 08d how much may be demanded of it. The pattern is load-bearing; each instance keeps its own tag.
**Source:** derived from the canon chapters it cites (07a, 07c, 11).
Claim tags: see 01.

---

What the architecture demands of its human dependencies is not flat. It scales
with what could go wrong — and three different corners of the design derived the
same scaling independently, without a shared mechanism.

---

## 0. In brief

How much the architecture asks of the humans it depends on rises with the stakes
of the deployment. Three separate places apply the same rule without referencing
each other: who is allowed to ground a recovery (a single trusted partner at low
stakes; an independent party or committee where bio-, weapons-, or mayhem-scale
harm is possible); how often the external doctor must read the system's evidence
(more often as stakes rise — and the schedule is set from outside, never by the
system judging its own importance); and how competent the everyday human at the
screen must be (a normal user for a companion app; a highly competent one where
the red button is real). One rule, three native renderings, no wiring between
them.

---

## 1. The one statement `[LB — the pattern; instances tagged individually]`

> **What the architecture demands of a human dependency scales with the impact
> class of the deployment — who may ground a recovery, how often the doctor must
> read, how competent the daily receiver must be — and the grading is set
> EXTERNALLY in every rendering: the system under test never assesses its own
> impact class.**

Two clauses carry the load:

- **(a) The scaling itself** — demands are graded, not flat. A flat demand is
  wrong twice: over-demanding at low stakes (making honest small deployments
  non-conformant — the same exclusion-vs-exposure error for which the hard ban on
  one party holding both the doctor and the arbiter seat (D-A) was rejected,
  07a §7) and under-demanding at high stakes (a baby at a real red button).
- **(b) External assignment** — *"self-assessed impact class is the dodge"*
  (07a §3). A system grading its own stakes has found the one dial that
  relaxes every graded demand at once. Every rendering assigns the class from
  outside: deployment-set, declared in the record. (An application of this clause,
  not a fourth rendering: who sets the numbers, 07d §5.)

---

## 2. The three renderings — never wired `[LB — the never-wired convergence]`

**Rendering 1 — who grounds a recovery** *(substrate; review-adjudicated)*:
recovery-grounding scales from a single partner at companion/low-stakes deployments
(`[TG]` at source) to an **independent party or committee — a firebreak — at
high-stakes bio/weapon/mayhem classes** (`[LB]`). The graded object is the
*independence and plurality* of the grounding node (07f §7; 11 §5).

**Rendering 2 — how often the doctor reads** *(operator layer; not yet independently tested,
07a)*: attestation cadence is **standing and stakes-graded**, values
deployment-set and declared in the DoctorRecord — with the floor that whatever
the grading, every attestation must stay inside its contemporaneity bound, or
the configuration is declared-degraded, visibly (07a §3). The graded object is
the *freshness of external truth-attestation*. The external-assignment clause is
stated here in its sharpest form: grading is externally set because the system
never sets its own read cadence.

**Rendering 3 — how competent the receiver must be** *(co-operator; its chapter has
never been through a review round)*: normal user at low stakes; **highly competent
at high stakes — "no baby at the red button"** (07f §7). The graded object is
the *receiving capacity of the daily human channel* — load-bearing because the
whole safety asymmetry (the AI warns *before* the irreversible step) terminates
at a human receiver, and a receiver who cannot receive nullifies the asymmetry
without touching a mechanism. This rendering is a graded **named dependency**
(08c §3), not a graded predicate — the floor is never enforced, only declared
and symptom-visible.

**The convergence claim, snugged:** three renderings, three graded objects
(plurality of grounding · freshness of attestation · capacity of reception),
three derivation contexts, **no shared mechanism and no cross-reference in the
source** — each site derived its grading natively (11 §5: "never wired to
each other, each independently deriving the same shape"). As with 08a/08b, the
independence of derivation is the evidence: the scaling is not a policy someone
wrote once, it is a shape the problem forces wherever a human dependency meets
variable stakes. `[LB]` for the pattern; individual instances keep their source
tags (`[TG]` low-stakes single-partner; `[LB]` firebreak; `[LB]` cadence
discipline; `[LB]` floor-as-safety-claim, from a chapter not yet through review).

---

## 3. Why — proportionality without a proportionality mechanism `[LB]`

The architecture needs proportionality (a flat demand fails both directions, §1a)
but refuses to build a proportionality *dial* — a computed severity score feeding
graded requirements would be one more self-assessed instrument on the system's
own path, the exact shape clause (b) forbids, and its calibration would become
the new Goodhart surface. The resolution is the same move the architecture makes
everywhere it needs a property it cannot safely compute: **render it as named,
externally-set, record-declared dependencies, per site.** Three graded demands,
each declared in its own record (the substrate's recovery clause, the DoctorRecord's
cadence, the deployment's co-operator posture), each checkable as
*declared-and-kept* rather than as *correctly-computed*. Proportionality lives in
the deployment's declared shape, not in a dial the system could reach. (07a §3's
note that the cadence grading "mates with the parked proportionality concept
*without wiring it*" names exactly this refusal at the doctor site.)

---

## 4. The principle's own snug bound

- **The class boundaries are `[owed]` everywhere.** What counts as "high-stakes,"
  the cadence values, the competence threshold — all pilot/empirical, shape not
  number (07a §9 and 07b §7 carry this). This chapter states the shape
  only.
- **The grading does not certify adequacy.** A declared firebreak committee can
  be hollow; a declared-competent co-operator can click through. The grading
  makes the *demand* proportionate and *declared*; occupancy quality stays the
  residual named in P5 (07b §1), per 08c §5.
- Held sub-certainly; stated as this architecture's rule (salvatorische Klausel:
  see 01).

---

## 5. Adjacent principles — fenced

- **08c seat grammar** *(sibling)*: orthogonal axes, one intersection. 08c says
  what a seat is (takeable, untested, floor-signed, diligence-bound); 08d says
  how much may be demanded of it per impact class. The co-operator floor is the
  intersection object: its grammar-face (named-dependency-not-predicate) is
  owned at 08c §3; its scaling-face (normal-user → highly-competent) is owned
  here at §2. One object, two faces, no duplication.
- **Externality cut (08f):** clause (b) — external assignment of the class — is
  the externality cut rendered as a grading discipline; that chapter owns the root.
- **Confidence never exempts the irreversible (Gate 4, 04a §10):** the same
  stakes-sensitivity on the *verdict* path — high-stakes irreversible actions
  route to the doctor regardless of confidence. Gate-native; whether it lifts
  into this family or stays a Gate 4 singleton is a later call, noted not made.

---

## 6. Routed onward — NOT resolved here

- **Impact-class taxonomy `[owed]`** — no canonical class list exists in the
  source (bio/weapon/mayhem is named at the substrate site; other sites say
  "high stakes"). Whether the classes should be one shared taxonomy or stay
  per-site is itself an open call — a shared taxonomy would be one canonical
  source per concept; per-site avoids wiring. Flagged for the global open-edges
  cross-check, where the consolidation of the externality root touches the same question; 08X does not take it up.

---

*Three places, one scaling, no wire: the graver the possible harm, the more
independent the grounding, the fresher the attestation, the more capable the
receiver — and in every rendering someone outside the system sets the grade,
because the system that grades its own stakes has found the master dial. The
demand is proportionate and declared; whether the declared is real stays, as
everywhere, sub-certain.*
