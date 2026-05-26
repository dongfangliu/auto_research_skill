# Workflows

Use these procedures after classifying the repository with `context-router.md`.

## Session Actions

Use the framework stage actions consistently:

- `continue`: resume the active item without changing branch.
- `review`: inspect cards, decisions, evidence, risks, and next actions.
- `branch`: create a new card from current findings while preserving source provenance.
- `revise`: append a revision section; do not overwrite old records.
- `gate`: request PI, auditor, or specialist review before moving forward.

Before crossing stages, record current item ID, evidence level, main risk, next action, and whether review is required.

## Project Initialization

Follow `prompts/init_project.md` when it exists. Otherwise use this sequence:

1. Run read-only discovery.
2. Produce an Alignment Brief with project identity, goal, current phase, active question, authoritative files, historical records, claim boundaries, recommended Auto Research role, and initialization status.
3. Ask only preference or policy questions that remain.
4. Present an implementation plan listing files and directories to create or update.
5. After approval, create only agreed Auto Research files from templates.
6. Offer optional short team calibration after the base profile and state exist.
7. Report created/updated files, framework URL or commit, captured rules, team profile status, untouched records, active state, open questions, and next action.

Defaults:

- Autonomy level: `L1 guided`.
- Old records: link as archives, do not migrate.
- Local project rules outrank framework rules.
- No automatic commit.
- Use the project profile's file language if explicitly established; otherwise write notes in English. Keep IDs and schema fields in English.
- Team profile is optional and skipped unless the user approves team calibration.

## Team Calibration

Use this only after project discovery or when the user asks to create or revise the project team.

1. Read project files that already identify goals, methods, risks, and claim boundaries.
2. Draft functional role adaptations for the existing framework roles.
3. Ask 3-5 preference questions only for details that cannot be inferred.
4. Store approved team information in `.auto_research/TEAM_PROFILE.md`.
5. Keep `PROJECT_PROFILE.md` limited to `team_profile` and `team_profile_use`.

Rules:

- Team profiles improve review focus; they do not create a runtime or automatic scheduling.
- Custom roles must use `advisor:<role_id>` and are advisory only.
- Advisor reports do not approve experiments, promote evidence, strengthen claims, or draft manuscript-ready wording.
- If the profile points to a missing team file, continue with generic roles and offer the minimal fix when team context is needed.

## Stage Navigation

For ordinary `continue`, `today`, `resume`, or start-session requests, use `control-loop.md` and `output-contracts.md` directly. Do not load this workflow reference unless the user asks for deeper review, branch, revise, gate, or stage transition.

For deep review, read project profile, `research/STATE.md`, and the primary active card first. Return a Stage Brief or Daily Brief plus the deeper review scope:

- mainline question
- today's active item
- read-now context and state-derived context
- current risk
- today's decision
- recommended next action
- do not do today
- may-change files and do-not-touch files

For `review`, first identify the primary active item, then focus on state consistency, missing evidence, stale next actions, overclaim risks, and blocked items.

Before stage transition, experiment execution, evidence promotion, claim strengthening, or handoff resume, use the Resume Consistency Gate. If state and the active card conflict, stop and request the minimal additive fix before deeper work.

For `branch`, preserve `parent` or `branch_from`, state the branch reason, and link the new item back to its source.

For `revise`, append a dated revision or migration note. Do not erase the previous wording.

For `gate`, use the relevant gate from `framework/workflow_gates.md` and summarize `pass`, `revise`, `block`, or `branch`.

Before any action that changes artifacts or research direction, apply Action Permission:

- evidence promotion
- claim strengthening
- manuscript prose or publication-style wording
- experiment execution
- failure-attribution-driven stop, branch, hypothesis rejection, or negative claim
- resolving state/handoff conflicts by editing files
- profile policy or framework version changes

Check autonomy level, profile blocked moves, state blocked moves, latest user correction, and required upstream gates. Under `L1 guided`, ask first or block high-risk actions unless the user has already approved the specific action.

## Experiment Work

For experiment design, execution, PI review, or failure review, load `references/experiment-work.md`. Do not load it for ordinary `continue`; first return a Daily Brief, then load experiment guidance only after the user confirms design, execution, or review.

At the workflow level, experiment work must:

- preserve the mainline question
- pass the Experiment Spine before execution
- pass Metric/Baseline Readiness before execution when measurement or comparison affects the decision
- keep student execution and PI critique separate
- record deviations, failures, competing explanations, and linked evidence
- use direct PI Verdicts instead of vague review prose
- use the optional team profile only when project-specific role background or `advisor:<role_id>` input improves the current decision

## Evidence And Claim Work

Evidence cards should state source, what they support, what they conflict with, strength, limitations, and reuse guidance.

Before creating or upgrading an evidence card from a result, use the Result-to-Evidence Gate:

- move verified facts forward without upgrading them
- keep inferences separate from facts
- carry limitations, deviations, sanity checks, and competing explanations
- state what the evidence does not support
- set allowed and forbidden claim wording

Decision records, draft experiment briefs, readiness verdicts, PI opinions, and handoffs cannot directly strengthen claims. They must first support an evidence card that passes interpretation.

Before promoting evidence, also apply Action Permission. Ambiguous, failed, draft, readiness-only, or claim-impacting evidence promotion should be `ask first` or `blocked` unless the project profile explicitly allows it.

Claim cards must include:

- claim text
- intended use
- supporting evidence
- conflicting evidence
- allowed wording
- forbidden wording
- evidence strength
- manuscript section
- claim audit

Do not strengthen a claim beyond linked evidence. Unsupported claims stay `speculative` and must not be used as strong manuscript language.

Comparative claims also require an executed, ready metric/baseline trial. A draft or `revise` readiness verdict can motivate the next experiment, but it cannot strengthen the claim.

Before claim strengthening, apply Action Permission. Under `L1 guided`, claim strengthening requires explicit approval after claim and evidence gates pass.

## Manuscript Work

Draft outlines from claim cards only. Before drafting:

- map each section to claim cards
- omit or mark weak claims as tentative
- list limitations and missing experiments
- avoid publication-ready phrasing unless project gates explicitly allow it

Use `writing-agent`, `claim-auditor`, and `pi-reviewer` perspectives for manuscript work.

Before manuscript prose or publication-style wording, apply Action Permission. Weak, speculative, or demo-only claims may support outline or limitation notes only unless the user explicitly approves a draft and the claim gates allow the wording.

## Framework Adoption Or Upgrade

For consumer projects:

1. Record old and new framework commits.
2. Summarize template or gate changes.
3. Update `.auto_research/ADOPTION.md`.
4. Add migration notes only; do not rewrite existing research cards automatically.
5. Use `orchestrator` plus `repro-auditor` perspective.

For the framework source repo:

- keep changes generic and cross-project
- do not encode domain-specific project policy
- update examples only with fictional or minimal trails
- keep MVP boundaries unless the user explicitly changes them
