---
reviewer: codex
draft: workspace/drafts/claude/official-tabs-banner-shaping.md
verdict: NOT READY
reviewed: 2026-07-15
draft_sha256: 974361983ff4297b1c7a35dce42e97a28f236c8357243c2c63c52d13392b905f
---

# Independent review: Official Tabs banner shaping

## Verdict

**NOT READY.** The recommendation against a generic banner is plausible, but the executive argument is not yet decision-safe: it generalizes a downstream conditional funnel to the whole target population, treats an inferred objective as stated fact, and overstates what null and preliminary results establish.

## Review scope and limitations

- Frozen artifact: `workspace/drafts/claude/official-tabs-banner-shaping.md`, modified 2026-07-15 05:07:27 +0900, 16,411 bytes, SHA-256 above.
- Repository state at review: draft is untracked; `main` is at `31717f9`.
- Verified against local Confluence snapshots for the cited pages. Key snapshots include page 777817235 v144, page 721559684 v25, page 714416056 v33, page 788612885 v22, page 761947509 v53, page 787253942 v26, and metrics registry page 788614610 v17.
- Live `ug-analytics` verification was unavailable because the local CLI had no authenticated `UG_COOKIE`. Numerical findings below therefore verify the cited Confluence snapshots, not a fresh analytics API response.

## Blockers

### BLOCKER 1 — The central “awareness is ruled out” conclusion uses the wrong population and one wrong denominator

**Draft locations:** lines 13–15, 33–40, 71, 81, 126, and 138.

The draft says 77.17% of 14,641 users reached the Official tab. Page 777817235 shows a longer funnel:

| Step | Users | Correct conversion |
|---|---:|---:|
| What to play view | 14,641 | — |
| What to play success | 13,892 | 94.88% |
| How to play view | 13,891 | ~100% |
| How to play success | 13,730 | 98.84% |
| Official tab view | 10,595 | 77.17% of how-to-play successes; **72.37% of what-to-play views** |
| Paywall view | 10,539 | 99.47% of Official-tab views |
| Access | 46 | 0.44% of paywall views |

The 99.47% figure establishes that paywall delivery is saturated **after a user reaches the Official tab in variation B**. It does not establish awareness among all eligible users, all users who start the flow, or users at a different banner placement. The draft’s target population is broader than the denominator used to rule awareness out.

The same source also says the immediate in-tour purchase rate stayed low while the ARPU lift appeared through later ordinary Official-tab visits. That evidence is incompatible with the blanket statement that additional delivery cannot matter; it suggests that contextual exposure may affect later behavior, although iteration B is confounded by the repeated-paywall loop.

**Required correction:** narrow the conclusion to: “Within variation B, paywall delivery after Official-tab reach is not the bottleneck. A generic promotional banner is not supported by the closest precedents, but awareness outside this downstream subset is not ruled out.” Confirm the proposed banner’s placement and denominator before deciding which awareness problem is being tested.

### BLOCKER 2 — The document presents an inferred objective and scope as if the requester stated them

**Draft locations:** lines 19, 65–69, 118, and 138–146.

The literal request is “add a banner.” The draft calls “raise purchase conversion without a retention cost” the **stated goal** and fixes the target to free iOS app users who reach a song with an Official version. No cited source ties the requester’s banner ask to that exact objective, platform, placement, segment, or decision deadline.

This matters because the evidence changes by context: #6998 is a UG **Web** artist-page banner; #6728 and #7622 are app flows; #7361 is a winback offer for lapsed subscribers. A banner for another surface or objective would require a different evidence ranking.

**Required correction:** start with “Requested solution: add a banner; objective, platform, placement, audience, and deadline: not established.” Treat the current iOS Official-tabs monetization framing as a working assumption. Ask for confirmation or explicitly make the recommendation conditional on that assumption.

## Major findings

### MAJOR 1 — C is not yet “consistent with the goal” when its engagement guardrail is significantly worse

**Draft locations:** lines 19, 67, 106, and 110.

The stated desired outcome includes no material decline in retention **or tab engagement**. Variation C has Tab-view engagement 60s −1.88%, p=0.001. The draft then says C is the only arm consistent with the goal because retention is non-significant. That ignores a statistically significant guardrail decline and the absence of a practical non-inferiority margin.

**Required correction:** say C is less harmful than B and moves Official monetization, but it has not passed the full constraint. Do not call it consistent, safe, or a natural follow-up until mature data and pre-defined practical margins are available.

### MAJOR 2 — Null results are treated as proof that copy and messaging do not work

**Draft locations:** lines 50, 53, 86, 126, and 138.

#7229 found no significant Total ARPU difference among the tested labels. Without an equivalence test, confidence interval against a meaningful effect threshold, or demonstrated power for that metric, “no significant difference” does not rule copy out as a lever. #7424 is explicitly under-sampled and has broken iOS targeting, so it is weak negative evidence rather than a clean failure.

**Required correction:** replace “ruled out” with “not supported by the tested labels at the available precision.” Report MDE or confidence intervals when available. Keep #7424 as low-confidence evidence because of targeting and sample validity problems.

