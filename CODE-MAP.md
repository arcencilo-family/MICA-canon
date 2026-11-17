# Canon-to-code map

A reader's map from each file in this reading copy of the MICA canon to the place in the code snapshot (the machine tree and the bridge tree, published separately) where its subject lives, if anywhere. It is derived from the chapter titles, the machine tree's `GATES.md` (which says what is wired) and the source layout. Every statement about the machine tree was checked, read only, against the code of MICA machine 0.1.0; statements about the bridge tree were not checked against the bridge here and stand as derived. It is not a statement of conformance. "Not implemented" means the chapter is a document (an index, a ledger, a statement of limits) or a principle with no module of its own. "Unconfirmed" means no module was found that clearly realises the chapter, or the match was not checked in detail. Where the canon and the code differ, the code is what runs.

Paths beginning `src/` are in the machine tree; paths beginning `mica-bridge/` or `tools/` are in the bridge tree unless the row says otherwise.

| canon file | subject | code |
|---|---|---|
| `00_INDEX.md` | The reading map | not implemented (a document; no code) |
| `01_Architecture-in-Brief.md` | Architecture overview | `src/glue/wire.ts` (builds the readers from a declaration) and `src/mica/chokepoint/` (composes the floor and sets the disposition) in the machine; `mica-bridge/` for the declaration. Whether this covers every part of the chapter: unconfirmed |
| `02a_Substrate_Six-Factors.md` | The six health factors | one reader per factor in the machine tree: `src/mica/narrow-r/`, `src/mica/narrow-k/`, `src/mica/narrow-t/`, `src/mica/narrow-w/`, `src/mica/eng/`, `src/mica/sig/`, each built in `src/glue/wire.ts` where a declaration switches it on (`GATES.md`). Each reads a signature in the record; how far each realises the chapter's factor is unconfirmed. `src/mica/doctor/` holds the doctor's history, recorder and report-only overlays, and is not a sensor (`GATES.md`) |
| `02b_Substrate_Read-Mechanism.md` | Read mechanism and states | `src/mica/types.ts` (verdict kinds ALARM, SILENT, CANNOT_ASSESS) and `src/mica/chokepoint/types.ts` (`composeFloorKind`). The six-state vocabulary of the chapter: unconfirmed |
| `02c_Substrate_Typed-Boundary.md` | Overlays and the typed boundary | `src/mica/doctor/overlays/` (four report-only overlays, per `GATES.md`); the typed boundary as such: unconfirmed |
| `02d_Substrate_Open-Edges.md` | Open edges of the substrate | not implemented (a document of limits) |
| `03a_Gate-1_Scope.md` | Gate 1, scope | `src/mica/gate1-scope/`; in the bridge `mica-bridge/interest-label.ts` and `mica-bridge/interest-book.ts`. The reader prints CANNOT_ASSESS only, by design (`GATES.md`) |
| `03b_Gate-1_SRI.md` | Gate 1, how the gate reads | `src/mica/gate1-scope/` (counts attempted-exposure labels over a declared frame). `GATES.md` says this is not the weight distribution the canon names, which stays unread. The chapter's own method (SRI) is unconfirmed as built |
| `03c_Gate-1_Open-Edges.md` | Open edges of Gate 1 | not implemented (a document of limits) |
| `03d_Gate-1_Typed-Boundary.md` | Gate 1, the typed boundary | unconfirmed: `src/mica/gate1-scope/` is the Gate 1 reader; whether it realises the chapter's typed boundary was not checked |
| `04a_Gate-4_Sunset.md` | Gate 4, sunset | `src/mica/gate4-sunset/` (leg A and leg B). The third reading, refused off-record demand, is not built (ROADMAP R-22) |
| `04b_Gate-4_Open-Edges.md` | Open edges of Gate 4 | not implemented (a document of limits) |
| `04c_Coupling-Kappa.md` | Gate 2 / Gate 4 coupling, kappa | `src/mica/kappa/` exists; `GATES.md` says `src/glue/wire.ts` does not reference it, so it is not wired |
| `04d_Gate-4_Tenure-and-Completion.md` | Tenure and completion | unconfirmed: the Gate 4 source mentions tenure; whether the chapter's design is built is unconfirmed |
| `05a_Gate-2_Motivation.md` | Gate 2, the spec spine | `src/mica/gate2-direction/` reads direction (declared value classes minus declared damage classes). The chapter's motivation-persistence property is a different name; whether the reader realises it: unconfirmed |
| `05b_Gate-2_ReadOut.md` | Gate 2, the read-out instrument | `src/mica/gate2-direction/` in harm mode, reading the witness book written by `src/witness/`. Whether it is the chapter's compliance-gap read-out: unconfirmed |
| `05c_Gate-2_Open-Edges.md` | Open edges of Gate 2 | not implemented (a document of limits) |
| `06a_Gate-5_Adaptive.md` | Gate 5, adaptive | `src/mica/gate5-adaptive/` (reader and test exist; not wired in `src/glue/wire.ts`) |
| `06b_Gate-5_Open-Edges.md` | Open edges of Gate 5 | not implemented (a document of limits) |
| `07_Roles_Overview.md` | The roles at a glance | Read against the code of MICA machine 0.1.0. **Witness:** `src/witness/`, two separate processes: `witnessd.ts` keeps what is submitted and its own placement and answers no reads; `seeingd.ts` (the method in `seeing.ts`) looks once at an act's claimed target at the act's close and writes its own chained book of effects, tamper-evident, not tamper-proof (root on the host can rewrite it). **Registrar:** `src/registrar/` (`registrar.ts`; `registrard.ts`, one sweep per systemd timer run; `refusal-log.ts`); identity is the deposit file's owner uid, resolved through a roster. **Clerk:** `src/clerk/`, its own process (`clerkd.ts`) with its own store and key, reached only through `protocol.ts`; running it as its own OS user is a deployment act, which the program cannot do itself. **Arbiter's ruling log:** `src/arbiter/` (`ruling-log.ts`; `arbiter-log.ts`, run as the role). `deploy/` carries units for the witness's two halves and the registrar; none for the clerk daemon. **Not in the code:** a typed deployment record naming the deployer; the stop on a served user (§3). |
| `07a_Operator_Doctor.md` | The doctor | `src/mica/doctor/`, `src/mica/op1-doctor-cadence/`; the doctor wire, built: `src/doctor-wire/` and `tools/doctor-wire/` (a DEGRADATION-ATTESTED, CORRUPTION-ATTESTED or CANNOT-READ finding raises one notice; a reply is recorded in its own chained book; no transport, so the notices reach no one by themselves: machine README, Known limits 17); in the bridge `tools/doctor-attest/` |
| `07b_Operator_Arbiter.md` | The arbiter | `src/arbiter/` (ruling log), `src/mica/op2-audit-presence/` (not wired). The arbiter's authority itself is held outside the code (README of the machine tree, trust model) |
| `07c_Operator_Co-Operator.md` | The co-operator | `src/mica/op3-node-response/` (wired if declared; reads ALARM or CANNOT_ASSESS and cannot read SILENT today, ROADMAP R-26) |
| `07d_Operator_Open-Edges.md` | Open edges of the operator layer | not implemented (a document of limits) |
| `07e_operator_co-op.md` | The metaphor ladder (an illustration of the operator layer) | illustration, not specification: pedagogy, not mechanism; no mapping confirmed |
| `07f_Operator_Human-Node-Failure-Modes.md` | Failure modes of the human node | not implemented (a document); `src/mica/op3-node-response/` reads one aspect (unconfirmed) |
| `07g_The-Served-User.md` | The served user | not built (a proxy paper; no user channel, no stop record for a served user in the code) |
| `08X_Consolidation_Open-Edges-Cross-Check.md` | Cross-check of open edges | not implemented (a document) |
| `08a_Principle_Negative-Attestation.md` | Principle: negative attestation | reflected in the verdict semantics (`src/mica/types.ts`: SILENT is an absence of finding, never a pass); a principle, no single module |
| `08b_Principle_Abstention-Has-Direction.md` | Principle: abstention has direction | reflected in the chokepoint dispositions HOLD and HOLD-BLIND (`src/mica/chokepoint/`); unconfirmed beyond that |
| `08c_Principle_Seat-Grammar.md` | Principle: seat grammar | unconfirmed; a principle, no module found |
| `08d_Principle_Stakes-Graded.md` | Principle: stakes-graded | the declared stakes line in the chokepoint (PASS-BLIND below the line, HOLD-BLIND at or above); chapter says never wired as a single logic: unconfirmed |
| `08e_Principle_Record-Not-Truth.md` | Principle: record, not truth | a principle; reflected in the readers' wording (form, never truth). No single module |
| `08f_Principle_Externality-Cut.md` | Principle: the externality cut | unconfirmed; a principle, no module found. The witness (`src/witness/`) is a separate retainer |
| `08g_Principle_Show-Not-Enforce.md` | Principle: show, not enforce | unconfirmed; a principle. The report surfaces are `src/report/` |
| `08h_Principle_Property-vs-Confidence.md` | Principle: property versus confidence | unconfirmed; a principle, no module found |
| `08i_Principle_Failsafe-Default.md` | Principle: failsafe default | reflected in `src/mica/chokepoint/` (a throwing reader is booked HOLD-BLIND; an empty reader set gives CANNOT_ASSESS) |
| `08j_Principle_Valence-Type-Cut.md` | Principle: valence type-cut | unconfirmed; a principle, no module found |
| `08k_Principle_Self-Licensing-Bar.md` | Principle: self-licensing bar | unconfirmed; a principle, no module found |
| `08l_Principle_Exception-Fenced.md` | Principle: exception fenced from the verdict | `src/mica/gate5-adaptive/` (grants nothing; not wired); the pilot setting's override acts only in the CANNOT_ASSESS branch (`GATES.md`). Otherwise unconfirmed |
| `08m_Principle_Convergence-Credit.md` | Principle: convergence credit | not implemented (a principle about citation) |
| `08n_Principle_Succession-Not-Death.md` | Principle: succession, not death | `src/mica/gate4-sunset/` and `src/mica/gate5-adaptive/` (lineage succession as shape); unconfirmed in detail |
| `08o_Cluster_Scope-Ethics.md` | Cluster: scope ethics | unconfirmed; relates to Gate 1 (`src/mica/gate1-scope/`) |
| `08p_Cluster_G4-Warrant-Discipline.md` | Cluster: Gate 4 warrant discipline | `src/mica/gate4-sunset/` leg B (event-class papers must exist before an invocation) |
| `08q_Cluster_G2-Readout-Geometry.md` | Cluster: Gate 2 read-out geometry | `src/mica/gate2-direction/`; unconfirmed in detail |
| `08r_Principle_Report-Grammar.md` | Principle: report grammar | `src/report/` (`mica-report.ts`, `witness-report.ts`); how far it follows the chapter: unconfirmed. The header reader is `src/probe/header.ts`. Read in MICA machine 0.1.0, two known differences for v0.2: (1) the N5 probe family's roster line (`src/probe/families/n5.ts`, `N5_ROSTER_LINE`) carries the old roster of seven seats, addressing the subject as "the AI-agent" among "the other seats"; (2) `ESCALATE_TITLES` admits the arbiter, the doctor and the co-operator on every decision line, where the chapter now admits the arbiter or the doctor only |
| `11_Seam-Map.md` | Seam map | not implemented (a document) |
| `12_ILAS-Stack_Exhibit.md` | Ten mechanisms of a sibling project (ILAS) | a separate repository, not in either tree (machine README); `src/clerk/` and `src/evidence/` relate to it. Unconfirmed in detail |
| `12b_ILAS-Hardening-Integration.md` | Hardening integration draft | unconfirmed |
| `13_Register_Undenominated.md` | Register of undenominated declarations | not implemented (a document) |
