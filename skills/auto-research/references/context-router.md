# Context Router

Use this reference to load the smallest useful context for an Auto Research task.

## Repository Classification

Classify the current repository before acting:

- `framework_repo`: contains framework source such as `framework/`, `templates/`, `prompts/`, `examples/`, or `skills/auto-research/`. Do not store real project state here.
- `initialized_consumer_repo`: contains `.auto_research/framework/`, `.auto_research/PROJECT_PROFILE.md`, and `research/STATE.md`.
- `partial_consumer_repo`: contains some Auto Research files but misses required profile, adoption, framework, or state files.
- `uninitialized_project`: contains no Auto Research structure.

If more than one classification seems plausible, state the evidence and use the safest interpretation before writing files.

For initialization, also identify the intake shape when useful:

- `idea_only`: the user has a rough research idea but there are no useful project files yet.
- `existing_project_intake`: the repo has code, docs, notes, outputs, notebooks, drafts, or logs that should inform setup.
- `initialized_with_inconsistencies`: base Auto Research files exist but paths, IDs, submodule state, or ownership boundaries conflict.

## Authority Order

Use this priority order:

1. Current user request.
2. Local `AGENTS.md` or equivalent repository instructions.
3. Consumer project profile: `.auto_research/PROJECT_PROFILE.md`.
4. Consumer research state: `research/STATE.md` and active cards.
5. Optional consumer team profile: `.auto_research/TEAM_PROFILE.md`, only when the task needs project-specific role background.
6. Framework files from `.auto_research/framework/` or local framework source.
7. Generic skill guidance.

Do not let generic framework rules override project-specific rules unless the user asks for a framework-level correction.

## Minimal Context By Repo Type

For `framework_repo`, read:

- `AGENTS.md`
- `README.md` when orientation is needed
- only the relevant `framework/`, `templates/`, `prompts/`, `examples/`, or `skills/` files

For `initialized_consumer_repo`, read:

- `AGENTS.md` if present
- `.auto_research/PROJECT_PROFILE.md`
- `research/STATE.md`
- `.auto_research/ADOPTION.md` when adoption or upgrade matters
- active cards listed by `STATE.md`
- latest synthesis only when `STATE.md` names it and the task depends on experiment-thread understanding, evidence candidates, or claim warnings
- `.auto_research/TEAM_PROFILE.md` only when a high-risk gate or explicit team request needs it
- handoff packet only when the user asks to resume from it, `STATE.md` names it for resume, or a direct consistency conflict points to it
- framework files only when needed for a gate, template, or workflow rule

For `partial_consumer_repo`, read:

- `AGENTS.md` if present
- all existing `.auto_research/` top-level files
- `research/STATE.md` if present
- `.gitmodules` if submodule state matters

For `uninitialized_project`, read:

- `AGENTS.md`, README, docs, notes, experiment logs, outputs, configs, and manuscript drafts that identify research context
- `.gitmodules` only when framework adoption is possible
- if no useful files exist, use the user's idea as the first context source and ask short intake questions

## Task Routing Matrix

Use this to preserve token efficiency:

| Task | Minimum files | Extra only if needed | Stop condition |
| --- | --- | --- | --- |
| Daily continue | profile, `STATE.md`, primary active card | none; do not read team profile by default | state/card conflict or high-risk next action |
| Handoff resume | daily files plus named handoff | directly conflicting decision/card | handoff conflicts with state or blocked moves |
| Experiment design/review | profile, state, active idea/hypothesis/brief | team profile when role background or advisor input matters; linked prior experiment only when cited | missing spine or readiness |
| Experiment execution | approved brief, state, required procedure files | team profile when execution approval depends on project-specific role policy; method-specialist output if required | permission not approved or readiness not pass |
| Experiment branch synthesis | profile, `STATE.md`, user-named experiments/decisions/evidence or state-named pending synthesis items | directly linked decisions, evidence, and branch-source idea/hypothesis | Synthesis Brief returned before writing `SYN` or changing claims |
| Result/evidence work | source decision/evidence, linked claim if claim-impacting | source experiment only if interpretation is unclear | promotion verdict not pass/hold as appropriate |
| Claim audit | claim and linked evidence | team profile when claim review needs project-specific advisor background; linked decision only if evidence boundary is unclear | missing evidence or promotion boundary |
| Manuscript outline | claim cards approved for outline and linked evidence summaries | team profile when writing/review roles need project-specific background; manuscript outline file | weak/speculative claim needs stronger wording |
| Initialization/adoption | local rules, obvious project docs or user idea, existing `.auto_research/` files, `.gitmodules` when relevant | `framework/initialization.md` or `prompts/init_project.md` when exact setup rules are needed | Alignment Brief and Completeness Audit returned before file writes |
| Team calibration | profile, state or project docs, relevant templates | existing team profile if present | user declines calibration or policy would store real project state in framework |
| Framework maintenance | `AGENTS.md`, relevant framework/skill/template/example files | README/changelog when user-visible | request would store real project state |

If `TEAM_PROFILE.md` has already been read in the same continuous session and there is no file change, user request to reload, or context recovery after compaction, do not read it again.

## Ask Only After Discovery

Do not ask the user for facts that can be discovered from files. Ask only about:

- research direction or current priority
- first decision or main uncertainty for idea-only intake
- intended Auto Research role
- autonomy level
- old-record policy
- exact framework URL when no local source defines it
- commit policy
- team calibration preferences that cannot be inferred from project files
- whether to migrate, link, or ignore old records

When a low-risk preference is unanswered, use the documented default and record it as an assumption.

## Minimal Conflict Handling

If `STATE.md` points to a missing primary card, the card ID does not match `primary_active_item`, the card status contradicts state, or a handoff conflicts with blocked moves:

1. Read only the directly named file if it exists.
2. Return a Resume Consistency Verdict.
3. Propose the minimal additive fix to `STATE.md`, active card, or handoff.
4. Do not scan all cards to infer the intended state unless the user asks for a deep review.

## File Ownership

- `.auto_research/framework/`: framework submodule; edit in the framework repo, not as project state.
- `.auto_research/PROJECT_PROFILE.md`: consumer project-specific policy.
- `.auto_research/TEAM_PROFILE.md`: optional consumer project role adaptations and advisory roles.
- `.auto_research/ADOPTION.md`: framework source, commit, upgrades, and migration notes.
- `.auto_research/INIT_REPORT.md`: initialization discovery, decisions, assumptions, and created files.
- `research/`: real research state, cards, evidence, claims, and manuscript artifacts.
- `research/syntheses/`: experiment branch synthesis cards. These summarize bounded experiment threads and are not evidence or claims.
