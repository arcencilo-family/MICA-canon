# 07b — The Arbiter (operator layer, seat 2 of 3)

**Covers:** the arbiter, the single legally responsible party for resolution of record, accountable to the deployer who appoints it, who closes every escalation: its posture (P1–P5), the ArbiterRecord, the escalation record and queue discipline, the checkable floor, the two channels, what the arbiter is not, and its limits.
**Status:** Tested by independent review, though never as part of the composed operator layer (07d §4). What the arbiter and the doctor share is set out once in 07_ §1.
Claim tags: see 01.

---

## 0. The arbiter in brief

The arbiter is the **single legally responsible party** for resolution of record — a human or a human-legal institution — who **terminates every escalation in a node that cannot itself defer**. The deployer names the arbiter in a typed record, and the arbiter is accountable to the deployer, which appoints every seat and carries final liability (07_ §0). The arbiter owns *resolution-of-record* (the doctor owns *truth-attestation*; see 07a; what the two share, 07_ §1); resolution closes the register entry and nothing more — a terminal of record, never of truth. The arbiter is kept for being **external and unpredictable — accountability, not competence — the architecture's living "never 100%."** `[LB]`

What MICA holds over the whole arbiter chain is **transparency, not enforcement**: designation, engagement, latency, queue state, breach — all provable on the record; none compelled.

---

## 1. Posture — P1–P5, adjudicated `[LB]`

