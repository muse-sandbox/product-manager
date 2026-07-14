# Example: from "add a banner" to an option space

This example encodes the reasoning pattern, not a validated conclusion about the live product.

## Raw request

```text
Add a banner for Official tabs.
```

Treat `banner` as the requested solution. Do not assume the underlying objective.

## Candidate objective

```text
Make the value and distinction of Official tabs clear enough that eligible users
can deliberately choose them at the relevant point in the song flow.
```

Label this as a candidate until the requester, strategy, or evidence establishes the intended behavior and business outcome.

## Candidate bottlenecks

- Users may not notice Official versions.
- Users may notice them but not understand the benefit.
- Official and community versions may be mixed in a way that obscures the distinction.
- The value message may appear before the user has intent to play the song.
- The paywall may interrupt the task before the value is demonstrated.

These are hypotheses. Analytics can show behavior; interviews or controlled tests may be needed to distinguish motivations.

## Materially different options

| Option | Mechanism | Product change | What it tests |
|---|---|---|---|
| Banner | Messaging | Explain Official tabs at the requested placement | Whether additional communication changes behavior |
| Separate states | Information architecture | Present Official and Community as distinct choices | Whether the content types are insufficiently differentiated |
| Official first | Choice architecture | Prioritize or recommend the Official version | Whether ordering/default drives deliberate selection |
| Contextual explanation | Timing | Explain Official value at song/version selection | Whether relevance improves at the moment of intent |
| Preview before Pro | Experience | Demonstrate part of the Official experience before gating | Whether experienced value improves willingness to upgrade |

Do not treat these as cosmetic A/B variants. Each option tests a different causal mechanism.

## Honest recommendation pattern

When behavioral evidence is missing, write:

```text
Separating Official and Community versions is the strongest structural option for
testing the choice-architecture hypothesis. It is not yet the recommended rollout:
current evidence does not distinguish between low visibility and weak perceived value.
First validate where users notice, understand, and reject the Official option.
```

When prior data supports one mechanism, cite the experiment, audience, placement, metric, result, and limitation before preferring that option.

## Metrics to consider

Select only metrics connected to the established objective. Possible examples include:

- Official option visibility or eligible reach;
- Official version selection rate;
- song-start conversion;
- successful tab load or engaged tab view;
- Pro trial or subscription entry;
- ARPU or expected ARPU;
- retention and tab-engagement guardrails.

Do not use this list as a fixed metric set. Define exposure and denominators for the actual flow.
