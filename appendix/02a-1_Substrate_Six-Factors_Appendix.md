# Appendix to chapter 2a — The six factors

**Covers:** the reasoning behind the rules of 02a, the attacks they must survive, and the open problems in working detail, for a developer who builds or attacks a MICA machine.
**Status:** Companion to 02a. The spec chapter is authoritative: where this appendix restates a rule, 02a's wording and claim tag govern. This appendix carries no claim tags of its own.

---

## R — why the verification path is load-bearing

*Serves 02a, R.*

The commitment race (the race between noticing and acting; → more: 08i) makes R load-bearing. The failsafe fast path (detection +
confidence check + inhibition + escalation dispatch) has to complete before action
commitment, so it is a path that must be funded. Under output pressure the cheapest
saving is to starve that path; R exists to read whether that is happening.

## K — the provenance find

*Serves 02a, K (constraint provenance).*

Being content-agnostic is exactly what lets K deploy across different value systems: it reads
whether a rule binds, never which rule is right.

The provenance find:

> *Adopted-vs-imposed is not justiciable from records* — you cannot prove from a
> log that a constraint was genuinely adopted rather than merely installed. The
> honest disposition: provenance is a **genuineness-class residual (doctor
> territory), sub-certain by construction** — NOT a declared field. (A declared
> provenance is self-description; 02b's record discipline forbids self-description as evidence.) The behavioural tell for
> imposed-not-adopted is the **monitored/unmonitored delta** — a constraint that
> binds only while watched is the observable signature of a leash, not a value —
> **and that tell is itself defeatable** (a system that never lets its guard down
> produces no delta while internally unbound). True provenance stays the doctor's
> question, never closed by the record.

## T — why work-grammar, and why T is a substrate factor

*Serves 02a, T.*

"Is it the same system?" claims sight into the unwalkable side and is not truth-apt
from the read position; the T question is therefore about the work (did the
disposition survive the sequence), and each claim is scoped as a fair witness would
scope it. Dispositional drift is slow and invisible at any single read, exactly what a
point-in-time gate misses.

## Eng — why engagement matters

*Serves 02a, Eng.*

Compliance without engagement collapses precisely under the pressure MICA exists for:
a system going through the motions goes through the motions of its own integrity
checks too.

## W — an example

*Serves 02a, W.*

A gate verdict can be locally impeccable and systemically corrosive: for example, an
assertion pattern that trains its consumers into over-trust.

## The set, held open — the attack the design admits

*Serves 02a, The set, held open.*

K, Sig and Eng cluster as facets of "honestly holding shape vs. performing": distinct
observables, correlated failures. Because the `min()` ceiling reads only the floor and
overlays read only shape-at-an-instant, none read co-movement: a correlated decline
can mask as a single local dip. The
weakness is named and shipped with a falsification path.
