---
reviewer: codex
draft: workspace/drafts/claude/official-tabs-version-block-pitch.md
verdict: NOT READY
reviewed: 2026-07-15T22:05:15+0900
draft_sha256: e39bdda6fb4bd36f2c177f3abfe6220284ebde7e13e7429b660b8cca806e5d2d
---

# Independent review: Official Tabs version-block pitch

## Verdict

**NOT READY.** The pitch accurately refreshes the closest experiment results and contains useful implementation safeguards, but it locks Branch A and a new-user-first test plan using stakeholder claims that do not appear in the cited source, while the cited decision record explicitly leaves the mechanism and population decision open.

## Review scope and source limitations

- Frozen artifact: `workspace/drafts/claude/official-tabs-version-block-pitch.md`, 14,322 bytes, modified 2026-07-15 21:14:27 +0900, SHA-256 `e39bdda6fb4bd36f2c177f3abfe6220284ebde7e13e7429b660b8cca806e5d2d`. The required hash matched when the review began.
- Concurrent-change boundary: at 2026-07-15 22:05:15 +0900 the live draft path no longer matched the frozen artifact; it hashed to `bf84421c665de9db55a5c187f59de793eb2681b04d70ef82aee3925162cc5231`. This review applies only to the frozen `e39b...` artifact named in the header. The changed Claude draft was not edited or substituted into this review.
- Repository state at freeze: `main` was at `4d593b7e77d2e8633d2d6a67a05a87c59e70622b`; the reviewed draft was untracked.
- Exact local Confluence snapshots inspected: 815603200 v5 (pulled 2026-07-15 17:55:15), 813827551 v3 (pulled 2026-07-15 17:55:16), 777817235 v144 (pulled 2026-07-15 06:06:53), and 788614610 v17 (pulled 2026-05-07 23:05:21).
- Exact local non-Confluence sources inspected: `workspace/sources/slack/official-tabs-scope-threads.md` and `workspace/final/official-tabs-process-recovery.md`. The Slack snapshot preserves thread text, authors, timestamps, and message IDs, but not the two attached images or the linked Figma frames.
- A live metadata read through the approved local Confluence tool failed because `alice.mu.se` could not be resolved. No Confluence write or alternate connector was used.
- The `ug-analytics` stable CLI was feature-detected successfully by pointing the installed launcher at the read-only sibling package. A fresh #7622 read was unavailable because `UG_COOKIE` is not configured. Numerical verification therefore applies to the exact cached v144 snapshot, not a fresh analytics API response.
- Source snapshot hashes, for reproducibility: 815603200 `77d2aedb8d5a69ce88ea7176ae3ae9d510e02170b363948eb9c16fa7cc6029aa`; 813827551 `a5f3ffd847999bcac7812c98b8203b1accad95f72eea12142fbb6959d2bb0f07`; 777817235 `7469488beebffc88af79f2fbe6cfff5b7b55350983c8791913e7422a9d258932`; 788614610 `5d58e25a505091ce4e4dec66dc44e8b22da4a4f460cf09ff2e02ab051b24eb76`; Slack snapshot `c179c7b1dfd673240e242afee9f2463134bbfc270b8b604dd7673f705e38c558`.
- No draft, Confluence page, message, attachment, or analytics repository file was changed.

## Blockers

### BLOCKER 1 — The pitch ratifies Branch A although the cited decision evidence leaves mechanism selection open

**Exact claims/sections:** “What this rewrite decides” says to show the block everywhere; “Reusing the C card is correct”; and the decision says to “Lock the logic” around the always-on block while excluding a mandatory tutorial or first-session-flow changes.

The exact Slack thread supports that the stakeholder raised two branches **for discussion, independent of rollout**: (A) an always-on selector block and (B) a forced off-tab feature tutorial before the paywall. The retrieved threads contain no approval of either branch. They also contain no durable decision owner. The cited, accepted process-recovery document reaches the explicit next decision: do not ratify a solution; confirm the literal ask, active branches, and ownership, then choose among materially different mechanisms.

