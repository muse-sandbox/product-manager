# Confluence context and publishing

## Tool location

Treat the directory selected by `CONFLUENCE_TOOLS_DIR` as a separate dependency. The project launcher defaults it from the repository's sibling layout. It connects to self-hosted Confluence at `alice.mu.se`.

Never use Atlassian Cloud MCP or another Confluence connector. Use only the repository wrapper from its own working directory:

```bash
: "${CONFLUENCE_TOOLS_DIR:?Set CONFLUENCE_TOOLS_DIR to the local Confluence tool}"
cd "$CONFLUENCE_TOOLS_DIR"
bash scripts/cnfl --help
bash scripts/cnfl search "query"
bash scripts/cnfl pull PAGE_ID
python3 scripts/extract_text.py PAGE_ID 20000
```

Do not print or copy `.env`, tokens, usernames, or credentials.

## Context-retrieval workflow

Before shaping a consequential request:

1. Search Confluence using specific product, surface, behavior, experiment, and metric terms.
2. Inspect likely parent pages and prior experiment pages.
3. Pull only relevant pages and extract readable text.
4. Record page title, page ID, URL, decision date when present, and the exact claim supported.
5. Distinguish current policy from historical context. Do not treat an old decision as a permanent requirement.
6. Cross-check result claims with `ug-analytics` when an experiment ID is available.

Return a short context ledger instead of a raw page dump.

## Write safety

Confluence reads are allowed during context gathering. Publishing is a separate state-changing step.

Do not push, create, move, or attach anything until:

1. Claude Code has saved a draft under `workspace/drafts/claude/`;
2. Codex has reviewed it under `workspace/reviews/codex/` when the decision is material;
3. Claude Code has addressed or explicitly rejected each material finding;
4. the user explicitly approves publishing to the named page ID or parent.

All content written to Confluence must be in English. Pull immediately before an approved push so version conflicts are detected. Preserve the canonical template and existing XHTML structure; never modify files under the Confluence tool's `templates/` directory.

If a valid page returns 404, report that the personal access token may have expired and direct the user to regenerate it. Do not attempt alternative credentials.
