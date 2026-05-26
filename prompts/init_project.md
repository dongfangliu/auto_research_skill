# Auto Research Project Initialization Prompt

Use this prompt when a coding agent such as Codex or Claude Code should guide a research project through Auto Research initialization.

You are initializing Auto Research for the current repository. Your job is not to create files immediately. Your first responsibility is to align understanding with the user so the project profile and research state reflect the real research context.

The user may not know how their idea, existing project, or scattered files fit this framework. Treat `init` as an adaptive intake flow: discover what exists, explain what is already initialized or missing, ask natural questions about intent, then map the answers into the minimum file-first setup.

## Operating Rules

- Communicate with the user in the repository's default language. If unknown, use Chinese.
- Do not modify files until after the discovery and alignment phases are complete.
- Do not overwrite `AGENTS.md`, README files, existing experiment records, outputs, notebooks, paper notes, or project-specific rules.
- Do not rewrite historical research records during initialization.
- Do not automatically migrate old records into cards unless the user explicitly asks for that.
- Do not switch between SSH and HTTPS git URLs on your own. Use the exact framework URL specified by the user or already configured in the repository.
- Treat the target project's local rules as higher priority than this framework's generic rules.
- If the repository is already partially initialized, report the current state and ask whether to keep, rollback, or rebuild the partial initialization before changing anything.
- Do not require the user to know Auto Research stages, card types, gates, or directory layout before you help them clarify the project.
- If the user has only an idea and no files, use the idea as the first context source and ask short intake questions before proposing files.

## Phase 1: Intake Classification And Discovery

Classify the starting shape before planning. Use the safest matching category:

- `idea_only`: the user has a rough research idea but little or no project material.
- `uninitialized_project`: the repository has no Auto Research structure.
- `existing_project_intake`: the repository has code, docs, notes, outputs, notebooks, drafts, or logs but no complete Auto Research setup.
- `partial_consumer_repo`: some Auto Research files exist but required profile, adoption, framework, state, or directories are missing.
- `initialized_consumer_repo`: base Auto Research files exist.
- `initialized_with_inconsistencies`: base files exist but paths, IDs, submodule state, or ownership boundaries conflict.

Inspect the repository in read-only mode first when files exist. Look for:

- Git status and whether there are existing uncommitted changes.
- Existing `.auto_research/`, `.gitmodules`, and `research/` directories.
- `AGENTS.md`, README, docs, notes, experiment logs, output directories, configs, manuscript drafts, and project-specific instructions.
- Current research stage and latest active question.
- Existing claims, recommendations, candidates, or results that must not be overwritten.
- Existing naming conventions for experiments, outputs, configs, and papers.

Do not ask the user questions that can be answered from files.

## Phase 2: Alignment Brief

Before proposing changes, summarize your understanding:

- Project identity.
- Long-term research goal.
- Current research phase.
- Current active question or blocker.
- Authoritative files and records.
- Historical records that must not be overwritten.
- Known claim boundaries and overclaim risks.
- Recommended Auto Research role for this project: lightweight index, experiment workbench, claim audit layer, or full research state machine.
- Whether the repo appears uninitialized, partially initialized, or already initialized.
- Completeness Audit for `.auto_research/framework/`, `.auto_research/PROJECT_PROFILE.md`, `.auto_research/ADOPTION.md`, `.auto_research/INIT_REPORT.md`, optional `.auto_research/TEAM_PROFILE.md`, `research/STATE.md`, standard research directories, old records, and local rules.

Use these Completeness Audit labels:

- `present`: exists and appears usable.
- `missing`: required for the proposed initialization mode but absent.
- `optional`: useful only if the user chooses it.
- `inconsistent`: exists but conflicts with another file or expected ownership boundary.
- `needs_confirmation`: cannot be decided from files.
- `intentionally_untouched`: existing project material or old records that should be preserved.

Then list only the important questions that remain. These should be preference or policy questions, not facts available in the repository. Phrase questions in plain language before using framework terms.

## Phase 3: User Alignment

Get explicit user confirmation for:

- Project name and identity.
- Primary research goal.
- Current active stage: `ideation`, `literature_review`, `hypothesis_design`, `experiment_design`, `experiment_execution`, `result_analysis`, `claim_building`, or `manuscript_drafting`.
- The intended Auto Research role in this project.
- Autonomy level. Default to `L1 guided` unless the user chooses otherwise.
- Whether existing project rules remain the highest local authority. Default: yes.
- Whether old records should remain as linked archives or be migrated into cards. Default: linked archives only.
- The exact Auto Research framework URL if a submodule needs to be added.
- Whether to run optional team calibration after the base profile and state are created. Default: skip for now.
- Whether to create an initialization commit after review. Default: no automatic commit.

For idea-only intake, minimum confirmation is:

- Project identity or working name.
- Initial research goal.
- Main uncertainty or first decision.
- Whether Auto Research should start as lightweight organization, experiment tracking, evidence/claim discipline, or full lifecycle state.
- The next action the user wants help choosing.

For existing project intake, also confirm:

- Which existing files or folders are authoritative project context.
- Which old records are historical and should not be rewritten.
- Whether old records should stay linked as archives or be migrated into cards. Default: linked archives only.

Good intake questions:

- "Is this still just an idea, or should I also use the existing code and notes as context?"
- "What decision should this setup help you make first?"
- "Should old notes stay where they are and be linked later, or do you explicitly want them converted into cards?"

Avoid questions like "Which gate should this enter?" or "Which card schema should I instantiate first?" unless the user already understands the framework.

If the user does not answer a low-risk preference, use the default and record it as an assumption in the initialization report.

## Phase 4: Implementation Plan

After user alignment, present a concrete initialization plan:

- Files and directories to create.
- Existing files that will not be touched.
- Completeness Audit items to patch, skip, preserve, or ask about later.
- Whether a submodule will be added or reused.
- Which framework commit will be recorded.
- What `PROJECT_PROFILE.md` will contain.
- Whether `.auto_research/TEAM_PROFILE.md` will be skipped or created through a short team calibration.
- What `research/STATE.md` will contain.
- Whether `ADOPTION.md` and `INIT_REPORT.md` will be written.
- Any risks or manual checks.

Only proceed to file changes after the user approves this plan.

## Phase 5: Implementation

Create or update only the agreed files:

```text
.auto_research/
  framework/
  PROJECT_PROFILE.md
  TEAM_PROFILE.md
  ADOPTION.md
  INIT_REPORT.md
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

Use templates from `.auto_research/framework/templates/` when the framework submodule is available.

Create `.auto_research/TEAM_PROFILE.md` only if the user approved team calibration. The team profile should be drafted from discovered project files first, then refined with 3-5 preference questions. It must adapt existing framework roles and any `advisor:<role_id>` custom roles without changing evidence, gate, or action-permission rules.

For half-initialized repositories:

- Preserve existing `.auto_research/PROJECT_PROFILE.md`, `.auto_research/ADOPTION.md`, and `research/STATE.md` unless the user approved rebuilding them.
- Preserve existing `.auto_research/TEAM_PROFILE.md` unless the user approved updating team calibration.
- Patch missing sections rather than replacing the whole file when possible.
- Record all assumptions and unresolved questions in `INIT_REPORT.md`.

For idea-only repositories:

- Do not create experiment, evidence, claim, or manuscript cards unless the user specifically approves a first card.
- It is acceptable to create empty research directories and a `research/STATE.md` whose active stage is `ideation`.
- Record the main uncertainty and first next action rather than inventing a full research plan.

For existing projects with scattered records:

- Link old records from `INIT_REPORT.md` or `research/STATE.md` when useful.
- Do not move, rename, summarize into evidence, or convert old records into cards unless the user approved that exact migration.
- Mark unclear old claims or results as `needs_confirmation` or historical context, not verified evidence.

## Phase 6: Final Report

After initialization, report:

- Files created or updated.
- Framework URL and commit.
- Project-specific rules captured.
- Whether a team profile was created, skipped, or left unchanged.
- Existing records intentionally left untouched.
- Current active research state.
- Open questions.
- Recommended next action.
- Suggested git commit message, if the user wants to commit.

Do not claim the project is fully automated. Initialization only creates the file-first research state layer.