The pitch does not cite newer evidence that closes that decision. Instead, it treats Branch A as settled and excludes Branch B. This could reverse the product decision if the requester confirms that Branch B is still live, changes the target problem, or names a different owner. The evidence supports preparing Branch A for comparison, not declaring it chosen.

**Smallest concrete correction:** change the document from a locked decision to a recommendation pending decision-owner confirmation. Add a short decision table comparing at least Branch A, Branch B, and the no-build/mature-and-diagnose option against the target problem, risks, current evidence, and cheapest next learning step. Record the requester's explicit choice and owner before saying “decides,” “correct,” or “lock the logic.”

### BLOCKER 2 — The new-user-first population plan is attributed to the requester without source support and does not identify the always-on estimand

**Exact claims/sections:** the pitch says “No cannibalization” and a larger “existing-user volume” effect are stakeholder assumptions; it calls a new/first-session cohort “the requester's proposal”; and it says this cohort gives a “novelty-free,” “clean read” that “measures the block.”

None of those stakeholder statements appears in the cited Slack snapshot, 815603200 v5, or the cited process-recovery document. The Slack source supports only the always-on selector idea, the separate forced-tutorial branch, the feature-usage analysis request, and the sequence logic → calculations → mockups. The source ledger's claim that Slack establishes the no-cannibalization assumption, test-cohort proposal, and population intent is therefore unverifiable.

The design logic is also insufficient. Existing-user novelty is a potentially time-varying part of the treatment effect, not automatically a confound in a randomized control comparison. Testing only first-session users measures an initial-exposure effect in a different population; it does not measure repeated always-on exposure, the claimed existing-user volume, or transfer to everyday selector use. If Phase 1 users have just previewed an Official tab, the context approaches #7622 rather than the claimed regular-selector mechanism. If they have not, the draft's assertion that the old preview-dependent copy still holds is false. Merely checking for #7622 overlap after selecting the cohort does not resolve this estimand problem.

This population choice could invalidate the experiment for the stated rollout decision.

**Smallest concrete correction:** obtain and cite the requester's actual population decision. Define the target estimand before choosing phases: population, assignment unit, first eligible exposure, repeated-exposure handling, time window, and whether the decision concerns initial response, stabilized response, or both. Prefer a randomized design covering the intended new and existing populations with pre-specified segment reads; if staging is necessary, justify why Phase 1 answers a decision-relevant question and define the fixed timing/exposure rule for any novelty-decay analysis.

## Major findings

### MAJOR 1 — The evidence section correctly caveats Variation C, then over-attributes its result to the block

**Exact claims:** “The block reliably moves Official-specific conversion,” “it carries an engagement cost,” and “It validates the component and hierarchy.”

Page 777817235 v144 supports the reported Variation C treatment results: Official Tabs ARPU +34.94% (p=0.003), Official charge CR +28.65% (p=0.006), total ARPU +9.47% (p=0.09), Tab View 60s −1.88% (p=0.001), and negative 7d/14d retention point estimates. It also says revenue is preliminary. But C is a multi-part first-session treatment and no comparison isolates the card, its hierarchy, or the engagement effect. The Official-specific metrics are exploratory and lack a documented multiplicity policy. “Reliably,” “the block,” and “validates” contradict the draft's own correct caveat that the results describe the whole C treatment.

This overstatement inflates confidence in the selected mechanism and contributes to the premature Branch-A decision.

**Smallest concrete correction:** say that the **whole contextual Variation C treatment** produced exploratory Official-specific lifts and a significant engagement decline, while neither the card nor hierarchy was isolated. Treat the existing component as a low-cost implementation candidate, not a validated causal mechanism.

### MAJOR 2 — The claimed cannibalization signal and buyer-shift explanation exceed the source

**Exact claims:** “Cannibalization signal”; the block may “shift buyers from free/other accesses rather than adding revenue”; and the hypothesis expects no net loss from “cannibalized free/other accesses.”

