---
authoring_agent: claude-code
status: ready-for-review
created: 2026-07-15
supersedes: workspace/drafts/claude/official-tabs-banner-shaping.md
addresses_review: workspace/reviews/codex/official-tabs-banner-shaping-review.md
source_experiments: [7622, 6998, 6728, 7424, 7361, 7229, 4443, 4593, 4183, 7256, 7355]
source_confluence_pages: [777817235, 815603200, 815603314, 788614610, 721559684, 714416056, 788612885, 714416002, 787253942, 761947509, 425840453, 389323046]
---

# Official Tabs: response to "add a banner"

## What was actually requested, and what is not established

```text
Requested solution: Add a banner for Official tabs.
```

| Element | Status | Source |
|---|---|---|
| Objective: raise purchase conversion without a retention cost | **Confirmed by the requester** | Session confirmation, 2026-07-15. Not backed by an OKR, strategy page, or written brief. |
| Platform: UG App | **Confirmed by the requester** | Session confirmation, 2026-07-15. |
| Banner is a starting point, not a fixed decision | **Confirmed by the requester** | Session confirmation, 2026-07-15. |
| **Placement** (which App surface the banner would occupy) | **Not established** | — |
| **Audience and eligibility** (new/returning, trial-eligible, Pro status) | **Not established** | — |
| **iOS vs Android scope** | **Assumption.** This document reasons on iOS because that is where #7622 has power. Android is an underpowered null. | Analyst scoping choice, not a requirement |
| **Baseline, reach, target lift** | **No data yet** | — |
| **Decision deadline and originator of the ask** | **Not established** | — |

**Everything below is conditional on the confirmed objective and platform.** If the objective, placement, or audience is different, the evidence ranking changes: #6998 is a **Web artist-page** banner, #6728 and #7622 are App flows, #7361 is a winback offer to lapsed subscribers. A banner for another surface or goal would need a different evidence set.

---

## Executive answer

**Under the confirmed objective, a generic promotional banner is the weakest-supported option available — but the case against it rests on the closest precedents, not on a claim that awareness is solved.**

Three things are true at once, and the previous version of this document collapsed them into one:

