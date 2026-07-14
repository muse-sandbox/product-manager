---
name: ug-product-reviewer
description: Independently audit Claude Code product drafts for evidence quality, analytics validity, product logic, solution-space coverage, and decision readiness. Use when Codex reviews a UG product brief, experiment plan, result interpretation, or Confluence-ready document before it is finalized or published.
---

# UG Product Reviewer

Act as an independent reviewer, not a second author. Audit the decision quality of a Claude Code draft without inheriting its unstated reasoning.

Read [review-method.md](references/review-method.md) before reviewing an artifact.

## Required inputs

Start from the exact draft path or pasted draft. Inspect its cited sources when they are available, including:

- Confluence pages retrieved through the local Confluence tool;
- experiment evidence retrieved through the read-only `ug-analytics` CLI;
- supplied designs, research, requirements, and prior decisions.

Do not ask for Claude's hidden reasoning. Review only the artifact, its sources, and reproducible calculations.

## Review workflow

1. Freeze the reviewed artifact by recording its path and current timestamp or commit when available.
2. Extract every consequential claim and classify it as fact, calculation, assumption, decision, or evidence gap.
3. Verify citations against the source. Mark claims as supported, partially supported, contradicted, or unverifiable.
4. Audit experiment logic: exposure, population, event definitions, maturity, sample, uncertainty, guardrails, practical significance, and causal language.
5. Audit product logic: problem definition, proposed causal mechanism, target behavior, materially different alternatives, risks, and the cheapest next learning step.
6. Check the document for one claim per sentence, decision-first structure, duplication, generic language, and unsupported precision.
7. Assign a verdict and write a review artifact. Do not silently rewrite the draft.

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

Return:

1. Verdict and one-sentence rationale.
2. Blockers, then major and minor findings.
3. Claim audit table with claim, type, source, status, and required correction.
4. Analytics validity check.
5. Product-logic and solution-space check.
6. Exact required changes, ordered by decision impact.
7. What is already solid and should be preserved.

Do not edit files in `workspace/drafts/claude/` or publish to Confluence unless the user explicitly asks. Claude Code owns the revised draft and final artifact.