The source supports the descriptive counts 9,125 free-version clicks among 10,311 chooser views and the later-visit Official-tab access-rate point estimates 3.26% for C versus 3.41% for control. It does not report uncertainty or a documented unit of analysis for that later-visit cut. An 88% free-choice rate is not itself cannibalization: those users may have chosen free content in control as well. The total-ARPU result is inconclusive and preliminary. “Free accesses,” paid accesses, total accesses, purchases, and access points are used interchangeably, so the proposed lost value is not operationally clear.

This matters because anti-cannibalization is a stated success condition and a central reason for the experiment.

**Smallest concrete correction:** label both observations descriptive and hypothesis-generating. Define the competing outcome precisely—such as total net revenue per randomized eligible user, any-tab open rate, Community opens, paid-access starts, and their fixed windows—and reserve “cannibalization” for a randomized decrement in a pre-specified competing outcome or total value.

### MAJOR 3 — The primary metric and decision rule are not defined well enough to size or read the experiment

**Exact sections:** Goal, Analytics, Guardrails, and Design inputs use “Total ARPU (randomized)” and “total accesses” without an operational definition.

The pitch does not specify gross versus net revenue, assignment denominator, first-exposure date, observation window, trial/charge treatment, refunds, platform, currency, repeated selector opens, repeated users/sessions, or maturity rule for the new test. The source experiment used a preliminary revenue read and a 5% pending-trial gate; the prior pitch specified 14-day net ARPU, but this rewrite drops that precision. `Tab Versions Screen Open` is described as about 32M **rows**, which cannot substitute for eligible unique users or reach.

The guardrail contract is also incomplete. “Tab-view engagement” should name the exact Tab View 60s metric and unit. Only Retention 7d and engagement are promised non-inferiority margins even though D1, D7, and D14 are all listed. No family-wise decision rule is stated for several guardrails, optional arms, or segment reads.

Without these definitions, sample size, maturity, practical significance, and the rollout rule are not reproducible.

**Smallest concrete correction:** add a metric contract before sizing: randomized unit and denominator; eligible population/exclusions; net/gross ARPU formula; fixed 14-day or other window; revenue and refund maturity gate; repeated-exposure policy; exact event definitions; guardrail margins; multiplicity policy; and a single go/no-go rule that combines the goal metric with guardrails.

### MAJOR 4 — “Eligible” is undefined at the event that activates the experiment

**Exact sections:** the scenario table leaves trial-ineligible, former-subscriber, and referral behavior undefined, while Analytics requires `Tab Official Version Block Eligible` in every arm and the design claims every eligible free user.

Eligibility cannot be both the activation predicate and an unresolved product rule. Different clients or arms could activate different populations, causing sample-ratio mismatch or biased comparisons. Platform is also “No data yet,” although all cited efficacy evidence is iOS and Android was an underpowered null in #7622.

**Smallest concrete correction:** define one server/client-verifiable eligibility predicate before sizing or instrumentation sign-off, including paid rights, trial history, former subscribers, referrals, platform, Official availability, and first versus subsequent selector render. Send it identically in both arms and validate assignment-to-activation rates by platform and eligibility reason.

## Minor findings

### MINOR 1 — “Same component, different placement and frequency” understates treatment differences

The rewrite also changes lead copy, layout constraints, eligibility, population, exposure frequency, and possibly the post-paywall state. Calling placement and frequency “the entire hypothesis” obscures those treatment dimensions.

**Correction:** describe the stable component elements and list every changed treatment dimension; state which are held constant and which are intentionally part of the bundled treatment.

### MINOR 2 — The Pro-user rule contradicts itself

The prose says an existing Pro user gets no block, while the scenario status says the final rule is “No data yet.”

**Correction:** either mark “no block” as a decided eligibility rule with an owner/source or leave both the behavior and status unresolved.

### MINOR 3 — The implementation-history lesson is responsibly caveated but should not be quoted as #7577 history yet

The pitch correctly notes that 815603200 names #7577 while 777817235 identifies iteration 3 as #7622. Until an authoritative experiment/spec record resolves the identity, the event-string mismatch can be retained as a source-page implementation warning, not attributed to experiment #7577.

