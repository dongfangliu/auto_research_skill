---
name: auto-research-init
description: Thin Auto Research initialization harness. Use only after $auto-research is active or when the user explicitly invokes $auto-research-init, asks Auto Research to initialize or adopt a project, repair a partial setup, plan team calibration, or review framework adoption without implementing runtime features.
---

# Auto Research Init

## Purpose

Guide alignment-first initialization, adaptive intake, submodule adoption, partial setup repair, initialization completeness review, and optional team calibration for Auto Research projects. Keep the work file-first and approval-gated.

## Applicable Stages

- Applicable stage: project initialization, adaptive idea intake, existing project intake, framework adoption, partial consumer repair, project profile revision, team calibration planning, or consumer framework upgrade preparation.
- Trigger condition: the user asks to initialize, adopt, install, repair, calibrate the team, review what is initialized, or create base Auto Research files after `$auto-research` is active or by invoking `$auto-research-init`; also trigger when the user simply says `init` in an Auto Research context.
- Failure risk: writing real research state into the framework repo, making the user choose framework internals before intent is clear, overwriting existing project records, migrating old records automatically, treating optional pieces as required, or creating a runtime registry.

## Minimum Context

1. Read local `AGENTS.md` or equivalent.
2. Load shared `../auto-research/references/context-router.md`.
3. Classify the repository and intake shape before planning any file change: `idea_only`, `uninitialized_project`, `existing_project_intake`, `partial_consumer_repo`, `initialized_consumer_repo`, or `initialized_with_inconsistencies`.
4. In consumer or uninitialized repos, read obvious project docs that identify research goal, current records, claim boundaries, and local policies.
5. In partial consumer repos, read existing top-level `.auto_research/` files, `research/STATE.md` if present, and `.gitmodules` only when submodule state matters.
6. If there are no useful files, use the user's idea as the first context source and ask natural intake questions.
7. In the framework source repo, use only generic framework files and do not create consumer `research/` state.

## Reference Loading

- For initialization, adaptive intake, completeness audit, or adoption, load `../auto-research/references/workflows.md`.
- Load `prompts/init_project.md` from the framework source or submodule when an initialization prompt is needed.
- Load `../auto-research/references/output-contracts.md` when producing an Alignment Brief, Team Calibration Brief, Action Brief, or Final Report.
- Load `framework/submodule_adoption.md` or `framework/initialization.md` only when their exact rules are needed.
- Do not load experiment, claim, or manuscript references during base initialization unless the user explicitly asks for those artifacts.

## Workflow

1. Identify the user's starting shape before asking for framework choices.
2. Produce read-only discovery before asking preference questions; if no files exist, treat the user's idea as discovery context.
3. Return an Alignment Brief that names project identity, research goal, current phase or likely starting stage, active blocker or first uncertainty, authoritative files, records to preserve, claim boundaries, recommended role, initialization status, and remaining questions.
4. Return a Completeness Audit that labels expected pieces as `present`, `missing`, `optional`, `inconsistent`, `needs_confirmation`, or `intentionally_untouched`.
5. Ask only policy, preference, or research-direction questions that files cannot answer. Phrase them as natural user choices; avoid making the user pick card schemas, gates, or internal roles unless needed now.
6. Present the minimum implementation plan before creating or modifying files, including what will be patched, skipped, preserved, or asked later.
7. Create only approved Auto Research files from templates.
8. Offer team calibration after base profile and state exist; keep it optional.
9. Report created or updated files, preserved records, assumptions, framework source, team profile status, completeness status, and next action.

## Blocked Actions

- Do not write files before approval under `L0` or `L1`.
- Do not store a concrete project's research state in this framework source repo.
- Do not rewrite historical cards or old records during adoption; link or append migration notes only.
- Do not create CLI commands, SQLite, Web UI, automatic migration, task queues, complete multi-agent runtime, or automatic literature download.
- Do not make `.auto_research/TEAM_PROFILE.md` mandatory or treat it as evidence or approval authority.
- Do not reject idea-only initialization just because the repo has no code or notes.
- Do not convert old notes, outputs, notebooks, or drafts into cards unless the user explicitly approved that migration.

## Output Contract

Use `Alignment Brief` plus a Completeness Audit before initialization or major setup changes. Use `Team Calibration Brief` for optional team setup. Use `Final Report` only after approved file changes.
