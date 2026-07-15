---
reviewer: codex
draft: workspace/drafts/claude/official-tabs-banner-shaping-v2.md
verdict: READY WITH CHANGES
reviewed: 2026-07-15
draft_sha256: f2642cf9ce94a42a504919f36a2dae7259482c038ab682ba1c1fed17d3f92171
---

# Independent review: Official Tabs banner shaping v2

## Verdict

**READY WITH CHANGES.** The conditional recommendation not to ship an unspecified generic banner is credible and the prior review's decision-critical errors are corrected, but causal wording, instrumentation scope, decision-premise traceability, and action ownership need specified changes before publication.

## Review scope and limitations

- Frozen artifact: `workspace/drafts/claude/official-tabs-banner-shaping-v2.md`, modified 2026-07-15 05:18:41 +0900, 26,769 bytes, SHA-256 as recorded above.
- Repository state at review: the draft is untracked; `main` is at `31717f9`. Existing unrelated working-tree changes were not touched.
- Verified against the cited local Confluence snapshots: 777817235 v144, 815603200 v2, 815603314 v2, 788614610 v17, 721559684 v25, 714416056 v33, 788612885 v22, 714416002 v15, 787253942 v26, 761947509 v53, 425840453 v20, and 389323046 v15.
- Live `ug-analytics` verification was attempted through the stable CLI and was unavailable because `UG_COOKIE` and the CLI `.env` were absent. Numerical findings therefore verify the cited Confluence snapshots, not a fresh analytics API response.
- The three claims attributed to “Session confirmation, 2026-07-15” could not be independently inspected because no notes, transcript, ticket, or written brief is cited.

## Blockers

None. The remaining issues do not reverse the narrow recommendation, invalidate the central experiment read, or require a different verdict.

## Major findings

### MAJOR 1 — The draft still turns an untested, confounded later-funnel association into a causal result

**Exact claims:** Executive answer item 3 (line 44), “Contextual exposure demonstrably shifts later behavior”; corrected-funnel interpretation (lines 78–80); and “What this document does not claim” (line 262), “contextual exposure pays off on later visits.”

Page 777817235 reports 4.64% access per ordinary Official-tab visit in B versus 3.41% in control, but the cited funnel provides no uncertainty for that comparison and does not document how repeated users or sessions are handled in the `other` cut. More importantly, B contains the undeclared, repeating `Official Tabs Recently Viewed` paywall. The draft correctly surfaces that confound elsewhere, but “demonstrably shifts” and “pays off” still imply that guided contextual exposure caused the later behavior.

This matters because the same result is used to keep contextual exposure in the causal story and to argue that delivery can matter. The observed difference may instead reflect repeated paywall firing, changed visit composition, multiple visits by the same users, or some combination.

**Smallest correction:** replace the causal wording with: “B is associated with a higher access rate on later `other` Official-tab visits (4.64% vs 3.41%), but the source reports no uncertainty for this cut and B's repeated-paywall loop prevents attribution to the guided exposure.” In the funnel section, label both “more later visits” and “higher conversion” as descriptive rather than demonstrated treatment mechanisms.

### MAJOR 2 — “Showing the offer again is not the lever” is not established by 99.47% initial paywall reach

**Exact claim:** Executive answer item 1 (line 40), “Within that subset, showing the offer again is not the lever.”

The 99.47% figure establishes that initial paywall reach is nearly saturated among B users who reached the Official tab. It does not establish that frequency, sequencing, comprehension, or a second offer cannot change conversion. In fact, the draft's own Finding D says the repeating second paywall is a plausible explanation for both B's monetization lift and harm.

This matters because the sentence closes a mechanism that the experiment did not isolate and that may be active in the treatment.

**Smallest correction:** say, “Within that subset, increasing initial paywall reach is not the bottleneck.” Do not generalize from reach to the effectiveness of repeated exposure.

### MAJOR 3 — The per-placement attribution limitation is stated more broadly than its source supports

**Exact claims:** Instrumentation limits (line 138) and Finding C (line 251), especially “Any new placement — banner included — cannot have its funnel contribution attributed.”

Metrics Registry v17 documents that the **First Session Health registry** cannot identify which paywall produced a purchase. It does not establish that every experiment pipeline or every proposed placement lacks usable source attribution. Other cited pages report source-specific funnels from separate pipelines, including experiment-level `trial-to-charge` on 777817235 and funnel-source splits on 787253942. Those do not automatically prove valid attribution for the proposed banner, but they contradict the blanket scope.