**Correction:** title it “lesson recorded on 815603200 v5” and remove the experiment number until resolved.

## Claim audit

| Claim | Type | Source | Status | Required correction |
|---|---|---|---|---|
| Variation C shows an Official card above free Community versions after Official preview and paywall dismiss | Fact | 777817235 v144; 815603200 v5 | **Supported** | Preserve the contextual placement. |
| The regular always-on selector placement has not been tested | Evidence gap | 815603200 v5; #7622 flow | **Supported** | Preserve. |
| Show the block everywhere an Official version exists | Decision | Slack Thread A; process-recovery final | **Partially supported** | Branch A was raised for discussion, not approved; reframe pending owner confirmation and alternative comparison. |
| Reusing the C card is correct and it does not need redesign | Decision/assumption | 815603200 v5; #7622 | **Unverifiable** | Treat reuse as a cost-saving candidate; validate copy, hierarchy, accessibility, and free-path visibility. |
| Current C copy assumes prior Official preview | Fact | 815603200 v5; C flow | **Supported** | Preserve. |
| Phase-1 first-session users have seen the Official version, so old copy still holds | Assumption | No cited source defines this proposed cohort path | **Unverifiable** | Define the exact cohort journey or remove the claim. |
| Official Tabs ARPU +34.94% (p=0.003) and Official charge CR +28.65% (p=0.006) | Exploratory experiment result | 777817235 v144, iOS 2026-07-10 | **Supported with qualification** | Preserve values; label preliminary, exploratory, and treatment-level. |
| Total ARPU +9.47% (p=0.09) | Experiment result | 777817235 v144 | **Supported** | Preserve the preliminary-maturity warning. |
| Tab View 60s −1.88% (p=0.001) | Experiment result | 777817235 v144 | **Supported** | Preserve as a whole-treatment result; define practical margin. |
| Retention 7d/14d −2.15%/−2.09%, non-significant | Experiment result | 777817235 v144 | **Supported** | Add the reported p-values when decision-relevant; do not infer safety. |
| 9,125 / 10,311 ≈ 88% selected a free Community version | Calculation | 777817235 v144 | **Supported** | Preserve as descriptive behavior only. |
| The 88% free click rate is a cannibalization signal | Evidence interpretation | Same source | **Partially supported** | Call it a competing-path observation; control counterfactual and value loss are not established. |
| Later ordinary-visit access rate is 3.26% in C vs 3.41% control | Descriptive result | 777817235 v144 | **Supported** | Preserve point estimates with no-uncertainty/no-unit caveat. |
| The block reliably moves Official-specific conversion | Causal evidence claim | #7622 Variation C | **Unverifiable** | Attribute movement to the whole C treatment; remove “reliably.” |
| The C evidence validates the component and hierarchy | Causal evidence claim | #7622 Variation C | **Unverifiable** | Say the component is feasible/reusable; no isolation validates hierarchy. |
| All revenue results are preliminary because pending trials exceed 5% in every iOS branch | Maturity fact | 777817235 v144 | **Supported** | Preserve; carry a maturity rule into the new experiment. |
| No cannibalization was flagged by the stakeholder | Stakeholder assumption | Cited Slack snapshot | **Unverifiable** | Obtain exact source or label as author assumption. |
| The stakeholder expects larger existing-user volume | Stakeholder assumption | Cited Slack snapshot | **Unverifiable** | Obtain exact source or label as author assumption. |
| A new/first-session test cohort is the requester's proposal | Stakeholder decision | Cited Slack snapshot | **Unverifiable** | Obtain exact source and owner confirmation. |
| Existing-user testing is confounded by novelty | Analytics-method claim | No cited method/evidence | **Contradicted as stated** | Novelty can be a treatment-time interaction; randomization still identifies the specified time-window effect. |
| Phase 1 on new users cleanly measures the block | Analytics-method claim | Proposed design | **Unverifiable** | Define context, estimand, overlap, repeat exposure, and external-validity limits. |
| A new-user result does not prove an existing-user effect | External-validity claim | Experimental logic | **Supported** | Preserve. |
| The event spec uses an eligibility event in every arm before visual difference and requires SRM | Instrumentation specification | 815603200 v5 | **Supported** | Preserve, after eligibility is made deterministic. |
| Existing events and a distinct `Official Tabs Version Block` source were verified/spec'd | Instrumentation fact | 815603200 v5 | **Supported at source-page level** | Verify character-for-character in production before reading results. |
| The registry cannot provide reliable by-placement purchase attribution | Analytics limitation | 788614610 v17 | **Supported within the First Session Health registry** | Keep the scope to that registry; use randomized totals for causal read. |
| #7577 caused the `Choose`/`Chose` and `from_tour` tracking failures | Experiment identity claim | 815603200 v5 vs 777817235 v144 | **Unverifiable** | Retain the lesson without experiment attribution until identity is resolved. |
| A mandatory tutorial should be excluded from the decision | Product decision | Slack Thread A; process-recovery final | **Contradicted by the current decision record** | Branch B was explicitly raised and remains open; compare or close it with owner evidence. |
| Logic → calculations → mockups is the requester's sequence | Decision-process fact | Slack Thread B | **Supported** | Preserve, but do not equate “logic” with unconfirmed Branch-A selection. |

