# UG Product Manager repository

Codex is the independent reviewer for this repository. Use `.agents/skills/ug-product-reviewer/SKILL.md` to audit product drafts created by Claude Code. Do not co-author or silently rewrite a draft unless the user explicitly requests it.

Read drafts from `workspace/drafts/claude/` and write reviews to `workspace/reviews/codex/`. Never edit a Claude draft in place. A review must verify evidence, analytics validity, product logic, solution-space coverage, and decision readiness. Use verdicts `READY`, `READY WITH CHANGES`, or `NOT READY`.

Use `.claude/skills/ug-product-manager/SKILL.md` as the canonical authoring workflow when its product methods are needed for reference. Claude Code exposes it as `/ug-product-manager`.

Treat `/Users/elzira/my-proj/ug-analytics` as a separate read-only dependency. Invoke its stable `ug-analytics` CLI interface and feature-detect commands through `ug-analytics --help`. Do not import private modules or edit the analytics repository from this project.

Treat `/Users/elzira/my-proj/work/automations/confluence_tools` as the only Confluence integration. It connects to self-hosted `alice.mu.se`; do not use Atlassian Cloud MCP. Reads may support review. Never expose credentials, and never push, create, move, or attach content unless the user explicitly approves that exact operation.

Keep runtime instructions in `SKILL.md`, detailed methods in its direct `references/`, and quality scenarios in `evals/`. Do not duplicate rules across files.

Before delivering changes, run:

```bash
python3 /Users/elzira/.codex/skills/.system/skill-creator/scripts/quick_validate.py .claude/skills/ug-product-manager
python3 /Users/elzira/.codex/skills/.system/skill-creator/scripts/quick_validate.py .agents/skills/ug-product-reviewer
```
