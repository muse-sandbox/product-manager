# Evidence and executive writing

## Evidence labels

Classify every consequential statement internally before using it:

- **Fact**: Directly observed in a named source.
- **Calculation**: Derived from cited inputs with a reproducible formula.
- **Assumption**: Plausible but not yet verified.
- **Decision**: A chosen action and its owner or decision-maker.
- **Gap**: Information required to evaluate a claim or decision.

Do not clutter the final document with labels when the status is obvious. Expose labels when fact and assumption could be confused.

## Source hierarchy

Prefer, in order:

1. UG product analytics and experiment results.
2. Prior UG experiments with comparable audience, placement, and mechanism.
3. Direct UG user research, support evidence, and observed behavior.
4. Current product flow, design, technical constraints, and business rules.
5. External research with a comparable population and context.
6. Competitor patterns as inspiration only.

Recency does not compensate for poor relevance. Explain material differences between the evidence source and the current proposal.

## Claim test

For each claim, answer:

1. What exactly is being asserted?
2. Which source or calculation supports it?
3. Does the source establish correlation or causation?
4. What limitation could change the conclusion?
5. What decision follows from the claim?

Delete claims that do not affect understanding or a decision.

## Executive writing contract

- Lead each section with its conclusion.
- Use one claim per sentence.
- Prefer concrete nouns and verbs.
- Quantify the baseline, target, population, and time window when known.
- Put evidence immediately after the claim it supports.
- End analytical sections with the implication or decision.
- Use tables for repeated comparisons, not for narrative reasoning.
- Keep background material out of the main decision path.

Replace vague language:

| Avoid | Require instead |
|---|---|
| significantly improve | target metric, baseline, expected change, basis |
| users prefer | observed behavior or research source |
| intuitive | task success, error rate, time, or research evidence |
| many users | audience count and period |
| industry best practice | named comparable source and relevance |
| should increase | causal mechanism plus evidence or assumption label |
| successful experiment | metric result, uncertainty, guardrails, and criterion |

## Forecast rules

Write the model before the forecast:

```text
Incremental outcome = eligible audience × exposure × behavioral lift × value per outcome
```

For every input, record value, definition, source, period, and uncertainty. Use a range when uncertainty is meaningful. Do not backfill unknown inputs with external benchmarks unless the user explicitly requests a scenario model; label such benchmarks as assumptions.

## Causal language

- Use `caused` only when supported by a valid experiment or strong causal design.
- Use `associated with` for observational relationships.
- Use `may explain` for an untested mechanism.
- Do not infer user motivation from click or conversion data alone.

## Honest stopping conditions

Stop before recommending rollout when exposure is invalid, sample balance is suspect, maturity windows are open, instrumentation is incomplete, or a critical guardrail is unavailable. State the missing condition and the next check.
