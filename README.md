# UG Product Manager

An evidence-led product management skill for turning vague UG requests into problem definitions, solution spaces, experiment plans, and concise Pitch/Solution/Decision documents.

The project deliberately separates responsibilities:

- Claude Code with `ug-product-manager` shapes and documents product decisions.
- Codex with `ug-product-reviewer` independently audits the draft.
- The sibling `ug-analytics` project supplies read-only experiment data through its CLI.
- `CONFLUENCE_TOOLS_DIR` selects the local self-hosted Confluence tool used for context and approved publication.

Both skills live under `.claude/skills/`. The `.agents` path is a symlink to `.claude`, allowing Codex and Claude Code to discover the same canonical files without maintaining copies.

## Accounts and authentication

Orca does not provide or share credentials for this project. Each operator must sign in with their own accounts and keep authentication local to their machine. Claude Code, Codex, and Git operations launched through Orca inherit those local sessions. Corporate GitHub access must use the operator's assigned corporate account; do not copy another person's tokens, cookies, SSH keys, or account configuration.

## Use with Claude Code

Launch Claude Code from this directory. It automatically loads `CLAUDE.md` and discovers the project skill at `.claude/skills/ug-product-manager/SKILL.md`.

Invoke the skill directly:

```text
/ug-product-manager The request is "add a banner for Official tabs".
```

Claude may also invoke it automatically when a request matches the skill description.

## Desktop launcher

Double-click `Claude — UG Product Manager.command` on the desktop. The launcher opens this repository in Orca, starts Claude Code as the primary author, and starts a second Orca-managed handoff terminal. It also grants Claude access to the sibling analytics project and the configured local Confluence tool.

The launcher derives the repository path from its own location. It uses `UG_ANALYTICS_DIR` and `CONFLUENCE_TOOLS_DIR` when dependencies are not in the default sibling layout, and `ORCA_BIN`, `CLAUDE_BIN`, or `CODEX_BIN` when the corresponding CLI is not discoverable automatically.

The launcher never selects an account or injects credentials. Confirm the active Orca, Claude Code, Codex, and corporate GitHub accounts before starting work.

Example:

```text
Use /ug-product-manager. The request is "add a banner for Official tabs".
Inspect the available flow and prior evidence, generate materially different product
mechanisms, and draft only the supported Pitch sections.
```

The skill must not invent metrics, research, ownership, or forecast inputs. Missing evidence is an explicit output.

## Automatic two-agent workflow

1. In the Claude tab in Orca:

   ```text
   /ug-product-manager The request is "add a banner for Official tabs". Search relevant Confluence context and prior experiment data, then save a review-ready draft.
   ```

2. Claude saves the completed draft with `status: ready-for-review`. Orca waits until Claude is idle, then starts Codex in a separate tab with `$ug-product-reviewer`.

3. Codex saves the review with the exact draft SHA-256. Orca verifies the hash and sends the review back to the same Claude session.

4. Claude resolves every blocker and major finding and saves the accepted artifact under `workspace/final/`.

5. Only after checking the final artifact, explicitly ask Claude Code to publish it to a named Confluence page.

An unchanged draft is not reviewed twice. If the draft changes, its hash changes and Orca automatically requests a fresh review. See `.orca/README.md` for the handoff contract.

See `workspace/WORKFLOW.md` for the artifact handoff contract.

## Confluence safety

The Confluence tool is local and targets self-hosted `alice.mu.se`. The agent runs `bash scripts/cnfl` from `CONFLUENCE_TOOLS_DIR`; it must not use Atlassian Cloud MCP. Reads are part of context gathering. Push, create, move, and attachment operations require explicit approval after Codex review.
