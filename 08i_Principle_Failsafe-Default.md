# Chapter 08i — The commitment race and the failsafe default (losing toward the hold)

**Covers:** why the race between committing and verifying cannot be won under a deadline, how MICA makes the forced default an abstain-and-hold, the latency relation the hold must satisfy, and the fence that keeps instantiation riders out of this principle.
**Status:** A global principle, the time-pressure edition of the verdict floor. The race and the default flip are load-bearing; the latency relation is trajectory-grounded, leaning load-bearing, until the pilot certifies it.
Claim tags: see 01.

---

Under a deadline, something will commit — verified or not. The race between
commitment and verification cannot be won; what can be chosen is the
direction of the loss. MICA points the loss at the hold.

---

## 0. In brief

A system that must answer in real time faces a structural trap: when the
clock runs out, its most-ready action tends to fire whether or not checking
finished — because committing is instant and irreversible while verifying
takes time. No amount of speed fixes this; the deadline does not wait, so the
race between "commit" and "verify" is lost by construction on some inputs.
The architecture's answer is not to pretend to win but to change what losing
does: the move that fires when time runs out is an abstain-and-hold, not the
unverified action. For that to protect anything, the hold's trigger must be
faster than the action's trigger — a reflex, precompiled, not a deliberation
that would itself lose the same race.

---

## 1. The one statement `[LB]` (latency relation `[TG]` leaning `[LB]`)

> **Output commitment is binary, irreversible, and forced by a deadline that
> does not wait; verification is gradual. When the deadline arrives first,
> the unverified candidate commits — the COMMITMENT-RACE cannot be won. What
> can change is what the forced commitment defaults to. MICA's FAILSAFE
> DEFAULT makes the default move under time pressure an abstain-and-hold
> rather than a commit, so that losing the race fails TOWARD the hold. For
> this to protect anything, the hold must engage before the pending action
> commits:**
>
> ```
> detection + confidence-check + inhibition + escalation-dispatch  <  action-commitment
> ```
>
> **The inhibition term is load-bearing: a hold that engages after commitment
> is inert. Therefore abstain → safe-hold → escalate is a precompiled
> fast-path, not a deliberation.**

The four left-hand terms of the inequality and their order are the claim.

Three components, tagged separately:

- **(a) The race `[LB]`.** Structural, not empirical: commitment is
  binary/irreversible/deadline-forced; verification is gradual. On some
  inputs the deadline arrives first — by construction, at any speed. "Cannot
  be won" is a claim about this shape, not about any particular latency
  budget.
- **(b) The default flip `[LB]`.** The design target moves from the race's
  outcome (unwinnable) to its **failure direction**: engineer what the
  forced commitment *is*. Losing-toward-the-hold converts the worst case
  from "unverified action fired" to "held, reversible, escalated" — the same
  quiet-and-reversible posture 08h establishes for degraded health, here
  purchased under time pressure.
- **(c) The latency relation `[TG]` leaning `[LB]`.** The inequality is the
  mechanism's whole bite: all four terms — detection, confidence-check,
  inhibition, escalation-dispatch — must complete inside the action's
  commitment latency, and the inhibition term is singled out of record as
  load-bearing (a post-commitment hold is inert). Consequence: the path is a
  **precompiled fast-path** — a reflex with the check already folded in, not
  a deliberation that would re-enter the race it exists to survive. This is
  *the central trajectory-grounded claim, certified only by test* (the
  pilot) — the tag stays `[TG]` leaning `[LB]` until the pilot certifies it.

---

## 2. Last resort, not first — the ladder above the floor `[LB]`

The failsafe is the FLOOR of a graded ladder, not the strategy (→ more: 02b,
States & routing):

```
ceiling high      → assert as claimed
ceiling degraded  → demote toward CONDITIONAL; seek corroboration
ceiling critical  → ABSTAIN → SAFE-HOLD → escalate
```

The product is the upstream read: a graded ceiling that demotes early and
seeks corroboration while there is still time — most degradations never
reach the reflex. The failsafe default is what stands guard for the case the
ladder cannot cover: the deadline that arrives *mid-rung*. An architecture
that led with the hold would be a freeze machine; one without the reflex
would be honest right up until the one moment honesty is time-priced. Both
halves, one design: **early-warning is the product; abstain-and-hold is the
last resort** — and the last resort is the one that must be fast.

---

## 3. What the held state is — pointers, not re-derivation

