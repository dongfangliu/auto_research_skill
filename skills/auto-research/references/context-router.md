# Context Router

Use this reference to load the smallest useful context for an Auto Research task.

## Repository Classification

Classify the current repository before acting:

- `framework_repo`: contains framework source such as `framework/`, `templates/`, `prompts/`, `examples/`, or `skills/auto-research/`. Do not store real project state here.
- `initialized_consumer_repo`: contains `.auto_research/framework/`, `.auto_research/PROJECT_PROFILE.md`, and `research/STATE.md`.
- `partial_consumer_repo`: contains some Auto Research files but misses required profile, adoption, framework, or state files.
- `uninitialized_project`: contains no Auto Research structure.

If more than one classification seems plausible, state the evidence and use the safest interpretation before writing files.

## Authority Order

Use this priority order:

1. Current user request.
2. Local `AGENTS.md` or equivalent repository instructions.
3. Consumer project profile: `.auto_research/PROJECT_PROFILE.md`.
4. Consumer research state: `research/STATE.md` and active cards.
5. Framework files from `.auto_research/framework/` or local framework source.
6. Generic skill guidance.

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
- framework files only when needed for a gate, template, or workflow rule

For `partial_consumer_repo`, read:

- `AGENTS.md` if present
- all existing `.auto_research/` top-level files
- `research/STATE.md` if present
- `.gitmodules` if submodule state matters

For `uninitialized_project`, read:

- `AGENTS.md`, README, docs, notes, experiment logs, outputs, configs, and manuscript drafts that identify research context
- `.gitmodules` only when framework adoption is possible

## Ask Only After Discovery

Do not ask the user for facts that can be discovered from files. Ask only about:

- research direction or current priority
- intended Auto Research role
- autonomy level
- old-record policy
- exact framework URL when no local source defines it
- commit policy
- whether to migrate, link, or ignore old records

When a low-risk preference is unanswered, use the documented default and record it as an assumption.

## File Ownership

- `.auto_research/framework/`: framework submodule; edit in the framework repo, not as project state.
- `.auto_research/PROJECT_PROFILE.md`: consumer project-specific policy.
- `.auto_research/ADOPTION.md`: framework source, commit, upgrades, and migration notes.
- `.auto_research/INIT_REPORT.md`: initialization discovery, decisions, assumptions, and created files.
- `research/`: real research state, cards, evidence, claims, and manuscript artifacts.
