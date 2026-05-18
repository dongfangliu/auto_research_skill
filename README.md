# Auto Research

Auto Research is a file-first MVP for agent-assisted research. It is not a full runtime yet. The goal is to validate a research workflow that can move from initial idea to manuscript outline while preserving provenance, allowing branch/review/revise at every stage, and keeping claims tied to evidence.

The framework is intended to be consumed by concrete research projects as a git submodule. The framework repo evolves independently; each project pins a specific framework commit and keeps its own research state, project profile, and artifacts outside the submodule.

## MVP Scope

This repository provides:

- Research lifecycle rules.
- Agent role and gate policies.
- Project profile guidance.
- Markdown templates for research cards.
- A minimal example project showing the full loop.
- Submodule adoption and upgrade instructions.

This MVP intentionally does not provide:

- CLI commands.
- SQLite or a graph database.
- Web UI.
- Automatic task queue.
- Automatic literature download.
- Automatic migration of old research records.

Those should be added only after file-based workflows have been tested in real projects.

## Recommended Consumer Layout

```text
<research_project>/
  .auto_research/
    framework/          # git submodule -> this repo
    PROJECT_PROFILE.md  # project-specific rules
    ADOPTION.md         # framework version and upgrade notes
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

The submodule stores reusable framework files only. Project research state belongs in `research/`, and project-specific behavior belongs in `.auto_research/PROJECT_PROFILE.md`.

## Research Loop

The framework supports eight stages:

```text
ideation
literature_review
hypothesis_design
experiment_design
experiment_execution
result_analysis
claim_building
manuscript_drafting
```

Every stage supports:

- `continue`: continue current work.
- `review`: inspect previous state and decisions.
- `branch`: create a new idea, hypothesis, or experiment from current findings.
- `revise`: append a revision without overwriting prior records.
- `gate`: request PI, audit, or specialist review before moving forward.

## Start Here

Read these files in order:

1. `framework/lifecycle.md`
2. `framework/state_model.md`
3. `framework/agent_roles.md`
4. `framework/profile_guide.md`
5. `framework/submodule_adoption.md`

Then inspect `examples/mini_project/` for a complete example trail.

