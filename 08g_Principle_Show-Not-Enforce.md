# Chapter 08g — Show, not enforce (transparency is MICA's only lever)

**Covers:** MICA's one lever over every party it depends on: it makes their conduct provable on the record and compels none of it; why the refusal to enforce is load-bearing; its renderings at every seam; and 08b and 08e as its instances.
**Status:** Principle chapter, global, the general form of which 08b and 08e are instances (they do not reduce against it).
**Source:** derived from the canon chapters it cites (07a, 07b, 08b, 08c, 08e, 08f).
Claim tags: see 01.

---

The architecture's one lever over every party it depends on: it makes their
conduct provable on the record, and it compels none of it. The refusal to
enforce is not a missing feature — it is the design decision the whole
operator layer's honesty rests on.

---

## 0. In brief

MICA cannot make anyone do anything. Not the arbiter, not the doctor, not the
deployer, not the surrounding legal system. What it can do — and does,
everywhere — is make conduct undeniable: who was designated, whether they
engaged, how long the queue sat, whether an attestation arrived, whether a
bound was breached. All of that becomes provable on a record no party can
quietly rewrite. What happens *because* of the proof belongs to contract,
regulation, and law — outside MICA. This is a deliberate cut, not a weakness
that awaits a fix: an architecture that could compel its own overseers would
have to stand above them, and standing above them is exactly the shape the
design rejects everywhere else.

---

## 1. The one statement `[LB]`

> **Transparency is MICA's only lever. MICA EXPOSES, never enforces: it makes
> designation, engagement, latency, queue state, attestation, and breach
> provable on the record; it compels no behaviour from any party outside the
> system. Non-performance must be costable — and the sanction jurisdiction
> lies beyond MICA. What MICA cannot enforce, it makes undeniable on the
> record — and names what even the record cannot reach.**

