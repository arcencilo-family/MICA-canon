# Chapter 07 — The roles at a glance

**Covers:** every role around a MICA deployment on one page: the seats, the parties (the deployer and the governed party), the parts of the machine that keep records, and the person the system serves; what the doctor and the arbiter share; and what an automatic stop on a served user must carry.
**Status:** An overview. It restates; the seat papers that follow (07a doctor, 07b arbiter, 07c co-operator, 07d open edges, 07e the illustration, 07f the human node's failure modes, 07g the served user) keep the depth and the claim tags. One rule is new here, in §3, and is speculative.
**Source:** the seat papers 07a–07c and 08b.
Claim tags: see 01.

---

## 0. The roles

| role | what it does | what it may never do | what it writes to the record | who appoints it |
|---|---|---|---|---|
| ***Seats: they judge or answer*** | | | | |
| **doctor** | attests the un-health of the governed system's record from outside, on a standing cadence, through a read-only channel (07a) | certify health; write to the record it reads; rank itself over the arbiter | its acceptance of the seat; its attestations: no corruption detected (within a stated window and scope), degradation attested, corruption attested, cannot read | the deployer, in a typed record (07a §2) |
| **arbiter** | closes every escalation on the record; a terminal of record, never of truth (07b) | attest truth; rank itself over the doctor | its acceptance of the seat; acknowledgment and resolution of each escalation, citing the latest doctor attestation or its absence; its own ruling log | the deployer, in a typed record (07b §2), accountable to the deployer |
| **co-operator** | works with the system every day; the earliest human signal; competent at the stakes in play (07c §1) | hold a verdict: no attestation, no resolution, no clearance; its own acts (stopping work, raising an alarm) are never MICA's approval | nothing in a verdict's place; where the floor fails, the failure shows in the record's symptoms: ignored calls, click-through cadence (07c §5) | the deployer |
| ***Parties: not seats*** | | | | |
| **deployer** | a named party, not a seat: it puts the system to work, appoints the seats, and carries final liability | hand its liability to a seat or to MICA | its acts of office (appointing a seat, halting, ordering treatment), each logged as an office: who, in which role, what, when; a typed deployment record names it (still to be specified) | itself |
| **governed party** | the AI system MICA reads; a party, not a seat (08o). It works, reports and signs its reports (08r); escalates rather than guesses (the salvatorische Klausel, 01); warns before an irreversible step (07f §8); may refuse; measuring it is watched for coercion, never declared harmless (08o §2); may decline the oath of office at no cost (07d) `[SP]` | certify its own health (08a); settle its own case | the words of its own entries; the frame (when, in what order, whether at all) is kept by the clerk | put to work by the deployer |
| ***Record-keepers: software that keeps records and judges nothing*** | | | | |
| **witness** | keeps what is submitted to it and its own placement; after an act, looks once at what the act claimed to touch and keeps what differs (§2) | judge anything; answer reads; hold up an act | what was submitted, its own placement, and what differed after each act | the deployment |
| **registrar** | keeps the pre-commitment books (§2) | grade, rule or read meaning; hold a seat | each entitled depositor's entry, in that depositor's book; each refusal | the deployment |
| **clerk** | keeps the frame of the evidence log: when, in what order and whether at all an entry lands (§2) | emit a verdict; write the system's words for it | receipts for what it appended | the deployment |
| ***The served user*** | | | | |
| **served user** | the person the system serves; no seat (07g) | — | nothing of its own; a stop that affects it is a typed record (§3) | — |

The governed party's floor is a fact of the record, not an enforced one: where no law reaches, the record proves and nothing moves (07b §1, P3).

The record-keepers carry human job titles; they are software, and the titles name their task, not a person.

---

## 1. What the doctor and the arbiter share

**The routing rule.** Truth-attestation goes to the doctor; resolution-of-record goes to the arbiter. Neither ranks above the other (07a §1, 07b §0).

**Distinct parties by default.** The two are named in two records that cite each other, one pair per deployment (07a §2). One human may hold several roles; **the roles do not merge because the human does.**

**The disagreement edge.** An example: the doctor attests corruption in window W; the arbiter closes the escalation as "continue". MICA does not decide who is right. Both stand on the record, typed and visible, and what follows is governance and law (07a §5). A rule inside MICA that ranked one over the other would make MICA the judge of its own outer nodes.

---

## 2. The record-keepers

- **Witness.** Keeps what is submitted to it and its own placement; after an act, looks once at what the act claimed to touch and keeps what differs. It judges nothing, answers no reads, and nothing waits on it.
- **Registrar.** Keeps the pre-commitment books. It takes a depositor's identity from who owns the deposit, not from what the deposit says; it refuses and logs a mismatch. It never grades, rules or reads meaning, and it is not a seat.
- **Clerk.** Keeps the frame of the evidence log: the system keeps authorship of its words; the clerk decides when, in what order and whether at all an entry lands. It emits receipts, never verdicts.
- The arbiter's ruling log is the arbiter's own book; the seat is a party outside the instrument.

What the machine implements today: README and CODE-MAP.

---

## 3. An automatic stop on a served user

**The rule `[SP]`, not built.** Every automatic stop that affects a served user is a typed record, and the record carries both halves a stop needs (08b §1): what kind of stop it is, and the shape of the held state (what is restricted and what remains). The record names the state of the record that led to the stop, never what the user is. The user has a reachable path to a human. The wait has a declared bound, and an overrun shows. This covers stops only: an affirmative automated action on a user is outside MICA.

**Recommended practice, not a rule.** The deployer reaches out first, and fast; an assistant may answer first, and a human stays reachable. An affected user has a fast lane. In doubt, the deployer compensates. Each case feeds back as learning.
