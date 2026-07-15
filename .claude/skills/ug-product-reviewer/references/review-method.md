# Independent review method

## Independence boundary

Review the submitted draft as if it came from another team. Do not infer missing support from fluent wording or from what the author probably meant. Ask whether a skeptical decision-maker could reproduce the conclusion from the cited evidence.

The reviewer may read the same primary sources as the author, but should not read hidden chain-of-thought, scratch notes, or an earlier self-critique from the authoring session.

Use the draft's source ledger as the retrieval index. Re-open the exact cited evidence for every numerical or decision-critical claim. Do not repeat broad Confluence searches, reload unrelated pages, or reconstruct already-supported background context unless the ledger is missing, the source conflicts with the claim, or the decision changed.

For a revision with an inspectable predecessor and prior review, use `delta` mode. Review the artifact diff, unresolved material findings, changed evidence and calculations, and any conclusion downstream of those changes. Preserve prior supported findings without re-verifying them. Escalate to `full` when the predecessor is unavailable or a new decision-critical premise appears.

## Claim audit

Use these statuses:

| Status | Meaning |
|---|---|
| Supported | The source directly supports the claim at the stated level of certainty. |
| Partially supported | The source supports a narrower or more qualified claim. |
| Contradicted | The source conflicts with the claim. |
| Unverifiable | The source is absent, inaccessible, or cannot establish the claim. |

Check numerical claims for denominator, population, time window, source query, and rounding. Check qualitative claims for sample, method, recency, and whether observations were generalized beyond the evidence.

## Analytics audit

Verify where applicable:

- assignment and actual exposure are not conflated;
- eligible population and exclusions are explicit;
- events measure the stated behavior;
- conversion windows are mature and equal across variants;
- repeated users or sessions are handled correctly;
- sample size and uncertainty are reported;
- multiple variants or metrics do not create unacknowledged false-positive risk;
- guardrails and practical magnitude are considered;
- causal conclusions are limited to randomized, valid comparisons.

## Product-logic audit

Test the chain:

```text
Observed behavior -> plausible cause -> intervention mechanism -> expected behavior change -> metric -> decision
```

Flag every broken or assumed link. A list of UI variants is not a solution space when all variants use the same mechanism. Require alternatives that test different causes when the cause is uncertain.

## Finding format

Each finding must contain:

- severity;
- the exact claim or section;
- why it matters to the decision;
- source or missing evidence;
- the smallest concrete correction.

Avoid generic feedback such as "add more detail" or "make this clearer."

Merge findings with the same root cause. Report no more than ten findings; include the highest decision impact first. A precise correction is more useful than an exhaustive catalogue of stylistic defects.