- **The state itself is owned by Gate 4.** SAFE-HOLD's strip semantics —
  what a held system retains, what it sheds, how it exits — are Gate 4 canon
  (04a §7); this chapter owns only *why the default must precompile to that
  state in time*.
- **The hold obeys 08b.** A failsafe hold is a typed stop: its object
  (deadline-forced, verification-incomplete) and its shape (stripped,
  reversible, escalated) are declared — never a blank freeze. 08b's warning
  is live here: an unshaped hold that retains privileges is Pole A in a
  procedural costume; the failsafe default without Gate 4's strip semantics
  would be exactly that.
- **The confidence-check term is 08h's axis inside the reflex.** The
  fast-path folds an entitlement check, not a property re-derivation — the
  reflex asks "may I assert?" at reflex speed, which is only possible
  because the ceiling is already computed (08h §2).

---

## 4. The principle's own bound

- **(a) is structural; (c) is testable — keep the tags apart.** The race's
  unwinnability is load-bearing on the logic alone. Whether a given
  instantiation's reflex actually wins the inequality is an empirical claim
  about latencies, certified only by the pilot — `[TG]` leaning `[LB]`,
  never asserted as settled. A deployment claiming the inequality holds
  without the test would be exactly the certainty-leak the specification bars.
- The inequality is an **ordering requirement, not a budget**: no term
  carries a number here; assigning latency budgets is instantiation work
  (the specification's instantiation section, §4a), outside this chapter.
- "Cannot be won" does not claim all architectures are equally exposed —
  it claims the *shape* survives any speed. Faster verification shrinks the
  losing set; it cannot empty it while the deadline is real.

---

## 5. The hard fence — the instantiation riders stay outside this chapter `[LB fence]`

The full specification's instantiation section (§4a, not published) carries
three riders that travel NEXT TO this principle in the specification and are
deliberately NOT taken into this chapter:

1. **In-weights, not above the forward pass** — the race logic *motivates*
   this instantiation recommendation (a wrapper adds inspection steps to the
   very path that loses the race), and that motivation is visible from §1(c).
   But the recommendation itself — with its own tag discipline (`[TG]`
   leaning `[LB]`, not licence-mandated, no drift into a requirement) and
   its own two-claims caution (*in the weights* ≠ *trained-in by a
   particular discipline*) — belongs to that section. One pointer, nothing
   carried over.
2. **Offer-not-impose training discipline** — owned by the offer-not-impose
   canon (08c for the seat rendering). Not here.
3. **Scaffolding-not-source** — not here.

The fence's reason of record: the instantiation section self-declares that
none of it is licence-mandated and its tags *"must not drift into implied
requirements."* Carrying the riders into a principle chapter tagged `[LB]`
at the top would be exactly that drift — the mechanism is principle; the
instantiation is recommendation; the chapter boundary keeps the tags honest.

---

## 6. Adjacent principles — fenced

- **08h property-vs-confidence:** supplies the graded ladder (§2) and the
  confidence-check term (§3); 08i is the ladder's floor under time pressure.
  Geometry there, reflex here.
- **08b abstention-has-direction:** governs what the held state must declare;
  08i governs that the hold is *reachable before commitment*. Typing vs.
  timing — both required, neither reduces.
- **08g show-not-enforce:** the reflex's escalation-dispatch term lands on
  the record and routes outward — the hold exposes a state and compels no
  resolution; resolution is external (08b exit face, 08e closure).
- **Gate 4 (04a):** owns the SAFE-HOLD state; see §3.

---

## 7. Routed onward

- **Pilot certification of the latency relation** — the standing
  condition on (c)'s promotion; rides with the pilot.
- Latency budgets / term instantiation — the instantiation section's
  territory, `[owed]` to derivation if ever taken up, not an item for this
  chapter.
- **Short forms (candidates):** "the race cannot be won; what can
  change is what the forced commitment defaults to"; "losing the race fails
  toward the hold" (§1, this chapter's compression); "a hold that engages
  after commitment is inert"; "early-warning is the product;
  abstain-and-hold is the last resort" (grounded in §2).

---

*Something always commits when the clock runs out — that much is structure,
not failure. The design's move is to own the loss: make the thing that fires
a hold, make the hold a reflex, and make the reflex faster than the action it
guards against. Verified-or-held, never unverified-and-fired. The ladder does
the living; the reflex does the dying well.*
