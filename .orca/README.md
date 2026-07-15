# Orca product control and handoff

Orca and every CLI it launches must use the current operator's own locally authenticated accounts. The handoff does not inject credentials, switch accounts, or reuse another person's session. Corporate GitHub operations must keep the operator's assigned corporate account and existing local Git configuration.

The desktop launcher starts three Orca-managed terminals in this repository:

1. `Claude · UG Product Manager` — the primary author.
2. `Orca · Product plan approval` — the business-plan and decision-gate coordinator.
3. `Orca · Claude → Codex handoff` — the deterministic review coordinator.

For material work, Claude first writes a structured plan under `workspace/plans/`. The plan coordinator renders the task cockpit, creates business-readable Orca tasks, opens the plan, and blocks execution at an approval gate. `Approve and execute` injects the approved plan into the original Claude terminal. `Revise before execution` returns the plan for correction. `Reject` closes it without execution.

Discovery findings are recorded in the same cockpit. If a finding changes a fixed product direction, target population, primary metric, experiment structure, or promised deliverable, Claude marks the plan `needs_reapproval`; Orca creates another gate before Delivery resumes.

The coordinator waits for the Claude terminal to become `tui-idle`. It then
looks for a Markdown draft under `workspace/drafts/claude/` whose YAML header
contains `status: ready-for-review` and whose SHA-256 is not already recorded
in the corresponding Codex review.

Codex runs non-interactively in a separate Orca terminal. A successful review
must be saved as `workspace/reviews/codex/<draft>-review.md` and record the exact
`draft_sha256`. Only then does Orca create a tracked revision task and inject
the verified review into the original Claude terminal. Claude resolves it and
writes the accepted artifact under `workspace/final/`.

This makes the handoff idempotent: an unchanged draft is never reviewed twice.
Publishing to Confluence remains outside the automation and requires explicit
user approval.