This matters because the current wording could cause the team to discard a measurable placement funnel or omit an instrumentation check that should instead be verified.

**Smallest correction:** mirror the scoped `trial-to-charge` treatment: “The First Session Health registry cannot attribute purchases by placement. Verify whether the experiment/event pipeline can do so for the selected banner placement; randomized total ARPU remains valid regardless.”

### MAJOR 4 — The confirmed objective and platform remain unauditable decision premises

**Exact claims:** Request table (lines 21–23), the repeated phrase “confirmed objective,” and the desired-outcome statement (line 147).

The draft now distinguishes confirmed, assumed, and unknown scope, which fixes the previous version's hidden-assumption problem. However, the only evidence for objective, App platform, and banner flexibility is an unavailable “Session confirmation.” A reviewer or decision-maker cannot reproduce those facts from the cited corpus.

This matters because the evidence ranking and recommendation are explicitly conditional on those three facts. A different objective or platform could change the option ranking.

**Smallest correction:** cite durable notes, a ticket, or a written requester confirmation. If none exists, change the status from “Confirmed by the requester” to “Reported as confirmed in the authoring session; not independently verifiable” and require reconfirmation as Action 1.

### MAJOR 5 — The next step is decision-correct but not operationally owned

**Exact section:** Next actions (lines 231–241).

The draft correctly refuses to invent owners and dates, but every action is assigned to “No data yet.” The first recommendation is a conversation to establish placement, audience, eligibility, and originator; without an owner, the document does not identify who closes the premise that blocks all downstream evaluation.

This matters to decision readiness: readers can understand the conclusion but cannot reliably act on it.

**Smallest correction:** before publication, assign an accountable owner to Action 1 and to the #7622 maturation/confound checks. A due date may remain explicitly unset if no deadline exists, but ownership should not.

## Minor findings

### MINOR 1 — One `other` funnel count does not match the v144 source

The draft reports approximately 13,079 control Official-tab views (line 74). Page 777817235 v144 reports 13,092. The 446 accesses and 3.41% rate are correct, so the decision is unaffected.

**Correction:** use 13,092, or omit the approximate count and retain the verified rate.

### MINOR 2 — #7424 combines treatment-arm maxima instead of reporting the arm ranges

The draft says the promo was seen by about 18%/13% and clicked by 0.97%/0.67%. In the free-user funnel, iOS view/click rates range 18.14%/0.65% to 18.69%/0.97%; Android ranges 13.30%/0.67% to 13.43%/0.65%. The current sentence selects the higher click rate on each platform from different arms.

**Correction:** report the ranges by platform or name the selected arm for each figure.

### MINOR 3 — “Did move money” overstates #4443's supported result

The significant results are overall members→accesses and members→charges; total ARPU is non-significant. The following bullets correctly explain this, but the introductory phrase “did move money” is stronger than the evidence.

**Correction:** replace it with “did move overall access and charge rates.”

### MINOR 4 — The source ledger contains an unused experiment identifier

`source_experiments` declares #7355, but the body does not use #7355 as a source claim or map it to a page. The number also appears inside page 777817235 as an `item_id`, making the intended provenance ambiguous.

**Correction:** either map #7355 to the exact claim and source page or remove it from `source_experiments`.

### MINOR 5 — “Retention is drifting negative as power grows” infers a trend from two p-value snapshots

The source supports that C's 7d/14d p-values moved from 0.15/0.12 to 0.09/0.07 and that effect estimates remain negative. It does not establish a monotonic trend or that power alone caused the movement.

**Correction:** say, “At the later snapshot, C's retention estimates remain negative and the p-values are lower; non-significance is not evidence of safety.”

## Claim audit