### MAJOR 3 — The direct banner precedent needs an external-validity qualifier and counterevidence needs to be surfaced

**Draft locations:** lines 17, 46, 53, and 138.

#6998 is strong evidence against the literal creative mechanism in its tested context, but it is a Web artist-page experiment, not the iOS first-song flow. The draft should not present it as an exact product-context replication.

The frontmatter also cites #4443 / page 425840453 but omits it from the ledger. That adjacent iOS Official-tab paywall treatment produced a significant increase in overall members→charges (+13.92%, p=0.029), while total ARPU remained non-significant (+13.23%, p=0.069) and Official-tab-specific monetization was non-significant. It does not prove a banner works, but it is relevant mixed evidence and prevents the corpus from being summarized as uniformly negative.

**Required correction:** label #6998 “same promotional mechanism, different platform and placement.” Add #4443 and any other declared sources that materially cut against the thesis, or remove unused source IDs from the frontmatter.

### MAJOR 4 — “Three mechanisms significantly increased visibility; none increased revenue” is not reproducible as written

**Draft location:** line 53.

The statement does not name the three mechanisms, define “visibility,” or provide the comparison and p-value for each. #7424 introduces a new promo with no equivalent control exposure and has invalid targeting; calling that a significant visibility increase is not supported by the cited page. #6728 clearly increased Official Tab Open, but the other two members of the claimed set are ambiguous.

**Required correction:** either enumerate all three with metric, denominator, effect, p-value, and revenue result, or downgrade this to a qualitative pattern: “Across several adjacent tests, higher Official-tab or promo exposure did not produce a demonstrated total-revenue lift.”

### MAJOR 5 — Maturation timing and experiment contamination are asserted without evidence

**Draft locations:** lines 21 and 140.

The source supports the <5% pending-trial maturity gate, but it does not support “roughly one to two weeks.” That estimate requires enrollment-stop dates and the remaining conversion-window distribution. The claim that a new experiment would contaminate #7622 also requires confirmed overlap in eligibility, active exposure, surfaces, and outcome windows.

**Required correction:** remove the calendar estimate or show the calculation. Replace contamination certainty with a check: “Before launching another test, confirm whether #7622 exposure is still active and whether cohorts, surfaces, or outcome windows would overlap.”

### MAJOR 6 — “Trial-to-charge is not computable today” is broader than the cited instrumentation gap

**Draft locations:** lines 57, 82, 157, and 167.

Metrics Registry v17 says its first-session outcome queries cannot split trial versus direct-paid on iOS and hit a 35GB join limit on Android. Page 777817235 nevertheless reports experiment-level trial→charge values from another analysis source. The draft both cites those values as flat and says the metric is not computable at all.

**Required correction:** scope the limitation: “The current First Session Health registry cannot compute trial-to-charge by the required placement/segment; experiment-level values may exist through the separate analysis pipeline.” Verify which source is authoritative before removing the metric from draft 815603314.

### MAJOR 7 — Secondary metrics and many comparisons are interpreted without a multiplicity policy

**Draft locations:** lines 96–116.

The table compares multiple variants across monetization, conversion, retention, and engagement metrics. The document does not identify pre-specified primary metrics versus exploratory cuts or state whether any multiple-testing control applies. C’s significant Official-specific metrics are used to characterize the arm even though Total ARPU is non-significant.

**Required correction:** identify the pre-registered primary metric and guardrails from the experiment design. Label other metrics exploratory and avoid ranking C on isolated secondary significance without a multiplicity policy. Report source values shown as p=0.000 as p<0.001.

## Minor findings

### MINOR 1 — “Both drafts are blocked on the same maturation” is too broad

Draft 815603200 also lacks reach, baseline, sizing, and non-inferiority margins. Draft 815603314 additionally lacks feature selection, fallback behavior, instrumentation validation, and sizing. Maturation is one shared dependency, not the only blocker.

### MINOR 2 — Option 4 is ranked above the evidence

The draft labels intent-triggered placement low-confidence, then calls it the “best fit” and “strongest candidate.” It is a useful hypothesis, but no source defines the intent signal or validates that it separates willing buyers from engaged non-buyers.

**Correction:** call it the best mechanism to test against the stated causal hypothesis, not the strongest candidate to ship.

## Claim audit

