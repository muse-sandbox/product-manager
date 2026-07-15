---
reviewer: codex
draft: workspace/drafts/claude/official-tabs-process-recovery.md
verdict: READY WITH CHANGES
reviewed: 2026-07-15T18:21:54+0900
draft_sha256: a466e5efd6a2f1a13967f86bb19c09d3c6b5b7c4033bcf593387eb408063d121
---

# Independent review: Official Tabs process recovery

## Verdict

**READY WITH CHANGES.** The exact Slack text now supports the decision-record reconstruction and the draft correctly retracts the unsupported research claim, but two causal statements still attribute retention harm to a repeating-paywall component that the experiment did not isolate.

## Review scope and source limitations

- Frozen artifact: `workspace/drafts/claude/official-tabs-process-recovery.md`, modified 2026-07-15 18:17:59 +0900, 28,335 bytes, with the SHA-256 recorded above.
- Repository state: the draft is untracked; `main` is at `4d593b7e77d2e8633d2d6a67a05a87c59e70622b`. The Claude draft was not edited.
- Exact Slack source inspected: `workspace/sources/slack/official-tabs-scope-threads.md`, containing the retrieved text, authors, timestamps, and message IDs for threads `1783595323.736059` and `1784050824.694299`. The two attachments, five prototype visuals, and Figma frames remain uninspected.
- Independently inspected cached Confluence snapshots: 815603200 v5 (pulled 2026-07-15 17:55:15), 813827551 v3 (pulled 2026-07-15 17:55:16), 777817235 v144 (pulled 2026-07-15 06:06:53), and 788614610 v17 (pulled 2026-05-07 23:05:21).
- A live metadata check through the approved local Confluence tool failed because `alice.mu.se` could not be resolved. No Confluence write or alternate connector was used.
- The `ug-analytics` CLI was feature-detected through the sibling read-only project. A fresh #7622 response was unavailable because `UG_COOKIE` is not configured. Numerical verification therefore applies to the named cached Confluence snapshots, not a fresh analytics API read.
- The secondary synthesis `workspace/final/official-tabs-banner-shaping.md` was inspected only for source routing and consistency, not treated as primary evidence.

## Blockers

None.

## Major findings

### MAJOR 1 — The draft isolates treatment effects correctly in §2, then causally assigns Variation B's retention harm to one unisolated component

**Exact claims:** §3 says, “Variation B's forced repeating-paywall loop is exactly what harms retention”; the Russian reply says, “именно форс-цикл роняет ретеншен в B.”

Page 777817235 v144 supports that the **whole Variation B treatment** has statistically significant retention declines: Retention 1d −7.76%, 7d −4.81%, and 14d −4.91%, each reported as p=0.000. It also documents a large increase in the `Official Tabs Recently Viewed` paywall reach within B. However, B changes the guided first-song path, routing, Official-tab exposure, paywall behavior, post-dismiss destination, and repeating-paywall opportunity together. No randomized comparison isolates the repeating loop from those other changes.

The research plan on 813827551 explicitly treats “value versus confusion/entrapment” as an unanswered question. Its statement that the lift comes from the repeat-paywall loop is a product interpretation motivating research, not component-level causal identification. The current draft's “exactly” and “именно” convert that open mechanism question into a causal conclusion.

This matters because the claim is used to justify replacing the colleague's forced tutorial branch with a voluntary selector preview. Avoiding compulsion is a reasonable risk-reduction choice, but the source does not establish that a repeating paywall caused the retention decline or that every forced tutorial would do so.

**Smallest concrete correction:** replace both causal statements with a treatment-level statement, for example: “Variation B's multi-part treatment, which includes a repeating-paywall loop, caused a significant retention decline; the loop is a plausible contributor but was not isolated.” Defend the voluntary design as a precaution consistent with prior forcing risks, not as a proven remedy for B's retention mechanism.

## Minor findings

### MINOR 1 — The forcing evidence is cited to the wrong primary page and is broader than the exact precedents