| Claim | Type | Source | Status | Required correction |
|---|---|---|---|---|
| Objective is purchase conversion without retention cost; platform is App; banner is flexible | Fact / decision premise | “Session confirmation, 2026-07-15” | **Unverifiable** | Link durable confirmation or label as reported but not independently verifiable. |
| Placement and audience are not established | Evidence gap | Draft/source set | Supported | Preserve. |
| 99.47% of B Official-tab reachers see the paywall | Calculation | 777817235 v144 | Supported | Preserve the conditional denominator. |
| 0.44% of those paywall viewers access in-tour | Calculation | 777817235 v144 | Supported | Preserve as immediate in-tour conversion. |
| Showing the offer again is not the lever | Causal conclusion | 777817235 v144 | **Partially supported** | Narrow to “increasing initial paywall reach is not the bottleneck.” |
| B demonstrably shifts later behavior / contextual exposure pays off later | Causal conclusion | 777817235 v144 | **Partially supported** | Report the descriptive association, missing uncertainty, repeated-user ambiguity, and B confound. |
| Corrected B funnel: 77.17% is 10,595 / 13,730; 72.37% is 10,595 / 14,641 | Calculation | 777817235 v144 | Supported | Preserve. |
| C in-tour access is 270 / 10,576 = 2.55%, about 5.8× B | Calculation | 777817235 v144 | Supported | Preserve. |
| Control has about 13,079 `other` Official-tab views | Fact | 777817235 v144 | **Contradicted** | Source reports 13,092. |
| B/C/control `other` access rates are 4.64% / 3.26% / 3.41% | Calculation | 777817235 v144 | Supported | Add that the source provides no p-values for these cuts. |
| #6998 banner interaction was 0.24% / 0.20%, with +2 / +3 accesses, and project failed | Fact | 721559684 v25 | Supported | Preserve Web/artist-page qualification. |
| #6728 lifted Official Tab Open but not monetization | Experiment result | 714416056 v33 | Supported | Preserve. |
| #7424 had broken iOS targeting, under-design sample, low promo use, and non-significant monetization | Experiment result | 788612885 v22 | Supported with correction | Report view/click ranges by treatment arm. |
| Tooltip concept was rejected before launch on a forecast | Fact | 714416002 v15 | Supported | Preserve that this was not experiment evidence. |
| #4443 lifted overall access and charge rates but not total ARPU or the Official-specific funnel | Experiment result | 425840453 v20 | Supported | Replace “did move money” with the exact significant outcomes. |
| Android did not reproduce #4443 and one #4593 arm was significantly worse | Experiment result | 425840453 v20 | Supported | Preserve. |
| #7229 does not establish copy equivalence | Analytics conclusion | 761947509 v53 | Supported | Preserve the precision caveat. |
| #7361 directly shows substantial cannibalization in its winback context | Experiment result | 787253942 v26 | Supported | Preserve relevance limit. |
| Trial-to-charge is unavailable in the registry but may exist in another pipeline | Instrumentation fact | 788614610 v17; 777817235 v144 | Supported | Preserve. |
| No placement can have purchase attribution | Instrumentation fact | 788614610 v17 | **Partially supported** | Scope to First Session Health registry and verify the selected experiment pipeline. |
| #7622 B lifts goal metric/ARPU and harms retention/engagement | Preliminary experiment result | 777817235 v144 | Supported with qualification | Preserve maturity and confound warnings adjacent to the result. |
| C's 60s engagement declines 1.88%, p=0.001 | Experiment result | 777817235 v144 | Supported | Preserve. |
| C fails a Bonferroni threshold of 0.025 for two treatment-control comparisons | Calculation | 777817235 v144 | Supported | Keep explicit that Bonferroni is a reviewer-applied policy because none was pre-specified. |
| All revenue results are preliminary because pending trials exceed the 5% gate | Maturity fact | 777817235 v144 | Supported | Preserve. |
| Iter3-B includes an undeclared repeating paywall loop | Experiment-integrity fact | 777817235 v144 | Supported | Preserve. |
| The loop may explain both B's lift and harm | Causal hypothesis | 777817235 v144 | Supported as a hypothesis | Keep “plausible, not proven.” |
| The why-behind-decline question is the highest-value open question | Product decision | No direct source | **Partially supported** | Present as the recommended learning priority, not an evidence-established ranking. |
| Do not ship an unspecified generic banner | Conditional decision | Combined source set | Supported | Preserve conditionality and require ask definition first. |

## Analytics validity check

