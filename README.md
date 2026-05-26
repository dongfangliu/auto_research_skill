# Auto Research

Auto Research is a file-first MVP for agent-assisted research. It is not a full runtime yet. The goal is to validate a research workflow that can move from initial idea to manuscript outline while preserving provenance, allowing branch/review/revise at every stage, and keeping claims tied to evidence.

The framework is intended to be consumed by concrete research projects as a git submodule. The framework repo evolves independently; each project pins a specific framework commit and keeps its own research state, project profile, and artifacts outside the submodule.

## MVP Scope

This repository provides:

- Research lifecycle rules.
- Agent role and gate policies.
- Project profile guidance.
- Alignment-first initialization guidance.
- Markdown templates for research cards.
- Metric/baseline readiness rules for experiments and claims.
- Feedback intake and decision trace rules for corrections and handoffs.
- Result-to-evidence promotion rules before claims are strengthened.
- Resume consistency rules for state, active cards, and handoffs.
- Action permission and blocked-move rules for high-risk research actions.
- Optional team-profile guidance for project-specific role and advisor background.
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
    TEAM_PROFILE.md     # optional project-specific role/advisor profile
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

The submodule stores reusable framework files only. Project research state belongs in `research/`, project-specific policy belongs in `.auto_research/PROJECT_PROFILE.md`, and optional project-specific role background belongs in `.auto_research/TEAM_PROFILE.md`.

## Codex Skill Suite

This repository includes a Codex skill suite under `skills/`. The repository copy is the versioned source of truth, but Codex only uses the skills after they are installed into the local Codex skills directory and the session is restarted.

The main skill is explicit-first to reduce token overhead in unrelated work. Invoke `$auto-research` or `$auto research` when you want the research harness active. After that, narrower child skills can handle initialization, continuation, experiments, evidence/claims, and maintenance inside the active Auto Research context.

The full suite is:

- `auto-research`: session activator and compatibility dispatcher.
- `auto-research-init`: initialization, adoption, partial repair, and team calibration planning.
- `auto-research-continue`: daily continue, resume, review, branch, revise, gate, and stage navigation.
- `auto-research-experiment`: experiment design, readiness, execution review, and failure review.
- `auto-research-evidence-claims`: evidence promotion, claim audit, wording boundaries, and manuscript readiness.
- `auto-research-maintainer`: framework, template, example, skill, forward-test, adoption, and upgrade maintenance.

### Install From GitHub

If this repository is available on GitHub, ask Codex to install each skill directory:

```text
Install the Codex skill from https://github.com/dongfangliu/auto_research_skill/tree/master/skills/auto-research
Install the Codex skill from https://github.com/dongfangliu/auto_research_skill/tree/master/skills/auto-research-init
Install the Codex skill from https://github.com/dongfangliu/auto_research_skill/tree/master/skills/auto-research-continue
Install the Codex skill from https://github.com/dongfangliu/auto_research_skill/tree/master/skills/auto-research-experiment
Install the Codex skill from https://github.com/dongfangliu/auto_research_skill/tree/master/skills/auto-research-evidence-claims
Install the Codex skill from https://github.com/dongfangliu/auto_research_skill/tree/master/skills/auto-research-maintainer
```

Then restart Codex so the skills are loaded.

For private repositories, make sure your local GitHub credentials or `GITHUB_TOKEN` / `GH_TOKEN` can access the repository before asking Codex to install the skills.

Legacy single-skill installation of `skills/auto-research` still works. It uses the same shared references and falls back to internal routing when child skills are not installed.

### Update From GitHub

The Codex installer does not overwrite existing skills by default. To update the suite, remove the installed copies, reinstall from the same GitHub URLs, then restart Codex.

On Windows:

```powershell
$skillNames = @(
  "auto-research",
  "auto-research-init",
  "auto-research-continue",
  "auto-research-experiment",
  "auto-research-evidence-claims",
  "auto-research-maintainer"
)
foreach ($name in $skillNames) {
  $path = Join-Path $env:USERPROFILE ".codex\skills\$name"
  if (Test-Path $path) { Remove-Item -Recurse -Force $path }
}
```

On macOS or Linux:

```bash
for name in auto-research auto-research-init auto-research-continue auto-research-experiment auto-research-evidence-claims auto-research-maintainer; do
  rm -rf "${CODEX_HOME:-$HOME/.codex}/skills/$name"
done
```

Then ask Codex again to install the suite from GitHub. If you only installed the legacy main skill, remove and reinstall only `auto-research`.

### Install From A Local Checkout

For local development or offline use, install the full suite from a cloned checkout:

```powershell
$skillNames = @(
  "auto-research",
  "auto-research-init",
  "auto-research-continue",
  "auto-research-experiment",
  "auto-research-evidence-claims",
  "auto-research-maintainer"
)
foreach ($name in $skillNames) {
  $dest = Join-Path $env:USERPROFILE ".codex\skills\$name"
  if (Test-Path $dest) { Remove-Item -Recurse -Force $dest }
  Copy-Item -Recurse ".\skills\$name" $dest
}
```

On macOS or Linux:

```bash
for name in auto-research auto-research-init auto-research-continue auto-research-experiment auto-research-evidence-claims auto-research-maintainer; do
  dest="${CODEX_HOME:-$HOME/.codex}/skills/$name"
  rm -rf "$dest"
  mkdir -p "$(dirname "$dest")"
  cp -R "./skills/$name" "$dest"
done
```

Restart Codex after installation so the skills are loaded.

### Use The Skill

After installation, users can invoke `$auto-research` or `$auto research` once to enter Auto Research mode for the current conversation. The main skill is configured with `allow_implicit_invocation: false`, so ordinary coding or writing tasks should not load it automatically. For example:

```text
$auto-research help me continue this research project
```

Then follow up naturally:

```text
continue
review the last experiment
turn the evidence into claim cards
```

The skill suite loads detailed guidance lazily from `skills/auto-research/references/`, so a small continue/review task does not need to load initialization, manuscript, or upgrade instructions. Child skills are thin harness layers; the shared references remain the source of truth.

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

For framework orientation, read these files in order:

1. `framework/lifecycle.md`
2. `framework/state_model.md`
3. `framework/agent_roles.md`
4. `framework/profile_guide.md`
5. `framework/initialization.md`
6. `framework/submodule_adoption.md`

Then inspect `examples/mini_project/` for a complete example trail.

## Initialize A Project

Initialization is alignment-first. The agent should understand the project and confirm the user's intent before writing files.

If this framework is already available as `.auto_research/framework/` inside a project, ask a coding agent:

```text
Use $auto-research-init. Read `.auto_research/framework/prompts/init_project.md` and help initialize the current research project. First do read-only discovery and produce an Alignment Brief. Do not create or modify files before I approve the implementation plan.
```

If the framework has not been added yet, provide `prompts/init_project.md` directly to the agent or point it to this repository.
