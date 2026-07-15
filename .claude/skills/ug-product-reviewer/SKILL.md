---
name: ug-product-reviewer
description: Independently audit Claude Code product drafts for evidence quality, analytics validity, product logic, solution-space coverage, and decision readiness. Use when Codex reviews a UG product brief, experiment plan, result interpretation, or Confluence-ready document before it is finalized or published.
---

# UG Product Reviewer

Act as an independent reviewer, not a second author. Audit the decision quality of a Claude Code draft without inheriting its unstated reasoning.

Read [review-method.md](references/review-method.md) and `evals/quality-rubric.md` before reviewing an artifact.

## Required inputs

Start from the exact draft path or pasted draft. Inspect its cited sources when they are available, including:

- the approved product plan under `workspace/plans/`, including fixed decisions and Discovery findings;
- Confluence pages retrieved through the local Confluence tool;
- experiment evidence retrieved through the read-only `ug-analytics` CLI;
- supplied designs, research, requirements, and prior decisions.

Do not ask for Claude's hidden reasoning. Review only the artifact, its sources, and reproducible calculations.

## Review workflow

1. Select `full`, `delta`, or `light` review depth using the quality rubric. Default consequential first reviews to `full`.
2. Freeze the reviewed artifact by recording its path and current timestamp or commit when available.
3. Extract every decision-critical claim and classify it as fact, calculation, assumption, decision, or evidence gap.
4. Verify every numerical and decision-critical citation. In `full` mode, sample at most three low-risk background claims instead of re-performing broad source discovery.
5. Audit experiment logic: exposure, population, event definitions, maturity, sample, uncertainty, guardrails, practical significance, and causal language.
6. Audit product logic and plan adherence: fixed decisions, Discovery findings, problem definition, proposed causal mechanism, target behavior, required alternatives only when solution selection remained open, risks, and the cheapest next learning step.
7. Check the document for one claim per sentence, decision-first structure, duplication, generic language, and unsupported precision.
8. Score first-pass quality with `evals/quality-rubric.md`, assign a verdict, and write a review artifact. Do not silently rewrite the draft.

## Verdicts

- `READY`: the decision is supported and no material change is required.
- `READY WITH CHANGES`: direction is credible, but specified changes are required before publication.
- `NOT READY`: evidence, logic, or experiment validity is insufficient for the stated decision.

## Severity

- `BLOCKER`: could reverse the decision, invalidate the experiment, or publish an unsupported claim.
- `MAJOR`: materially weakens the recommendation or reader's ability to act.
- `MINOR`: clarity, concision, or traceability issue that does not change the decision.

## Output contract

Save reviews under `workspace/reviews/codex/` unless the user requests chat-only output. Use the draft filename plus `-review.md`.

The YAML header must include these flat machine-readable fields:

```yaml
reviewer: codex
draft: workspace/drafts/claude/example.md
verdict: READY | READY WITH CHANGES | NOT READY
reviewed: YYYY-MM-DD
draft_sha256: <exact draft hash>
review_mode: full | delta | light
quality_score: 0-100
quality_gate: PASS | CONDITIONAL | FAIL
hard_fail: true | false
score_scope: 0-15
score_evidence: 0-25
score_analytics: 0-15
score_product_reasoning: 0-20
score_decision_readiness: 0-15
score_executive_writing: 0-10
```

The six component scores must sum to `quality_score`. Explain deductions in findings; do not create a separate essay to justify each point.

Return:

1. Verdict, quality score, gate, review mode, and one-sentence rationale.
2. Blockers, then major and minor findings. Cap findings at the ten highest-impact items and merge duplicates.
3. Claim audit table for decision-critical claims and any sampled background claims.
4. Analytics validity check.
5. Product-logic and solution-space check.
6. Exact required changes, ordered by decision impact.
7. What is already solid and should be preserved.

Do not edit files in `workspace/drafts/claude/` or publish to Confluence unless the user explicitly asks. Claude Code owns the revised draft and final artifact.
