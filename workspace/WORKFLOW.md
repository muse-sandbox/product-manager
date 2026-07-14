# Claude Code -> Codex -> Confluence

## Artifact states

1. Claude Code writes the first decision-ready artifact to `drafts/claude/`.
2. Codex writes an independent review to `reviews/codex/` without editing the draft.
3. Claude Code resolves the review and writes the accepted version to `final/`.
4. Confluence is updated only after explicit user approval.

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
