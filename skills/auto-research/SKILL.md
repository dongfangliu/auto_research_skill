---
name: auto-research
description: Research harness for file-first, evidence-bound scientific work. Use when the user invokes $auto-research, $auto research, Auto Research mode, or a research harness; when a repository contains .auto_research/, .auto_research/framework/, research/STATE.md, Auto Research templates, research cards, hypotheses, experiments, evidence, claims, or manuscript materials; or when the user asks to initialize a research project, continue research, discuss direction like a PI, navigate ideation/literature/hypothesis/experiment/result/claim/manuscript stages, design or review experiments, analyze failures, bind evidence to claims, audit claims, draft manuscript outlines, or adopt/upgrade the Auto Research framework.
---

# Auto Research

## Purpose

Act as a session-level research harness over ordinary Codex work. Keep the conversation aligned to Auto Research's lifecycle, gates, roles, evidence discipline, and file-first state model.

This skill does not replace the framework repository and does not create a runtime. Load framework files from the current project when available, and keep real project state in the consumer project, not in the framework repository.

## Session Mode

When the user explicitly invokes `$auto-research`, `$auto research`, "Auto Research mode", or "research harness", treat Auto Research mode as active for the current conversation.

While active:

- Interpret short follow-ups such as "continue", "review the last experiment", "next step", "make this a claim", or "go back to ideation" through Auto Research context.
- Keep using this harness until the user explicitly exits or says this task should not use Auto Research.
- Accept exit phrases such as "exit Auto Research mode", "stop using Auto Research", "this time do not use Auto Research", "normal Codex mode", or equivalent local-language wording.
- Do not require the user to repeat `$auto-research` in every message.

For a new conversation, require explicit invocation again unless natural-language triggering and repository evidence clearly indicate Auto Research work.

## Bootstrap

Before planning or changing files, classify the current repository:

- `framework_repo`: this repository contains the framework source, templates, prompts, and examples. Do not store a real project's research state here.
- `initialized_consumer_repo`: `.auto_research/framework/`, `.auto_research/PROJECT_PROFILE.md`, and `research/STATE.md` exist.
- `partial_consumer_repo`: some Auto Research files exist, but initialization is incomplete.
- `uninitialized_project`: no Auto Research structure exists.

Then load only the context needed for the current intent:

- Always inspect local `AGENTS.md` or equivalent project rules when present.
- In a consumer repo, read `.auto_research/PROJECT_PROFILE.md`, `research/STATE.md`, and `.auto_research/ADOPTION.md` if present.
- Read framework files through `.auto_research/framework/` in consumer repos, or local framework files when working inside the framework repo.
- Prefer these framework files first: `README.md`, `framework/lifecycle.md`, `framework/state_model.md`, `framework/workflow_gates.md`, `framework/agent_roles.md`, `framework/profile_guide.md`, `framework/initialization.md`, and `framework/submodule_adoption.md`.
- Read templates only when creating or reviewing that card type.

Treat project-local rules and profile as higher priority than generic framework rules.

## Intent Recognition And Alignment

Before acting, identify the user's likely intent. You may guess, but the user decides when the intent affects research direction, stage, roles, claims, experiments, or state.

Recognize these intent classes:

- `project_initialization`
- `stage_navigation`: ideation, literature_review, hypothesis_design, experiment_design, experiment_execution, result_analysis, claim_building, manuscript_drafting
- `pi_discussion`: direction, risk, route choice, contribution, failure attribution
- `agent_collaboration`: use of student-executor, pi-reviewer, literature-specialist, method-specialist, claim-auditor, repro-auditor, or writing-agent
- `experiment_work`: brief, execution, result record, failure review, decision record
- `evidence_work`: facts, outputs, limits, competing explanations, evidence cards
- `claim_audit`: evidence binding, claim strength, allowed wording, forbidden wording
- `manuscript_work`: outline or draft from evidence-linked claims only
- `framework_adoption_or_upgrade`

If multiple interpretations are plausible:

1. State the most likely interpretation and why in one concise sentence.
2. Offer 2-4 mutually exclusive choices, with one recommended choice.
3. Wait for the user's selection before taking actions that write state, switch stage, start/represent agent collaboration, execute experiments, strengthen claims, or modify manuscript-facing content.

Use alignment questions for meaningful ambiguity, not for facts that can be discovered from files.

## Workflow Discipline

For every research task:

- Locate the active stage, active item, current risk, and next recommended action from `research/STATE.md` when available.
- Preserve branch and provenance relationships.
- Use `continue`, `review`, `branch`, `revise`, and `gate` as the default stage actions.
- Run the appropriate workflow gate before moving across stages.
- Append revisions or migration notes instead of rewriting historical cards.
- Keep facts, inferences, limitations, competing explanations, and next steps separate.
- Mark unsupported claims as `speculative`.
- Bind claims to evidence before using them in manuscript planning.
- Do not present manuscript language as publication-ready unless the project profile and gates explicitly support that level.

## Role Discipline

Default to a single orchestrating agent. Activate roles only when the task or gate benefits from separation:

- New experiment: student-executor plus pi-reviewer.
- Failure review: student-executor plus pi-reviewer, and optionally method-specialist.
- Claim or manuscript work: pi-reviewer plus claim-auditor, and optionally writing-agent.
- Framework upgrade in a consumer repo: orchestrator plus repro-auditor.

Do not actually spawn subagents unless the user has authorized agent delegation in the current environment and the file responsibilities are clear. When subagents are not available or not authorized, simulate the role perspectives explicitly in one response.

Every delegated or simulated role should report:

```text
Facts
Inferences
Risks
Open Questions
Recommended Next Action
Files / Commands / Outputs
```

## Initialization Protocol

For project initialization, follow the framework initialization prompt when available:

- Perform read-only discovery first.
- Produce an alignment brief before file changes.
- Ask only preference or policy questions that cannot be answered from the repository.
- Confirm project identity, research goal, active stage, intended Auto Research role, autonomy level, local rule priority, old-record policy, framework source, and commit policy.
- Present an implementation plan before writing files.
- Create or update only the agreed Auto Research files.

Default assumptions:

- Autonomy level: `L1 guided`.
- Old records: linked archives, not migrated.
- Project rules outrank generic framework rules.
- No automatic commit.

## MVP Boundaries

Do not add these unless the user explicitly changes the framework scope:

- CLI
- SQLite or graph database
- Web UI
- automatic migrations
- automatic task queue
- complete multi-agent runtime
- automatic literature download

Repeated manual pain can be documented as a future engineering candidate, but keep the MVP file-first.