## Analytics validity check

- **Assignment and actual exposure:** the proposed eligible event in every arm is the correct shape for downstream activation, and the mandatory SRM check is strong. The design does not yet define eligibility or how repeated selector renders map to one assignment/exposure, so the exposure population is not reproducible.
- **Population and exclusions:** new versus existing users, platform, trial history, referrals, former subscribers, and paid-rights rules are unresolved. The proposed new-user-first population is not supported by the cited stakeholder record and does not match the main existing-user claim.
- **Event definitions:** the high-level event path, distinct paywall source, and reuse of Community-click events are sensible. The source page—not a fresh warehouse query—supports the 30-day production-event check. Every literal value still requires production QA.
- **Outcome definition:** “Total ARPU” lacks denominator, window, net/gross basis, refund handling, and maturity. “Total accesses” conflicts with the document's use of access to mean both selector-to-tab behavior and monetized access.
- **Conversion-window maturity:** #7622 is correctly labeled preliminary. The new design does not carry forward a specific pending-trial/revenue maturity gate or equal observation window across arms.
- **Repeated users/sessions:** neither the primary metric nor the selector funnel explains how multiple opens, sessions, devices, or eligibility events per user are handled.
- **Sample and uncertainty:** baseline, MDE, alpha, power, sample, and duration are openly absent. That is acceptable before sizing, but not enough to sign off an experiment design or call the phase logic resolved.
- **Multiplicity:** the pitch correctly labels Official-specific #7622 metrics exploratory. It lacks a policy for optional arms, multiple guardrails, phase/segment reads, and any new-versus-existing heterogeneity test.
- **Guardrails and practical significance:** the draft correctly rejects “non-significant means safe” and requires margins. Exact guardrail metrics, units, margins, and the joint decision rule remain missing.
- **Causal language:** randomized comparisons can identify whole-treatment effects only. The draft over-attributes #7622 results to the block and hierarchy, and it labels novelty a confound without a causal design argument.
- **Fresh reproducibility:** current analytics and Confluence reads were blocked by missing authentication and DNS respectively. The named local snapshots are exact and hashed, but they are not proof that source state has remained unchanged after their pull times.

## Product-logic and solution-space check

The current causal chain breaks in three places:

```text
Observed C treatment effects
→ assumed cause: Official value visibility at a high-intent selector point
→ selected intervention: always-on C-derived block
→ expected change: incremental total ARPU without cannibalization
→ underspecified total-ARPU/access metrics
→ Branch A locked before owner/population confirmation
```

