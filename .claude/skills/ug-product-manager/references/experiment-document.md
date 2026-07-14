# UG experiment document

Preserve the existing document lifecycle: **Pitch → Solution → Decision**. Fill only supported sections and delete instructional boilerplate from the deliverable.

## Header

Include link to OKR, status, DRI/project owner, and team only when provided or discoverable. Never invent ownership or status.

## Pitch

### Context & Idea

Lead with the observed problem and intended outcome. Include current behavior, target audience, why now, and the proposed mechanism at a high level. Keep solution detail out of the problem statement.

### Questions & Answers

Include only questions that affect the hypothesis, scope, measurement, or decision. Classify them as answered with evidence, working assumption, open, or blocking.

### Confidence research

Use the structure:

```text
Evidence → relevance to this hypothesis → limitation
```

Include counterevidence and failed comparable experiments when available. A competitor implementation demonstrates feasibility or a pattern, not UG impact.

### Reach & Impact

Show current audience and behavior, target metric baseline, forecast formula, input sources, and uncertainty. Separate Reach from behavioral lift and value per outcome.

End with one of: proceed to shaping, run a cheaper validation, collect missing data, or stop.

### Hypothesis

Use:

```text
If we implement [change] for [audience] in [scenario], then [target metric]
will change from [baseline] to [target] within [period], without worsening
[guardrail] beyond [threshold], because [supported mechanism].
```

Mark unavailable inputs instead of producing a generic sentence.

### Experiment design

Specify platform, population, exposure, variants, target and guardrail metrics, baseline, MDE, power, alpha, sample size, duration, eligibility, exclusions, and stopping or decision rules. Link calculations when available.

## Solution

### Description of the Solution & Mockups

Describe observable behavior for every variant, entry point, state, transition, dismissal, error, and edge case. Include current screens and mockups when supplied. State what is intentionally out of scope.

### Mockups & Texts

Map each screen or state to control and variations. Preserve exact approved copy and localization status. Do not invent final copy when only a concept is approved.

### Analytics

List events, parameters, firing conditions, and their purpose. Confirm how exposure, target metrics, guardrails, and diagnostic funnels will be computed.

### Execution

List owner + action + date only when these are known. Separate required launch tasks from optional follow-ups.

## Decision

### Decision

Lead with rollout, partial rollout, iteration, rejection, or wait. Support the decision with target metric, guardrails, maturity, uncertainty, and segment consistency. Explicitly answer whether the null hypothesis was rejected without making it the sole decision criterion.

### Forecast

Update the original model using experiment results. Show before, expected after rollout, realistic range, and assumptions. Do not extrapolate beyond the exposed population without an adjustment.

### Insights

Separate:

- observed result;
- supported explanation;
- plausible but untested explanation;
- reusable learning.

Use funnel or segment breakdowns to explain deviations. Do not infer motivation from metrics alone.

### Significance analysis

Report control, each variation, difference, uncertainty or p-value, daily stability, cumulative result, and practical threshold for target and guardrail metrics.

### Research

Investigate why the result differed from the model. Follow the causal chain until the next link requires new evidence. Attach the supporting breakdown or mark the explanation as a hypothesis.

### Next steps

Tie each action to the decision or a specific evidence gap. Include owner and timing only when known.

### Post-Rollout Analysis

Use only for delayed outcomes such as renewal, refund, long-term retention, or cohort survival. Define the revisit date and decision that the delayed metric may change.

## Duplication rules

- Put raw support in Confidence research; put the decision-relevant conclusion in Context & Idea.
- Put the forecast model in Reach & Impact; put the observed update in Forecast.
- Put result values in Significance analysis; put their meaning in Insights.
- Put unresolved uncertainty in Questions & Answers; put required actions in Next steps.
