# Claude Code -> Codex -> Confluence

## Artifact states

1. Claude Code writes the first decision-ready artifact to `workspace/drafts/claude/` and sets `status: ready-for-review` only when its turn is complete.
2. Orca waits for the Claude terminal to become idle and starts Codex for any ready draft whose content hash has not been reviewed.
3. Codex writes an independent review to `workspace/reviews/codex/` without editing the draft and records the exact `draft_sha256`.
4. Orca sends the verified review path back to the original Claude terminal.
5. Claude Code resolves the review and writes the accepted version to `workspace/final/`.
6. Confluence is updated only after explicit user approval.

## Draft header

```yaml
---
authoring_agent: claude-code
status: ready-for-review
created: YYYY-MM-DD
source_experiments: []
source_confluence_pages: []
---
```

## Review header

```yaml
---
reviewer: codex
draft: workspace/drafts/claude/example.md
verdict: READY | READY WITH CHANGES | NOT READY
reviewed: YYYY-MM-DD
draft_sha256: <sha256 of the exact reviewed draft>
---
```

## Final header

```yaml
---
authoring_agent: claude-code
reviewed_by: codex
review: workspace/reviews/codex/example-review.md
status: final
---
```

Keep raw exports and temporary analysis outside `final/`.

The hash makes the handoff idempotent. Editing a reviewed draft produces a new
hash and therefore a new Codex pass; leaving it unchanged does not trigger a
duplicate review.
