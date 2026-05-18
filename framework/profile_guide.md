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

Put cross-project rules in this framework:

- General lifecycle.
- Common card schema.
- Generic agent roles.
- Generic gates.
- Submodule upgrade process.

## Update Triggers

Suggest a profile update when:

- A repeated workflow problem appears.
- A new artifact class becomes central.
- A gate is too weak or too heavy.
- A project-specific claim boundary changes.
- The project adopts a new framework version.