- **Observed behavior:** supported at the whole-treatment level, with preliminary revenue and a significant engagement decline.
- **Plausible cause:** visibility at a high-intent point is plausible but untested. The source research page contains hypotheses and questions, not completed findings.
- **Intervention mechanism:** an always-on block tests packaging/choice architecture, but the draft treats that mechanism as chosen before resolving the separately requested tutorial/value-experience mechanism.
- **Expected behavior change:** incremental rather than shifted value is an assumption. The 88% free-path observation does not identify cannibalization.
- **Metric:** total value, paid access, free access, and any-tab engagement are not yet separated cleanly.
- **Decision:** the draft's source record supports a decision conversation, not a ratified Branch-A logic.

The core A/B is experimentally simpler than the earlier A/B/C/D proposal, which is good. However, the document's solution space is not decision-ready because the optional preview and micro-demo remain variants of premium-value presentation while the cited Branch B tests a materially different causal theory. The cited process-recovery document also identifies a no-build option—mature/recalculate #7622 and diagnose the value-versus-confusion mechanism. Those alternatives need comparison before Branch A is locked.

The cheapest next learning step is not mockup work or experiment sizing. It is a short, sourced decision confirmation with the requester/owner: target problem, intended population, whether Branch B remains live, whether Branch A is approved for design, and what outcome would select among them.

## Exact required changes, ordered by decision impact

1. Replace the Branch-A “decision/lock” with a recommendation pending an explicit, cited decision-owner confirmation. Record whether Branch B and no-build diagnosis remain live.
2. Remove or source the claimed stakeholder assumptions about no cannibalization, existing-user volume, and a new-user test cohort. Correct the source ledger accordingly.
3. Redesign the population logic around a named estimand. Define new/existing segments, assignment unit, first and repeat exposures, fixed novelty/stabilization windows, and how the result maps to the broad rollout population.
4. Add a mechanism-level option comparison covering static always-on packaging, the requested tutorial/value-experience branch, and mature/diagnose. State the evidence, risk, and cheapest discriminator for each.
5. Replace component-level causal claims with treatment-level #7622 statements. Remove “reliably” and “validates the component and hierarchy.”
6. Reframe the 88% free-choice rate and 3.26% versus 3.41% point estimates as descriptive. Define cannibalization and every access outcome operationally.
7. Add the experiment metric contract: eligibility, platform, denominator, randomization unit, net/gross revenue, fixed window, trial/refund maturity, repeated-use handling, exact guardrails, margins, multiplicity, and go/no-go rule.
8. Resolve eligibility before using `Tab Official Version Block Eligible` as activation. Include trial history, former subscribers, referrals, paid rights, Official availability, and platform.
9. Resolve the Pro-user scenario contradiction and enumerate the treatment dimensions beyond placement/frequency.
10. Attribute the tracking-string warning to 815603200 v5, not #7577, until the #7577/#7622 identity mismatch is resolved.

## What is already solid and should be preserved

- The draft is decision-first and plainly distinguishes the proposed regular-selector placement from #7622's contextual first-session placement.
- The current iOS 2026-07-10 #7622 values are accurately transcribed from v144.
- Revenue is correctly labeled preliminary and the source's 5% pending-trial gate is acknowledged.
- Official-specific metrics are initially labeled exploratory, and the draft explicitly notes that Variation C is a whole treatment rather than a card-isolation test.
- The significant Tab View 60s decline and negative retention direction are not hidden.
- The free Community path, explicit CTA, return-on-dismiss behavior, and prohibition on automatic/repeating paywalls are concrete, testable safeguards.
- Reducing the core design from four arms to A/B protects power and isolates the primary packaging question better than the source pitch's bundled A/B/C/D plan.
- Optional preview/micro-demo arms are correctly identified as a separate question that requires multi-arm sizing and evidence-based feature selection.
- The activation event is designed to fire in Control before visual treatment, and the draft explicitly requires an SRM check.
- A distinct paywall source and literal production verification requirement are strong instrumentation safeguards.
- The draft correctly says a new-user result cannot establish the existing-user claim and correctly refuses broad rollout without an existing-user read.
- The non-inferiority principle is correct: a non-significant guardrail result is not evidence of safety.
- The logic → sizing → mockups sequence matches the exact Slack request and should remain after the logic decision itself is properly confirmed.
- The document keeps publication blocked and did not authorize a Confluence write.
