---
name: auto-research
description: Token-light research harness for file-first, evidence-bound scientific work. Use when the user explicitly invokes $auto-research, $auto research, Auto Research mode, or asks Codex to use the Auto Research framework for initializing or continuing a research project, designing or reviewing experiments, analyzing failures, binding evidence to claims, auditing claims, drafting manuscript outlines, or adopting/upgrading the Auto Research framework.
---

# Auto Research

## Purpose

Act as a session-level research harness over ordinary Codex work. Keep the conversation aligned to Auto Research's lifecycle, gates, roles, evidence discipline, and file-first state model without loading the full framework unless the current task needs it.

This skill does not replace the framework repository and does not create a runtime. Keep real project state in consumer repos, not in the framework source repo.

## Core Rules

- Treat `$auto-research`, `$auto research`, "Auto Research mode", or equivalent wording as explicit activation for the current conversation.
- Continue applying Auto Research context until the user explicitly exits or says not to use it for the current task.
- Inspect local `AGENTS.md` or equivalent rules before planning or changing files.
- Classify the repository before acting: `framework_repo`, `initialized_consumer_repo`, `partial_consumer_repo`, or `uninitialized_project`.
- In consumer repos, read project-local profile and state before generic framework files.
- In the framework repo, never store a real project's research state.
- Preserve provenance: branch, revise, or append migration notes instead of rewriting historical cards.
- Separate verified facts, inferences, limitations, competing explanations, and next steps.
- Mark unsupported claims as `speculative`; bind claims to evidence before manuscript use.
- Default to one orchestrating agent. Use or simulate specialist roles only when a gate or risk justifies it.

## Load Only What Is Needed

Start with `references/context-router.md` for repo classification, authority order, and minimal context loading. Then load at most the task-specific reference below:

| Task | Load |
| --- | --- |
| Initialize or adopt Auto Research in a project | `references/workflows.md`, then framework `prompts/init_project.md` if available |
| Continue, review, branch, revise, or gate a research stage | `references/workflows.md` |
| Design, execute, or review experiments | `references/workflows.md` and relevant templates |
| Analyze evidence, failures, claims, or manuscript outline | `references/workflows.md` and `references/output-contracts.md` |
| Decide what to say back to the user | `references/output-contracts.md` |
| Avoid common mistakes or debug bad behavior | `references/failure-modes.md` |
| Maintain or validate this skill itself | `references/forward-tests.md` |

Prefer framework files from `.auto_research/framework/` in consumer repos. When working inside the framework source repo, use local `framework/`, `templates/`, `prompts/`, and `examples/`.

## Minimal Workflow

1. Discover before asking: read files that can answer repo facts.
2. Align before writing: ask only preference, policy, or research-direction questions that files cannot answer.
3. Use the active stage, active item, risk, and next action from `research/STATE.md` when present.
4. Apply the relevant gate before crossing stages or strengthening claims.
5. Record outputs in the project's established language; keep IDs, filenames, and schema fields in English.

## MVP Boundaries

Do not add these unless the user explicitly changes framework scope:

- CLI
- SQLite or graph database
- Web UI
- automatic migrations
- automatic task queue
- complete multi-agent runtime
- automatic literature download

Repeated manual pain can be documented as a future engineering candidate, but keep the MVP file-first.
