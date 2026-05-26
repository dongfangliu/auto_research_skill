# Initialization Guide

Auto Research initialization is alignment-first. The framework should not be dropped into a research project as a blind file copy. The agent must first understand the project and confirm the user's intent.

Initialization should also be adaptive. A user may type `init` with only a rough idea, with an existing codebase, with old notes and outputs, or with a half-created Auto Research structure. The agent's job is to translate that starting point into the smallest useful Auto Research setup without requiring the user to already understand the framework.

## What Initialization Creates

A typical project receives:

```text
.auto_research/
  framework/          # optional submodule
  PROJECT_PROFILE.md  # local project profile
  TEAM_PROFILE.md     # optional project-specific role/advisor profile
  ADOPTION.md         # framework version and adoption history
  INIT_REPORT.md      # initialization alignment and audit report
research/
  STATE.md
  ideas/
  literature/
  hypotheses/
  experiments/
  evidence/
  syntheses/
  claims/
  manuscripts/
```

The project profile and research state belong to the consumer project, not to the framework submodule.

## Initialization Modes

### Idea-only intake

Use when the user has a research idea but the repository has little or no project material.

The agent should accept the idea as sufficient starting context, ask natural questions about the goal and next decision, then create a lightweight profile and `research/STATE.md` only after approval. Do not force the user to choose card types, gate names, or directory details before the project identity and mainline question are clear.

### New project

Use when the repository has no `.auto_research/` and no `research/` directory.

The agent should discover existing project files, align with the user, then create the Auto Research directories and first state/profile files.

### Existing project intake

Use when the repository already contains code, README files, configs, notes, outputs, notebooks, paper drafts, or other materials but no complete Auto Research setup.

The agent should infer only what files support, separate facts from inferences, identify old records that must be preserved, and ask the user how Auto Research should fit the project. Default to linking old records as archives rather than migrating them into cards.

### Partial initialization

Use when some Auto Research files already exist.

The agent should report what exists, identify missing pieces, and ask whether to keep, rollback, or rebuild the partial setup before changing files.

### Existing project with old research records

Use when the repository already has experiments, notes, papers, outputs, or logs.

Default behavior is overlay mode: keep old records in place and link to them from `research/STATE.md` or future cards. Do not migrate records unless requested.

## Adaptive Intake Flow

The intake flow is for users who do not know how their idea or repository maps to Auto Research.

- Applicable stage: project initialization, framework adoption, partial setup repair, or first-time project profile creation.
- Trigger condition: the user invokes `init`, asks to initialize/adopt Auto Research, or gives a rough idea or existing project and wants help fitting it into the framework.
- Failure risk: asking the user to choose framework internals too early, copying templates before understanding intent, migrating old records without approval, or treating initialization as a complete runtime.

Use this sequence:

1. **Listen for the starting shape.** Determine whether the user has idea-only context, an existing project, old research records, a partial Auto Research setup, or an already initialized project with inconsistencies.
2. **Discover before asking.** Read local rules and obvious project files before asking for facts. If there are no files, use the user's idea as the first source of context.
3. **Return an Alignment Brief and Completeness Audit.** Explain what is known, what is inferred, what is missing, and what should be left untouched.
4. **Ask natural intake questions.** Ask about research intent and policy in plain language. Do not ask the user to choose internal card types or gates unless the choice matters now.
5. **Map the answer to framework artifacts.** Translate the user's goal into `PROJECT_PROFILE.md`, `research/STATE.md`, `ADOPTION.md`, `INIT_REPORT.md`, and optional empty research directories.
6. **Plan before writing.** Present the exact files to create or patch and get approval.

Good intake questions are about user intent:

- "Is this still just an idea, or should I also use the existing code and notes as context?"
- "What is the first decision you want this research setup to help with?"
- "Should old notes stay as linked archives for now, or do you explicitly want them converted into cards?"
- "Do you want lightweight organization, experiment tracking, evidence/claim discipline, or full lifecycle state?"

Avoid questions that expose internal machinery too early:

- "Which gate should this enter?"
- "Which card schema should I instantiate first?"
- "Do you want the state machine role to be claim audit layer or full research state machine?" unless the user already understands those terms.

## Completeness Audit

