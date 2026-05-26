# Project Profile: Research Continuity Mini Project

```yaml
project_id: mini_project
project_name: Research Continuity Mini Project
autonomy_level: L1 guided
default_language: English
framework_commit: mvp-0.15-example
team_profile: TEAM_PROFILE.md
team_profile_use: needed_only
updated_at: 2026-05-26
```

## Project Identity

This mini project explores whether structured research cards help agents resume interrupted research tasks with fewer missing context errors.

## Research Goal

Create a small demonstration trail that tests whether a structured state file plus linked cards improves task resumption.

## Research Boundaries

This example does not claim statistical validity, real human productivity improvement, or publication-ready evidence.

## Claim Boundaries

Do not claim that the framework improves all research workflows. Only claim that this example demonstrates a plausible audit path and highlights the need for a recovery metric and baseline.

## Required Context

Daily continue:

- `STATE.md`
- Primary active card listed by `STATE.md`

Deep review or gate:

- Relevant card files linked from `STATE.md`
- Latest synthesis when `STATE.md` names one and the task concerns experiment branch understanding, evidence candidates, or claim warnings.
- Framework lifecycle, state model, and workflow gates when needed

## Artifact Policy

Use manual IDs. Do not rewrite earlier cards; append revision notes.

## Evidence Standards

- Weak: single simulated trial or qualitative observation.
- Moderate: repeated trials across different task types.
- Strong: controlled evaluation with independent raters or quantitative recovery metrics.

## Agent Policy

- New experiment: student-executor + pi-reviewer.
- Failure review: student-executor + pi-reviewer.
- Claim recommendation: pi-reviewer + claim-auditor.
- Manuscript: writing-agent + claim-auditor + pi-reviewer.

## Team Profile Policy

- Team profile path: `TEAM_PROFILE.md`.
- Use rule: read only for experiment design/review, method readiness, claim audit, manuscript outline review, or when the user names the team or `advisor:recovery-evaluator`.
- Applicable stage: high-risk gates and team calibration, not ordinary daily continue.
- Trigger condition: recovery-quality scoring, baseline construction, or advisor background can improve the current decision.
- Failure risk: treating advisor or PI opinion as evidence would overstate `CLM-0001`.
- Custom advisors: `advisor:recovery-evaluator` is advisory only and cannot approve execution, evidence promotion, claim strengthening, or manuscript prose.

## Blocked Moves

- Experiment execution: do not execute `EXP-0002` until readiness passes and the user approves.
- Evidence promotion: do not promote draft briefs, readiness verdicts, or handoffs as evidence.
- Claim strengthening: do not strengthen `CLM-0001` from weak evidence.
- Manuscript prose: do not write publication-ready language from current evidence.
- Experiment synthesis: do not treat `SYN-0001` as evidence or claim support.
- Profile or framework changes: ask before changing project policy or framework version.
- Specialist or multi-agent work: use only for experiment/method/claim gates, not ordinary organization.

## Publish Standards

At least moderate evidence is required before writing a real paper draft. This example may only produce a manuscript outline.

## Profile Update Triggers

Update if recovery metrics become central, synthesis use rules change, or the team profile path, use rule, or advisor boundary changes.

## Persistent Feedback Rules

- Persist feedback that changes claim boundaries, experiment execution permission, or context budget.
- Do not persist one-off response formatting preferences.
- PI feedback should stay direct and action-oriented.
