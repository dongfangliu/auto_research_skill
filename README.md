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
- Experiment branch synthesis for PR-style consolidation of related experiment results.
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
    INIT_REPORT.md      # initialization discovery and audit record
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

The submodule stores reusable framework files only. Project research state belongs in `research/`, project-specific policy belongs in `.auto_research/PROJECT_PROFILE.md`, and optional project-specific role background belongs in `.auto_research/TEAM_PROFILE.md`.

## Quick Use / 快速使用

### What This Repo Is / 这个仓库是什么

**English:** Auto Research is a file-first framework for turning a research idea or an existing project into a traceable research workflow. It keeps project-specific state in the consumer repository and keeps this repository reusable as a framework.

**中文：** Auto Research 是一个“文件优先”的科研协作框架，用来把一个研究点子或已有工程接入可追踪的研究流程。真实项目状态放在使用它的项目仓库里，本仓库只保存可复用的框架规则、模板和技能。

### Relationship To Codex Or Claude Init / 和 Codex 或 Claude 初始化的关系

**English:** Codex or Claude Code initialization usually teaches the coding assistant how to work in a software repository. Auto Research initialization teaches the research workflow how to track goals, state, evidence, claims, and next actions. They can coexist.

**中文：** Codex 或 Claude Code 自己的初始化，通常是在告诉代码助手“这个工程怎么开发”。Auto Research 的初始化，是在告诉研究流程“这个科研项目怎么记录目标、状态、证据、结论和下一步”。两者可以共存。

Recommended order:

1. Run the coding assistant's normal project initialization first if you need `AGENTS.md`, `CLAUDE.md`, or local development rules.
2. Run Auto Research init after that, so it can read those local rules.
3. Use explicit wording such as `$auto-research-init` or `Read prompts/init_project.md`; avoid a bare `/init` when the tool may interpret it as its own built-in initializer.

推荐顺序：

1. 如果你需要 `AGENTS.md`、`CLAUDE.md` 或本地开发规则，先运行代码助手自己的工程初始化。
2. 再运行 Auto Research init，这样它会读取并尊重这些本地规则。
3. 使用明确说法，例如 `$auto-research-init` 或 `Read prompts/init_project.md`；不要只写一个模糊的 `/init`，因为不同工具可能会当成自己的内置初始化。

### Use With Codex / 在 Codex 中使用

After installing the skills and restarting Codex, activate Auto Research explicitly:

安装技能并重启 Codex 后，显式启用 Auto Research：

```text
$auto-research
```

Initialize a project:

初始化项目：

```text
Use $auto-research-init. 我想初始化当前研究项目。
先做只读 discovery，输出 Alignment Brief 和 Completeness Audit。
不要在我确认前创建或修改文件。
```

If you only have an idea:

如果你现在只有一个想法：

```text
Use $auto-research-init. 我现在只有一个研究点子：<写下你的想法>。
帮我判断怎么融入 Auto Research。先不要写文件。
```

If the repo already has code, notes, outputs, or drafts:

如果仓库里已经有代码、笔记、输出或草稿：

```text
Use $auto-research-init. 这个仓库已经有一些工程文件和研究材料。
请先做只读 discovery，告诉我哪些部分已经适合接入 Auto Research，哪些还缺失。
不要迁移或覆盖旧文件，先给我计划。
```

### Use With Claude Code Or Other Agents / 在 Claude Code 或其他代理中使用

If the framework is already available in the target project as `.auto_research/framework/`, ask:

如果目标项目里已经有 `.auto_research/framework/`，可以这样说：

```text
Read .auto_research/framework/prompts/init_project.md and follow it to initialize this research project.
First do read-only discovery, produce an Alignment Brief and Completeness Audit, then ask me the remaining intake questions.
Do not create or modify files before I approve the implementation plan.
```

If the framework has not been added yet, give the agent the contents of `prompts/init_project.md` from this repository or point it to this repository.

如果还没有添加 framework submodule，就把本仓库的 `prompts/init_project.md` 内容直接给代理，或者让它读取这个仓库。

### After Initialization / 初始化之后

Use short research commands after the base files exist:

基础文件创建后，可以用短指令继续工作：

```text
continue
review the current experiment
design the next experiment
audit whether this result can support the claim
turn this result into an evidence card
```

中文也可以直接说：

```text
继续
 review 当前实验
设计下一个实验
检查这个结果能不能支持这个结论
把这个结果整理成 evidence card
```

Auto Research should read the project profile and `research/STATE.md`, find the current active item, and avoid jumping into experiments, evidence promotion, claim strengthening, or manuscript wording without the required review and approval.

Auto Research 会读取项目 profile 和 `research/STATE.md`，找到当前活跃事项，并避免在没有必要确认和审查的情况下直接运行实验、提升证据、强化结论或写论文式表述。

### What Not To Expect / 不要期待它做什么

**English:** This MVP does not provide a CLI, database, web UI, automatic migration, task queue, or fully autonomous research runtime. It is a disciplined Markdown-based workflow for agents and humans.

**中文：** 当前 MVP 不提供 CLI、数据库、Web UI、自动迁移、任务队列或完整自动化科研运行时。它是一套给代理和人类共同使用的 Markdown 工作流纪律。

## Codex Skill Suite

This repository includes a Codex skill suite under `skills/`. The repository copy is the versioned source of truth, but Codex only uses the skills after they are installed into the local Codex skills directory and the session is restarted.

The main skill is explicit-first to reduce token overhead in unrelated work. Invoke `$auto-research` or `$auto research` when you want the research harness active. After that, narrower child skills can handle initialization, continuation, experiments, experiment synthesis, evidence/claims, and maintenance inside the active Auto Research context.

The full suite is:

- `auto-research`: session activator and compatibility dispatcher.
- `auto-research-init`: initialization, adoption, partial repair, and team calibration planning.
- `auto-research-continue`: daily continue, resume, review, branch, revise, gate, and stage navigation.
- `auto-research-experiment`: experiment design, readiness, execution review, branch synthesis, and failure review.
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

Experiment-heavy projects can also use PR-style branch synthesis after results accumulate:

```text
digest recent experiments
synthesize this experiment branch
consolidate EXP-0001-DECISION and EVD-0001 before claim audit
```

Synthesis cards live in `research/syntheses/`. They summarize bounded experiment threads and may recommend evidence promotion or claim audit, but they are not evidence and cannot strengthen claims directly.

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

Initialization is alignment-first and adaptive. The agent should understand whether the user has only a rough idea, an existing codebase, scattered notes/outputs, or a partial Auto Research setup before writing files.

During init, the agent should produce:

- an Alignment Brief that explains the project identity, goal, current uncertainty, records to preserve, and recommended Auto Research role
- a Completeness Audit that shows which initialization pieces are present, missing, optional, inconsistent, or intentionally untouched
- a short set of natural intake questions only for choices that files cannot answer
- an approved implementation plan before any file changes

If this framework is already available as `.auto_research/framework/` inside a project, ask a coding agent:

```text
Use $auto-research-init. Read `.auto_research/framework/prompts/init_project.md` and help initialize the current research project. First do read-only discovery, produce an Alignment Brief and Completeness Audit, then ask only the remaining intake questions. Do not create or modify files before I approve the implementation plan.
```

If the framework has not been added yet, provide `prompts/init_project.md` directly to the agent or point it to this repository.
