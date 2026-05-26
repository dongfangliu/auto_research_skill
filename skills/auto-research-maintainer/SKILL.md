---
name: auto-research-maintainer
description: Thin Auto Research framework-maintenance harness. Use only after $auto-research is active or when the user explicitly invokes $auto-research-maintainer, asks Auto Research to maintain framework docs, templates, examples, skill files, forward tests, adoption guidance, upgrade rules, or consumer compatibility without adding runtime features.
---

# Auto Research Maintainer

## Purpose

Improve the reusable Auto Research framework and skill suite while preserving file-first MVP boundaries and consumer-state compatibility.

## Applicable Stages

- Applicable stage: framework source maintenance, skill-suite maintenance, forward-test maintenance, template/example updates, and consumer framework adoption or upgrade review.
- Trigger condition: the user asks to change reusable framework files, prompts, templates, examples, skill routing, skill validation, forward tests, adoption guidance, or upgrade rules after `$auto-research` is active or by invoking `$auto-research-maintainer`.
- Failure risk: storing a real project's research state in the framework repo, adding runtime engineering during MVP, breaking existing consumer projects, or rewriting historical cards automatically.

## Minimum Context

1. Read local `AGENTS.md` or equivalent.
2. Load shared `../auto-research/references/context-router.md`.
3. In the framework source repo, read only the relevant `framework/`, `templates/`, `prompts/`, `examples/`, `skills/`, README, and changelog files.
4. For skill changes, read the affected `SKILL.md`, `agents/openai.yaml`, shared references, and `../auto-research/references/forward-tests.md`.
5. For consumer upgrade guidance, read `.auto_research/ADOPTION.md`, project profile, state, and directly affected migration notes only.

## Reference Loading

- Load `../auto-research/references/forward-tests.md` for skill or harness behavior changes.
- Load `../auto-research/references/failure-modes.md` when tightening guardrails.
- Load `../auto-research/references/stage-router.md` when routing or child-skill behavior changes.
- Load `framework/upgrade_path.md` and `framework/submodule_adoption.md` for adoption or upgrade guidance.
- Load `../auto-research/references/output-contracts.md` for Final Report or Gate Review after maintenance work.

## Workflow

1. Confirm the change is generic and reusable across consumer projects.
2. Identify applicable stage, trigger condition, and failure risk for every new rule.
3. Keep Markdown readable, diffable, and directly usable by agents.
4. Update examples only with fictional or minimal research trails.
5. Add or adjust forward tests for any changed routing, gate, output, or failure-mode behavior.
6. Validate skill files after edits and report any validator or environment limitations.

## Blocked Actions

- Do not add CLI, SQLite, graph database, Web UI, automatic migration, automatic task queue, complete multi-agent runtime, or automatic literature download.
- Do not store real project progress, experimental outputs, or manuscript artifacts in this framework repo.
- Do not put a single project's domain-specific policy into generic templates.
- Do not automatically rewrite consumer historical cards.
- Do not create extra skill documentation files such as skill-local README, installation guide, quick reference, or changelog.

## Output Contract

Use `Final Report` after file changes. Use `Gate Review` for compatibility or upgrade decisions. For review-only work, report changed behavior, validation, not-changed boundaries, open risks, and next action.
