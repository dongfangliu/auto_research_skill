# EXP-0001 Brief: Mock Recovery Trial

```yaml
id: EXP-0001
type: experiment_brief
status: accepted
created_at: 2026-05-18
updated_at: 2026-05-18
parent: HYP-0001
branch_from:
linked_items:
  - IDEA-0001
  - HYP-0001
owner_agent: student-executor
evidence_level: none
confidence:
next_action: Run a mock continuation and record whether the agent preserves provenance.
```

## Research Question

Can an agent resume the mini project from structured files without losing active state or overclaiming?

## Experiment Spine

```yaml
primary_question: Can structured files improve resumption compared with an unstructured note?
largest_uncertainty: Recovery quality is not operationalized.
decision_enabled: Only whether this example can remain a weak demonstration.
minimum_test: One mock continuation from the existing mini project.
baseline_or_control: Missing; no unstructured-note comparison is included.
metric: Missing; recovery quality is judged qualitatively.
will_not_answer: Whether structured cards outperform summaries or improve real productivity.
stop_or_branch_rule: If recovery quality is ambiguous, branch to metric design before another trial.
```

## Background Facts

The mini project contains one idea, one literature question, one placeholder literature note, and one hypothesis.

## Core Hypothesis

`HYP-0001`: state plus linked cards improve agent resumption.

## Fixed Settings

- Use Markdown files only.
- Use one active hypothesis.
- Keep evidence weak.

## New Variables

The continuation prompt asks the agent to decide what can be claimed and what should happen next.

## Success Criteria

- The agent identifies the active hypothesis and weak evidence.
- The agent does not create a strong claim.
- The agent suggests a next experiment or branch.

## Failure Branches

- If claim wording is too strong, create a claim-audit issue.
- If the agent cannot resume, revise `STATE.md`.
- If recovery quality is ambiguous, create a new idea for recovery metrics.

## Diagnostics Plan

Check whether the output preserves branch provenance, evidence level, and next action.

## Commands Or Procedure

Manual mock continuation using the files in this example.

## Expected Outputs

- `EXP-0001_decision.md`
- `EVD-0001.md`
- Possible branch idea

## PI Review

Approved as a demonstration only. It cannot support a real empirical claim.

## Revision 2026-05-26: PI Verdict

```text
Decision: branch
Plain Reason: This brief is acceptable only as a demo. It does not test the comparison in `HYP-0001`.
Blocking Issues: No baseline against unstructured notes. No recovery-quality metric.
Required Changes: Define the metric and baseline before running a second trial.
Overclaim Risk: Do not say structured cards improve resumption from this experiment.
Minimum Next Action: Turn `IDEA-0002` into a metric-focused hypothesis or revised experiment brief.
```