Before planning file changes, report the initialization status of each expected piece.

- Applicable stage: every initialization, adoption, repair, or init review.
- Trigger condition: the repository may be uninitialized, partially initialized, already initialized, or inconsistent.
- Failure risk: overwriting useful local state, treating optional files as required, or missing a broken setup because some files exist.

Use these labels:

- `present`: exists and appears usable.
- `missing`: required for the approved initialization mode but absent.
- `optional`: useful only if the user chooses that feature.
- `inconsistent`: exists but conflicts with another file or expected ownership boundary.
- `needs_confirmation`: cannot be decided from files.
- `intentionally_untouched`: existing project material or old records that should be preserved.

Check at least:

| Area | Paths | Notes |
| --- | --- | --- |
| Framework source | `.auto_research/framework/`, `.gitmodules` | Reuse existing submodule; do not change URL protocol silently. |
| Project profile | `.auto_research/PROJECT_PROFILE.md` | Required for initialized consumers. |
| Adoption record | `.auto_research/ADOPTION.md` | Required when framework adoption is recorded. |
| Init report | `.auto_research/INIT_REPORT.md` | Records discovery, answers, assumptions, and audit results. |
| Team profile | `.auto_research/TEAM_PROFILE.md` | Optional; create only after team calibration approval. |
| Research state | `research/STATE.md` | Required dashboard for active stage and next action. |
| Research directories | `ideas/`, `literature/`, `hypotheses/`, `experiments/`, `evidence/`, `syntheses/`, `claims/`, `manuscripts/` | Empty directories are acceptable after initialization. |
| Existing records | notes, outputs, notebooks, drafts, old logs | Preserve and link; migrate only on explicit request. |
| Local rules | `AGENTS.md`, README, docs, configs | Treat project-specific rules as higher authority. |

Completeness audit should guide the plan, not act as an automatic migration engine.

## User Alignment Checklist

Before writing files, align on:

- Project identity and goal.
- Current research stage.
- Current active question or blocker.
- Intended role of Auto Research.
- Autonomy level.
- Whether project-specific rules outrank framework rules.
- Whether old records should be linked or migrated.
- Exact framework submodule URL, if adding a submodule.
- Whether to run optional team calibration after the base profile and state are created.
- Whether to commit after initialization.

For idea-only intake, the minimum alignment is project identity, initial research goal, current uncertainty, intended Auto Research role, autonomy level, and first next action. For existing project intake, also align on which existing materials are authoritative, which records are historical, and whether old records should be linked or migrated.

## Defaults

- Autonomy level: `L1 guided`.
- Old records: linked archive, not migrated.
- Project rules: highest local authority.
- Commit: no automatic commit.
- Language: use the project's established language; otherwise Chinese for research notes and English for field names.
- Team profile: optional; if created, read only when a high-risk decision or explicit team request needs it.

## Safety Rules

- Do not overwrite `AGENTS.md`.
- Do not rewrite old experiment records.
- Do not silently change framework submodule URL protocol.
- Do not make publication-readiness claims during initialization.
- Do not elevate generic framework rules above local project rules.

## Optional Team Calibration

After `PROJECT_PROFILE.md` and `research/STATE.md` exist, the agent may offer a short team calibration flow.

- Applicable stage: project initialization, project profile revision, or the first high-risk gate where project-specific role background would improve review.
- Trigger condition: the user wants a concrete project research team, repeated role-specific mistakes appear, or the project enters experiment, failure, claim, or manuscript work.
- Failure risk: making team setup mandatory can overload initialization; using team personas as authority can bypass evidence and gates.

The agent should first draft the team from discovered project files, then ask only 3-5 preference questions that cannot be inferred. Store the result in `.auto_research/TEAM_PROFILE.md` and keep `PROJECT_PROFILE.md` to the path and use rule.

## Recommended Agent Entry Point

Ask the agent:

```text
Use $auto-research-init. Read `.auto_research/framework/prompts/init_project.md` and help initialize the current research project. First do read-only discovery, produce an Alignment Brief and Completeness Audit, then ask only the remaining intake questions. Do not create or modify files before I approve the implementation plan.
```

If the framework submodule has not been added yet, provide the prompt text directly to the agent or point it to the framework repository.
