---
authoring_agent: claude-code
status: ready-for-review
created: 2026-07-15
source_experiments: [7622, 6998, 6728, 7424, 7361, 7229, 7256, 7355, 4443, 4183]
source_confluence_pages: [777817235, 815603200, 815603314, 788614610, 721559684, 714416056, 788612885, 714416002, 787253942, 761947509, 425840453, 389323046]
---

# Official Tabs: response to "add a banner"

## Executive answer

**Do not build the banner.** It targets a bottleneck that does not exist.

In the guided first-song flow, 77% of users reach the Official tab, **99.47% of them see the paywall, and 0.44% buy** (#7622, iOS, snapshot 2026-07-10). Message delivery is already saturated. A banner is a messaging mechanism: it increases delivery. Delivery is not the constraint. Conversion on an already-seen paywall is the constraint.

The mechanism also has a direct, documented failure at UG. Experiment **#6998** placed a banner about Official Tabs on the artist page. **0.2% of users interacted with it.** Verdict on the page: *"Minimal interaction with a prominent banner suggests that this monetization tool is not working well. We are closing the project as a failure."*

**The stated goal — raise purchase conversion without a retention cost — is already being answered by a live experiment.** #7622 contains exactly that fork. Variation B buys conversion and pays for it in retention, which fails the constraint. Variation C is the only arm that moves Official Tabs monetization significantly while its retention effects remain non-significant.

**Recommended next step: mature and recalculate #7622 rather than launch anything new.** It is roughly one to two weeks from being readable. Both open drafts (815603200, 815603314) are blocked on the same maturation.

---

## Evidence ledger

All figures pulled from Confluence (`alice.mu.se`) on 2026-07-15. Page 777817235 was refreshed from v135 to v144 before reading.

### The decisive funnel — #7622, iteration 3, iOS, snapshot 2026-07-10

| Step | Variation B (guided first song) |
|---|---|
| "What to play" view | 14,641 |
| Reach Official tab view | 10,595 (77.17%) |
| **See the paywall** | **10,539 (99.47% of tab views)** |
| **Access (purchase)** | **46 — 0.44% of paywall views** |

Fact. Source: 777817235, iteration 3 results, iOS `from_tour` funnel.

*Implication: the offer is seen by essentially everyone who arrives. Adding another surface that shows the offer cannot move a 0.44% conversion rate on an offer that is already shown to 99.47% of the population.*

### Prior UG evidence on the banner / messaging mechanism

| Source | Mechanism tested | Result |
|---|---|---|
| **#6998** (721559684) — Official Tabs banner on the artist page | The literal requested solution | **Red FAIL.** Block interaction **0.24% / 0.20%**. Absolute gain: +2 and +3 accesses. No p-values computed. Page: *"any revenue difference is highly unstable"*, project closed as a failure. |
| **#6728** (714416056) — Official Tabs in search suggestions | Discoverability | Official Tab Open **+7.37% iOS / +6.89% Android (p<0.001)**. ARPU **−2.55% (p=0.451)** iOS, Conv to Access **+0.17% (p=0.942)** iOS. **Closed without rollout.** Page: *"~half of users who opened Official Tab didn't have active Pro rights."* |
| **#7424** (788612885) — preview prewall promo on Official Tabs | Messaging + preview | ~18% iOS / 13% Android saw the promo; **0.97% / 0.67% clicked**. All monetization metrics non-significant (p = 0.13 … 0.98). iOS targeting broken (promo shown beyond New/Free); sample undershot design. No decision recorded. |
| **714416002** — tooltip explaining Official Tabs | Awareness | Killed before launch: *"potential effect on ARPU is no more than +1%. When we need +16%."* |
| **#7229** (761947509, iter 3) — 5 different copy labels at identical price | Isolates the effect of wording | **No significant difference in Total ARPU** across any label (p = 0.12 … 0.68). |
| **#7361** (787253942) — winback banner on Explore | Cannibalization | The only direct cannibalization measurement at UG. Android: banner produced 63 subscriptions, non-winback fell by 28 → **net ≈ 0** (301 → 335 / 297). |

**Cross-cutting pattern (fact): three separate mechanisms significantly increased Official Tabs visibility. None of them increased revenue.**

### Instrumentation blockers — 788614610 (First Session Health — Metrics Registry)

- **Gap 1 — `trial-to-charge` is currently not computable.** iOS: *"Apple does not pass unified_id"*. Android: the join *"hits the 35GB memory limit"*. It cannot be used as a success metric today.
- **Gap 4 — per-placement purchase attribution does not work.** *"The paywall a purchase came through is not visible."* This does not block a randomized A/B readout of total ARPU between arms, but it does block funnel-level attribution of any new placement — including a banner.
- Direct empirical warning: *"Tab Open cannot be forced. Forcing tab display worsens results — verified in experiment 7256, iteration 1."*

---

## Problem framing

- **Target user:** free UG App users, iOS, who reach a song where an Official version exists.
- **Current behavior:** they reach the Official tab, see the paywall (99.47%), and do not purchase (99.56%).
- **Desired outcome:** higher purchase conversion, with no material decline in retention or tab engagement.
- **Evidence the current state is costly:** the one flow that did lift revenue (#7622 Variation B, total ARPU +17.25%, p=0.002) did so at a significant retention cost (Retention 1d −7.76%, 7d −4.81%, 14d −4.91%, all p=0.000). That trade is what the goal explicitly rules out.
- **What remains unknown:** why users who have seen the offer do not buy it. No UG source distinguishes "did not understand the value" from "understood it and did not want it at this price" from "was not in a buying moment". This is the central evidence gap.

The problem is not stated as a feature. Note that it is also not an awareness problem — the funnel above rules that out.

---

## Causal map

Plausible reasons a user sees the Official paywall and does not buy:

| Mechanism | Status |
|---|---|
| **Awareness** — user does not notice Official exists | **Ruled out.** 99.47% of tab-reachers see the paywall. |
| **Comprehension** — user sees it but has not experienced why it is worth paying for | **Unvalidated.** Never isolated at UG. In #7622, trial→charge and AOV stayed flat while purchase volume rose, which is consistent with more people being asked rather than more people being convinced. |
| **Relevance / timing** — the ask arrives before purchase intent exists | **Unvalidated, but indirectly supported.** #6728: *"~half of users who opened Official Tab didn't have active Pro rights"* — opening ≠ intent. The retention damage in B is consistent with pressing an offer on users who never intended to pay. |
| **Choice architecture** — Official and Community are not presented as a real choice | **Partially supported.** #7622 Variation C (version chooser) raised Official charge CR +28.65% (p=0.006) without a significant retention cost. |
| **Price / value** | **Unvalidated.** No UG experiment in this set isolates price for Official Tabs. |
| **Message / copy** | **Ruled out as a lever.** #7229 tested 5 labels at one price and found no significant Total ARPU difference. |

---

## What the live experiment already says

**#7622, iteration 3, iOS, snapshot 2026-07-10.** Sample: 24,685 / 24,316 / 24,503 members. Duration 21 days vs 7 by design. All four design-vs-reality checks complete; spread under 1.5%, no SRM concern.

Variation 2 = B (guided first song). Variation 3 = C (version chooser on paywall dismiss).

| Metric | Control | B | B diff (p) | C | C diff (p) |
|---|---|---|---|---|---|
| Total ARPU | $0.66 | $0.77 | **+17.25% (0.002)** | $0.72 | +9.47% (0.09) |
| members→buyers (charge CR) | 3.66% | 4.17% | **+13.87% (0.004)** | 3.74% | +2.08% (0.65) |
| Official Tabs ARPU | $0.16 | $0.24 | +52.12% (0.000) | $0.22 | **+34.94% (0.003)** |
| Official access CR | 1.58% | 2.62% | +65.65% (0.000) | 2.45% | **+54.85% (0.000)** |
| Official charge CR | 0.86% | 1.27% | +47.27% (0.000) | 1.11% | **+28.65% (0.006)** |
| Retention 1d | 15.97% | 14.73% | **−7.76% (0.000)** | 15.68% | −1.76% (0.39) |
| Retention 7d | 34.00% | 32.37% | **−4.81% (0.000)** | 33.27% | −2.15% (0.09) |
| Retention 14d | 37.58% | 35.74% | **−4.91% (0.000)** | 36.80% | −2.09% (0.07) |
| Tab-view engagement 60s | 73.43% | 69.40% | **−5.48% (0.000)** | 72.05% | −1.88% (0.001) |

**B fails the stated constraint.** It raises conversion and significantly reduces retention and engagement. The page authors say so themselves: *"We are paying for the lift with engagement… the rollout call is a trade-off decision, not an automatic yes."*

**C is the only arm consistent with the goal.** It moves Official Tabs monetization significantly while its retention effects stay non-significant.

### Three qualifications that prevent recommending C for rollout

1. **Everything above is preliminary.** Pending trials exceed the 5% maturity gate in every branch (iOS 9.9% / 11.6% / 12.6%). Only about a quarter of charges are older than 14 days. The page states ARPU, AOV, trial→charge, churn and refund *"can still move"*.
2. **Non-significant is not safe.** C's retention is drifting negative as power grows: Retention 7d / 14d moved from p=0.15 / 0.12 at the 2026-07-05 cut to **p=0.09 / 0.07** at 2026-07-10. That is a warning, not a clean bill of health. A non-inferiority margin must be set before this can be called safe; none exists today (gap).
3. **C's total ARPU is not significant** (+9.47%, p=0.09). C is not decision-ready.

**Decision status on the page: *"Preliminary — no final decision yet."* Nothing is rolled out. Android: no effect, underpowered null, do not roll out.**

---

## Option comparison

| # | Option | Mechanism | Target metric | Evidence | Main risk | Confidence |
|---|---|---|---|---|---|---|
| 1 | **Banner in the App** (the request) | Messaging | Official access CR | **Against:** #6998 (0.2% interaction), #6728, #7424, #7229. Exposure already 99.47%. | Repeats a known failure; adds a fourth "make it more visible" test | **Low — not recommended** |
| 2 | **Always-on Official block in the version selector** | Choice architecture at the moment of version choice | Total ARPU | **For:** #7622 arm C. Extends C's mechanism beyond the first session. Existing draft 815603200. | C's own total ARPU is not yet significant; retention drift unresolved | Medium |
| 3 | **Voluntary micro-demo of one premium feature** | Experience / proven value | 14-day net ARPU | No UG experiment has ever isolated comprehension. Existing draft 815603314. | May produce curiosity without willingness to pay; feature choice has no data | Low–Medium, high learning value |
| 4 | **Surface the offer only on an intent signal** (locked-feature taps, replay, favourite) | Timing / relevance / personalization | Official charge CR, with retention as co-primary | Not previously proposed. Directly targets the constraint: B's retention damage is consistent with pressing the offer on users who never intended to pay. | Reduces reach; requires an intent signal that is not yet defined | Low (hypothesis), **best fit to the stated goal** |
| 5 | **Diagnose instead of build** | No-build validation | — | Mature and recalculate #7622; investigate why 99.56% of paywall viewers do not convert; fix Gap 1 and Gap 4. | Delivers no shipped change this cycle | — |

Options 1–4 differ by mechanism, not by wording or styling.

---

## Recommendation

**1. Do not build the banner.** The mechanism has a direct failure at UG (#6998) and zero monetization return across three adjacent tests, and the bottleneck it addresses — message delivery — is already saturated at 99.47%.

**2. The cheapest next learning step is maturation, not a new experiment.** Recalculate #7622 once the pending-trial share drops below 5% in every branch. The decision that answers the stated goal is already inside a running experiment. Launching a new test now would spend sample on a question that is about to be answered, and would contaminate the surface that #7622 is still measuring.

**3. Before that read, set the non-inferiority margins that do not exist.** Retention 7d and tab-view engagement have no defined margin anywhere. Without one, "C's retention decline was not significant" is an untestable claim rather than a pass.

**4. If C holds after maturation,** the natural follow-up is Option 2 (always-on version selector, draft 815603200) — it takes C's mechanism and extends it past the first session. **Add Option 4 as an arm**: it is the strongest candidate for capturing B's conversion without B's retention cost, and no one has tested it.

If the requester needs a shipped change this cycle regardless, say so — that is a scheduling constraint, not evidence, and it should be recorded as such rather than resolved by building the option with the weakest support.

---

## Next actions

| # | Action | Owner | Status |
|---|---|---|---|
| 1 | Recalculate #7622 once pending trials < 5% in every branch | No data yet | Not started |
| 2 | Define non-inferiority margins for Retention 7d and tab-view engagement | No data yet | Not started |
| 3 | Refresh drafts 815603200 and 815603314 onto the 2026-07-10 cut (see below) | No data yet | Not started |
| 4 | Remove `trial-to-charge` from 815603314 success metrics until Gap 1 is fixed | No data yet | Not started |
| 5 | Investigate the undeclared second paywall in iteration 3 B (see below) | No data yet | Not started |
| 6 | Diagnose the 0.44% paywall→access conversion: what do non-converters do next? | No data yet | Not started |

---

## Findings that stand on their own

**A. Both open drafts cite a stale cut.** 815603200 and 815603314 quote the **2026-07-05** cumulative point. All 15 quoted figures verify verbatim — but the page's final table is **2026-07-10**, and several numbers have moved materially: B's Retention 1d −5.9% → **−7.76%**; C's Retention 7d p=0.15 → **0.09**; C's Official access CR +47.60% → **+54.85%**. Both drafts should be refreshed, and every figure should carry the preliminary label.

**B. `trial-to-charge` is not computable today (Gap 1).** Draft 815603314 lists it among revenue-quality metrics. It cannot be read until the instrumentation is fixed.

**C. Per-placement purchase attribution does not work (Gap 4).** *"The paywall a purchase came through is not visible."* Any new placement — banner included — cannot have its funnel contribution read. A randomized total-ARPU comparison still works; a "this block drove N purchases" claim does not.

**D. Iteration 3 arm B contains an undeclared second paywall.** The page's own Investigation section: a second paywall, **"Official Tabs Recently Viewed"**, re-triggers on every entry to a recently-viewed tab. Reach went from 6.4% to **43.5%**. After dismissal, **0.1% reach Explore — *"the user is locked on the tab"***. The authors describe iter3-B as *"iter2-B plus a retention loop"*. This is a mechanic that is not in the design, and it is a plausible cause of a material share of B's retention damage. **It means B's +17.25% ARPU and its −4.81% Retention 7d may both be effects of the trap rather than of the guided flow.** This should be resolved before B is considered for rollout.

---

## What this document does not claim

- It does **not** claim a banner would produce zero effect. It claims the mechanism is unsupported at UG, addresses a saturated bottleneck, and has a direct precedent failure.
- It does **not** claim C is safe for retention. C's retention effects are non-significant and drifting negative; no non-inferiority margin exists to test them against.
- It does **not** claim C is ready to roll out. Its total ARPU is not significant (p=0.09) and all revenue metrics are preliminary.
- It does **not** claim Android behaves like iOS. Android in #7622 is an underpowered null (~18.6k per arm against 46,566 by design), not a proven zero.
- It does **not** infer user motivation from conversion data. Why users decline an offer they have seen is the central open question, and no source in this ledger answers it.
- Reach, segment-level baseline funnel, MDE, sample size and expected revenue for any new experiment: **no data yet.**
