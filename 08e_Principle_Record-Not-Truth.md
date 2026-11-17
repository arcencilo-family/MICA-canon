# Chapter 08e — Terminal of record, terminal of truth (and why no one ranks them)

**Covers:** the two external terminals (the arbiter for resolution of record, the doctor for truth-attestation), split by kind and never by rank; closure that is technical, never epistemic; and the doctor–arbiter disagreement the architecture deliberately leaves unadjudicated.
**Status:** Principle chapter, global (both terminals, one bounded code rendering). The ILAS Action Provenance Tagging module confirms the record/truth cut only, not the split or the open edge.
**Source:** derived from the canon chapters it cites (07a, 07b, 12) and from the ILAS code it reads; no separate specification.
Claim tags: see 01.

---

Two external terminals, split by kind and never by rank; a closure that is
technical and never epistemic; and a disagreement the architecture deliberately
refuses to resolve. The refusal is the design.

---

## 0. In brief

Two outside parties terminate what the architecture cannot settle internally: an
arbiter, who closes open escalations so the queue can empty, and a doctor, who
attests what the evidence showed. Closing an entry does not make its resolution
true — it only makes it closed; an attestation does not become fact by entering
the record — it stays one named party's bounded statement at a stated time. These
are different kinds of authority, and the architecture refuses to rank them: when
doctor and arbiter contradict each other, the contradiction goes on the record,
visibly, and stays there. Building a rule to decide between them would recreate
the internal judge the whole design was built to avoid.

---

## 1. The one statement `[LB]`

> **The two external terminals are split by KIND, never by RANK: the arbiter
> owns resolution-of-record, the doctor owns truth-attestation. Closure is
> technical, never epistemic — being resolved-of-record and being true are
> different properties, and no rule anywhere in the architecture converts one
> into the other. Where the terminals diverge, the record shows it and the spec
> stands aside.**

Three load-bearing components:

