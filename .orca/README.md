# Orca handoff

Orca and every CLI it launches must use the current operator's own locally authenticated accounts. The handoff does not inject credentials, switch accounts, or reuse another person's session. Corporate GitHub operations must keep the operator's assigned corporate account and existing local Git configuration.

The desktop launcher starts two Orca-managed terminals in this repository:

1. `Claude · UG Product Manager` — the primary author.
2. `Orca · Claude → Codex handoff` — the deterministic coordinator.

The coordinator waits for the Claude terminal to become `tui-idle`. It then
looks for a Markdown draft under `workspace/drafts/claude/` whose YAML header
contains `status: ready-for-review` and whose SHA-256 is not already recorded
in the corresponding Codex review.

Codex runs non-interactively in a separate Orca terminal. A successful review
must be saved as `workspace/reviews/codex/<draft>-review.md` and record the exact
`draft_sha256`. Only then does Orca send the review path back to the original
Claude terminal and request the accepted artifact under `workspace/final/`.

This makes the handoff idempotent: an unchanged draft is never reviewed twice.
Publishing to Confluence remains outside the automation and requires explicit
user approval.