**Exact claim:** §3 attributes “Forcing tab display worsens results — verified in experiment 7256, iteration 1” to 777817235 v144, and the source ledger groups “forcing worsens results (7256)” under that page.

The exact sentence “Forcing tab display worsens results — verified in experiment 7256, iteration 1” appears in 788614610 v17. Page 777817235 instead says “Forcing actions destroys best segments” and cites a minimum-three-song selection result, while its iteration-1 flow combines autoplay, timed presentation, and a forced path. These precedents support a risk hypothesis about compulsion; they do not directly test a forced feature tutorial.

**Correction:** cite 788614610 for the exact tab-display sentence and 777817235 for the minimum-song/iteration evidence. Narrow the conclusion to “forced flows have shown risk in adjacent first-session contexts.”

### MINOR 2 — Two absence claims should remain bounded to the retrieved threads

**Exact claims:** the executive answer says “Neither branch was approved for build” and “there is no message agreeing to remove the free Community versions.”

The cited Slack extract supports that neither retrieved thread contains approval and that no later reply appears to the free-version question. It cannot establish that no approval or agreement exists in another channel, call, document, or omitted message.

**Correction:** say “Neither branch is approved for build in the retrieved threads” and “the retrieved thread contains no reply agreeing to remove the free Community versions.” The table already uses this appropriately bounded wording.

### MINOR 3 — The executive phrase “the evidence settles the one substantive question” conflicts with the document's own residual content question

The next paragraphs correctly establish that branch B is not represented and remains open. Calling the disagreement's “one substantive question” settled makes the executive answer internally inconsistent and obscures the distinction between the unsupported research claim, which is settled, and the product mechanism, which is not.

**Correction:** replace it with “the evidence settles the research-claim dispute and clarifies what remains open.”

## Claim audit

