# EXP-0001 Decision: Mock Recovery Trial

```yaml
id: EXP-0001-DECISION
type: decision_record
status: accepted
created_at: 2026-05-18
updated_at: 2026-05-18
parent: EXP-0001
branch_from:
linked_items:
  - EVD-0001
  - IDEA-0002
  - CLM-0001
owner_agent: student-executor
evidence_level: weak
confidence: low
next_action: Branch to recovery-quality metric design.
```

## Verified Facts

The mock continuation preserved the project state in this example trail: active hypothesis, weak evidence, and next action were recoverable from the files.

## Inferences

Structured cards may help agents resume, but the current example only demonstrates a plausible workflow, not a validated improvement.

## Limitations

- Single simulated trial.
- No comparison against unstructured notes.
- No quantitative recovery metric.
- Placeholder literature review only.

## Failures Or Regressions

The experiment exposed that "resume quality" was not operationalized. Without a metric, future agents could disagree about whether recovery succeeded.

## Competing Explanations

- The files are useful because they are short, not because the schema is correct.
- A plain summary might be enough.
- The task is too simple to test real research continuity.

## Minimum Next Step

Create a branch idea to define recovery-quality metrics before stronger evaluation.

## PI Review

Keep as a weak demonstration. Branch to a metric-focused idea. Do not strengthen `HYP-0001` yet.

## Linked Evidence

- `EVD-0001`