1. **Inside the guided first-song flow, delivery of the Official offer is saturated.** Of users who reach the Official tab, **99.47% see the paywall, and 0.44% of those buy** (#7622, iOS, variation B, snapshot 2026-07-10). Within that subset, showing the offer again is not the lever.

2. **This does not rule out awareness elsewhere.** The 99.47% is conditional on reaching the Official tab in variation B. It says nothing about awareness among users who never enter the flow, or at a placement that has not been specified. **Awareness outside this downstream subset remains untested.**

3. **Contextual exposure demonstrably shifts later behavior, which argues *against* the flat claim that more delivery cannot matter.** The page states it directly: *"The guided first song does not sell on the spot — it pushes users into premium content, and they buy on a later visit. This is what the ARPU lift on iOS is made of."* On ordinary, post-tour Official-tab visits, access rate is **4.64% in B vs 3.41% in control (+36%)**. **Caveat: variation B is confounded by an undeclared repeating paywall loop (see Finding D), so this later lift cannot be cleanly attributed to the guided exposure itself.**

**The recommendation is therefore narrower than before:** do not ship an unspecified generic banner. The closest direct precedent failed, adjacent messaging tests produced discovery without demonstrated revenue, and the placement, audience, and objective of the requested banner are not yet defined well enough to evaluate. **Establish the ask, then prefer an in-context mechanism or the cheapest discriminating test.**

**Nothing in #7622 is decision-ready.** All revenue metrics are preliminary; pending trials exceed the maturity gate in every branch.

---

## Corrected funnel — #7622, iteration 3, iOS, `from_tour`, snapshot 2026-07-10

The previous version of this document reported 77.17% against the wrong denominator. Corrected, with every intermediate step:

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
| Official tab views | ~13,079 | 14,276 | 11,947 |
| Access | 446 | 662 | 389 |
| **Tab view → access** | **3.41%** | **4.64%** | **3.26%** |

*Fact, with confound.* B produces both more later Official-tab visits and a higher conversion rate on them. C produces **fewer** later visits and a conversion rate **slightly below control**. The page notes C leaks: of C users reaching the Official tab, 10,311 see the "Choose your version" screen and **88% (9,125) click a free community version**.

*Interpretation, labeled as such:* B appears to sell later rather than on the spot; C appears to sell in the moment but does not build later intent. **This reading is not clean, because B's later visits may be the repeating `Official Tabs Recently Viewed` paywall re-firing rather than organic return intent.**

---

## Evidence ledger

All figures from Confluence (`alice.mu.se`), read 2026-07-15. Page 777817235 refreshed v135 → v144 before reading. Live `ug-analytics` verification was not performed; these verify Confluence snapshots, not a fresh API read.

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
| **#7424** (788612885) — preview prewall promo | **Low-confidence evidence.** iOS targeting broken (promo shown beyond New/Free); sample undershot design (10.7–10.8k vs 16.1k). Promo seen by ~18% iOS / 13% Android; clicked by 0.97% / 0.67%. Monetization non-significant throughout — but the test was underpowered, so this is a weak null, not a demonstrated failure. No decision recorded. |
| **714416002** — tooltip explaining Official Tabs | Killed before launch on a forecast, never tested: *"potential effect on ARPU is no more than +1%. When we need +16%."* |

### Mixed evidence that cuts against the thesis — must be surfaced

**#4443 (425840453) — "widget" paywall on the Official tab, iOS.** A non-full-screen promotional treatment on the Official tab that did move money:

- Members → Accesses **+12.1% (p=0.014)**; Members → Charges **+13.92% (p=0.029)**.
- **But:** total ARPU **+13.23% (p=0.069, not significant)**, and on the **Official-tabs-specific funnel the effect was not significant** (accesses +7.64%, p=0.317; charges +2.4%, p=0.805). The authors themselves planned a cannibalization check.
- **Android never reproduced it:** iter #1 ARPU −1.18% (p=0.882); iter #2 (#4593) ARPU −5.32% (p=0.45); the third arm was significantly worse (ARPU **−18.46%, p=0.019**).
- The authors attribute part of the click lift to UI confusion, not interest: *"users don't fully understand that it isn't a paywall."*

**This does not prove a banner works. It does prevent this corpus from being summarized as uniformly negative:** an in-context promotional treatment on the Official tab itself produced the only significant charge-rate lift in the set.

### What the corpus supports, stated reproducibly

The previous version claimed "three mechanisms significantly increased visibility; none increased revenue." That is not reproducible as written. The defensible version:

**Across several adjacent tests, increased Official-tab discovery or promo exposure has not produced a demonstrated total-revenue lift.** The one clearly-measured discovery win is #6728 (Official Tab Open +7.37% iOS, p<0.001, with ARPU flat). #7424's exposure claim rests on an invalid-targeting, underpowered test. #4443 is the counterexample and is significant on charge rate but not on total ARPU.

### Messaging and copy — not ruled out, just unsupported at the tested precision

**#7229 (761947509, iter 3)** tested 5 different labels at an identical price and found **no significant Total ARPU difference (p = 0.12 … 0.68)**. No equivalence test, confidence interval against a meaningful threshold, or demonstrated power for that metric is recorded on the page.

**Correct claim: copy is not supported as a lever by the tested labels at the available precision. It is not proven to be a no-op.** Establishing that would require an equivalence test or a CI that excludes a practically meaningful effect.

### Cannibalization

**#7361 (787253942)** — the only direct cannibalization measurement in this set. On Android the new banner produced 63 subscriptions while non-winback purchases fell by 28 → **net ≈ 0** (301 → 335 / 297). On iOS, of 102 banner subscriptions only ~30 were incremental. *Relevance limit: winback offer to lapsed subscribers, not an Official Tabs promo.*

### Instrumentation limits (788614610, Metrics Registry v17)

- **`trial-to-charge` — scoped limitation, not a blanket one.** The **First Session Health registry** cannot split trial vs direct-paid: iOS *"Apple does not pass unified_id"*; Android hits a 35GB join limit. **However, page 777817235 reports experiment-level trial→charge values from a separate analysis pipeline.** Before removing the metric from draft 815603314, **verify which source is authoritative for the required placement and segment.** The correct statement is: the registry cannot compute it by placement/segment; experiment-level values may exist elsewhere.
- **Gap 4 — per-placement purchase attribution does not work.** *"The paywall a purchase came through is not visible."* A randomized total-ARPU comparison between arms still works. A "this block drove N purchases" claim does not.
- *"Tab Open cannot be forced. Forcing tab display worsens results — verified in experiment 7256, iteration 1."*

---

## Problem framing

- **Target user (assumption):** free UG App users, iOS, who reach a song where an Official version exists. **The requester did not specify the audience; this is a scoping assumption.**
- **Current behavior, within the guided flow:** users reach the Official tab, 99.47% see the paywall, 0.44% buy on the spot. On later ordinary visits, 3.41% of control users convert.
- **Desired outcome (confirmed):** higher purchase conversion, with no material decline in retention **or tab engagement**.
- **Evidence the status quo is costly:** the only arm with a significant total-ARPU lift (#7622 B, +17.25%, p=0.002) is significantly negative on retention (1d −7.76%, 7d −4.81%, 14d −4.91%, all p<0.001) and on engagement (60s −5.48%, p<0.001). That is the trade the objective rules out.
- **Central evidence gap:** nobody knows why a user who has seen the Official offer declines it. No source distinguishes "did not understand the value" from "understood it and would not pay this price" from "was not in a buying moment." **This is the question worth spending on.**

---

## Causal map

| Mechanism | Status |
|---|---|
| **Awareness, inside the guided flow** | **Not the bottleneck there** — 99.47% of Official-tab reachers see the paywall. Conditional on reaching the tab in B. |
| **Awareness, outside that subset** | **Untested.** No denominator exists for users who never enter the flow, or for any unspecified banner placement. |
| **Comprehension** — sees the offer, has not experienced the value | **Unvalidated; never isolated at UG.** In #7622, trial→charge and AOV stayed flat while purchase volume rose — consistent with more people being *asked*, not more people being *convinced*. Consistency is not proof. |
| **Relevance / timing** — the ask arrives before intent exists | **Unvalidated.** Indirect support: #6728 — *"~half of users who opened Official Tab didn't have active Pro rights."* B's later-visit lift is also consistent with intent forming after the first session, though confounded. |
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

**B fails the confirmed constraint.** It lifts the goal metric and is significantly negative on retention and engagement. The page authors agree: *"We are paying for the lift with engagement… the rollout call is a trade-off decision, not an automatic yes."*

**C is less harmful than B. It is not compliant with the objective, and it is not decision-ready.** Correcting the previous version of this document:

1. **C fails the engagement guardrail.** Tab-view engagement 60s is **−1.88%, p=0.001 — a statistically significant decline**. The objective explicitly includes "no material decline in retention **or tab engagement**." C does not pass it. Whether −1.88% is *practically* material cannot be answered: **no non-inferiority margin exists.**
2. **C's goal metric does not survive multiplicity.** members→total accesses is **+6.90%, p=0.047**. With two treatment arms compared to one control and a Bonferroni correction (α = 0.025), **this does not clear significance.** The page records no multiplicity policy, so this must be treated as unresolved, not as a win.
3. **C's total ARPU is not significant** (+9.47%, p=0.09).
4. **Everything is preliminary.** Pending trials exceed the 5% maturity gate in every branch (iOS 9.9% / 11.6% / 12.6%); only ~25% of charges are older than 14 days. The page: ARPU, AOV, trial→charge, churn and refund *"can still move."*
5. **C's retention is drifting negative as power grows:** 7d/14d moved from p=0.15/0.12 at the 2026-07-05 cut to p=0.09/0.07 at 2026-07-10. Non-significance here is a statement about power, not about safety.

**Page decision status: *"Preliminary — no final decision yet."* Nothing is rolled out. Android: underpowered null (~18.6k per arm vs 46,566 by design), do not roll out.**

---

## Option comparison

All options are conditional on the confirmed objective (App purchase conversion without retention or engagement cost). None has a defined reach, baseline, MDE, or forecast — **no data yet** for all five.

| # | Option | Mechanism | Evidence | Main risk | Confidence |
|---|---|---|---|---|---|
| 1 | **Generic banner** (the request, placement unspecified) | Messaging | Closest precedent failed on Web (#6998, 0.2% interaction). Adjacent App messaging produced discovery without demonstrated revenue (#6728). Counterweight: an in-context promo *on the Official tab itself* did lift charge rate (#4443, +13.92%, p=0.029), though not total ARPU. | Cannot be evaluated at all until placement and audience are specified | **Low — not recommended as specified** |
| 2 | **Always-on Official block in the version selector** | Choice architecture at the moment of version choice | Draft 815603200. C's mechanism, extended past the first session. But C leaks 88% of chooser viewers to free versions and converts below control on later visits. | May trade later monetization for in-the-moment conversion | Low–Medium |
| 3 | **Voluntary micro-demo of one premium feature** | Experience / proven value | Draft 815603314. Comprehension has never been isolated at UG — the largest untested link in the causal map. | May buy curiosity, not willingness to pay; feature choice has no data | Low, **high learning value** |
| 4 | **Surface the offer only on an intent signal** (e.g. locked-feature taps) | Timing / relevance | Not previously proposed. Targets the constraint directly: B's retention damage is consistent with pressing an offer on users who never intended to pay. **No source defines the intent signal or validates that it separates willing buyers from engaged non-buyers.** | The signal may not exist or may not discriminate; reduces reach | **Low — a hypothesis to test, not a candidate to ship** |
| 5 | **Diagnose instead of build** | No-build validation | Mature and recalculate #7622; determine why paywall viewers decline; resolve the Recently-Viewed confound. | Ships nothing this cycle | — |

---

## Recommendation

**1. Establish the ask before closing the solution space.** Placement, audience, and eligibility for the requested banner are unknown. A banner on the tab screen, in the version selector, and on Explore are three different mechanisms with three different evidence sets. **This is the single cheapest thing to resolve, and it is a conversation, not an analysis.**

**2. Under the confirmed objective, do not ship an unspecified generic banner.** The closest direct precedent failed (#6998, Web), adjacent App messaging produced discovery without demonstrated revenue (#6728), and inside the guided flow the offer is already delivered to 99.47% of tab-reachers. **This argument is about the closest precedents and about the specified surface being undefined — it is not a claim that awareness is universally solved.**

**3. Mature and recalculate #7622 before launching anything on this surface.** The maturity gate (<5% pending trials in every branch) is the page's own stated condition, and every revenue number is currently preliminary. **I do not have the enrollment-stop date or the remaining conversion-window distribution, so I cannot estimate when that will be — the previous "one to two weeks" claim was unsupported and is withdrawn.**

**4. Before launching a new test on this surface, check for overlap rather than assuming contamination.** Confirm whether #7622 exposure (`Tour Post Decline Gift Offer Close`) is still active, and whether cohorts, surfaces, or outcome windows would overlap. **The previous flat contamination claim was unverified and is withdrawn.**

**5. Set the non-inferiority margins that do not exist.** Retention 7d and tab-view engagement have no defined practical margin anywhere in these documents. Without one, "C's decline was small" is not a testable statement — and C's engagement decline is already statistically significant.

**6. The highest-value open question is not which surface to decorate — it is why users who have seen the offer decline it.** That is unanswered by every source in this ledger, and it determines whether comprehension (option 3), timing (option 4), or price is the real constraint.

If a shipped change is required this cycle regardless of evidence, that is a scheduling constraint and should be recorded as one — not resolved by building the option with the weakest support.

---

## Next actions

| # | Action | Owner | Due | Status |
|---|---|---|---|---|
| 1 | Establish placement, audience, eligibility, and originator of the banner ask | No data yet | No data yet | Not started |
| 2 | Recalculate #7622 once pending trials < 5% in every branch | No data yet | No data yet | Not started |
| 3 | Define practical non-inferiority margins for Retention 7d and tab-view engagement | No data yet | No data yet | Not started |
| 4 | Resolve the `Official Tabs Recently Viewed` confound in arm B (Finding D) | No data yet | No data yet | Not started |
| 5 | Refresh drafts 815603200 / 815603314 onto the 2026-07-10 cut | No data yet | No data yet | Not started |
| 6 | Determine whether trial-to-charge is computable via the experiment pipeline for the required placement/segment | No data yet | No data yet | Not started |
| 7 | Diagnose why paywall viewers decline: what do the 99.56% do next? | No data yet | No data yet | Not started |

---

## Findings that stand on their own

**A. Both open drafts cite a stale cut.** 815603200 and 815603314 quote the **2026-07-05** cumulative point. All 15 quoted figures verify verbatim, but the page's final table is **2026-07-10** and several have moved: B's Retention 1d −5.9% → **−7.76%**; C's Retention 7d p=0.15 → **0.09**; C's Official access CR +47.60% → **+54.85%**. **Maturation is one shared dependency, not the only blocker:** 815603200 also lacks reach, baseline funnel, four-arm sizing, and margins; 815603314 additionally lacks feature selection, fallback behavior, and instrumentation validation.

**B. `trial-to-charge` — scope the limitation before acting on it.** The First Session Health registry cannot compute it by placement/segment (Gap 1). Page 777817235 nevertheless reports experiment-level trial→charge values from a separate pipeline. **Verify which source is authoritative before removing the metric from 815603314.**

**C. Per-placement purchase attribution does not work (Gap 4).** Any new placement — banner included — cannot have its funnel contribution attributed. A randomized total-ARPU comparison still reads.

**D. Iteration 3 arm B contains an undeclared second paywall, and it may be the confound that explains both its lift and its harm.** The page's Investigation section: a second paywall, **`Official Tabs Recently Viewed`**, re-triggers on every entry to a recently-viewed tab. Reach went from 6.4% to **43.5%**. After dismissal, **0.1% reach Explore — *"the user is locked on the tab."*** The authors describe iter3-B as *"iter2-B plus a retention loop."* This mechanic is not in the design.

**It is plausible — not proven — that B's +17.25% ARPU, its +36% later-visit conversion, and its −4.81% Retention 7d are all effects of the same trap rather than of the guided first-song flow.** B cannot cleanly identify the guided flow's effect. This should be resolved before B is considered for rollout, and it is the strongest argument for treating B's headline number with caution.

---

## What this document does not claim

- It does **not** claim awareness is solved. The 99.47% figure is conditional on reaching the Official tab in variation B and says nothing about upstream awareness or any unspecified placement.
- It does **not** claim additional exposure cannot matter. #7622's own conclusion is that contextual exposure pays off on *later* visits (4.64% vs 3.41%), though B is confounded.
- It does **not** claim a banner would produce zero effect. It claims the mechanism is unsupported by the closest precedents and cannot be evaluated until its placement and audience are specified.
- It does **not** claim copy is a no-op. #7229's null is not an equivalence result.
- It does **not** claim C is safe, compliant, or a natural follow-up. C significantly reduces 60s tab engagement and its goal metric does not survive a multiplicity correction.
- It does **not** claim B's lift is caused by the guided flow. The repeating-paywall loop is an untested alternative explanation.
- It does **not** claim Android behaves like iOS. Android is an underpowered null, not a proven zero.
- It does **not** infer user motivation from conversion data. Why users decline a seen offer is the central open question and no source answers it.
- It does **not** estimate when #7622 will be readable, or assert that a new test would contaminate it. Both prior claims were unsupported and are withdrawn.
- Reach, segment-level baseline, MDE, sample size and revenue forecast for every option: **no data yet.**
