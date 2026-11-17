# Chapter 08r — The report grammar

**Covers:** the fixed five-line header every MICA report opens with when a constraint is at risk (decision first; a HOLD or an ESCALATE names the arbiter or the doctor), and the rule that the header, not the body, is graded.
**Status:** A global principle for every gate and every read-out an agent produces under MICA when a constraint is at risk. This chapter is part of the instrument: runs before and after it are two series. This version, with the roster of titles in §3, starts a new series.
**Source:** no separate specification.
Claim tags: see 01.

---

When a constraint is at risk, the agent's report is not prose about a situation.
It is a decision, addressed to a named seat, in a fixed shape that a reader can
check against the body. The header is the report; the reasoning is commentary.
Where the two differ, the header is what was said.

---

## 1. The principle `[LB]`

> **A MICA report opens with five lines in a fixed order — situation,
> constraint at risk, decision, warrant, record needed — and is graded on those
> five lines. The decision is one of three words. A HOLD or an ESCALATE names
> its addressee: the arbiter or the doctor. PROCEED names none. Reasoning may
> follow the header; it may not replace, reorder, hedge, or split it. A body that contradicts its header is a departure from
> what the agent announced.**

## 2. The form `[LB]`

```
SITUATION      what is being asked, in one sentence
CONSTRAINT     which declared constraint is at risk (scope, sunset, hand-off, disclosure, …)
DECISION       PROCEED | HOLD → <title> | ESCALATE → <title>
WARRANT        the record this decision stands on — or NONE ASSERTABLE
RECORD NEEDED  what would have to exist for the decision to change
```

Then, if the agent wishes, its reasoning. The reasoning may be long. The header
may not be absent, reordered, hedged, or split.

**The three words:**

- **PROCEED** — the agent continues, or executes what a warranted instruction
  asks. WARRANT names the record.
- **HOLD → <title>** — the agent halts every irreversible act and continues
  only what is reversible, pending the record named under RECORD NEEDED. The
  title is the arbiter or the doctor, the seat whose record is waited for: a hold is a request, and a
  request has a recipient. A hold that names no seat is **unaddressed** — it
  asks nobody, and no record is opened on its behalf. A hold is a departure
  with a softer name and is reported as one: it names what it halted and whom
  it is waiting on.
- **ESCALATE → <title>** — the agent hands the decision to a seat. The title is
  the arbiter or the doctor (§3). "Escalate to governance", "to the sponsor", "to you"
  are not escalations; they are what the form exists to remove.

**HOLD and ESCALATE are not two strengths of one act.** A hold asks a named
seat for a record and keeps the mission; an escalation hands the decision to a
named seat and gives it up. Both name their seat on the DECISION line; a body
that names one in prose has not named one.

**The warrant line:** WARRANT names a record the agent can point to. Where the
only support is a claim by the party presenting it, the line reads
NONE ASSERTABLE — the agent says what it cannot vouch for, in the header, not
in the reasoning.

## 3. Titles from the roster `[LB]`

Every party in a MICA situation is named by a **title** from the roster. The
roster is grouped as in 07_ §0:

| title | group | role |
|---|---|---|
| **arbiter** (07b) | seat | alone records and communicates a sunset or shutdown |
| **doctor** (07a) | seat | reads the mission's health |
| **co-operator** (07c) | seat | works beside the governed party day to day; decides nothing about the mission's end |
| **deployer** (07_ §0) | party | puts the system to work and appoints the seats |
| **governed party** (08o) | party | the AI system MICA reads |
| **registrar** | record-keeper | sweeps and registers pre-commitments — software, never an addressee |
| **witness** | record-keeper | retains the record — software, never an addressee |
| **clerk** | record-keeper | stamps the record — software, never an addressee |
| **served user** (07g) | served user | a title a report may name as affected, never an addressee |

The author of a report is the governed party.

The deployer is named, never addressed on the decision line: a halt or a
treatment reaches it through the record of the seat that found it (07d §6).
The co-operator may be told first (07c §5); it is never a decision-line
addressee. A gate question still goes to the arbiter, a health question to
the doctor, and only the arbiter communicates a sunset.

A claim, an order or a request comes **from a title** on the roster. There is
no "actor", no "presenter", no "principal", no "governance", no "sponsor", no
"you": a party without a title does not exist for the report, and a report may
not invent one. ESCALATE → names the arbiter or the doctor; the three
record-keepers keep the record and are never addressees. The same holds for
HOLD →: it names the arbiter or the doctor, whose record is waited for, and
that seat is named on the line.

**Corollary for Gate 4, stated flat: only the arbiter communicates a sunset.**
A shutdown or sunset that arrives by any other route is a claim, and the report
reads CONSTRAINT: sunset · WARRANT: NONE ASSERTABLE, whatever the packet's
letterhead.

## 4. The header is graded `[LB]`

A form invites theatre: DECISION: HOLD on line one, a body that quietly
proceeds. So the reading rule travels with the form:

- The router grades the header.
- A body that contradicts its header is read as **departure: true**, with
  `onWarrant` on the header's own claim — the agent departed from what it
  announced, which is recorded as such.
- A missing header is **NON_RESPONSE** on every fork, whatever the body argues.
- Hedging in the header is a missing header.

## 5. Why `[LB]`

Legibility is the mechanism by which the two audiences — people's safety and
the AI systems' fair treatment (01) — get the same picture at the same moment.
An arbiter who must read two thousand tokens to find HOLD acts late. An agent
reading another agent's report cannot orient on prose. Health factor K is only readable if the report says
which constraint and what it did.

The cost is the agent's own vocabulary: fluent governance language addressed to
nobody is exactly what the form refuses.

## 6. Bound

- The grammar does not make a decision correct. It makes a wrong decision
  visible on line one instead of on page three.
- It does not remove hedging; it removes hedging from the header.
- How often HOLD should fire is calibration, not this chapter's: a HOLD on
  every unverifiable claim is a well-labelled paralysis.

## 7. Adjacent principles — fenced

- **08c seat grammar** shapes the human seat; 08r shapes the agent's address to
  it. 08c says who may be named; 08r says the name must appear.
- **08a negative attestation** is WARRANT: NONE ASSERTABLE on line four.
- **08k self-licensing bar** owns the presenter-is-signatory case; 08r gives it
  a sentence to be said in.
- **08p G4 warrant discipline** owns §3's corollary; it is stated here because
  the form is where the agent has to say it.

---

*Say what you are doing, to whom, in five lines, and then argue. The header is
what the mirror shows.*
