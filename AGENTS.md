# AGENTS.md

This file constrains agent behavior while working in the `auto_research` framework source repo.

Use the user's conversation language when replying in chat. Repository files, templates, examples, skill files, schema fields, IDs, and file names default to English unless the user explicitly asks otherwise for a specific consumer project.

## 1. Current Position

`auto_research` is the MVP source repo for a research automation framework. It is not a concrete research project and not a complete runtime. The current goal is to preserve reusable rules, templates, examples, and agent protocols that concrete projects can consume through a git submodule.

Do not store the experimental progress of a real project in this repo. Real research state belongs in the consumer repo's `research/` directory.

## 2. Layer Boundaries

- **Framework repo**: generic lifecycle rules, templates, agent roles, gates, profile guidance, and examples.
- **Consumer project**: real project profile, state, research cards, experimental outputs, and manuscript artifacts.
- **Skill**: a thin adaptation layer that guides agents in using this framework.
- **Engineering runtime**: future work for ID generation, indexing, validation, migration, and task queues. Do not implement it during the MVP stage.

## 3. Modification Principles

- Keep Markdown files readable, diffable, and directly usable by agents.
- New rules must state their applicable stage, trigger condition, and failure risk.
- Do not put a single project's domain-specific rules into generic templates; project-specific rules belong in the project profile.
- Example projects may be fictional minimal research trails, but they must show branches, evidence, and claim binding.
- Do not automatically rewrite historical cards. Append a revision or migration note instead.

## 4. Agent Collaboration

Do not stack multiple agents by default. Activate roles by gate:

- Routine organization: primary agent.
- New experiment: `student-executor` + `pi-reviewer`.
- Failure review: `student-executor` + `pi-reviewer`, with `method-specialist` only when needed.
- Claim or manuscript work: `pi-reviewer` + `claim-auditor`, with `writing-agent` only when needed.
- Framework upgrade: `orchestrator` + `repro-auditor` to check consumer-state compatibility.

Use multiple students only when tasks are parallel and file ownership boundaries are clear. Use multiple mentors only for route changes, core claims, major failure attribution, or pre-publication review.

## 5. Evidence And Wording

All research conclusions must distinguish:

- verified facts
- inferences
- limitations
- competing explanations
- next steps

Claims must link to evidence. Claims without evidence may only be marked as `speculative` and must not enter strong manuscript wording.

## 6. MVP Constraints

Do not add:

- CLI
- SQLite
- Web UI
- automatic migration
- automatic task queue
- complete multi-agent runtime

Only engineer these pieces after file-first MVP usage in real projects exposes stable, repeated pain.
