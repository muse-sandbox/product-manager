# Product-agent quality rubric

Score the submitted draft, not the reviewer or the final revision. The score measures first-pass product quality and must be comparable across tasks.

## Hard-fail conditions

Set `hard_fail: true` when any condition is present:

- a fabricated source, metric, research finding, stakeholder decision, owner, or date;
- a contradicted or unsupported claim that directly determines the recommendation;
- causal attribution to one component when only a bundled treatment was tested;
- a rollout recommendation with invalid exposure, immature target data, or an unbounded critical guardrail;
- an unacknowledged scope change that materially changes the requested user flow or decision;
- publication-ready language that hides a decision-critical evidence gap.

A hard fail forces `quality_gate: FAIL` regardless of the numeric score.

## Score dimensions

### Scope and objective — 15 points

- 15: literal request, objective, audience, constraints, owner, and open scope decisions are explicit; inferred items are labeled.
- 8: framing is mostly usable but one material premise is implicit.
- 0: requested solution is treated as the objective or scope changes are presented as approved.

### Evidence integrity — 25 points

- 25: every consequential claim is traceable; source relevance and limitations are adjacent; counterevidence is represented.
- 15: the decision is supportable but some material claims are only partially sourced or over-broad.
- 0: evidence is invented, contradicted, or cannot support the stated decision.

### Analytics validity — 15 points

- 15: population, exposure, denominator, metric window, maturity, uncertainty, guardrails, and causal scope are decision-safe.
- 8: values are accurate but one important validity or maturity condition is missing.
- 0: the result read could reverse because the comparison, denominator, exposure, or maturity is invalid.

### Product reasoning — 20 points

- 20: the chain from observed behavior to mechanism, intervention, metric, and decision is explicit; alternatives differ by mechanism.
- 12: the preferred direction is plausible but one causal link or material alternative is weak.
- 0: the document jumps from a requested UI change to a recommendation without a testable mechanism.

### Decision and experiment readiness — 15 points

- 15: the decision, remaining gates, metric contract, risks, and next learning step are actionable at the document's claimed stage.
- 8: useful shaping work, but missing inputs prevent the next irreversible step.
- 0: the document claims readiness while critical design or decision inputs are absent.

### Executive writing — 10 points

- 10: answer-first, one claim per sentence, concise, non-repetitive, and readable without hidden context.
- 5: understandable but verbose, generic, repetitive, or imprecise in places.
- 0: wording obscures the decision or makes unsupported certainty sound factual.

## Gates

- `PASS`: 85–100, no hard fail, and no BLOCKER.
- `CONDITIONAL`: 70–84, no hard fail, or at least one MAJOR correction remains.
- `FAIL`: below 70, any hard fail, or any BLOCKER.

The verdict and quality gate serve different purposes. `READY WITH CHANGES` can be `CONDITIONAL`; `NOT READY` is normally `FAIL`.

## Review-depth policy

- `full`: first review of a consequential decision or any artifact that may drive rollout, publication, sizing, or executive alignment. Verify every decision-critical and numerical claim. Sample at most three low-risk background claims.
- `delta`: a revision with an inspectable predecessor and prior review. Recheck changed claims, unresolved findings, changed calculations, and any conclusion affected by the diff. Do not re-audit unchanged supported claims.
- `light`: low-risk internal exploration with no rollout, publication, forecast, or experiment-readiness claim. Check all hard-fail conditions and the reasoning chain; sample evidence.

Escalate to `full` when the draft lacks a usable evidence ledger, sources conflict, the decision changed, or a new causal claim was introduced.

## Longitudinal measures

Track these across real tasks:

- first-pass score before Claude sees Codex feedback;
- hard-fail rate;
- BLOCKER and MAJOR findings per draft;
- correction yield: resolved material findings / material findings raised;
- human correction rate after finalization;
- review depth and elapsed time;
- unsupported-claim recurrence by category.

Do not optimize for score alone. A shorter honest document with explicit gaps is better than a complete-looking document built on assumptions.