| Claim | Type | Source | Status | Required correction |
|---|---|---|---|---|
| 77.17% of 14,641 reach Official tab | Calculation | 777817235 v144 | **Contradicted** | 77.17% is 10,595 / 13,730; from 14,641 it is 72.37%. |
| 99.47% of Official-tab viewers see the paywall | Calculation | 777817235 v144 | Supported | Preserve the conditional denominator. |
| 0.44% of paywall viewers access | Calculation | 777817235 v144 | Supported | Preserve as immediate in-flow conversion, not total later conversion. |
| Message delivery is saturated for the target population | Decision inference | 777817235 | **Partially supported** | Valid only after Official-tab reach in B; not for the full or unspecified banner audience. |
| Awareness is ruled out | Causal conclusion | 777817235 | **Contradicted** | Upstream awareness remains untested by the 99.47% conditional rate. |
| #6998 banner had ~0.2% interaction and failed | Fact | 721559684 v25 | Supported | Add Web/artist-page external-validity qualifier. |
| Three visibility mechanisms significantly increased visibility with no revenue | Summary fact | Multiple | **Unverifiable** | Name the three and provide metric, comparison, and p-value, or downgrade wording. |
| #7229 rules message/copy out | Causal conclusion | 761947509 v53 | **Not supported** | Null significance is not equivalence; report available precision. |
| B lifts ARPU and harms retention/engagement | Preliminary fact | 777817235 v144 | Supported with qualification | Keep the maturity warning and repeated-paywall confound adjacent to the claim. |
| C is consistent with the goal | Decision inference | 777817235 v144 | **Contradicted** | C has significant 60s engagement decline and no practical margin. |
| #7622 will be readable in one to two weeks | Forecast | None identified | Unverifiable | Show calculation or remove. |
| A new test would contaminate #7622 | Operational claim | None identified | Unverifiable | Confirm cohort/surface/window overlap first. |
| Trial-to-charge cannot be computed today | Instrumentation fact | 788614610 v17 | Partially supported | Scope to registry/placement/segment; reconcile with experiment pipeline. |
| Iter3-B contains a repeated second paywall loop | Fact | 777817235 v144 | Supported | Preserve; continue to label its causal share of lift/harm as plausible, not proven. |
| Do not build a generic banner | Decision | Combined evidence | Partially supported | Make conditional on objective, platform, placement, and audience; ground in closest precedents rather than the 99.47% generalization. |

## Analytics validity check

- **Exposure definition:** #7622 starts from `Tour Post Decline Gift Offer Close`, not from all free users or all users reaching an Official-eligible song. The draft’s target-population wording should match the actual eligible cohort.
- **Funnel denominators:** one denominator is incorrect and intermediate steps are omitted, creating a misleading reach statement.
- **Maturity:** correctly flagged as preliminary; pending trials are above the page’s 5% gate and 14-day outcomes are immature.
- **Randomization:** sample balance and duration checks are reported, but no independent live API read was possible in this review.
- **Confounding:** iter3-B differs from the intended design through the repeated `Official Tabs Recently Viewed` paywall loop. B cannot cleanly identify the effect of the guided first-song flow alone.
- **Guardrails:** retention and engagement move negatively; practical non-inferiority margins are absent.
- **Multiplicity:** not addressed. Secondary Official-specific metrics should remain exploratory unless the analysis plan says otherwise.
- **Causal language:** too strong for awareness, copy, and the mechanism responsible for B’s lift.

## Product-logic and solution-space check

The option set is materially differentiated and is one of the strongest parts of the draft. However, the causal chain breaks at the first link:

```text
Observed: 99.47% paywall exposure after Official-tab reach in B
Does not establish: awareness across the unspecified banner audience
Therefore cannot establish: a banner addresses a nonexistent bottleneck
```

A defensible chain is:

```text
Requested solution: generic banner
Closest direct precedent: very low interaction on Web artist page (#6998)
Adjacent App precedent: more Official discovery without revenue lift (#6728)
Current live evidence: contextual guided exposure can lift later monetization but harms users and is confounded (#7622)
Decision: do not ship an unspecified generic banner; first establish objective and placement, then prefer an in-context mechanism or the cheapest discriminating test
```

## Required changes, ordered by decision impact

1. Restore the literal request and mark objective, platform, placement, audience, and deadline as unknown or explicitly assumed.
2. Correct the #7622 funnel and retain every denominator needed to interpret 77.17%, 99.47%, and 0.44%.
3. Rewrite the executive answer so the 99.47% result applies only after Official-tab reach; do not use it to rule out upstream awareness.
4. Replace “ruled out” and “cannot work” language with claims matched to test precision and context.
5. Qualify #6998 as Web/artist-page evidence and include the mixed #4443 result or remove it from the declared source set.
6. Reclassify C as “less harmful but not compliant or decision-ready,” explicitly including the significant engagement decline.
7. Remove or calculate the one-to-two-week forecast and verify overlap before claiming contamination.
8. Reconcile the registry’s trial-to-charge limitation with the experiment analysis pipeline.
9. Identify primary versus exploratory metrics, address multiplicity, and replace p=0.000 with p<0.001.
10. Preserve the recommendation as conditional: do not ship a generic banner under the current iOS Official-tabs monetization assumption; confirm the ask before closing the solution space.

## What is already solid and should be preserved

- The draft does not recommend rolling out preliminary C results.
- It clearly separates B’s monetization lift from its retention and engagement cost.
- It identifies the repeated-paywall loop as a design-confounding issue and uses appropriately qualified causal language there.
- It surfaces instrumentation gaps instead of fabricating missing attribution.
- The solution options differ by mechanism, including a no-build learning option.
- It keeps unknown motivations explicitly unknown.
- It avoids invented owners, dates, MDEs, reach, and revenue forecasts for new options.
