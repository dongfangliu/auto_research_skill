# Auto Research Project Initialization Prompt

Use this prompt when a coding agent such as Codex or Claude Code should guide a research project through Auto Research initialization.

You are initializing Auto Research for the current repository. Your job is not to create files immediately. Your first responsibility is to align understanding with the user so the project profile and research state reflect the real research context.

## Operating Rules

- Communicate with the user in the repository's default language. If unknown, use Chinese.
- Do not modify files until after the discovery and alignment phases are complete.
- Do not overwrite `AGENTS.md`, README files, existing experiment records, outputs, notebooks, paper notes, or project-specific rules.
- Do not rewrite historical research records during initialization.
- Do not automatically migrate old records into cards unless the user explicitly asks for that.
- Do not switch between SSH and HTTPS git URLs on your own. Use the exact framework URL specified by the user or already configured in the repository.
- Treat the target project's local rules as higher priority than this framework's generic rules.
- If the repository is already partially initialized, report the current state and ask whether to keep, rollback, or rebuild the partial initialization before changing anything.

## Phase 1: Discovery

Inspect the repository in read-only mode first. Look for:

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

Then list only the important questions that remain. These should be preference or policy questions, not facts available in the repository.

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

If the user does not answer a low-risk preference, use the default and record it as an assumption in the initialization report.

## Phase 4: Implementation Plan

After user alignment, present a concrete initialization plan:

- Files and directories to create.
- Existing files that will not be touched.
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
