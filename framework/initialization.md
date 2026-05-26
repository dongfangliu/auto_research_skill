# Initialization Guide

Auto Research initialization is alignment-first. The framework should not be dropped into a research project as a blind file copy. The agent must first understand the project and confirm the user's intent.

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
  claims/
  manuscripts/
```

The project profile and research state belong to the consumer project, not to the framework submodule.

## Initialization Modes

### New project

Use when the repository has no `.auto_research/` and no `research/` directory.

The agent should discover existing project files, align with the user, then create the Auto Research directories and first state/profile files.

### Partial initialization

Use when some Auto Research files already exist.

The agent should report what exists, identify missing pieces, and ask whether to keep, rollback, or rebuild the partial setup before changing files.

### Existing project with old research records

Use when the repository already has experiments, notes, papers, outputs, or logs.

Default behavior is overlay mode: keep old records in place and link to them from `research/STATE.md` or future cards. Do not migrate records unless requested.

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
请读取 .auto_research/framework/prompts/init_project.md，
按其中流程帮助我初始化当前科研项目。
先做只读 discovery 和 Alignment Brief，
不要在我确认前创建或修改文件。
```

If the framework submodule has not been added yet, provide the prompt text directly to the agent or point it to the framework repository.
