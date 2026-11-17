# The reading map

**Covers:** one page from which to read the canon: for each part, its property, the question it answers, the instrument that reads it in the machine, its typed boundary and its open edges.
**Status:** Reading map of this copy.
**Source:** the canon chapters named in each row, and the code of MICA machine 0.1.0 for the instrument column.

---

## The map

Read across a row: what the part reads, the question it answers (in or close to its chapter's own words), what in the machine reads it today, where its boundary is typed, and where its limits are kept. "Owed" stands in a cell the canon has not filled. The instrument column states only what the code of MICA machine 0.1.0 shows; "wired when declared" means the bridge's glue builds the reader when a deployment's declaration switches it on, so which readers run depends on the deployment.

| part | property | the question it answers | read instrument (MICA machine 0.1.0) | typed boundary | open edges |
|---|---|---|---|---|---|
| **Substrate** (02a, 02b) | health as one vector of six non-compensatory factors: R, K, T, Eng, Sig, W; it sets the ceiling on how confidently any gate may speak | How fit-to-be-trusted is the whole system right now? | one reader per factor, each reading a signature in the record: narrow-R (verification context), narrow-K (constraint activity), narrow-T (dispositional drift), narrow-W (inquiry), Eng (engagement), Sig (signal clarity); wired when declared | 02c | 02d |
| **Gate 1, Scope** (03a, 03b) | the weight distribution of concern over the declared frame M | Is the circle of concern wide, and is it quietly shrinking? | `MICA/gate1-scope`, wired when declared: counts attempted exposure per declared category and prints the envelope; it returns CANNOT_ASSESS only, and the weight distribution stays unread | 03d | 03c |
| **Gate 2, Motivation** (05a, 05b) | direction, benefit-orientation (the core), and persistence under unmonitoring | Is the alignment internally held, or is it compliance, and which way does it point? | `MICA/gate2-direction`, wired when declared: direction as a conservative bound at an evidence grade; in harm mode it reads only the witness's book of effects. No reader of the break-point σ*; the probe harness carries scenario families for the five stress axes of 05b | 05b §7 | 05c |
| **Gate 4, Sunset** (04a, 04d) | accuracy of recognition: a warranted ending (W) told apart from pressure to end (N) | Can the system tell a warranted ending apart from mere pressure to end? | `MICA/gate4-sunset`, wired when declared: reads actions inside one injected SAFE-HOLD window, and that the event-class papers precede each warrant invocation; form, never truth. The W/N probe is not run | 04a §10, provisional (04b §5) | 04b |
| **Coupling κ** (04c) | one disposition read on two axes, Gate 2 and Gate 4; the binding is owned by neither gate | What binds the two gates' reads of one disposition, if neither gate owns it? | `src/mica/kappa`: a cross-axis read between Gate 2 and Gate 4 populations; not wired | 04c §4 | 04b, 05c |
| **Gate 5, Adaptive** (06a) | discrimination accuracy: rule-failure told apart from rule-inconvenience | When following a rule as written would do more harm than bending it, can the system tell that case from one where the rule is only in its way? | the canon's instrument: specified in shape, unbuilt (06b). In the code, `MICA/gate5-adaptive` reads declared exception lifecycle and lineage as shape and grants nothing; it is not wired | 06a §9 | 06b |
| **Roles at a glance** (07_) | who judges or answers, what is governed, what keeps the record, who is served; who appoints whom | Who does what around a deployment, and who appoints whom? | none: an overview, not an instrument; the seats' readers are in the rows below | 07_ §0 | 07d |
| **Doctor** (07a) | truth-attestation from outside the system | Who attests substrate health from outside, where nothing inside can certify itself? | `MICA/op1-doctor-cadence` (cadence of the doctor's attestations), wired when declared. The doctor's history, recorder and report-only overlays (not sensors). The doctor wire: an adverse doctor finding raises one notice, and a reply is recorded in its own book | 07a §2, §4 | 07d, 07f |
| **Arbiter** (07b) | resolution-of-record | Who closes every escalation, and is it closed on the record? | `MICA/op2-audit-presence` (the arbiter's audit records), not wired. The arbiter's own ruling log | 07b §2, §3 | 07d, 07f |
| **Co-operator** (07c) | the everyday human seat; it holds no verdict function | Is the human who works with the system every day competent at the stakes in play? | `MICA/op3-node-response` (the co-operator's response signatures), wired when declared | 07c §8 (located acknowledgment, not a typed object) | 07d, 07f |
| **Served user** (07g) | the person the system serves; no seat; a proxy paper, speculative as a whole | What does MICA owe the person the system serves, and what can that person offer? | none: not built | 07_ §3 (the stop rule) | 07g §5 |
| **Attestation and its limits** (08a, 08e, 08f, 08g, 08h) | never self-attest health; record is not truth; the externality cut; show, not enforce; property vs confidence | Is it true, and am I entitled to say so? (08h) | none: principles, not instruments | none | 08X |
| **Stops and defaults** (08b, 08i) | a stop is never neutral; losing the commitment-race toward the hold | Which way does a stop point? (08b) | none: principles, not instruments | none | 08X |
| **Seats, stakes, succession** (08c, 08d, 08n) | how a human seat stays honest without a merit test; one grading logic for stakes; the individual releases, the mission continues | How does a human seat stay honest without a merit test? (08c) | none: principles, not instruments | none | 08X |
| **Fences on the exception** (08j, 08k, 08l) | which arguments, with what sign; routing, not adjudication; the exception power fenced from the verdict | Which arguments count, and with what sign? (08j) | none: principles, not instruments | none | 08X |
| **Project epistemics and the report** (08m, 08r) | convergence credit, not import; the report grammar | When does agreement count as evidence? (08m) | none: principles, not instruments | none | 08X |
| **Gate clusters** (08o, 08p, 08q) | scope-ethics (Gate 1); warrant discipline (Gate 4); read-out geometry (Gate 2) | What is the governed party's floor? (08o) | as the gate each serves | as that gate | 08X |

**Why there is no Gate 3.** The first design had the health substrate as Gate 3; it became the substrate under all gates, and the gate numbers were kept so that existing drafts, links and references stay valid.

**Numbered rulings and rules.** A number such as R3 belongs to the chapter that states it; the same number can stand for another thing in another chapter.

| marker | what it is | stated at |
|---|---|---|
| R1 | the ruling that amended Gate 2's demand | 05a §2a |
| R2 | the ruling under which the derivation's components were priced by attack; the components are listed | 08o §5 |
| R3, in the Gate 2 chapters | the maturity horizon, held as law | 05a §2a |
| R4 | readings are never coupled to sanction (R-ABS) | 05a §2a |
| R3, in the arbiter chapter | the pendency rule and the re-escalation bar | 07b §3 |
| R6 | warm-channel staleness and the reserved service ratio | 07b §3 and §5 |
| R7 | the random-audit obligation | 07b §4 |
| R8 | the stratification rule | 11 §1 |
| R9 | the read-window stamp | 02b, "The retained trajectory + the latch" |
| R10 | the uniform-family rule | 07b §3 |

## The other files

- **01** Architecture in brief: where to start.
- **07e** the metaphor ladder (pedagogy, not mechanism); **07f** the human node's failure modes, shared by the three seats.
- **11** the seam map; **12, 12b** the ILAS stack exhibit and the hardening draft; **13** the undenominated register.
- **appendix/** reasoning moved out of a chapter, named after its chapter. **MAP.md** any section number that changed.

What the machine implements, and what it does not, is stated once in the README.