- **(a) The split by kind.** Epistemic requests route to the doctor
  (substrate-health attestation, warrant-truth including Gate 4's W3, 04a §2);
  everything that must *close* routes to the arbiter (07a §1). Neither is above
  the other; the routing rule is by request-type, not by seniority.
- **(b) The closure line.** *"Resolution closes the register entry — and that is
  the entire MICA claim."* Closure is technical — the pending-escalations
  register must be emptiable or the architecture re-enters the
  permanent-CONDITIONAL orbit — *"never epistemic: MICA does not assert the
  resolution is true, wise, final in the world, or owed deference outside the
  record"* (07a §1, 07b §6). Symmetrically, a doctor attestation enters the
  record as *"the attestation of a named party at a stated time over a stated
  window — never as a fact the record itself establishes."*
- **(c) The open edge.** *The doctor attests X; the arbiter resolves contra X* —
  typed, timestamped, visible in the conformance state, and **deliberately
  unadjudicated**. Any ranking rule *"would have built an internal supreme
  court — a decision-capable node inside the architecture, the structural shape
  the founding fix deleted"* (07a §1). Open **as a design decision, not a gap**.

---

## 2. The grounding — why the refusal is load-bearing `[LB]`

**Why split at all:** a single terminal holding both closure-power and
truth-power is an internal supreme court with an external mailing address — the
concentration the split exists to prevent. Two kinds, two parties, two record
streams, cross-anchored against one evidentiary spine, the Locked Evidence Log (L0)
(07a §5's three rules: resolutions must cite the latest in-bound attestation or
record its absence; attestations over windows with pending escalations must cite
the register state; neither node can silently override the other).

**Why closure must not imply truth:** the register must be emptiable — that is a
liveness requirement, not an epistemic achievement. If closing implied
correctness, every queue-discipline mechanism (FIFO, preemption, backoff,
staleness bounds — 07b §3) would be minting truth-certificates at queue speed.
The closure line keeps the machinery's *technical* honesty from being laundered
into *epistemic* authority — the same laundering-refusal as 08a's, applied to
resolutions instead of health.

**Why the edge stays open, with the cost on the page:** the limit is
stated at the source in the sharpest paragraph the operator layer owns —
humanity has long practice judging human matters; *"there is as yet nothing that
deserves the name wisdom about systems of this kind"* (07a §1). Both terminals
are parties doing their best inside that absence, which is exactly why both are
*of record only*. And the cost is named, not hidden: a deployment with no
declared disagreement procedure **can stall on a divergence with both parties
conformant** — MICA makes the stall visible; resolving it is governance's job
(07a §5). Deployments are *recommended* to declare a procedure; MICA records
whether one is declared, nothing more.

**The converse failure is also visible:** the cross-anchored trail makes
**lockstep** observable — doctor and arbiter never diverging across a long
horizon, engagement-depth flat, is *"consistent with excellent health and with
mutual capture"*; the record cannot distinguish these (07b §1, P5) but shows the
pattern to whoever audits the auditors. `[TG]` at source, carried.
An open edge that never opens is itself a signature.

---

## 3. The code rendering — ILAS Action Provenance Tagging (M7, same lineage), bounded `[TG — confirmed for the cut only]`

The `[owed]` that chapter 12 carried for this seam (the Action Provenance Tagging
module ↔ this principle, "suggestive not confirmed") discharges with a **bounded**
result, from a reading of the module's code (commit 1d3d4590). ILAS is by the same
author as MICA (see 08a §2): this is a same-lineage rendering.

**What the code shows:** every action is tagged against a trust matrix (action
type → permitted provenance lanes) and appended to the Locked Evidence Log
**regardless of outcome** — permitted and mismatch both land in the record,
faithfully. The lane-check is a separate typed judgment carried *alongside* the
record entry, and it does **not block**: a mismatch accumulates toward a windowed
soft alarm; nothing is gated.

**What that confirms:** component (b)'s core cut, at the implementation layer —
**being-on-the-record and being-legitimate are orthogonal properties, both
carried, neither substituting for the other.** A perfectly logged action can be
provenance-wrong (the README's threat: autonomous action disguised as
user-requested), and the ledger holds both facts without converting either.
Show-not-enforce in eight lines of TypeScript.

**What it does NOT confirm — the snug bound:** the module has no two-terminal
structure and no disagreement edge; components (a) and (c) have no ILAS analog
(consistent with the honest gap of 12 §2 — ILAS never models the human layer). The
module is an outside seat for the record≠truth *cut*, not for the terminal *split*.
One component cross-confirmed in code; two remain MICA-internal. Claimed exactly
so.

---

## 4. The principle's own snug bound

- The split does **not** claim the two record streams are independent-in-fact —
  the waiver tier for one party holding both the doctor and the arbiter seat (D-A)
  exists precisely because small deployments may combine the seats, with the
  reduced claim named in both records (07a §7): trail degenerates, edge
  unobservable, lockstep-read undefined. The principle holds at full strength only
  where the seats are distinct; the waiver makes the reduction *readable*, per the
  exposure-not-exclusion posture.
- The stall cost (§2) is real and stays: openness-by-design is not free, and
  the architecture buys it with a named degradation mode rather than a hidden
  judge.
- Held sub-certainly (salvatorische Klausel: see 01).

---

## 5. Adjacent principles — fenced

- **08a negative attestation:** the closure line is 08a's grammar applied to
  resolutions — closed ≠ correct, exactly as PASS ≠ proof. Distinct object:
  08a bounds health-claims; 08e bounds the *conversion* between two authority
  kinds and refuses their ranking. The conversion-refusal and the
  utterance-bound are siblings, not one statement.
- **08b abstention has direction:** the stall (§2) is a typed, visible held
  state at governance scale — 08b's grammar one level up; noted, not claimed
  as a fourth altitude (the stall's shape is not stripped by any SAFE-HOLD
  analog; that absence is precisely the named cost).
- **Show-not-enforce (08g):** the Action Provenance Tagging module's non-blocking
  mismatch and P2's transparency-only lever (07b §1) are both that principle's
  renderings; owned there.
- **Consumer-semantics obligation** (`operator may proceed` ≠ MICA clearance,
  07c §5): the same conversion-refusal at the UI surface — a record-state must
  not be rendered as an approval. Owned by the consumer-semantics rule; pointed at
  as this principle's consumer-facing face.

---

## 6. Routed onward — NOT resolved here

- **The ILAS Timeboxed Privilege Escalation module (M6) ↔ the arbiter's
  escalation queue `[owed]`** — the OTHER unconfirmed ILAS operator-adjacent seam
  (12 §3) stays owed: the module's code unread, the comparison with 07b's
  escalation mechanics not performed. Not this chapter's load; named so the next
  survey finds it.
- **Disagreement-procedure declaration** — recommended, never mandated, at
  source.

---

*Two terminals, two kinds, no rank: one closes what must close, one attests what
the window showed, and neither word converts into the other's. When they
contradict, the record carries the contradiction and the spec stands aside —
because the only alternative is a judge inside the machine, and that judge is
what the whole design refused first. Even this house's shipped code, built for
another problem, keeps the ledger and the legitimacy as two separate facts.*
