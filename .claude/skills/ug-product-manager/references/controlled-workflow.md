# Controlled product workflow

Use this workflow for every material product request. A material request can change a product decision, experiment, specification, durable document, forecast, or stakeholder commitment.

## Mandatory preflight

Before research or authoring, inspect only enough supplied context to avoid redundant questions. Do not create a Pitch, Solution, experiment specification, mockup brief, or final recommendation yet.

Return:

1. **Task understanding** — business outcome, literal request, intended reader, and promised deliverable.
2. **Decision state** — what is already fixed, what is open, and whether the work is Discovery, Delivery, or both.
3. **Product questions** — ask at most three questions that can change scope, method, population, or deliverable. Always clarify whether a requested solution is approved for delivery or still requires evaluation when the evidence is ambiguous.
4. **Proposed plan** — business-readable Discovery, Delivery, and Review tasks.

Each task must state:

- the business question or output;
- why it matters;
- owner (`product-manager`, `analytics`, `user`, or `reviewer`);
- completion evidence;
- current status.

Do not describe shell commands, file reads, searches, or model operations as tasks.

## Plan artifact

Create `workspace/plans/<slug>.json` using this schema:

```json
{
  "schema_version": 1,
  "slug": "official-tabs-version-block",
  "title": "Official Tabs version block",
  "goal": "Prepare a test-ready product and measurement specification for the agreed Official Tabs block.",
  "status": "awaiting_approval",
  "decision_state": {
    "stage": "Discovery + Delivery",
    "fixed": ["Test the always-on Official Tabs block against the current selector"],
    "open": ["Validate whether first-session users answer the existing-user hypothesis"]
  },
  "questions_for_user": ["Confirm that the block direction is approved and does not require option comparison."],
  "assumptions": ["No cannibalization is a hypothesis, not a fact."],
  "deliverable": "Pitch, Control/Treatment solution specification, and analytics contract.",
  "tasks": [
    {
      "id": "D1",
      "phase": "Discovery",
      "title": "Validate the experiment population",
      "why": "The expected value comes from existing users, so a first-session-only test may estimate the wrong population.",
      "owner": "analytics",
      "done_when": "The analyst supports or rejects the population and provides the required segment read.",
      "status": "pending",
      "finding": null
    },
    {
      "id": "L1",
      "phase": "Delivery",
      "title": "Write the Control and Treatment behavior",
      "why": "Engineering needs one unambiguous implementation contract.",
      "owner": "product-manager",
      "done_when": "Every eligible state, transition, and paywall behavior is specified.",
      "status": "pending",
      "finding": null
    }
  ]
}
```

Run:

```bash
scripts/product-plan validate workspace/plans/<slug>.json
scripts/product-plan render workspace/plans/<slug>.json
```

The rendered Markdown is the human task cockpit. Set `status: awaiting_approval`, tell the user where the plan is, and stop. Do not treat silence, earlier generic approval, or a stakeholder quote as plan approval.

## Execution after approval

Begin only after Orca or the user explicitly approves the named plan. Execute the tasks in the approved order. Before starting a task, run:

```bash
scripts/product-plan task workspace/plans/<slug>.json D1 in_progress
```

After completing it, record the decision-relevant finding:

```bash
scripts/product-plan task workspace/plans/<slug>.json D1 completed --finding "First-session users do not estimate the expected existing-user effect; include both cohorts and pre-specify the split."
```

Keep findings concise and business-readable. Store detailed calculations and raw exports in their normal source locations, not in the cockpit.

## Re-approval gate

Set the plan to `needs_reapproval` and stop when Discovery changes any of these:

- fixed product direction or scope;
- target population or eligibility;
- primary metric or causal estimand;
- experiment structure;
- promised deliverable;
- a stakeholder assumption required for Delivery.

Explain the finding, its impact, and the smallest decision required. Do not quietly repair the premise inside the final document.

If the finding only fills an already-declared open input without changing the approved plan, continue automatically.

## Exceptions

Do not create a plan for a simple factual answer, a chat-only explanation, or a read-only critique that the user did not ask to operationalize. When the user asks to edit, publish, design, test, calculate, or produce a durable artifact, use the gate.
