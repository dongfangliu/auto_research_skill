# Upgrade Path

The MVP starts file-first. Engineering should be added only when repeated pain appears in real projects.

## Upgrade Triggers

- Manual IDs become error-prone: add a lightweight CLI for ID generation.
- More than 50 cards: add an index generator.
- Evidence and claims become hard to audit: add graph validation.
- Multiple projects use the framework regularly: create a global Codex skill.
- Agents frequently miss context files: add a context loader.
- Users need visual navigation: consider a small web UI.
- Complex querying becomes necessary: consider SQLite or another local index.

## Expected Evolution

```text
submodule MVP
-> global skill
-> lightweight CLI
-> indexed research graph
-> optional web UI / runtime
```

## Non-Goals For MVP

- Fully autonomous publication.
- Automatic paper download and citation management.
- Database-backed task queue.
- Automated migration of historical cards.
- One-size-fits-all research methodology.

