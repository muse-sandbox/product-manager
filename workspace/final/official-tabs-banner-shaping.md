---
authoring_agent: claude-code
reviewed_by: codex
review: workspace/reviews/codex/official-tabs-banner-shaping-v2-review.md
status: final
created: 2026-07-15
supersedes: workspace/drafts/claude/official-tabs-banner-shaping-v2.md
review_verdict: READY WITH CHANGES (0 blockers, 5 major, 5 minor — all resolved; see Resolution log)
source_experiments: [7622, 7355, 6998, 6728, 7424, 7361, 7229, 4443, 4593, 4183, 7256]
source_confluence_pages: [777817235, 815603200, 815603314, 788614610, 721559684, 714416056, 788612885, 714416002, 787253942, 761947509, 425840453, 389323046]
publication: not published — requires explicit user approval of the exact page operation
---

# Official Tabs: response to "add a banner"

## What was actually requested, and what is not established

```text
Requested solution: Add a banner for Official tabs.
```

| Element | Status | Source |
|---|---|---|
| Objective: raise purchase conversion without a retention cost | **Reported as confirmed in the authoring session; not independently verifiable** | No ticket, brief, OKR, or written note exists. Requires reconfirmation — Action 1. |
| Platform: UG App | **Reported as confirmed in the authoring session; not independently verifiable** | Same. Requires reconfirmation — Action 1. |
| Banner is a starting point, not a fixed decision | **Reported as confirmed in the authoring session; not independently verifiable** | Same. Requires reconfirmation — Action 1. |
| **Placement** (which App surface the banner would occupy) | **Not established** | — |
| **Audience and eligibility** (new/returning, trial-eligible, Pro status) | **Not established** | — |
| **iOS vs Android scope** | **Assumption.** This document reasons on iOS because that is where #7622 has power. Android is an underpowered null. | Analyst scoping choice, not a requirement |
| **Baseline, reach, target lift** | **No data yet** | — |
| **Decision deadline and originator of the ask** | **Not established** | — |

**Everything below is conditional on the reported objective and platform, and those premises cannot be reproduced from the cited corpus.** If the objective, placement, or audience is different, the evidence ranking changes: #6998 is a **Web artist-page** banner, #6728 and #7622 are App flows, #7361 is a winback offer to lapsed subscribers. A banner for another surface or goal would need a different evidence set. **Reconfirming these three premises in a durable form is a precondition for acting on this document, not a formality.**

---

## Executive answer

**Under the reported objective, a generic promotional banner is the weakest-supported option available — but the case against it rests on the closest precedents, not on a claim that awareness is solved.**

Three things are true at once, and the first version of this document collapsed them into one:

1. **Inside the guided first-song flow, delivery of the Official offer is saturated.** Of users who reach the Official tab, **99.47% see the paywall, and 0.44% of those buy** (#7622, iOS, variation B, snapshot 2026-07-10). Within that subset, **increasing initial paywall reach is not the bottleneck.** This says nothing about whether frequency, sequencing, or comprehension could change conversion — the experiment did not isolate them, and B's own repeating paywall (Finding D) suggests repeated exposure is not inert.

2. **This does not rule out awareness elsewhere.** The 99.47% is conditional on reaching the Official tab in variation B. It says nothing about awareness among users who never enter the flow, or at a placement that has not been specified. **Awareness outside this downstream subset remains untested.**

3. **B is associated with more later Official-tab activity, which argues against the flat claim that more delivery cannot matter — but the association cannot be attributed to the guided exposure.** On ordinary, post-tour Official-tab visits, access rate is **4.64% in B vs 3.41% in control**. The source reports **no p-values, no confidence intervals, and no unit-of-analysis documentation for this cut** (repeat users and repeat sessions may be counted more than once), and **variation B contains an undeclared repeating paywall loop (Finding D)**, so the difference may reflect that loop re-firing rather than intent built by the guided flow. The page's own narrative — *"The guided first song does not sell on the spot — it pushes users into premium content, and they buy on a later visit"* — is an author interpretation, not a demonstrated mechanism.

**The recommendation is therefore narrow:** do not ship an unspecified generic banner. The closest direct precedent failed, adjacent messaging tests produced discovery without demonstrated revenue, and the placement, audience, and objective of the requested banner are not yet defined well enough to evaluate. **Establish the ask, then prefer an in-context mechanism or the cheapest discriminating test.**

**Nothing in #7622 is decision-ready.** All revenue metrics are preliminary; pending trials exceed the maturity gate in every branch.

---

## Corrected funnel — #7622, iteration 3, iOS, `from_tour`, snapshot 2026-07-10

The first version of this document reported 77.17% against the wrong denominator. Corrected, with every intermediate step:

| Step | Variation B | Conversion |
|---|---:|---|
| What to play — view | 14,641 | — |
| What to play — success | 13,892 | 94.88% of views |
| How to play — view | 13,891 | ~100% |
| How to play — success | 13,730 | 98.84% of views |
| **Official tab view** | **10,595** | **77.17% of how-to-play successes; 72.37% of what-to-play views** |
| **Paywall view** | **10,539** | **99.47% of Official-tab views** |
| **Access** | **46** | **0.44% of paywall views; 0.31% of what-to-play views** |

The page's own column header is *"how to play success → official tab, %"* — 77.17% is 10,595 / 13,730. It is **not** the share of everyone who enters the flow.

**Variation C, same funnel:** tab view 10,648 (77.17%) → paywall 10,576 (99.32%) → **access 270 = 2.55% of paywall views**, roughly 5.8× B's in-tour rate.

**Outside the tour (`other` — ordinary Official-tab visits):**

| | Control | B | C |
|---|---:|---:|---:|
| Official tab views | 13,092 | 14,276 | 11,947 |
| Paywall views | 12,509 (95.55%) | 13,733 (96.20%) | 11,163 (93.44%) |
| Access | 446 | 662 | 389 |
| **Tab view → access** | **3.41%** | **4.64%** | **3.26%** |

*Descriptive, with uncertainty and a confound.* B is associated with both more later Official-tab visits and a higher access rate on them; C is associated with **fewer** later visits and an access rate **slightly below control**. The page notes C leaks: of C users reaching the Official tab, 10,311 see the "Choose your version" screen and **88% (9,125) click a free community version**.

**Three limits on reading this table as a treatment mechanism:**

- **No uncertainty is reported for this cut** — no p-values, no intervals. The differences are point estimates.
- **The unit of analysis is undocumented.** Whether these rows count users, visits, or repeated visits by the same users is not stated, so "more later visits" may be composition rather than more returning buyers.
- **Paywall reach on later visits is high in every arm** (95.55% control, 96.20% B, 93.44% C). Whatever separates 4.64% from 3.41% is therefore **not** additional exposure on the later visit — and in B, the repeating `Official Tabs Recently Viewed` paywall (Finding D) is a live alternative explanation for both the extra visits and the extra conversions.

*Interpretation, labeled as such:* B **may** sell later rather than on the spot; C **may** sell in the moment without building later intent. Neither reading is established by this table.

---

## Evidence ledger

All figures from Confluence (`alice.mu.se`), read and re-verified 2026-07-15 against page versions 777817235 v144 and 788612885 v22. Live `ug-analytics` verification was not performed; these verify Confluence snapshots, not a fresh API read.

Values printed on the source pages as `p=0.000` are reported here as **p<0.001**.

### Closest precedent — the literal mechanism

**#6998 (721559684) — Official Tabs banner on the artist page. Same promotional mechanism; different platform and placement (UG Web, artist page — not the iOS first-song flow).**

- Block interaction: **0.24% / 0.20%**. Absolute gain: **+2 and +3 accesses**.
- No p-values computed. Page: *"statistical significance cannot be established, any revenue difference is highly unstable"*; the observed revenue difference was *"primarily driven by product mix variance, not structural conversion improvement."*
- Verdict: **Red FAIL**, *"we are closing the project as a failure."*

**External-validity limit: this is strong evidence that a promotional block failed on a Web browse surface. It is not a replication of any App placement, and no App banner placement has been specified.**

### Adjacent App evidence — discovery without demonstrated revenue

| Source | Result |
|---|---|
| **#6728** (714416056) — Official Tabs in search suggestions | Official Tab Open **+7.37% iOS / +6.89% Android (p<0.001)**. ARPU −2.55% (p=0.451); Conv to Access +0.17% (p=0.942). **Closed without rollout.** *"~half of users who opened Official Tab didn't have active Pro rights."* |
| **#7424** (788612885) — preview prewall promo | **Low-confidence evidence.** iOS targeting broken (promo shown beyond New/Free); sample undershot design (10.7–10.8k vs 16.1k). Free-user promo funnel, **by arm**: iOS view 18.14% (arm 2) / 18.69% (arm 3), click 0.65% (arm 2) / 0.97% (arm 3); Android view 13.30% (arm 2) / 13.43% (arm 3), click 0.67% (arm 2) / 0.65% (arm 3). Monetization non-significant throughout — but the test was underpowered, so this is a weak null, not a demonstrated failure. No decision recorded. |
| **714416002** — tooltip explaining Official Tabs | Killed before launch on a forecast, never tested: *"potential effect on ARPU is no more than +1%. When we need +16%."* |

### Mixed evidence that cuts against the thesis — must be surfaced

**#4443 (425840453) — "widget" paywall on the Official tab, iOS.** A non-full-screen promotional treatment on the Official tab that **did move overall access and charge rates**:

- Members → Accesses **+12.1% (p=0.014)**; Members → Charges **+13.92% (p=0.029)**.
- **But:** total ARPU **+13.23% (p=0.069, not significant)**, and on the **Official-tabs-specific funnel the effect was not significant** (accesses +7.64%, p=0.317; charges +2.4%, p=0.805). The authors themselves planned a cannibalization check.
- **Android never reproduced it:** iter #1 ARPU −1.18% (p=0.882); iter #2 (#4593) ARPU −5.32% (p=0.45); the third arm was significantly worse (ARPU **−18.46%, p=0.019**).
- The authors attribute part of the click lift to UI confusion, not interest: *"users don't fully understand that it isn't a paywall."*

**This does not prove a banner works. It does prevent this corpus from being summarized as uniformly negative:** an in-context promotional treatment on the Official tab itself produced the only significant charge-rate lift in the set.

### What the corpus supports, stated reproducibly

**Across several adjacent tests, increased Official-tab discovery or promo exposure has not produced a demonstrated total-revenue lift.** The one clearly-measured discovery win is #6728 (Official Tab Open +7.37% iOS, p<0.001, with ARPU flat). #7424's exposure claim rests on an invalid-targeting, underpowered test. #4443 is the counterexample and is significant on charge rate but not on total ARPU.

### Messaging and copy — not ruled out, just unsupported at the tested precision

**#7229 (761947509, iter 3)** tested 5 different labels at an identical price and found **no significant Total ARPU difference (p = 0.12 … 0.68)**. No equivalence test, confidence interval against a meaningful threshold, or demonstrated power for that metric is recorded on the page.

**Correct claim: copy is not supported as a lever by the tested labels at the available precision. It is not proven to be a no-op.** Establishing that would require an equivalence test or a CI that excludes a practically meaningful effect.

### Cannibalization

**#7361 (787253942)** — the only direct cannibalization measurement in this set. On Android the new banner produced 63 subscriptions while non-winback purchases fell by 28 → **net ≈ 0** (301 → 335 / 297). On iOS, of 102 banner subscriptions only ~30 were incremental. *Relevance limit: winback offer to lapsed subscribers, not an Official Tabs promo.*

### Instrumentation limits (788614610, Metrics Registry v17)

- **`trial-to-charge` — scoped limitation, not a blanket one.** The **First Session Health registry** cannot split trial vs direct-paid: iOS *"Apple does not pass unified_id"*; Android hits a 35GB join limit. **However, page 777817235 reports experiment-level trial→charge values from a separate analysis pipeline.** Before removing the metric from draft 815603314, **verify which source is authoritative for the required placement and segment.**
- **Per-placement purchase attribution — scoped to the registry (Gap 4).** *"The paywall a purchase came through is not visible"* **in the First Session Health registry.** The registry cannot attribute purchases by placement. It does **not** follow that no pipeline can: other cited pages report source-specific funnels from separate pipelines (experiment-level `trial-to-charge` on 777817235; funnel-source splits on 787253942). **Verify whether the experiment/event pipeline can attribute the selected banner placement before assuming it cannot.** A randomized total-ARPU comparison between arms remains valid regardless.
- *"Tab Open cannot be forced. Forcing tab display worsens results — verified in experiment 7256, iteration 1."*

---

## Problem framing

- **Target user (assumption):** free UG App users, iOS, who reach a song where an Official version exists. **The requester did not specify the audience; this is a scoping assumption.**
- **Current behavior, within the guided flow:** users reach the Official tab, 99.47% see the paywall, 0.44% buy on the spot. On later ordinary visits, 3.41% of control users convert.
- **Desired outcome (reported, pending reconfirmation):** higher purchase conversion, with no material decline in retention **or tab engagement**.
- **Evidence the status quo is costly:** the only arm with a significant total-ARPU lift (#7622 B, +17.25%, p=0.002) is significantly negative on retention (1d −7.76%, 7d −4.81%, 14d −4.91%, all p<0.001) and on engagement (60s −5.48%, p<0.001). That is the trade the reported objective rules out.
- **Central evidence gap:** nobody knows why a user who has seen the Official offer declines it. No source distinguishes "did not understand the value" from "understood it and would not pay this price" from "was not in a buying moment." **This is the recommended learning priority — a judgement, not an evidence-established ranking.**

---

## Causal map

| Mechanism | Status |
|---|---|
| **Initial paywall reach, inside the guided flow** | **Not the bottleneck there** — 99.47% of Official-tab reachers see the paywall. Conditional on reaching the tab in B. Says nothing about frequency, sequencing, or comprehension. |
| **Awareness, outside that subset** | **Untested.** No denominator exists for users who never enter the flow, or for any unspecified banner placement. |
| **Repeated exposure / frequency** | **Not isolated, and not inert.** B's undeclared repeating paywall (Finding D) is a plausible driver of both its lift and its harm. No experiment tests repetition as a designed lever. |
| **Comprehension** — sees the offer, has not experienced the value | **Unvalidated; never isolated at UG.** In #7622, trial→charge and AOV stayed flat while purchase volume rose — consistent with more people being *asked*, not more people being *convinced*. Consistency is not proof. |
| **Relevance / timing** — the ask arrives before intent exists | **Unvalidated.** Indirect support: #6728 — *"~half of users who opened Official Tab didn't have active Pro rights."* B's later-visit association is also consistent with intent forming after the first session, but it is confounded. |
| **Choice architecture** — Official and Community not presented as a real choice | **Partially supported and ambiguous.** C lifts Official charge CR (+28.65%, exploratory) but leaks 88% of chooser viewers to free versions and converts *below control* on later visits. |
| **Price / value** | **Unvalidated.** No experiment in this set isolates price for Official Tabs. |
| **Message / copy** | **Unsupported at tested precision** (#7229). Not ruled out. |

---

## What #7622 does and does not establish

**Design context (needed to read the table honestly).** The only goal metric documented on the page is **members → total accesses, % (14d)**, baseline iOS 6.79%, target lift 10%, MDE 0.026, power 0.8, alpha 0.05. The page states *"Design / each metric TBD — to be calculated before launch."* **There is no pre-registered secondary-metric plan, no multiplicity policy, and no guardrail non-inferiority margin.** Official-tabs-specific cuts below are therefore **exploratory**.

iOS, snapshot 2026-07-10. Samples 24,685 / 24,316 / 24,503; 21 days; balance spread under 1.5%.

| Metric | Control | B | B diff (p) | C | C diff (p) |
|---|---|---|---|---|---|
| **members→total accesses (goal metric)** | 6.49% | 7.34% | **+13.11% (p<0.001)** | 6.94% | **+6.90% (p=0.047)** |
| Total ARPU | $0.66 | $0.77 | +17.25% (p=0.002) | $0.72 | +9.47% (p=0.09) |
| members→buyers | 3.66% | 4.17% | +13.87% (p=0.004) | 3.74% | +2.08% (p=0.65) |
| *Official Tabs ARPU (exploratory)* | $0.16 | $0.24 | +52.12% (p<0.001) | $0.22 | +34.94% (p=0.003) |
| *Official charge CR (exploratory)* | 0.86% | 1.27% | +47.27% (p<0.001) | 1.11% | +28.65% (p=0.006) |
| Retention 1d | 15.97% | 14.73% | **−7.76% (p<0.001)** | 15.68% | −1.76% (p=0.39) |
| Retention 7d | 34.00% | 32.37% | **−4.81% (p<0.001)** | 33.27% | −2.15% (p=0.09) |
| Retention 14d | 37.58% | 35.74% | **−4.91% (p<0.001)** | 36.80% | −2.09% (p=0.07) |
| **Tab-view engagement 60s** | 73.43% | 69.40% | **−5.48% (p<0.001)** | 72.05% | **−1.88% (p=0.001)** |

**B fails the reported constraint.** It lifts the goal metric and is significantly negative on retention and engagement. The page authors agree: *"We are paying for the lift with engagement… the rollout call is a trade-off decision, not an automatic yes."*

**C is less harmful than B. It is not compliant with the reported objective, and it is not decision-ready.**

1. **C fails the engagement guardrail.** Tab-view engagement 60s is **−1.88%, p=0.001 — a statistically significant decline**. The reported objective explicitly includes "no material decline in retention **or tab engagement**." C does not pass it. Whether −1.88% is *practically* material cannot be answered: **no non-inferiority margin exists.**
2. **C's goal metric does not survive multiplicity.** members→total accesses is **+6.90%, p=0.047**. **The page records no multiplicity policy.** Applying a Bonferroni correction for two treatment-control comparisons (α = 0.025) — **a reviewer-applied policy, not the experiment's pre-specified decision rule** — this does not clear significance. Treat it as unresolved, not as a win.
3. **C's total ARPU is not significant** (+9.47%, p=0.09).
4. **Everything is preliminary.** Pending trials exceed the 5% maturity gate in every branch (iOS 9.9% / 11.6% / 12.6%); only ~25% of charges are older than 14 days. The page: ARPU, AOV, trial→charge, churn and refund *"can still move."*
5. **C's retention is not demonstrably safe.** At the later (2026-07-10) snapshot, C's 7d/14d retention estimates remain negative and their p-values are lower than at the 2026-07-05 cut (0.15/0.12 → 0.09/0.07). Two snapshots do not establish a trend or identify its cause. **Non-significance is not evidence of safety.**

**Page decision status: *"Preliminary — no final decision yet."* Nothing is rolled out. Android: underpowered null (~18.6k per arm vs 46,566 by design), do not roll out.**

---

## Option comparison

All options are conditional on the reported objective (App purchase conversion without retention or engagement cost). None has a defined reach, baseline, MDE, or forecast — **no data yet** for all five.

| # | Option | Mechanism | Evidence | Main risk | Confidence |
|---|---|---|---|---|---|
| 1 | **Generic banner** (the request, placement unspecified) | Messaging | Closest precedent failed on Web (#6998, 0.2% interaction). Adjacent App messaging produced discovery without demonstrated revenue (#6728). Counterweight: an in-context promo *on the Official tab itself* did lift charge rate (#4443, +13.92%, p=0.029), though not total ARPU. | Cannot be evaluated at all until placement and audience are specified | **Low — not recommended as specified** |
| 2 | **Always-on Official block in the version selector** | Choice architecture at the moment of version choice | Draft 815603200. C's mechanism, extended past the first session. But C leaks 88% of chooser viewers to free versions and converts below control on later visits. | May trade later monetization for in-the-moment conversion | Low–Medium |
| 3 | **Voluntary micro-demo of one premium feature** | Experience / proven value | Draft 815603314. Comprehension has never been isolated at UG — the largest untested link in the causal map. | May buy curiosity, not willingness to pay; feature choice has no data | Low, **high learning value** |
| 4 | **Surface the offer only on an intent signal** (e.g. locked-feature taps) | Timing / relevance | Not previously proposed. Targets the constraint directly: B's retention damage is consistent with pressing an offer on users who never intended to pay. **No source defines the intent signal or validates that it separates willing buyers from engaged non-buyers.** | The signal may not exist or may not discriminate; reduces reach | **Low — a hypothesis to test, not a candidate to ship** |
| 5 | **Diagnose instead of build** | No-build validation | Mature and recalculate #7622; determine why paywall viewers decline; resolve the Recently-Viewed confound. | Ships nothing this cycle | — |

---

## Recommendation

**1. Establish the ask before closing the solution space, and put the objective/platform premises in writing.** Placement, audience, and eligibility for the requested banner are unknown, and the objective and platform exist only as an unrecorded session confirmation. A banner on the tab screen, in the version selector, and on Explore are three different mechanisms with three different evidence sets. **This is the single cheapest thing to resolve, and it is a conversation, not an analysis.**

**2. Under the reported objective, do not ship an unspecified generic banner.** The closest direct precedent failed (#6998, Web), adjacent App messaging produced discovery without demonstrated revenue (#6728), and inside the guided flow the offer is already delivered to 99.47% of tab-reachers. **This argument is about the closest precedents and about the specified surface being undefined — it is not a claim that awareness is universally solved, nor that repeated exposure cannot matter.**

**3. Mature and recalculate #7622 before launching anything on this surface.** The maturity gate (<5% pending trials in every branch) is the page's own stated condition, and every revenue number is currently preliminary. **I do not have the enrollment-stop date or the remaining conversion-window distribution, so I cannot estimate when that will be.**

**4. Before launching a new test on this surface, check for overlap rather than assuming contamination.** Confirm whether #7622 exposure (`Tour Post Decline Gift Offer Close`) is still active, and whether cohorts, surfaces, or outcome windows would overlap.

**5. Set the non-inferiority margins that do not exist.** Retention 7d and tab-view engagement have no defined practical margin anywhere in these documents. Without one, "C's decline was small" is not a testable statement — and C's engagement decline is already statistically significant.

**6. The recommended learning priority is not which surface to decorate — it is why users who have seen the offer decline it.** That is unanswered by every source in this ledger, and it determines whether comprehension (option 3), timing (option 4), or price is the real constraint. **This is a judgement about where learning is cheapest and most decision-relevant, not a ranking the evidence establishes.**

If a shipped change is required this cycle regardless of evidence, that is a scheduling constraint and should be recorded as one — not resolved by building the option with the weakest support.

---

## Next actions

| # | Action | Owner | Due | Status |
|---|---|---|---|---|
| 1 | Establish placement, audience, eligibility, and originator of the ask; **reconfirm objective, platform, and banner flexibility in a durable written form** | **Ilzira Badretdinova** | Not set (no deadline exists) | Not started |
| 2 | Recalculate #7622 once pending trials < 5% in every branch | **Ilzira Badretdinova** | Not set (gated on trial maturity) | Not started |
| 3 | Define practical non-inferiority margins for Retention 7d and tab-view engagement | No data yet | No data yet | Not started |
| 4 | Resolve the `Official Tabs Recently Viewed` confound in arm B (Finding D) | **Ilzira Badretdinova** | Not set (no deadline exists) | Not started |
| 5 | Refresh drafts 815603200 / 815603314 onto the 2026-07-10 cut | No data yet | No data yet | Not started |
| 6 | Determine whether the experiment/event pipeline can attribute purchases by placement, and whether trial-to-charge is computable there for the required placement/segment | No data yet | No data yet | Not started |
| 7 | Diagnose why paywall viewers decline: what do the 99.56% do next? | No data yet | No data yet | Not started |

Actions 1, 2 and 4 have an accountable owner. Actions 3, 5, 6 and 7 do not, and no source names one — they should be assigned when the ask is established (Action 1).

---

## Findings that stand on their own

**A. Both open drafts cite a stale cut.** 815603200 and 815603314 quote the **2026-07-05** cumulative point. All 15 quoted figures verify verbatim, but the page's final table is **2026-07-10** and several have moved: B's Retention 1d −5.9% → **−7.76%**; C's Retention 7d p=0.15 → **0.09**; C's Official access CR +47.60% → **+54.85%**. **Maturation is one shared dependency, not the only blocker:** 815603200 also lacks reach, baseline funnel, four-arm sizing, and margins; 815603314 additionally lacks feature selection, fallback behavior, and instrumentation validation.

**B. `trial-to-charge` — scope the limitation before acting on it.** The First Session Health registry cannot compute it by placement/segment (Gap 1). Page 777817235 nevertheless reports experiment-level trial→charge values from a separate pipeline. **Verify which source is authoritative before removing the metric from 815603314.**

**C. Per-placement purchase attribution fails in the First Session Health registry (Gap 4) — the limit is registry-scoped, not universal.** The registry cannot say which paywall produced a purchase. Other cited pages report source-specific funnels from separate pipelines, so **whether the selected banner placement can be attributed is a verification task (Action 6), not a settled no.** A randomized total-ARPU comparison reads regardless.

**D. Iteration 3 arm B contains an undeclared second paywall, and it may be the confound that explains both its lift and its harm.** The page's Investigation section: a second paywall, **`Official Tabs Recently Viewed`**, re-triggers on every entry to a recently-viewed tab. Reach went from 6.4% to **43.5%**. After dismissal, **0.1% reach Explore — *"the user is locked on the tab."*** The authors describe iter3-B as *"iter2-B plus a retention loop."* This mechanic is not in the design. *(Iterations 1–2 of this flow ran as experiment **#7355**, reported on the same page 777817235; iteration 3 is #7622. "iter2-B" refers to the #7355 arm.)*

**It is plausible — not proven — that B's +17.25% ARPU, its higher later-visit access rate, and its −4.81% Retention 7d are all effects of the same trap rather than of the guided first-song flow.** B cannot cleanly identify the guided flow's effect. This should be resolved before B is considered for rollout, and it is the strongest argument for treating B's headline number with caution.

---

## What this document does not claim

- It does **not** claim awareness is solved. The 99.47% figure is conditional on reaching the Official tab in variation B and says nothing about upstream awareness or any unspecified placement.
- It does **not** claim additional or repeated exposure cannot matter. It claims only that **initial paywall reach** is saturated inside the guided flow. B's own repeating paywall suggests repetition is not inert — in both directions.
- It does **not** claim contextual exposure pays off on later visits. B's later-visit access rate (4.64% vs 3.41%) is a descriptive association with no reported uncertainty, undocumented unit of analysis, and an active paywall-loop confound.
- It does **not** claim a banner would produce zero effect. It claims the mechanism is unsupported by the closest precedents and cannot be evaluated until its placement and audience are specified.
- It does **not** claim copy is a no-op. #7229's null is not an equivalence result.
- It does **not** claim C is safe, compliant, or a natural follow-up. C significantly reduces 60s tab engagement, and its goal metric does not survive a reviewer-applied multiplicity correction.
- It does **not** claim B's lift is caused by the guided flow. The repeating-paywall loop is an untested alternative explanation.
- It does **not** claim Android behaves like iOS. Android is an underpowered null, not a proven zero.
- It does **not** infer user motivation from conversion data. Why users decline a seen offer is the central open question and no source answers it.
- It does **not** claim purchase attribution is impossible for every pipeline — only for the First Session Health registry.
- It does **not** treat the objective, platform, or banner flexibility as independently verified facts. They are session-reported premises pending durable reconfirmation.
- Reach, segment-level baseline, MDE, sample size and revenue forecast for every option: **no data yet.**

---

## Resolution log — Codex review v2

Review: [`workspace/reviews/codex/official-tabs-banner-shaping-v2-review.md`](../reviews/codex/official-tabs-banner-shaping-v2-review.md) — verdict READY WITH CHANGES, 0 blockers, 5 major, 5 minor.

| Finding | Resolution |
|---|---|
| MAJOR 1 — later-funnel association stated causally | **Accepted.** Executive item 3, the `other` funnel section, and the "does not claim" list now report a descriptive association with no reported uncertainty, undocumented unit of analysis, and the paywall-loop confound. Added a verified source fact: later-visit paywall reach is high in all arms (95.55% / 96.20% / 93.44%), so the gap is not later-visit exposure. |
| MAJOR 2 — "showing the offer again is not the lever" | **Accepted.** Narrowed to "increasing initial paywall reach is not the bottleneck," with an explicit note that frequency/sequencing/comprehension were not isolated. Added a "repeated exposure" row to the causal map. |
| MAJOR 3 — attribution limit stated too broadly | **Accepted.** Scoped to the First Session Health registry in the instrumentation section, Finding C, and the "does not claim" list; verification of the experiment pipeline moved into Action 6. |
| MAJOR 4 — unauditable decision premises | **Accepted.** User confirmed no durable source exists. The three premises are now labeled "reported as confirmed in the authoring session; not independently verifiable," and reconfirmation is folded into Action 1. All conditional language changed from "confirmed" to "reported." |
| MAJOR 5 — no owner for the blocking actions | **Accepted.** Ilzira Badretdinova assigned as accountable owner for Actions 1, 2 and 4 (user-confirmed). Due dates remain explicitly unset because no deadline exists. Actions 3, 5, 6, 7 remain unowned and are flagged as such. |
| MINOR 1 — control `other` view count | **Accepted; independently re-verified** against 777817235 v144: the source reports **13,092**. Corrected from 13,079. |
| MINOR 2 — #7424 combined arm maxima | **Accepted; independently re-verified** against 788612885 v22. Now reported by arm: iOS 18.14%/0.65% (arm 2), 18.69%/0.97% (arm 3); Android 13.30%/0.67% (arm 2), 13.43%/0.65% (arm 3). |
| MINOR 3 — #4443 "did move money" | **Accepted.** Replaced with "did move overall access and charge rates." |
| MINOR 4 — unused experiment #7355 | **Accepted, resolved by mapping rather than removal.** Page 777817235 v144 states *"Experiment: 7355 — UG App First Session Flow Update (iteration 2)"*; #7622 is iteration 3 of the same flow. Finding D now maps "iter2-B" to #7355 explicitly, so the ledger entry is used. |
| MINOR 5 — C retention "drifting negative as power grows" | **Accepted.** Rewritten as a later-snapshot observation: estimates remain negative, p-values are lower, two snapshots do not establish a trend or its cause, and non-significance is not safety. |

Also applied from the review's analytics check: the Bonferroni threshold is now labeled explicitly as a reviewer-applied correction rather than the experiment's decision rule, and the "highest-value open question" is presented as a recommended learning priority rather than an evidence-established ranking.

**No disagreements recorded.** Every major and minor finding was accepted; the four checkable factual findings (MINOR 1, MINOR 2, MINOR 4, and the funnel denominators) were re-verified against the live Confluence sources rather than accepted on the reviewer's word.
