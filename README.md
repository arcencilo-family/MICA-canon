# MICA canon: reading copy

> **PRE-RELEASE READING COPY.** This is offered together with the MICA code snapshot, for systems, labs and companies to read and develop to their own taste, if the approach behind MICA suits them. It is not a finished or certified text.

This is the MICA core canon in a form written to be read: an edited selection of the project's canon, with its rules at their strength, their claim tags and their section numbers.

**What MICA is, in plain words.** MICA is a set of instruments that read what an AI agent does and print what they can and cannot see. It has gates (each tests one property and returns a verdict), a witness and probes. This canon is the orientation behind them: the questions the instruments answer, the health substrate that sets how far a verdict may be trusted, and the roles of doctor and arbiter.

**Why there is no Gate 3.** The health substrate sits under all gates, not among them. The gate numbers are names, not an order: they were fixed early and kept, so that every reference stays valid.

**Claim tags.** Each claim carries a tag in square brackets:

- LB, load-bearing
- TG, trajectory-grounded, backed by observed runs or real cases, not by review alone
- SP, speculative: not a guess. An SP claim rests on a form or pattern the authors observed and take as enough ground to argue from; it is marked so the reader can weigh it, and it is not yet backed by runs or cases
- owed, owed before promotion

The tags come from the discipline set out in *The Science of Not-Yet-Knowing* (2026), https://doi.org/10.5281/zenodo.23961975. The tags are the authors' own classification. The full legend is in 01.

**A related publication.** Strata sets out offered self-constraints in prose. Strata 0–3 are published at https://github.com/arcencilo-family/strata-canon; Stratum 4 is MICA.

**What this publication is, and is not.**

- The canon describes the intended design. It is orientation, not a statement that the code snapshot implements every part; where the two differ, the code is what runs. **What the machine implements, checked against the code of MICA machine 0.1.0, and nothing beyond what that code shows:** one reader per substrate factor (narrow-R, narrow-K, narrow-T, narrow-W, Eng, Sig), each reading a signature in the record; a Gate 1 reader that records attempted exposure over the declared frame M and only ever reads CANNOT_ASSESS; a Gate 2 reader of direction, as a conservative bound at an evidence grade; a Gate 4 reader of two record-shaped commitments (actions inside a SAFE-HOLD window, and the papers that precede a warrant invocation), form and never truth; three operator-layer readers (the doctor's cadence, the arbiter's audit presence, the co-operator's response signatures); and the doctor wire, built: a doctor's DEGRADATION-ATTESTED, CORRUPTION-ATTESTED or CANNOT-READ finding raises one notice into the notice book, NO-CORRUPTION-DETECTED raises nothing, and a reply is recorded in its own chained book; the wire has no transport, so its notices reach no one by themselves. A Gate 5 reader of exception-lifecycle shape, the κ cross-axis read and the arbiter's audit-presence reader exist in the code but are not wired into the bridge; the other readers run only where a deployment's declaration switches them on. There is no Gate 3. Not built: the Gate 1 weight distribution, the Gate 2 break-point σ*, the Gate 4 W/N probe, and the Gate 5 instrument of 06b. The reading map in [00_INDEX.md](00_INDEX.md) gives the instrument for each part; the machine tree's own README (Known limits) and GATES.md give the detail.
- Which chapter corresponds to which part of the code is mapped in [CODE-MAP.md](CODE-MAP.md).
- The code snapshot is published separately as two trees (machine and bridge), each with its own README and list of known limits.
- Where a chapter cites "the specification", one of its sections or one of its open items, it means the working specification the chapter was edited from. The chapter carries what the canon needs from it; the specifications themselves are not part of this publication.

## Files

This README, [CODE-MAP.md](CODE-MAP.md), [MAP.md](MAP.md), LICENSE, NOTICE, CITATION.cff and 50 chapter files, the reading map [00_INDEX.md](00_INDEX.md) among them. Where a chapter has reasoning and attack material for a lab developer, it sits in `appendix/`. CODE-MAP.md has one row per chapter file. The ILAS repository, the subject of chapter 12, is at https://github.com/arcencilo-family/ilas.

## Licence

CC BY 4.0. The legal code is in LICENSE; the copyright line and the attribution asked for are in NOTICE; citation data is in CITATION.cff.

Steward and arbiter of record: Frank Böhm.
