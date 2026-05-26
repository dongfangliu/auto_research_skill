---
name: auto-research-continue
description: Thin Auto Research continuation and stage-navigation harness. Use only after $auto-research is active or when the user explicitly invokes $auto-research-continue, asks Auto Research to continue, resume, start today, review, branch, revise, gate, or navigate a research stage.
---

# Auto Research Continue

## Purpose

Resume Auto Research work with the smallest useful context. Keep daily work on one mainline decision and route high-risk actions to the proper gate or child skill.

## Applicable Stages

- Applicable stage: all research lifecycle stages for `continue`, `review`, `branch`, `revise`, `gate`, daily brief, handoff resume, and stage transition.
- Trigger condition: the user asks to continue, resume, start today, review progress, branch, revise, run a gate, or decide the next research action after `$auto-research` is active or by invoking `$auto-research-continue`.
- Failure risk: scanning the whole repo, reading team profile by default, trusting stale state, crossing into execution/evidence/claim/manuscript work without permission, or rewriting history.

## Minimum Context

1. Read local `AGENTS.md` or equivalent.
2. Load shared `../auto-research/references/context-router.md`.
3. In consumer repos, read `.auto_research/PROJECT_PROFILE.md`, `research/STATE.md`, and the primary active card named by state.
4. Read a handoff only when the user asks to resume from it, state names it, or a direct consistency conflict points to it.
5. Read `.auto_research/TEAM_PROFILE.md` only for high-risk gates, team calibration, explicit team/role requests, or when the task depends on project-specific role background.
6. In framework source repo maintenance, route to `$auto-research-maintainer`.

## Reference Loading

- For daily continue, resume, user feedback, context budget, or autonomy checks, load `../auto-research/references/control-loop.md` and `../auto-research/references/output-contracts.md`.
- For review, branch, revise, gate, or stage transition, load `../auto-research/references/workflows.md`.
- For stage-first requests, load `../auto-research/references/stage-router.md`.
- Load task-specific child skills or references only after state and the active card show they are needed.

## Workflow

1. Classify the repo and identify the primary active item.
2. Check state/card consistency before doing deeper work.
3. Name the mainline question, today's decision, current risk, minimum next action, parking lot, and do-not-touch scope.
4. For conflicts, return a Resume Consistency Verdict and stop before execution, evidence promotion, claim strengthening, or manuscript work.
5. For high-risk next actions, return an Action Permission Verdict or route to the proper child skill.
6. For branch or revise, preserve provenance and append rather than overwrite.

## Blocked Actions

- Do not load unrelated cards, manuscripts, old branches, or full experiment history for ordinary daily continue.
- Do not read the team profile merely because it exists.
- Do not execute experiments, promote evidence, strengthen claims, or draft manuscript prose from a daily brief.
- Do not treat `STATE.md` summaries as verified evidence unless source cards or evidence are read.
- Do not rewrite previous cards; append revision or migration notes.

## Output Contract

Use `Daily Brief` for today/start/resume requests. Use `Plain Research Reply` for short user-facing answers. Use `Stage Brief`, `Resume Consistency Verdict`, `Action Brief`, or `Action Permission Verdict` when the route or permission needs to be explicit.
