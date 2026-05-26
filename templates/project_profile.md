# Project Profile Template

```yaml
project_id:
project_name:
autonomy_level: L1 guided
default_language: English
framework_commit:
team_profile: .auto_research/TEAM_PROFILE.md
team_profile_use: needed_only
updated_at:
```

## Project Identity

Describe the project in one paragraph.

## Research Goal

State the current research goal and what would count as meaningful progress.

## Research Boundaries

List what the project is not claiming or not trying to solve.

## Claim Boundaries

List claims that must not be over-stated.

## Required Context

Files agents must read before meaningful work:

- 

## Artifact Policy

Naming, directory, and record-keeping rules:

- 

## Evidence Standards

What counts as weak, moderate, and strong evidence in this project:

- Weak:
- Moderate:
- Strong:

## Agent Policy

Project-specific activation rules:

- New experiment:
- Failure review:
- Claim recommendation:
- Manuscript:

## Team Profile Policy

Optional project-specific team profile:

- Team profile path:
- Use rule: read only for experiment design/review, failure review, method readiness, claim audit, manuscript planning, or when the user names the team or a role.
- Applicable stage: high-risk gates and team calibration, not ordinary daily continue.
- Trigger condition: a project-specific role background or custom advisor can improve the current decision.
- Failure risk: loading team context for routine work wastes context; treating role opinions as evidence can overstate claims.
- Custom advisors: use `advisor:<role_id>` for advisory reports only. They do not replace framework roles or approve gates.

## Blocked Moves

Moves that agents should not take without explicit approval:

- Experiment execution:
- Evidence promotion:
- Experiment synthesis:
- Claim strengthening:
- Manuscript prose:
- Profile or framework changes:
- Specialist or multi-agent work:

## Publish Standards

Minimum conditions before manuscript drafting or external claims:

- 

## Profile Update Triggers

When this profile should be revised:

- 

## Persistent Feedback Rules

Only record feedback here when it changes future project behavior, terms, claim boundaries, context budget, autonomy, or default review style. One-off response preferences should stay in the current response or affected card.
