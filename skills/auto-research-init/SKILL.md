---
name: auto-research-init
description: Thin Auto Research initialization harness. Use only after $auto-research is active or when the user explicitly invokes $auto-research-init, asks Auto Research to initialize or adopt a project, repair a partial setup, plan team calibration, or review framework adoption without implementing runtime features.
---

# Auto Research Init

## Purpose

Guide alignment-first initialization, submodule adoption, partial setup repair, and optional team calibration for Auto Research projects. Keep the work file-first and approval-gated.

## Applicable Stages

- Applicable stage: project initialization, framework adoption, partial consumer repair, project profile revision, team calibration planning, or consumer framework upgrade preparation.
- Trigger condition: the user asks to initialize, adopt, install, repair, calibrate the team, or create base Auto Research files after `$auto-research` is active or by invoking `$auto-research-init`.
- Failure risk: writing real research state into the framework repo, overwriting existing project records, migrating old records automatically, or creating a runtime registry.

## Minimum Context

1. Read local `AGENTS.md` or equivalent.
2. Load shared `../auto-research/references/context-router.md`.
3. Classify the repository before planning any file change.
4. In consumer or uninitialized repos, read obvious project docs that identify research goal, current records, claim boundaries, and local policies.
5. In partial consumer repos, read existing top-level `.auto_research/` files, `research/STATE.md` if present, and `.gitmodules` only when submodule state matters.
6. In the framework source repo, use only generic framework files and do not create consumer `research/` state.

## Reference Loading

- For initialization or adoption, load `../auto-research/references/workflows.md`.
- Load `prompts/init_project.md` from the framework source or submodule when an initialization prompt is needed.
- Load `../auto-research/references/output-contracts.md` when producing an Alignment Brief, Team Calibration Brief, Action Brief, or Final Report.
- Load `framework/submodule_adoption.md` or `framework/initialization.md` only when their exact rules are needed.
- Do not load experiment, claim, or manuscript references during base initialization unless the user explicitly asks for those artifacts.

## Workflow

1. Produce read-only discovery before asking preference questions.
2. Return an Alignment Brief that names project identity, research goal, current phase, active blocker, authoritative files, records to preserve, claim boundaries, recommended role, initialization status, and remaining questions.
3. Ask only policy or preference questions that files cannot answer.
4. Present the minimum implementation plan before creating or modifying files.
5. Create only approved Auto Research files from templates.
6. Offer team calibration after base profile and state exist; keep it optional.
7. Report created or updated files, preserved records, assumptions, framework source, team profile status, and next action.

## Blocked Actions

- Do not write files before approval under `L0` or `L1`.
- Do not store a concrete project's research state in this framework source repo.
- Do not rewrite historical cards or old records during adoption; link or append migration notes only.
- Do not create CLI commands, SQLite, Web UI, automatic migration, task queues, complete multi-agent runtime, or automatic literature download.
- Do not make `.auto_research/TEAM_PROFILE.md` mandatory or treat it as evidence or approval authority.

## Output Contract

Use `Alignment Brief` before initialization or major setup changes. Use `Team Calibration Brief` for optional team setup. Use `Final Report` only after approved file changes.
