# Team Profile: Research Continuity Mini Project

```yaml
project_id: mini_project
team_profile_id: team-0001
status: active
created_at: 2026-05-26
updated_at: 2026-05-26
source_project_profile: PROJECT_PROFILE.md
team_profile_use: needed_only
calibration_status: example
review_owner: orchestrator
```

## Purpose

This example team profile adapts Auto Research roles to a small fictional project about research-agent continuity. It focuses reviewers on recovery quality, baseline comparability, and claim boundaries.

This file is not evidence and not a runtime agent registry.

## Use Rule

- Applicable stage: experiment design/review, method readiness, claim audit, manuscript outline review, or explicit team/advisor requests.
- Trigger condition: a decision depends on recovery-quality metrics, baseline construction, or whether a weak demonstration can support a claim.
- Failure risk: reading this file for ordinary daily continue wastes context; treating role opinions as evidence would overstate `CLM-0001`.

## Source Context Used

- `PROJECT_PROFILE.md`
- `STATE.md`
- `experiments/EXP-0002_brief.md`
- `claims/CLM-0001.md`
- `evidence/EVD-0001.md`

## Core Role Adaptations

| Framework Role | Project Background | Review Focus | Blind Spots To Counter | Output Constraints |
| --- | --- | --- | --- | --- |
| orchestrator | Research workflow and provenance discipline. | Keep the active decision on `EXP-0002` readiness. | Letting manuscript or claim work interrupt metric review. | Must keep daily continue token-light and avoid reading this file unless needed. |
| student-executor | Mock continuation protocol designer. | Smallest paired trial that can compare structured cards with an unstructured baseline. | Designing a pleasant demo instead of an interpretable comparison. | Must record commands or manual procedure, fixed settings, outputs, and deviations. |
| pi-reviewer | Skeptical research-direction reviewer. | Whether the experiment can change the claim boundary. | Approving a demo that cannot test recovery quality. | Must give a direct verdict and minimum next action. |
| method-specialist | Evaluation and rubric reviewer. | Rubric anchors, baseline generation, ambiguity handling, and scorer independence. | Accepting a qualitative score that another reviewer cannot reproduce. | Must block execution while readiness is `revise`. |
| claim-auditor | Evidence-to-wording reviewer. | Keep `CLM-0001` weak and outline-only until a ready paired trial is executed. | Treating `EXP-0002` draft readiness as evidence. | Must forbid productivity or general recovery-improvement wording. |
| writing-agent | Demonstration outline organizer. | Use only approved claim cards and limitations. | Turning a framework demo into publication-ready prose. | Must not draft polished manuscript claims from current evidence. |

## Custom Advisory Roles

| Advisor ID | When To Consult | Background | Can Advise On | Must Not Decide | Required Output |
| --- | --- | --- | --- | --- | --- |
| advisor:recovery-evaluator | When recovery-quality scoring or baseline comparability is under review. | Rubric design for task-resumption quality. | Rubric anchors, baseline leakage, ambiguity handling, scorer independence. | Experiment approval, evidence promotion, claim strength, manuscript readiness. | Role Report |

## Collaboration Rules

- `advisor:recovery-evaluator` may report risks or dissent, but cannot approve `EXP-0002`.
- `method-specialist` still decides whether readiness can pass.
- `pi-reviewer` still gives the direction verdict.
- Advisor reports, PI opinions, and readiness verdicts are not evidence.
- `orchestrator` resolves advisor input against `PROJECT_PROFILE.md`, `STATE.md`, and active cards.

## Revision Notes

- 2026-05-26: Added an example advisor for recovery-quality scoring. This does not change the blocked move against executing `EXP-0002` while readiness remains `revise`.
