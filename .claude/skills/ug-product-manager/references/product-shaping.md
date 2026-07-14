# Product shaping workflow

## Convert a requested solution into an objective

Treat requests such as `add a banner`, `move the button`, or `copy competitor X` as inputs, not requirements.

Recover five elements:

1. **Outcome**: What user or business behavior should change?
2. **Audience**: For whom and in which state?
3. **Current behavior**: What happens today?
4. **Constraint**: What is fixed by policy, technology, timing, or strategy?
5. **Evidence**: Why believe a problem exists or that the mechanism could work?

If the outcome cannot be recovered, present candidate interpretations and show how each interpretation creates a different solution space.

## Map plausible bottlenecks

Consider these mechanism families:

- awareness: the user does not notice the option;
- comprehension: the user notices it but does not understand it;
- relevance: the value is not connected to the current goal;
- trust: the user doubts quality or credibility;
- discoverability: the option is hard to find;
- choice architecture: options are grouped, ordered, or defaulted poorly;
- timing: the request appears before intent or after the decision;
- friction: the path requires unnecessary work;
- access: eligibility or gating prevents use;
- price/value: the benefit does not justify the cost.

Do not select one bottleneck without evidence. Use the option set to distinguish between plausible mechanisms when necessary.

## Use the intervention ladder

Move from the lightest intervention to structural changes:

1. **No-build validation**: interview, prototype test, fake door, event audit.
2. **Messaging**: copy, banner, education, benefit explanation.
3. **Visual hierarchy**: badge, prominence, ordering, emphasis.
4. **Information architecture**: grouping, separation, navigation, states.
5. **Choice architecture**: default, recommendation, progressive disclosure.
6. **Timing and context**: move the intervention to the moment of intent.
7. **Experience**: preview, sample, trial, or demonstration of value.
8. **Monetization**: packaging, gating, paywall, offer, or price presentation.
9. **Personalization**: adapt content, timing, or default to a validated segment.

Generate at least three options from different levels. Cosmetic copy variations count as one option.

## Option contract

Describe each option with:

| Field | Requirement |
|---|---|
| Mechanism | Why this change could alter behavior |
| Product change | What becomes observably different |
| Audience/state | Who sees it and when |
| Evidence | Supporting fact or explicit assumption |
| Target metric | Behavior the option is expected to change |
| Guardrail | Harm the experiment must not create |
| Risk | Main failure mode or confound |
| Learning value | What the result will and will not tell us |

## Compare without false precision

Use qualitative confidence when inputs are incomplete:

- **High**: multiple directly relevant UG sources agree.
- **Medium**: one relevant UG source or several indirect sources.
- **Low**: mechanism is plausible but not supported by relevant evidence.

Do not create numeric RICE or ICE scores without defensible Reach, Impact, Confidence, and Effort inputs.

## Choose the next action

- Recommend implementation when the problem, mechanism, and measurement are sufficiently supported.
- Recommend a prototype or fake-door test when the mechanism is uncertain but cheap to validate.
- Recommend instrumentation or research when the current behavior cannot be diagnosed.
- Return multiple viable options without ranking when evidence does not distinguish them.
