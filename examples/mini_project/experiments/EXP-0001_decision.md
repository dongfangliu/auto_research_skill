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

## Decision Made

Branch to recovery-quality metric design before another trial.

## Deviations From Brief

No execution deviation was recorded. The limitation is in the brief: it did not include a baseline or metric.

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

## What Remains Unknown

Whether structured research cards improve recovery compared with an unstructured summary.

## Minimum Next Step

Create a branch idea to define recovery-quality metrics before stronger evaluation.

## PI Review

Keep as a weak demonstration. Branch to a metric-focused idea. Do not strengthen `HYP-0001` yet.

## Revision 2026-05-26: PI Verdict

```text
Decision: branch
Plain Reason: The result preserves state in one example, but it cannot answer the comparative hypothesis.
Blocking Issues: No baseline, no recovery metric, and no repeated task type.
Required Changes: Define recovery quality and add a baseline before claiming improvement.
Overclaim Risk: `CLM-0001` must remain outline-only and weak.
Minimum Next Action: Build the next experiment around `IDEA-0002`.
```

## Linked Evidence

- `EVD-0001`
