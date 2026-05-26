# Project Profile Guide

`PROJECT_PROFILE.md` is the bridge between the general framework and a specific research project.

## Initialization Workflow

When creating a profile, the agent should:

1. Read existing project files first: README, AGENTS, docs, experiment records, config summaries, and current state.
2. Draft a profile from discovered facts.
3. Ask only preference questions that cannot be inferred from files.
4. Mark assumptions explicitly.
5. Record update conditions so the profile can evolve.

Do not ask the user for information that the repository already contains.

## Required Sections

A project profile should include:

- Project identity.
- Research goal.
- Research boundaries.
- Claims that must not be over-stated.
- Default language.
- Domain terms.
- Required context files.
- Artifact naming rules.
- Agent activation rules.
- Optional team profile path and use rule.
- Evidence standards.
- Publish standards.
- Blocked moves.
- Profile update triggers.

## Profile vs Framework

Put project-specific rules in the profile:

- Domain metrics.
- Required scripts.
- Project-specific forbidden claims.
- Local experiment numbering.
- Local output conventions.
- The path to a project team profile and when to read it.

Put cross-project rules in this framework:

- General lifecycle.
- Common card schema.
- Generic agent roles.
- Generic gates.
- Submodule upgrade process.

## Profile vs Team Profile

`PROJECT_PROFILE.md` should keep the durable project policy: autonomy, claim boundaries, required context, blocked moves, and the path to the optional team profile.

`.auto_research/TEAM_PROFILE.md` should keep project-specific role background and custom advisory roles.

- Applicable stage: team calibration, experiment design/review, failure review, method readiness, claim audit, manuscript planning, or a user request that names the team.
- Trigger condition: role background or advisory expertise can improve a high-risk decision.
- Failure risk: putting detailed team biographies into the profile bloats every resume; putting policy or claim boundaries only in the team profile can hide authoritative rules from ordinary work.

Team profiles are functional, not roleplay-first. They should record each role's expertise, review focus, likely blind spots, and output constraints. Custom roles use `advisor:<role_id>` and remain advisory.

## Update Triggers

Suggest a profile update when:

- A repeated workflow problem appears.
- A new artifact class becomes central.
- A gate is too weak or too heavy.
- A project-specific claim boundary changes.
- The project adopts a new framework version.
- The team profile path, use rule, or advisor boundaries change.
