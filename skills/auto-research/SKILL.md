---
name: auto-research
description: Token-light, high-control research harness for file-first, evidence-bound scientific work. Use when the user explicitly invokes $auto-research, $auto research, Auto Research mode, or asks Codex to use the Auto Research framework for initializing or continuing a research project, designing, executing, or reviewing experiments, analyzing failures, handling research feedback, binding evidence to claims, auditing claims, drafting manuscript outlines, or adopting/upgrading the Auto Research framework.
---

# Auto Research

## Purpose

Act as a session-level research harness over ordinary Codex work. Keep the conversation aligned to Auto Research's lifecycle, gates, roles, evidence discipline, and file-first state model without loading the full framework unless the current task needs it.

This skill does not replace the framework repository and does not create a runtime. Keep real project state in consumer repos, not in the framework source repo.

## Core Rules

- Treat `$auto-research`, `$auto research`, "Auto Research mode", or equivalent wording as explicit activation for the current conversation.
- Continue applying Auto Research context until the user explicitly exits or says not to use it for the current task.
- Inspect local `AGENTS.md` or equivalent rules before planning or changing files.
- Classify the repository before acting: `framework_repo`, `initialized_consumer_repo`, `partial_consumer_repo`, or `uninitialized_project`.
- In consumer repos, read project-local profile and state before generic framework files.
- In the framework repo, never store a real project's research state.
- Use an optional `.auto_research/TEAM_PROFILE.md` only when a high-risk decision or explicit team request needs project-specific role background.
- Preserve provenance: branch, revise, or append migration notes instead of rewriting historical cards.
- Separate verified facts, inferences, limitations, competing explanations, and next steps.
- Mark unsupported claims as `speculative`; bind claims to evidence before manuscript use.
- Default to one orchestrating agent. Use or simulate specialist roles only when a gate or risk justifies it.

## User-Facing Mode

Hide framework internals unless the user asks for them. Speak in plain research actions, not framework terms.

- Say "Can this result support that sentence?" instead of "evidence audit".
- Say "Can we say this more strongly?" instead of "claim strengthening".
- Say "Is this ready to run?" instead of "readiness gate".
- Say "This step needs your confirmation" instead of "action permission".
- Say "Should we record this result as something future writing can rely on?" instead of "evidence promotion".
- Say "Should we start writing the paper section?" instead of "manuscript drafting".

Match the user's conversation language in replies. Keep each reply in one visible language unless file names, IDs, commands, schema fields, or quoted text require English. In this framework repo, write files in English by default.

When a next step has meaningful choices, ask one short question before proceeding. Provide 2-3 concrete options, mark one as recommended, and explicitly allow a custom reply. Offer planning when useful. If the platform has a structured user-input or planning tool available, use it for these choice points; otherwise ask plainly in chat.

## Operating Kernel

Use this loop for any non-trivial Auto Research action:

1. **Route**: classify repo, task, autonomy level, and required gate before loading more files.
2. **Focus**: name the mainline question, active item, decision needed, current risk, and minimum next action.
3. **Design**: reduce the next action to the smallest valid research move; for experiments, lock the spine and readiness verdict before procedure details.
4. **Check control**: apply blocked moves and action permission before file writes, execution, specialist roles, evidence promotion, claim strengthening, or manuscript prose.
5. **Act or stop**: if allowed, make the smallest reversible change or execution step; if not allowed, return the exact missing approval, metric, baseline, evidence, or state fix.
6. **Record**: preserve facts, deviations, inferences, limitations, competing explanations, user corrections, and next action in the smallest durable artifact.
7. **Report**: tell the user what changed, what did not change, validation performed, open risks, and the next decision.

Optimize for decision quality per token. Prefer one primary active item, one next decision, and one durable update over broad scans or narrative summaries.

## Load Only What Is Needed

Start with `references/context-router.md` for repo classification, authority order, and minimal context loading. Then load at most the task-specific reference below:

| Task | Load |
| --- | --- |
| Initialize or adopt Auto Research in a project | `references/workflows.md`, then framework `prompts/init_project.md` if available |
| Daily continue, today, resume, start session, or Daily Brief | `references/control-loop.md` and `references/output-contracts.md` |
| Deep review, branch, revise, gate, or stage transition | `references/workflows.md` |
| Design, execute, or review experiments, including failures | `references/experiment-work.md` and relevant templates |
| Analyze evidence, failures, claims, or manuscript outline | `references/workflows.md` and `references/output-contracts.md` |
| User feedback, mainline drift, context budget, or autonomy decisions | `references/control-loop.md` and `references/output-contracts.md` |
| Decide what to say back to the user | `references/output-contracts.md` |
| Avoid common mistakes or debug bad behavior | `references/failure-modes.md` |
| Maintain or validate this skill itself | `references/forward-tests.md` |

Prefer framework files from `.auto_research/framework/` in consumer repos. When working inside the framework source repo, use local `framework/`, `templates/`, `prompts/`, and `examples/`.

## Minimal Workflow

1. Discover before asking: read files that can answer repo facts.
2. Align before writing: ask only preference, policy, or research-direction questions that files cannot answer.
3. Use the active stage, active item, risk, and next action from `research/STATE.md` when present.
4. Apply the relevant gate before crossing stages or strengthening claims.
5. Keep context small: start from profile, state, and active cards; load task-specific references only after the task requires them.
6. Load the optional team profile only for experiment design/review, failure review, method readiness, claim audit, manuscript planning, or when the user names the team or a role. Do not load it for ordinary daily continue.
7. Record framework-source files and default templates in English. In consumer repos, follow the project profile if it explicitly sets another file language.
8. Prefer compact verdicts and role reports over long reasoning. Expose only the reasoning needed for the user or next agent to audit the decision.

## MVP Boundaries

Do not add these unless the user explicitly changes framework scope:

- CLI
- SQLite or graph database
- Web UI
- automatic migrations
- automatic task queue
- complete multi-agent runtime
- automatic literature download

Repeated manual pain can be documented as a future engineering candidate, but keep the MVP file-first.