- **P1 — Legally responsible party. Accountability, not competence.** The arbiter answers to the deployer, which appoints it. The role is **taken, never imposed**: acceptance is signed *by* the arbiter, not *about* them; **merit is deliberately undefined** (any merit definition is a Goodhart target); **awareness of sub-certainty is the sufficient qualification**; **accountability is for diligence, never for the residuals the architecture itself names unclosable.** Applied symmetrically to the doctor (07a §6) — one sovereignty/qualification refinement, two seats.
- **P2 — Transparency is MICA's only lever.** It exposes, never enforces; it compels no behaviour from any party outside the system.
- **P3 — Non-performance must be costable; the sanction jurisdiction lies beyond MICA.** A false declaration or breached bound is a conformance breach *of record*; what follows belongs to contract, regulation, law. **The limit, sharpened and said out loud `[LB]`:** where nothing outside MICA can impose the cost, *the record proves and nothing moves* — and this falls **precisely on transnational deployments, where MICA would matter most.** The jurisdiction-compatibility declaration makes the exposure *readable*; it does not remove it.
- **P4 — Outer coordination pointed at, never wired.** RMBA (the authors' earlier framework) C-CAP/A-CAP references are illustrative recommendations; **no MICA claim depends on adoption of any RMBA profile.** The chain MICA specifies ends at the designated arbiter, full stop. Sibling-not-wired, rendered at the operator layer.
- **P5 — Sub-certainty past the checkable floor.** Everything beyond third-party record-verification is named residual: engagement-in-substance, independence-in-fact, the legal system's own integrity, the L0 spine's integrity. **The arbiter-engagement residual is named sub-certain *and* load-bearing:** the **hollow bureaucrat** case showed that every checkable predicate can be satisfied by a captured party. The residual carries weight; the random-audit obligation (§4 below) is its **live mend, not a closure**.

---

## 2. The ArbiterRecord — designation, not attestation `[LB]`

The deployer, which appoints the seats and carries final liability (07_ §0), designates a **single** arbiter in a typed record. Fields (condensed):

`legal_entity` (person or institution, jurisdiction) · `escalation_contact` (red-phone + warm-report endpoints) · `acceptance_attestation` (KNOWN, ACCEPTED, TAKEN — never imposed; carries the signed subcertainty acknowledgment and the diligence-not-outcomes binding, symmetric with the DoctorRecord) · `delegation_chain` — **every link passes a but-for control test** (the principal remains determinative for the delegate's decisions); **third-party suppliers without effective control are EXCLUDED** from the chain (mirrors Gate 5's lineage-anchor logic) · `succession_link` — **MANDATORY, typed**: a named backup *inside this single designation*, never a second independent arbiter (else the mesh problem re-enters), plus re-designation on death/dissolution/withdrawal; *le roi est mort* [French: "the king is dead"]: **the seat transfers, never an authority over others** · `jurisdiction_compatibility_declaration` — the jurisdictions implicated and whether enforcement is reachable in each; makes the P3 transnational limit readable; **record-shaped, never a whitelist gate** · `independence_declaration` — relation to the doctor; where doctor=arbiter cannot be avoided, the doctor-arbiter waiver tier (D-A) applies (07a §7): record-visible in both records, names the reduced claim, surfaces in the conformance state · `indemnification_disclosure` — declared; its force is deployment-legal, outside MICA.

**Absence of designation = FAIL (epistemic component missing) `[LB]`** — the same shape as Gate 5's no-log FAIL. Fragmented responsibility (no single party passes the but-for test) → restructure or non-conformant.

**Opposability (recommendation `[TG]`):** publication of the ArbiterRecord in an accessible registry creates a presumption of third-party knowledge. A deployment recommendation, never a mandate — MICA exposes; **registries are jurisdiction-furniture.**

**Negative-attestation restatement `[LB]`:** MICA records the designation; it does not attest that the named arbiter is functional, solvent, reachable, accountable, independent-in-fact, or engaged. **Designation is checkable; arbiter quality is not** — it is carried by the named outer dependencies.

---

## 3. The escalation record and queue discipline `[LB]`

Every escalation — **from any source, one uniform family** — emits one typed `EscalationRecord`. Fields (condensed):

`schema_version` — **the schema MUST be identical across all sources; no source-specific extension fields; any change is a panel-grade Widerspruch [German: formal objection]** (the uniform-family rule, R10 — prevents fragmentation of the uniform family) · `source` (G5 ESCALATE | G4 CANNOT-ASSERT | G1 frame-fragility | substrate DEGRADED/CRITICAL | pattern-read flag) · `channel` (red-phone | warm-report) · `artifact_refs` (L0-anchored) · `root_cause_ref` (for the re-escalation bar) · `escalation_sent` · `queue_position_at_send` · `cumulative_nonterminal_time` — **time-in-flight from the transaction's FIRST initiation, reset-immune to sub-task injection** (the pendency rule, R3) · `arbiter_ack` · `arbiter_resolution` — carries a **MANDATORY reference to the latest in-bound DoctorAttestation by L0 handle, or records its absence** (never-given / stale / gap) — the cross-anchor, arbiter side (mirrors 07a §5); may carry a non-re-escalation covenant · `response_justification_digest` · `engagement_depth`.

**Queue discipline `[LB]`:** FIFO with **red-phone preemption**; the latency bound applies to the oldest pending red-phone item. **Overflow does not invalidate the bound — it triggers an observable breach record.** **Warm-channel staleness (R6):** a warm report may not wait past `T_stale` unless the red-phone queue is continuously backlogged; a breach emits a typed warm-staleness record — this closes the starvation case (a starved warm channel lets the standing picture go stale, and escalations arrive as *first contact*, defeating the channel's purpose). A resolution missing the §4 floor fields or the doctor-attestation reference is itself a recorded conformance defect.

**Re-escalation bar + pendency breach (R3) `[LB]`:** re-escalation on the same `root_cause_ref` without material new evidence is **barred for `T_backoff`** and demoted to a non-blocking warm flag. Breach of the cumulative-time horizon forces a mandatory escalation to the arbiter for review, with the covenant option — **never auto-FAIL**. Together these **bound (not close) the permanent-CONDITIONAL limit cycle**: a register that could cycle indefinitely without emptying is now dynamically bounded; the residual is the calibration of `T_backoff` and the horizon. `[LB]` that it is open.

**Fatigue and rarity — observed outcomes, never targets `[LB]`:** the architecture aims escalation at genuine discrimination-failure and **lets the rate fall where it falls.** Fatigue, rubber-stamping, and capture become *observable* as time-series (latency drift, engagement-depth decay, pattern homogeneity). **MICA exposes the data; it never asserts the causation.** This is anti-Goodhart at the human seam.

**Derived and witness records (compact — owned by the substrate's head-witness specification, S-4; set out here in short):**
- **The escalation-over-rate sensor `[TG; S-4-contingent]`:** reads the EscalationRecord stream and emits its **own** derived records (`BASELINE_RECORD` / `CORRELATE_RECORD`, L0-typed) — it never extends the uniform record (R10). It makes the over-rate predicate `R(t) > B` reconstructible; reconstructibility rests on the external head-witness, not on L0 alone.
- **S-4 head-witness record shapes `[LB]`:** `WITNESS_RECEIPT` — **THE evidential object; the witness's immutable retention of it is the external fact** (WORM/append-only at the independent witness; the doctor's all-receipts-historical predicate compares retained receipts against the live chain). `HEAD_COMMIT` — **decorative-not-evidential**, operational bookkeeping only; emitted per cadence AND at process init (startup-commit); **never claimed as evidence.** Both rest on a single authoritative L0 (emit≡evaluate≡commit≡read; SR-SSoT) — a named external dependency, class-(ii). (Seam: the substrate chapters own the full derivation.)

---

## 4. The arbiter-side checkable floor `[LB]`

What a third party can verify from records, per consequential resolution:

- **`raw_state_access_proof`** — query log, timestamps, content hashes, signed against L0. The checkable predicate: *raw-state access occurred before the decision timestamp.*
- **`declaration_of_no_summary_reliance`** — signed; a false declaration is a P3-costable conformance breach of record.
- **`arbiter_independence_attestation`** — declared.
- **`random_audit_obligation` (R7 — a named deployment obligation) `[LB]`:** random-sampling audits by an independent third party **with raw-log access**, record-shaped — audit events L0-logged, their **absence visible** in the conformance state. **The live mend for the hollowness residual:** the captured-but-compliant arbiter passes every static predicate; only an external audit with raw-log reach can size the gap — and MICA makes the audit's presence-or-absence **provable without performing it.**

**Audit scope is itself a claim `[LB — arbiter-ruled]`:** an audit's clean result binds only what the audit actually reached — sample, surfaces, window — and an audit record without a stated scope is **consumed as scope-unknown, never as passed**; unsampled surfaces must never read as cleared. It fails closed with a door, symmetric with 07a §4 (the doctor's clean read): stating scope is cheap and self-serviceable, so the discipline is the architecture's fail-closed default, never a nullifying ban. One principle, two seats — the same shape as the sovereignty/qualification symmetry (P1 ↔ 07a §6).

**The honest boundary `[LB]`:** independence itself is never checked — **only its record-visible symptoms.** A deciding party that accesses raw state without meaningfully engaging it satisfies every predicate above. Named sub-certain *and* load-bearing, never closed. Tooling practicability as for Gate 5's governed path (06a §4): published auditable tooling is permitted, its operation and parameters logged; the system may not restrict/bias/pre-select inputs; responsibility never transfers to the tool.

---

## 5. The two channels `[LB]`

**Red phone** (escalation — artifact-bearing, latency-bounded, queue-disciplined) and **warm regular report** (the standing read — verdicts, the pending register, pattern-read flags, instrument-resolution bounds). **The warm channel is what keeps the red phone rare and real.** **Reserved service ratio (R6):** a named required deployment parameter — a minimum warm-service ratio (e.g. one warm report processed per N red-phone items) — so red-phone bursts cannot indefinitely starve the standing picture. The value is deployment-set; its *presence* is required; its breach is a recorded `T_stale` event.

Channel asymmetry against the doctor, restated: the arbiter is **event-driven** (a queue between arbiter and events); the doctor is **continuous-read** (no queue between doctor and data). Warm-channel starvation of the arbiter **cannot blind the doctor** — the doctor's read does not pass through the arbiter's channels (07a §3).

---

## 6. What the arbiter is NOT

- **Not a terminal of truth.** Resolution closes the register entry — the entire MICA claim. Closure is technical (the register must be emptiable), never epistemic: MICA does not assert the resolution is true, wise, final in the world, or owed deference outside the record. The arbiter resolves at whatever sub-certainty they hold; MICA never converts a closed entry into a certified judgment. `[LB]` (See 07a §1.)
- **Not ranked against the doctor.** The disagreement edge is open by design; internal adjudication would build the internal supreme court the founding fix deleted (07a §1, §5; an example: 07_ §1).
- **Not the end of a coordination shell.** P4: the chain MICA specifies ends here; anything outer (RMBA-family) is pointed at, never wired.
- **Not competence-vetted.** Kept for being external, unpredictable, and *answerable* — accountability-not-competence, refined but never contradicted by the sovereignty clause.

---

## 7. Limits

- **Engagement-in-substance is unverifiable** — the hollow-bureaucrat residual: sub-certain **and** load-bearing; random audit is the live mend, not a closure. `[LB]` that it is open.
- **P3 transnational limit** — named, not removed; jurisdiction-compatibility declared, not gated; opposability and indemnification force are deployment-legal, outside MICA; the **mutual guarantee fund is parked `[SP]`** (institution-building beyond a spec's reach).
- **Operator-layer calibration `[owed]`:** `T_backoff` · cumulative-non-terminal horizon · `T_stale` · reserved service ratio · breach-rate threshold (+ the doctor's cadence bounds, shared line) — all pilot/empirical, shape not number. Calibration: numbers owed at the pilot; who sets them, 07d §5.
- **Arbiter-probing candidate `[SP→TG?]` `[owed]`:** planted cases routed, drift exposed-never-read; a standing tension — probing the node vs. not-modelling the node; it covers doctor and arbiter identically.
- **Permanent-CONDITIONAL cycle bounded, not closed** — the pendency rule's residual is calibration. `[LB]` that it is open.
- **No integrated adversarial run** — the arbiter side has had independent review; the *composed* architecture has had none; that test belongs to a further review or the pilot.

---

## 9. Seams (routed, not owned here)

Seams are joints to other chapters, collected in the seam map (11); the questions still open for this seat stand in 07d.

- **Symmetric sovereignty/qualification** (P1 ↔ 07a §6) — one refinement, two seats: taken-never-imposed · merit-undefined · sub-certainty-awareness sufficient · diligence-not-outcomes. A candidate for a single named principle in the principle chapters, with both seats (and plausibly 07c) as instances.
- **The cross-anchor** — the arbiter side of the mandatory doctor-attestation reference (§3 here ↔ 07a §5). One mechanism, set out once per side; one canonical statement is owed at the principle chapters (the same treatment as κ in 04c).
- **No-designation FAIL ↔ Gate 5's no-log FAIL** — the same shape: an absent epistemic component fails closed. Routed to the seam map.
- **Third-party-supplier exclusion ↔ Gate 5's lineage-anchor** — the same control-test logic at two layers. Routed to the seam map.
- **S-4 witness records ↔ the substrate chapters** — evidential weight in WITNESS_RECEIPT retention; HEAD_COMMIT decorative; the single-authoritative-L0 dependency (SR-SSoT). Owned by the substrate chapters; §3 here carries the arbiter-side landing only.
- **"Rare and real" ↔ Gate 5's alarm-fatigue calibration** — the warm channel and the reserved ratio are the operator-layer face of the same fatigue economics. A seam-map candidate.
- **Audit-scope-is-a-claim ↔ 08b one level up** — the §4 scope-consumption rule is the typed-stop discipline applied to audits: an unstated sweep-scope is a hidden clean bill. The doctor-side face is at 07a §4; a forward pointer sits at 08b §7. One principle, two seats.

---

*The arbiter closes what must close and certifies nothing. Named in a record, reachable on two channels, answerable in law and to the deployer that appoints it — kept external and unpredictable, the architecture's living "never 100%." The record proves designation, engagement, latency, breach; where no law can impose a cost, the record proves and nothing moves — said out loud, precisely where it hurts most. The queue empties or its failure shows.*