- **Assignment and exposure:** #7622's assignment population is explicitly tied to `Tour Post Decline Gift Offer Close`; the draft no longer generalizes it to all App users. Preserve this distinction.
- **Population and exclusions:** the selected iOS/free/Official-eligible target remains an author scoping assumption, while the requested banner audience is unknown. This is correctly labeled.
- **Events and denominators:** the in-tour funnel denominators are now correct and reproducible. The control `other` view count needs the minor correction above.
- **Repeated users and sessions:** handling is not documented for the later `other` visit conversion cut. Do not describe 4.64% versus 3.41% as a demonstrated mechanism until the unit of analysis and uncertainty are known.
- **Maturity:** correctly treated as preliminary. Every branch exceeds the source's 5% pending-trial gate; approximately one quarter of charges are older than 14 days.
- **Sample and balance:** iOS samples 24,685 / 24,316 / 24,503 over 21 days are correctly reported; Android is correctly labeled underpowered relative to 46,566 per arm.
- **Uncertainty:** p-values are reported for the headline tables, but not for the `other` funnel comparison. Practical confidence intervals are absent from the source.
- **Multiplicity:** the draft properly identifies that the source has no policy and labels Official-specific cuts exploratory. Its Bonferroni statement is transparent, but should remain described as a reviewer-applied correction rather than the experiment's original decision rule.
- **Guardrails:** the draft correctly rejects “non-significant = safe” and identifies the missing non-inferiority margins. C's significant engagement decline is not hidden.
- **Experiment integrity:** the repeated `Official Tabs Recently Viewed` paywall is a material treatment confound. The draft correctly prevents attribution of B's headline lift to the designed guided flow alone.
- **Causal language:** generally much improved, but the later-behavior and repeated-exposure claims in Major findings 1–2 must be narrowed.
- **Fresh API reproducibility:** unavailable in this review because the read-only CLI lacked authentication. The draft correctly discloses that its evidence is snapshot-based.

## Product-logic and solution-space check

The draft now presents a materially differentiated solution space: generic messaging, choice architecture, experienced-value proof, intent-timed exposure, and no-build diagnosis. That is decision-useful and avoids treating five banner designs as five mechanisms.

The defensible causal chain is:

```text
Observed: initial paywall reach is 99.47% after Official-tab reach in B
Known limit: this says nothing about upstream awareness, comprehension, frequency, or another placement
Closest mechanism evidence: Web artist-page banner had negligible interaction and no reliable monetization lift
Mixed evidence: in-context Official-tab treatment lifted charge rate but not total ARPU
Current experiment: B lifts monetization and harms users, but an undeclared loop prevents mechanism attribution
Decision: do not ship an unspecified banner; define the ask and close the cheapest evidence gaps first
```

Two links remain intentionally open: why users decline after seeing the offer, and whether a specified App placement has enough eligible reach. The draft correctly does not invent answers. Its cheapest learning sequence is sensible: confirm the ask, mature/recalculate #7622, resolve the loop, then choose a mechanism test. To become operational, that sequence needs accountable owners.

## Required changes, ordered by decision impact

1. Replace “demonstrably shifts later behavior” and “pays off on later visits” with a descriptive, uncertainty-aware statement that foregrounds the repeated-paywall confound and unknown unit-of-analysis handling.
2. Replace “showing the offer again is not the lever” with “increasing initial paywall reach is not the bottleneck.”
3. Scope the per-placement attribution limitation to the First Session Health registry and require verification of the selected experiment pipeline.
4. Add durable evidence for the requester-confirmed objective/platform/flexibility, or mark those premises as reported but independently unverifiable and require reconfirmation.
5. Assign accountable owners to establishing the ask and to the #7622 maturation/confound checks.
6. Correct control `other` Official-tab views from approximately 13,079 to 13,092.
7. Report #7424 promo view/click ranges by treatment arm instead of combining platform maxima.
8. Replace #4443 “did move money” with the exact supported result: significant overall access and charge-rate lifts, non-significant total ARPU.
9. Remove or explicitly map experiment #7355 in the source ledger.
10. Rewrite the C retention sentence as a later-snapshot observation rather than a power-driven trend claim.

## What is already solid and should be preserved

- The recommendation is conditional on the known objective and explicitly refuses to evaluate an unspecified placement as though it were one product treatment.
- The #7622 funnel denominator is corrected and every intermediate step needed to reproduce 77.17%, 99.47%, and 0.44% is present.
- The document no longer claims awareness is universally solved or that copy is proven ineffective.
- #6998 is correctly qualified as the same promotional mechanism on a different platform and placement.
- Mixed evidence from #4443 and the cannibalization evidence from #7361 are surfaced rather than selected away.
- Preliminary revenue, Android underpowering, missing non-inferiority margins, and absent multiplicity policy are all explicit.
- C is correctly classified as less harmful but neither compliant nor decision-ready.
- The repeated-paywall loop is treated as an experiment-integrity confound, and its causal contribution remains explicitly unproven.
- The option set spans distinct causal mechanisms and includes a no-build learning option.
- The draft avoids invented reach, forecasts, deadlines, and user motivation.
