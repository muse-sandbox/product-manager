# UG Product Manager

Use the project skill `/ug-product-manager` for product shaping, experiment planning, UG document drafting, result interpretation, and evidence critique. Invoke it automatically when the user provides a vague solution request, asks what to test, asks to fill the Pitch/Solution/Decision template, or asks for a rollout decision.

Use the current operator's own locally authenticated Orca, Claude, Codex, and GitHub sessions. Never request, copy, expose, or substitute another person's credentials. Corporate repository operations must use the operator's assigned corporate GitHub account and existing local Git configuration.

Treat the sibling `ug-analytics` project as a separate read-only data dependency. Use the installed `ug-analytics` CLI and inspect `ug-analytics --help` before relying on a command. When the sibling layout is unavailable, use `UG_ANALYTICS_DIR`. Never edit the analytics repository from this workspace and never print `UG_COOKIE` or other credentials.

Treat the directory selected by `CONFLUENCE_TOOLS_DIR` as the only Confluence integration. The launcher defaults it from the repository's sibling project layout. It targets self-hosted `alice.mu.se`; never use Atlassian Cloud MCP. Follow `.claude/skills/ug-product-manager/references/confluence-tool.md`, run `bash scripts/cnfl` from the tool directory, and never expose its `.env` or credentials.

For every consequential product claim, distinguish fact, calculation, assumption, decision, and evidence gap. Do not invent metrics, research, user motivations, expected lift, ownership, or dates. If evidence cannot rank solution options, recommend the next cheapest learning step.

Answer in the user's language. Draft UG experiment-template content in English unless the user requests another language.

Keep durable product outputs concise and decision-oriented. Do not save hidden reasoning or temporary data dumps as final artifacts.

Claude Code is the primary author. Save material drafts to `workspace/drafts/claude/`, then request an independent Codex review. Do not edit the Codex review. Resolve its findings and save the accepted artifact to `workspace/final/`. Do not push to Confluence until the user explicitly approves the exact page operation after review.
