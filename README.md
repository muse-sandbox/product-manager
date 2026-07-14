# UG Product Manager

An evidence-led product management skill for turning vague UG requests into problem definitions, solution spaces, experiment plans, and concise Pitch/Solution/Decision documents.

The project deliberately separates responsibilities:

- Claude Code with `ug-product-manager` shapes and documents product decisions.
- Codex with `ug-product-reviewer` independently audits the draft.
- `/Users/elzira/my-proj/ug-analytics` supplies read-only experiment data through its CLI.
- `/Users/elzira/my-proj/work/automations/confluence_tools` supplies self-hosted Confluence context and publishes approved final documents.

## Use with Claude Code

Launch Claude Code from this directory. It automatically loads `CLAUDE.md` and discovers the project skill at `.claude/skills/ug-product-manager/SKILL.md`.

Invoke the skill directly:

```text
/ug-product-manager The request is "add a banner for Official tabs".
```

Claude may also invoke it automatically when a request matches the skill description.

## Desktop launcher

Double-click `Claude — UG Product Manager.command` on the desktop. The launcher opens Claude Code in this project, grants read access to `/Users/elzira/my-proj/ug-analytics`, and configures the Python path required by the current `ug-analytics` installation.

Example:

```text
Use /ug-product-manager. The request is "add a banner for Official tabs".
Inspect the available flow and prior evidence, generate materially different product
mechanisms, and draft only the supported Pitch sections.
```

The skill must not invent metrics, research, ownership, or forecast inputs. Missing evidence is an explicit output.

## Two-agent workflow

1. In Claude Code:

   ```text
   /ug-product-manager The request is "add a banner for Official tabs". Search relevant Confluence context and prior experiment data, then save a review-ready draft.
   ```

2. Open this same repository in Codex and run:

   ```text
   Use $ug-product-reviewer to review workspace/drafts/claude/<draft>.md independently.
   ```

3. Back in Claude Code:

   ```text
   Read workspace/reviews/codex/<draft>-review.md. Resolve every blocker and major finding, record any evidence-backed disagreement, and save the accepted version under workspace/final/.
   ```

4. Only after checking the final artifact, explicitly ask Claude Code to publish it to a named Confluence page.

See `workspace/WORKFLOW.md` for the artifact handoff contract.

## Confluence safety

The Confluence tool is local and targets self-hosted `alice.mu.se`. The agent uses `bash scripts/cnfl` from `/Users/elzira/my-proj/work/automations/confluence_tools`; it must not use Atlassian Cloud MCP. Reads are part of context gathering. Push, create, move, and attachment operations require explicit approval after Codex review.