| Claim | Type | Source | Status | Required correction |
|---|---|---|---|---|
| The 2026-07-09 message proposed two branches for discussion, independent of rollout | Fact | Exact Slack Thread A | **Supported** | Preserve. |
| The colleague requested retention maturation, 14-day conversions for Variation 3, and questions/hypotheses in the research plan | Fact | Exact Slack Thread A | **Supported** | Preserve. |
| The colleague requested logic → calculations → mockups | Fact | Exact Slack Thread B | **Supported** | Preserve. |
| Neither branch was approved for build | Decision status | Retrieved Slack threads | **Partially supported** | Bound the claim to the retrieved threads. |
| No one agreed to remove Community versions | Decision status | Retrieved Slack Thread A | **Partially supported** | Say the retrieved thread contains no reply or agreement. |
| The five textual prototype descriptions were presented | Fact | Exact Slack Thread B | **Supported** | Preserve the text-only limitation. |
| The prototype visuals, Slack images, and Figma frames were not inspected | Evidence gap | Slack snapshot provenance; draft record | **Supported** | Preserve. |
| 815603200 keeps Community versions visible, requires explicit CTA before paywall, returns to the selector on dismiss, and forbids an automatic/repeating loop | Fact | 815603200 v5 | **Supported** | Preserve. |
| 815603200 excludes a mandatory tutorial and first-session-flow changes | Scope fact | 815603200 v5 | **Supported** | Preserve. |
| 815603200's decision is “proceed to design/sizing; do not roll out without experiment evidence” | Decision | 815603200 v5 | **Supported** | Preserve. |
| 813827551 is a research plan with hypotheses/questions but no completed method or findings | Fact | 813827551 v3 | **Supported** | Preserve. |
| “I did research and learned this won't work” is established | Evidence claim under audit | 813827551 v3; 777817235 v144 | **Contradicted** | Retraction is correct; preserve the narrower “always-on placement is untested.” |
| Variation C members→total accesses is +6.90%, p=0.047 | Experiment result | 777817235 v144, iOS snapshot 2026-07-10 | **Supported** | Preserve as a treatment result and keep the reviewer-applied multiplicity caveat. |
| A two-comparison Bonferroni threshold is 0.025 | Calculation / reviewer check | 0.05 / 2 | **Supported** | Preserve the statement that this was not the experiment's specified rule. |
| Variation C total ARPU is +9.47%, p=0.09 | Experiment result | 777817235 v144 | **Supported** | Preserve with preliminary-maturity warning. |
| Variation C Official ARPU is +34.94%, p=0.003, and Official charge CR is +28.65%, p=0.006 | Exploratory experiment result | 777817235 v144 | **Supported with qualification** | Preserve the exploratory label and treatment-level attribution. |
| Variation C Retention 7d/14d is −2.15%/−2.09%, p=0.09/0.07 | Experiment result | 777817235 v144 | **Supported** | Preserve; non-significance does not establish safety. |
| Variation C Tab View 60s is −1.88%, p=0.001 | Experiment result | 777817235 v144 | **Supported** | Preserve; practical significance remains undefined. |
| The `other` funnel point estimate is C 3.26% vs control 3.41% | Descriptive result | 777817235 v144 | **Supported** | Preserve the no-uncertainty/no-unit caveat. |
| 9,125 / 10,311 ≈ 88% of C chooser viewers clicked a free version | Calculation | 777817235 v144 | **Supported** | Preserve as descriptive; do not infer motivation. |
| The always-on regular-selector placement is untested | Evidence gap | 815603200 v5; #7622 context | **Supported** | Preserve. |
| All current revenue results are preliminary because pending trials exceed 5% and only about one quarter of charges are 14d old | Maturity fact | 777817235 v144 | **Supported** | Preserve. |
| Branch A is represented by 815603200 | Product mapping | Slack Thread A; 815603200 v5 | **Supported** | Preserve. |
| Branch B's forced off-tab tutorial is not represented by a voluntary selector preview | Product mapping | Slack Thread A; 815603200 v5 | **Supported** | Preserve. |
| Forced flows have shown risk in adjacent contexts | Evidence synthesis | 788614610 v17; 777817235 v144 | **Partially supported** | Cite both sources and avoid generalizing to every tutorial. |
| Variation B's repeating-paywall loop is exactly what harms retention | Causal claim | 777817235 v144; 813827551 v3 | **Unverifiable** | Attribute harm to the whole B treatment; label the loop a plausible, unisolated contributor. |
| The draft concept satisfies three interaction constraints but is not experiment-ready | Product decision | 815603200 v5; 777817235 v144 | **Supported** | Preserve. |
| Activation event, SRM check, and distinct paywall source are careful pre-launch specification choices | Instrumentation fact | 815603200 v5 | **Supported** | Preserve the distinction from shipped tracking validation. |
| Experiment 7577 is the iteration-3 source of the tracking-string failure | Identity claim | 815603200 v5 vs 777817235 v144 | **Unverifiable** | Preserve the explicit 7577/7622 conflict until an authoritative experiment record resolves it. |
| Confirming the literal ask, active branches, and decision owner is the cheapest next step | Product decision | Slack evidence; unresolved scope/ownership | **Supported** | Preserve. |
| The four options in §5 test materially different mechanisms | Solution-space assessment | Draft synthesis | **Supported** | Preserve. |

## Analytics validity check

