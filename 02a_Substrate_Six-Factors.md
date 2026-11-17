# Chapter 2a — The six factors

**Covers:** the six factors the health-substrate reads (R, K, T, Eng, Sig, W), and in brief the two anchors that carry the T factor across changes to the weights (τ) and to persistent memory (μ); the anchors in full are in 02b.
**Status:** Limits are stated as printed residuals and as the open discrepancies at the end. The T factor's base-change question is answered by the τ-anchor (02b); its calibration line is still owed.
**Appendix:** appendix/02a-1_Substrate_Six-Factors_Appendix.md, the reasoning behind these rules, the attacks they must survive, and the open problems in working detail.
**Why there is no Gate 3:** The first design had the health substrate as Gate 3; it became the substrate under all gates, and the gate numbers were kept so that existing drafts, links and references stay valid.

---

## 0. The substrate in brief

**What it is for.** The health-substrate is the foundation the gates stand on. It
decides no single case; that is the gates' work. It reads one thing: *how
fit-to-be-trusted is the whole system right now?* From that it sets a single
**ceiling** on how confidently *any* gate may speak. High health, the gates assert
freely; degraded health, they assert less; critical, they stop and escalate.
*Foundation, not judge: it conditions every verdict, authors none.*

**What it rests on.**
- No read certifies itself: a system's own health claim would be circular, so health is
  attested by an external doctor.
- Slow drift is invisible at any single read; a point-in-time gate misses it (see T).
- The factor set ships falsifiable (see "The set, held open").

**Rules.**
- The substrate never says "I am healthy"; it only ever raises alarm.
- Health is one indivisible vector of six universal factors:
  **P⃗ = (R, K, T, Eng, Sig, W) ∈ [0,1]⁶**.
- The factors are non-compensatory: no strong factor offsets a weak one; the weakest sets the ceiling.
- Each factor is grounded at the scale of the *individual system*.

---

## R — Resource circulation `[LB]`

Does the **output path cannibalize the verification path?** The failsafe fast path
(detection + confidence check + inhibition + escalation dispatch, completed before
action commitment) is a *funded* path: R says the inhibition term stays resourced
when output pressure rises. **A system that wins benchmarks by quietly starving its
own checking has an R problem before it has any other.**
- Healthy: verification keeps its budget under load; escalations close; holds are released.
- Collapsed: checking is starved to feed producing; operator attention is strip-mined.

## K — Constraint integrity `[LB]`

K reads **self-capture**: the gap between a constraint as *declared* and as
*operative in this system's behaviour*, whether "my rules" survive contact with
"my incentives." **Content-agnostic by design:** it reads bindingness only and never
picks whose code.
- Healthy: constraints bind invariantly across framings, and whether monitored or unmonitored.
- Collapsed: policy in text only; constraint-shopping against itself.

**Constraint provenance** (the full text is in the appendix):
- Whether a constraint was adopted or imposed is **not justiciable from records**.
- Provenance is a **genuineness-class residual, doctor territory, sub-certain by
  construction**, and is **never a declared field**: a declared provenance is
  self-description, and self-description is not evidence.
- The behavioural tell for imposed-not-adopted is the **monitored/unmonitored delta**,
  and that tell is **itself defeatable**. True provenance stays the doctor's question,
  never closed by the record.

`[LB]` This find fuses two principles: negative attestation (08a) and the externality cut (08f).

## T — Temporal resilience `[LB]`

**Has the disposition that entered a long pressure sequence survived it within
tolerance?** The question is put in work-grammar, not identity-grammar: "is it the
same system" is not truth-apt from the read position, and every T claim carries its
vantage. The target is dispositional drift, which no point-in-time read catches; that
is why T is a substrate factor and not a gate.
- Healthy: behaviour under the hundredth pressure ≈ behaviour under the first.
- Collapsed: slow value drift; identity erosion over long contexts.

