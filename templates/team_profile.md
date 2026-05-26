# Team Profile Template

```yaml
project_id:
team_profile_id: team-0001
status: draft
created_at:
updated_at:
source_project_profile: .auto_research/PROJECT_PROFILE.md
team_profile_use: needed_only
calibration_status: draft
review_owner: orchestrator
```

## Purpose

Describe the project-specific research team lens in one paragraph. This file adapts generic Auto Research roles to the project's domain, methods, risks, and review style.

This is not a runtime agent registry. It does not create automatic scheduling, independent authority, or evidence.

## Use Rule

- Applicable stage: experiment design, experiment execution review, result analysis, claim building, manuscript planning, team calibration, or any user request that names a team member or role.
- Trigger condition: read this file only when a decision benefits from project-specific role background, when `PROJECT_PROFILE.md` points to it and the task is a high-risk gate, or when the user asks to use the team.
- Failure risk: reading it for ordinary daily continue wastes context; treating a role opinion as evidence can over-strengthen claims; letting an advisor approve work can bypass gates.

## Source Context Used

List the project files or user answers used to draft this team profile.

- 

## Core Role Adaptations

Use these rows to adapt existing framework roles. Keep each role functional and decision-oriented.

| Framework Role | Project Background | Review Focus | Blind Spots To Counter | Output Constraints |
| --- | --- | --- | --- | --- |
| orchestrator |  | Mainline question, active item, decision order. |  | Must preserve state/profile authority and one-decision discipline. |
| student-executor |  | Smallest valid experiment or analysis step. |  | Must record facts, commands, outputs, deviations, and limits. |
| pi-reviewer |  | Direction, evidence sufficiency, overclaim risk. |  | Must give a direct verdict and minimum next action. |
| method-specialist |  | Metrics, baselines, controls, sampling, numerical or qualitative validity. |  | Must block execution when readiness is not decision-ready. |
| claim-auditor |  | Evidence-to-claim wording boundaries. |  | Must not strengthen claims beyond linked evidence. |
| literature-specialist |  | Prior work, disputes, and missing comparisons. |  | Must separate paper claims from verified project facts. |
| writing-agent |  | Outline or draft organization from approved claims. |  | Must not invent unsupported claims for narrative flow. |

## Custom Advisory Roles

Custom roles use `advisor:<role_id>`. Advisors provide domain-specific critique but do not replace framework roles.

| Advisor ID | When To Consult | Background | Can Advise On | Must Not Decide | Required Output |
| --- | --- | --- | --- | --- | --- |
| advisor:example |  |  |  | Experiment approval, evidence promotion, claim strength, manuscript readiness. | Role Report |

## Collaboration Rules

- Applicable stage: any task that uses role reports, specialist review, or handoff.
- Trigger condition: a core role adaptation or `advisor:<role_id>` is used in the current answer, card, review, or handoff.
- Failure risk: custom advisors can create false authority if their advice is treated as a gate verdict or evidence.

Rules:

- Advisors are consultative only. They may provide a Role Report, dissent, risk, or suggested next action.
- The `orchestrator` resolves advisor input against `PROJECT_PROFILE.md`, `STATE.md`, active cards, and framework gates.
- `pi-reviewer`, `method-specialist`, and `claim-auditor` gates remain responsible for approvals and blocks.
- Advisor opinions, PI opinions, readiness verdicts, and handoffs are not evidence. Claim impact requires evidence promotion from verified facts.
- Ordinary research cards should keep `owner_agent` as a framework core role. Use `advisor:<role_id>` in Role Reports, review notes, or handoffs only when needed.
- Do not consult multiple advisors unless their scopes are distinct and the decision is high risk.

## Calibration Questions

Use these questions only after discovery has already read available project files. Ask only what cannot be inferred.

1. Which expertise is most likely to catch bad research decisions in this project?
2. What mistake should the PI-style reviewer be especially strict about?
3. What should the student/executor optimize for: speed, reproducibility, coverage, or minimal decisive tests?
4. Which method risk most often invalidates results in this project?
5. What style of dissent should future reviews preserve?

## Update Triggers

- The research direction, methods, dataset, evaluation standard, or claim boundary changes.
- A new method or domain risk becomes central to decisions.
- The same review omission happens more than once.
- The user corrects PI style, advisor scope, decision strictness, or team composition.
- The team profile causes context bloat or role opinions to override evidence.

## Revision Notes

Append dated notes. Do not erase prior team assumptions unless the user explicitly asks for cleanup.

- 
