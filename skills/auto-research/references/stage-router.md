# Stage Router

Use this reference after `context-router.md` when a user names a lifecycle stage, asks to navigate stages, or gives an ambiguous Auto Research request that needs routing before deeper context loading.

This file routes work. It does not replace `framework/lifecycle.md`, `framework/workflow_gates.md`, or the task-specific skill references.

## Stage Routes

| Stage | Primary child skill | Minimum files | Gate or stop condition | Output contract | Failure risk |
| --- | --- | --- | --- | --- | --- |
| `ideation` | `$auto-research-continue` | profile, `STATE.md`, active idea card | Ideation Gate before hypothesis creation | Stage Brief or Gate Review | Treating a raw idea as a hypothesis without contribution, counterargument, or literature questions. |
| `literature_review` | `$auto-research-continue` | profile, `STATE.md`, active literature question or note | Literature Gate before hypothesis design | Stage Brief or Gate Review | Treating paper claims as verified project facts or skipping conflicting findings. |
| `hypothesis_design` | `$auto-research-continue` | profile, `STATE.md`, active idea or hypothesis card | Hypothesis Gate before experiment design | Stage Brief or Gate Review | Creating an experiment from an unfalsifiable or weakly scoped hypothesis. |
| `experiment_design` | `$auto-research-experiment` | profile, `STATE.md`, active hypothesis or experiment brief | Experiment Spine and Metric/Baseline Readiness | Readiness Verdict or PI Verdict | Writing procedure details before the mainline question, metric, baseline, and stop rule are ready. |
| `experiment_execution` | `$auto-research-experiment` | approved brief, `STATE.md`, required procedure files | Resume Consistency, readiness pass, and Action Permission | Action Permission Verdict or Execution Report | Treating a recommended next action as execution approval or crossing into evidence/claim work. |
| `result_analysis` | `$auto-research-evidence-claims` | source decision/result, `STATE.md`, linked evidence only when needed | Decision Record Gate and Result-to-Evidence Gate | Evidence Promotion Verdict or Gate Review | Turning ambiguous, failed, or deviated results into positive evidence. |
| `claim_building` | `$auto-research-evidence-claims` | claim card, linked evidence, conflicting evidence | Claim Gate and Action Permission before strengthening | Claim Audit | Strengthening wording beyond linked evidence or ignoring forbidden wording. |
| `manuscript_drafting` | `$auto-research-evidence-claims` | claim ledger, manuscript outline, linked evidence summaries | Manuscript Gate and Action Permission before prose | Claim Audit or Gate Review | Drafting publication-style prose from weak, speculative, or missing claims. |

## Action Routes

| Stage action | Primary child skill | Minimum rule | Stop condition | Failure risk |
| --- | --- | --- | --- | --- |
| `continue` | `$auto-research-continue` | Read profile, `STATE.md`, and the primary active card only. | State/card conflict or high-risk next action. | Full-repo scans and side-branch drift. |
| `review` | `$auto-research-continue` | Review the primary active item and directly linked files first. | Missing evidence, stale next action, or overclaim risk. | Reviewing everything instead of the decision at hand. |
| `branch` | `$auto-research-continue` | Preserve `parent` or `branch_from` and state the branch reason. | Missing provenance or unclear branch decision. | Losing source context or rewriting history. |
| `revise` | `$auto-research-continue` | Append a dated revision or migration note. | Request would erase previous wording. | Overwriting historical cards. |
| `gate` | Child skill for the current stage | Use the specific gate from `framework/workflow_gates.md`. | Decision is `revise`, `block`, or `branch`. | Treating a gate as vague advice instead of a decision. |

## Maintenance Route

Use `$auto-research-maintainer` when the current repository is the framework source repo and the user asks to change framework files, templates, examples, skill routing, forward tests, adoption guidance, or upgrade rules.

- Applicable stage: framework maintenance or consumer framework upgrade.
- Trigger condition: a reusable framework, template, example, prompt, or skill change is requested.
- Failure risk: storing real project state in this repo, introducing runtime features during MVP, or breaking consumer-state compatibility.

## Routing Rules

1. Classify the repository before loading stage details.
2. Prefer profile and state over generic framework assumptions in consumer repos.
3. If stage and action point to different child skills, choose the child skill for the higher-risk action class: execution, evidence promotion, claim strengthening, manuscript prose, framework upgrade.
4. If the route is unclear after reading state and the active card, return a Stage Brief or Resume Consistency Verdict instead of scanning the whole repository.
5. Do not use this file to approve execution, evidence promotion, claim strengthening, manuscript prose, or framework upgrades. It only chooses the next reference and output shape.
