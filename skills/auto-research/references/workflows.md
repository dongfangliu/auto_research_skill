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
6. Report created/updated files, framework URL or commit, captured rules, untouched records, active state, open questions, and next action.

Defaults:

- Autonomy level: `L1 guided`.
- Old records: link as archives, do not migrate.
- Local project rules outrank framework rules.
- No automatic commit.
- Use project language if established; otherwise Chinese for notes and English for IDs/schema fields.

## Stage Navigation

For `continue`, read `research/STATE.md`, active cards, and project profile. Return a short Stage Brief:

- active stage and item
- verified context
- current risk
- recommended next action
- files that will change, if any

For `review`, focus on state consistency, missing evidence, stale next actions, overclaim risks, and blocked items.

For `branch`, preserve `parent` or `branch_from`, state the branch reason, and link the new item back to its source.

For `revise`, append a dated revision or migration note. Do not erase the previous wording.

For `gate`, use the relevant gate from `framework/workflow_gates.md` and summarize pass, fail, or branch.

## Experiment Work

Before execution, create or review an experiment brief. Confirm:

- research question
- background facts
- fixed settings
- new variables
- success criteria
- failure branches
- diagnostics
- commands or procedure
- expected outputs
- PI review status

After execution, write or update a decision record separating:

- verified facts
- inferences
- limitations
- failures or regressions
- competing explanations
- minimum next step
- linked evidence

New experiments normally use `student-executor` plus `pi-reviewer`. If subagents are unavailable or unauthorized, simulate those roles explicitly.

## Evidence And Claim Work

Evidence cards should state source, what they support, what they conflict with, strength, limitations, and reuse guidance.

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

## Manuscript Work

Draft outlines from claim cards only. Before drafting:

- map each section to claim cards
- omit or mark weak claims as tentative
- list limitations and missing experiments
- avoid publication-ready phrasing unless project gates explicitly allow it

Use `writing-agent`, `claim-auditor`, and `pi-reviewer` perspectives for manuscript work.

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