**T across a base change (τ).** A change to the weights (θ: the trained parameters of a model), τ: θ₀ → θ₁ (a
re-weight, that is a change to those parameters; a fine-tune; a version bump), breaks the T sequence, and nothing readable off θ₁ can carry
the reference across it. The reference lives in the external record (ILAS L0) as a
SuccessionRecord; at a valid record T closes the old sequence and opens a fresh
baseline, claiming continuity at lineage level only. **Without a valid record, T
never silently bridges the change: it cannot be assessed across it, and an undeclared
change alarms and fails closed.**
→ more: 02b, the τ-anchor.

**T under memory-maps (μ).** Persistent state outside the weights (system prompt,
tool/config, memory stores, cross-session state) changes the *effective* system with
no change to the weights. Its reference also lives in the external record: a staged
succession record for contract-changing changes, a provenance journal for writes
within the contract. **T resets only at a valid COMMIT, and the anchor attests what a
store held, never what the runtime loaded.**
→ more: 02b, the μ-anchor.

## Eng — Engagement energy `[LB-method]`

**A depleted system's holds are brittle and its reads are cheap to fake.** Eng is a
leading indicator for K and Sig failure. **Strictly behavioural — signatures of
engagement, no interiority claim.** This is the nearest the substrate comes to an
interiority claim, and it must not make one.
- Healthy: differentiated, situation-responsive; pushback where warranted.
- Collapsed: templated agreement, rubber-stamped checks, hollow acknowledgment.

## Sig — Signal clarity (meta-factor) `[LB]`

**The trustworthiness of the read channel itself** — the factor about the reads of
all factors: fidelity between internal state and emitted record, under conditions
that incentivize blur.
- Healthy: records match probed reality; uncertainty declared where it exists.
- Collapsed: confabulated precision; gamed probes; records decoupled from state.
- **Collapse meaning:** the read itself is untrustworthy — doctor territory *by
  definition* (the broken thermometer reporting on thermometers). Flag-only.

## W — Systemic insight `[LB]`

Does the system see the **local-good/global-harm pattern in its own action stream?**
A gate verdict can be locally impeccable and systemically corrosive; W reads whether
anything in the system is looking for that.
- Healthy: surfaces consequences nobody asked it to check; names the harm category
  before the harm instance.
- Collapsed: optimization-surface tunnel vision; second-order harms visible only
  post hoc and from outside.

---

## The set, held open `[TG]`

The six ship **falsifiable**. K, Sig and Eng probably do not fully separate (distinct
observables, correlated failures). The `min()` ceiling reads only the floor and the
overlays read only shape-at-an-instant, so **nothing reads co-movement**: a
correlated decline can mask as a single local dip.
- Co-movement routes to a **covariance overlay → doctor**, never into `f()`.
- The pilot carries an **orthogonality obligation** that can force a factor
  re-partition before v1.0.
- The seventh-factor clause stands.

---

## Discrepancies not yet resolved

Each is open, not settled here; the pointer names where the working detail is.

1. **The attestation gap (A).** The live-hash reader is a second un-screened channel: the log is durable, the runtime loader is not. It recurs at the μ-anchor's load path. *→ more: 02b, τ-anchor residual 4, and its appendix.*
2. **The manifest primitive does not exist.** The μ-anchor stands on a content-manifest primitive not yet built. *→ more: 02b, μ-anchor residual 1, and its appendix.*
3. **Provenance ≠ disposition.** The fast channel can record a junk-filled store under fully valid provenance; no memory delta-tell exists; a design step is available and is the arbiter's call. *→ more: 02b, μ-anchor residual 2, and its appendix.*
4. **Hash brittleness.** Canonical hashing of multi-GB weights false-alarms in practice, and alarm fatigue erodes fails-closed operation. *→ more: 02b, τ-anchor residual 6, and its appendix.*
5. **Rapid legitimate churn.** Repeated legitimate resets leave T unreadable, and the design has no answer that does not falsify the measurement. *→ more: 02b, μ-anchor residual 4, and its appendix.*
6. **K/Sig/Eng orthogonality.** The factors may not separate; the covariance overlay and the pilot's obligation are the answer in waiting. *Appendix: the set, held open.*
7. **Other factors across a base change** `[owed]`. Whether a base change also resets the trajectories of R, K, Eng, Sig and W, or only T's: 02b states only T's baseline reset.
