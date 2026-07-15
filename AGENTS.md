# UG Product Manager repository

Codex is the independent reviewer for this repository. Use `.agents/skills/ug-product-reviewer/SKILL.md` to audit product drafts created by Claude Code. `.agents` is a discovery alias for the canonical `.claude` directory, so maintain both skills only under `.claude/skills/`. Do not co-author or silently rewrite a draft unless the user explicitly requests it.

Use only the current operator's own locally authenticated accounts in Orca and in every CLI that Orca launches. Never reuse another person's session, shared credentials, copied cookies, or hardcoded tokens. For corporate GitHub operations, preserve the operator's assigned corporate account and existing local Git identity; do not rewrite authentication or account settings automatically.

Read drafts from `workspace/drafts/claude/` and write reviews to `workspace/reviews/codex/`. Never edit a Claude draft in place. A review must verify evidence, analytics validity, product logic, solution-space coverage, and decision readiness. Use verdicts `READY`, `READY WITH CHANGES`, or `NOT READY`.

For material work, inspect the approved business plan under `workspace/plans/`. Verify that the draft preserves fixed decisions, incorporates Discovery findings, and does not silently change scope, population, primary metric, experiment structure, or deliverable. Do not penalize a Delivery document for omitting solution alternatives when the approved plan records the mechanism as fixed.

Use `.claude/skills/ug-product-manager/SKILL.md` as the canonical authoring workflow when its product methods are needed for reference. Claude Code exposes it as `/ug-product-manager`.

Treat the sibling `ug-analytics` project as a separate read-only dependency. Invoke its stable `ug-analytics` CLI interface and feature-detect commands through `ug-analytics --help`. When the sibling layout is unavailable, use `UG_ANALYTICS_DIR`. Do not import private modules or edit the analytics repository from this project.

Treat the directory selected by `CONFLUENCE_TOOLS_DIR` as the only Confluence integration. The launcher defaults it from the repository's sibling project layout. It connects to self-hosted `alice.mu.se`; do not use Atlassian Cloud MCP. Reads may support review. Never expose credentials, and never push, create, move, or attach content unless the user explicitly approves that exact operation.

Keep runtime instructions in `SKILL.md`, detailed methods in its direct `references/`, and quality scenarios in `evals/`. Do not duplicate rules across files.

Before delivering changes, run:

```bash
python3 "${CODEX_HOME:-$HOME/.codex}/skills/.system/skill-creator/scripts/quick_validate.py" .claude/skills/ug-product-manager
python3 "${CODEX_HOME:-$HOME/.codex}/skills/.system/skill-creator/scripts/quick_validate.py" .claude/skills/ug-product-reviewer
```