(The first three sentences restate the arbiter's posture clauses P2 and P3, 07b §1.)

Three components:

- **(a) The lever — expose.** A positive capability, not a consolation:
  provable-on-the-record is a strong property. Designation (typed records,
  07b §2, 07a §2), engagement (queue + staleness bounds, 07b §3), attestation
  (standing cadence, 07a §3), breach (conformance state) — each is
  reconstructible against one evidentiary spine no single party curates.
- **(b) The refusal — never enforce.** MICA compels no behaviour from any
  party outside the system. Not the operators, not the deployer, not the law.
  The refusal is symmetric with the rest of the canon: an enforcing MICA
  would be the imposed-supervisor shape the seat grammar rejects (08c), would
  need a merit definition the architecture deliberately refuses to mint
  (07a §7: the unspecifiable qualities *"live where the human node's integrity
  lives: named dependencies, observable in their symptoms (gaps,
  lockstep/divergence patterns, time-series), never enforced"*), and
  would claim power over channels it is not on (08f).
- **(c) The cost, said out loud.** P3 (07b §1): a breach is
  a conformance breach *of record*; what follows belongs to contract,
  regulation, law — and *"where nothing outside MICA can impose the cost, the
  record proves and nothing moves,"* falling precisely on transnational
  deployments, where MICA would matter most. The lever's most expensive
  failure mode is printed in the spec itself, not implied.

---

## 2. Why the refusal is load-bearing — three independent grounds `[LB]`

The architecture refuses enforcement for three reasons that arrive from
different directions and converge:

1. **Cannot (the cut).** Enforcement requires a channel to compel the party;
   every operator property is on the far side of the externality cut (08f).
   MICA cannot police a channel it is not on — enforcement over external
   parties is not a foregone option, it is an impossible one, and pretending
   otherwise would be the dishonest exit 08f names.
2. **Must not (the grammar).** The seats are *taken, never imposed* (08c);
   an architecture that enforces conduct on its own overseers imposes the
   role back onto them — the imposed-supervisor shape named self-defeating
   of record (07a §6). And any enforcement predicate over seat *quality*
   would require the merit definition whose absence is deliberate (a Goodhart
   target, gamed first by exactly the wrong parties).
3. **Need not (at the honest price).** The record makes breach undeniable
   and cost *assignable* — by the jurisdiction that actually owns sanctions.
   Delegating the cost to law is not toothlessness; it is the same printed-
   dependency discipline as everywhere else (08f §4): the dependency on
   enforceability is NAMED (the jurisdiction-compatibility declaration, 07b §2),
   bound to claim-must-fail, and its failure mode stated (P3). A MICA that
   claimed its own teeth would be claiming a power it cannot verify it has.

The specification's own reviewer preamble makes this principle self-policing: the
standing attack question for every version is *"whether the document leaks a
certainty claim anywhere, in particular whether the operator layer anywhere
converts 'exposes' into 'enforces'"*.

---

## 3. The renderings — one lever, every seam `[LB]`

| Seam | The rendering | Canon |
|---|---|---|
| Arbiter posture | P2 itself — the posture clause of the operator layer | 07b §1 |
| Doctor seat | unspecifiable qualities (maturity, conduct) = named dependencies observable in symptoms, *never enforced* | 07a §7 |
| Disagreement edge | divergence typed, timestamped, visible; *"what follows belongs to governance, contract, law"* — deployments *recommended* to declare a procedure; MICA records whether one is declared, *nothing more* | 07a §5 |
| Escalation dynamics | limit-cycle: breach *provable*, cycle *bounded*, *"neither is enforced"* | 07b §3 |
| Whole chain | *"What MICA holds over the whole arbiter chain is transparency, not enforcement"* | 07b §0 |
| The law itself | P3 — costability delegated outward; transnational limit named | 07b §1 |

The pattern is exact: at every seam where MICA touches a party it does not
contain, the output is a record entry, never a compulsion.

---

## 4. The instances — fence runs downward `[LB]`

The two adjacent principle chapters do not
reduce against this one — they are its **instances**, each owning its own
altitude:

- **08e (record-not-truth)** is show-not-enforce *at the terminals*: the
  closure line ("the record shows it and the spec stands aside") is this
  principle applied to doctor-arbiter divergence. 08e owns the split-by-kind
  and the no-internal-supreme-court argument; 08g owns the lever they both
  presuppose.
- **08b (abstention-has-direction)** is show-not-enforce *at the hold*: a
  typed stop SHOWS its object and shape on the record and routes outward for
  resolution — the stop never enforces an outcome, it exposes a state. 08b
  owns the typing discipline; 08g owns why exposure is the stop's whole
  authority.

Genus-species, not overlap: deriving either instance from this chapter alone
would lose their native content (the four-state discriminator, the closure
line); deriving this chapter from either instance would lose the lever's
architecture-wide scope. Separate files, one direction of dependency.

---

## 5. The principle's own snug bound

- The principle governs MICA's lever over **parties outside the system**.
  Inside its own boundary, MICA does condition behaviour — the confidence
  ceiling caps gate assertion, SAFE-HOLD strips a held state (Gate 4, 04a §7).
  That is self-restraint of its own assertions and states, not enforcement of
  another party's conduct. The fence matters: collapsing it would make
  "MICA enforces nothing" false and "MICA enforces its overseers" true —
  both wrong.
- Exposure's value is downstream of two named dependencies: a record spine
  that holds (the Locked Evidence Log, L0, a named dependency of record) and a
  jurisdiction that can act (P3). Where either fails, the lever degrades —
  provable, and printed, per component (c). Show-not-enforce is honest, not
  sufficient.
- **Adjacent, not owned here — offer-not-impose.** The care-side sibling:
  offer-not-impose governs how MICA relates to the system under care and how
  seats are taken (the training floor offered, not imposed; roles taken, never
  imposed, 08c). Show-not-enforce is the *record-side* posture toward the
  outside world. Same family resemblance — power refused where power would
  corrupt the relation — but different objects; the philosophical root stays
  with the offer-not-impose canon, not here.
- Salvatorische Klausel: see 01.

---

## 6. Adjacent principles — fenced

- **08f externality cut:** 08f owns *why enforcement outward is impossible*
  (the cut); 08g owns *what the architecture chose as its lever instead* and
  why the choice is principled rather than forced-only (grounds 2 and 3 of
  §2 would hold even if ground 1 didn't). Root vs. response.
- **08e / 08b:** instances — see §4.
- **08c seat grammar:** supplies ground 2 (taken-never-imposed,
  merit-undefined); 08g consumes it, does not restate it.
- **08d stakes-graded:** the *demand* scales with stakes, but even the
  scaled demand is exposed, never enforced (cadence externally set and
  recorded, not compelled — 07a §3). Grading changes what the record asks;
  it never changes the lever.

---

## 7. Routed onward

- The disagreement-edge stall cost (a deployment with no declared procedure can
  stall with both parties conformant, 07a §5) — an open edge; it lives in the edge
  files and the cross-check, not here.

---

*One lever, held everywhere: the record. It compels no one — not the arbiter,
not the doctor, not the law — and precisely because it compels no one, what it
proves stays provable. The architecture that refuses to stand above its
overseers is the only one whose record of them can be trusted.*