- **Assignment and exposure:** the draft correctly separates #7622's contextual post-preview/post-paywall placement from the proposed always-on selector placement. It does not claim exposure equivalence.
- **Population and exclusions:** the proposed selector experiment still lacks platform and trial-ineligible/former-subscriber/referral rules. The draft correctly labels these as unresolved.
- **Event definitions:** `Tab Official Version Block Eligible`, control inclusion, distinct block-view events, a distinct paywall source, and mandatory SRM are strong specification choices in 815603200. They are not yet production validation.
- **Maturity:** #7622 remains preliminary. The draft correctly reports iOS pending-trial shares of 9.9% / 11.6% / 12.6%, above the source's 5% gate, and notes that roughly one quarter of charges are older than 14 days.
- **Sample and uncertainty:** the draft reports relevant p-values and avoids claiming a difference for the `other` funnel. It does not report #7622 arm sizes or confidence intervals, but its purpose is process recovery rather than a complete results read; the omission does not alter its no-decision conclusion.
- **Repeated users/sessions:** the draft explicitly flags the undocumented unit and possible double-counting in the `other` cut.
- **Multiplicity:** Official-specific metrics are correctly labeled exploratory. The Bonferroni threshold is clearly a reviewer-applied sensitivity check, not a retroactive decision rule.
- **Guardrails and practical significance:** the significant Tab View 60s decline is reported, and the missing non-inferiority margin is explicit.
- **Causal language:** Variation C is correctly described as a multi-part treatment. Variation B is not: the repeating loop is not isolated from the rest of B and must not be named as the proven cause of retention harm.
- **Fresh reproducibility:** fresh API verification was blocked by missing analytics authentication, and live Confluence verification was DNS-blocked. The review remains reproducible against the exact named local snapshots.

## Product-logic and solution-space check

The draft's main decision chain is now sound:

```text
Exact Slack record
→ two branches were proposed for discussion, not approved in the retrieved threads
→ the claimed completed research does not exist
→ always-on selector behavior is untested
→ branch B was transformed rather than represented
→ confirm the record and ownership before selecting or sizing a mechanism
```

The observed-behavior link is supported by the exact thread. The evidence-gap link is supported by the research-plan and experiment pages. The draft also keeps four materially different next choices visible: static selector packaging, selector value proof, first-session tutorial, and no-build diagnosis/maturation. This is a genuine solution space, not cosmetic variants.

The remaining broken link is narrower: adjacent evidence that compulsory flows can be risky does not prove that the repeating loop caused B's retention decline or that a voluntary selector preview solves the same causal problem. Correcting that attribution leaves the recommendation unchanged: confirm whether branch B is still live, then select the mechanism before sizing or mockups.

## Exact required changes, ordered by decision impact

1. Replace both component-level causal claims about Variation B with a treatment-level statement: B caused significant retention harm; the repeating loop is a plausible but unisolated contributor.
2. Reframe voluntary preview as a precautionary product choice consistent with adjacent forcing risks, not as an evidence-proven correction to B's retention mechanism.
3. Cite 788614610 for the exact “Forcing tab display worsens results” sentence and 777817235 for the distinct minimum-song/iteration evidence; state that neither directly tests a forced feature tutorial.
4. Bound “not approved” and “no agreement to remove free versions” to the retrieved Slack threads.
5. Replace “the evidence settles the one substantive question” with wording that distinguishes the settled research-claim dispute from the still-open mechanism decision.

## What is already solid and should be preserved

- The exact Slack source resolves the prior review's central blocker and supports the quoted asks, replies, no-reply status, and sequencing request.
- The artifact maintains a clear boundary between verified text and uninspected visuals/intent.
- The unsupported “research proved it won't work” statement is retracted directly and responsibly.
- The research plan is correctly distinguished from completed findings.
- The analytics section uses the current 2026-07-10 snapshot, labels revenue preliminary, and includes the significant engagement decline.
- Variation C results are correctly attributed to the whole treatment and Official-specific metrics are labeled exploratory.
- The draft distinguishes discussion scope, selector-test scope, and prototype-exploration scope.
- It correctly identifies branch B as a different mechanism rather than claiming it is covered by selector previews.
- It narrows “guardrails satisfied” to three actual interaction constraints and lists the unresolved experiment inputs.
- The proposed next step—confirm record, live branches, and ownership before mechanism, calculations, or mockups—is decision-ready.
- The source ledger separates primary sources, a secondary synthesis, and excluded visuals, and it discloses the 7577/7622 identity conflict.
- The document retains explicit safeguards against sending the personal reply or publishing to Confluence.
