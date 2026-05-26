# Research State: Mini Project

```yaml
project_id: mini_project
framework_commit: mvp-0.13-example
updated_at: 2026-05-26
active_stage: experiment_design
active_items:
  - IDEA-0002
  - HYP-0002
  - EXP-0002
primary_active_item: EXP-0002
primary_active_path: experiments/EXP-0002_brief.md
mainline_question: Can the next recovery-quality experiment pass metric/baseline readiness before execution?
primary_decision: Decide whether EXP-0002 is ready to execute or must revise its rubric and baseline.
current_risk: A paired trial or claim could proceed before the readiness verdict passes.
next_recommended_action: Review EXP-0002 Metric/Baseline Readiness with method-specialist and PI.
parking_lot:
  - Manuscript wording.
  - Stronger productivity claims.
  - Any new trial before metric, baseline, thresholds, and ambiguity rule pass readiness.
blocked_moves_today:
  - Execute EXP-0002.
  - Strengthen CLM-0001.
  - Expand OUTLINE-0001 into manuscript prose.
  - Treat EXP-0002 draft readiness as evidence.
last_user_correction: Do not execute EXP-0002; only review metric/baseline readiness and keep manuscript/claim work parked.
last_decision_source: experiments/EXP-0002_brief.md
handoff_to_read_if_resuming: handoffs/HANDOFF-0001.md
known_stale_links: []
state_consistency: pass
last_mainline_check: 2026-05-26
```

## Snapshot

The project started with an idea that structured research cards may help agents resume interrupted work. A first mock experiment partially supported the workflow but exposed an unmeasured failure mode: recovery quality needs an explicit metric. This generated `IDEA-0002`, `HYP-0002`, and a draft `EXP-0002` readiness review.

## Mainline

- Mainline question: Can the next recovery-quality experiment pass metric/baseline readiness before execution?
- Primary active item: `EXP-0002`
- Primary active path: `experiments/EXP-0002_brief.md`
- Primary decision needed: Whether `EXP-0002` is ready to execute or must revise its rubric and baseline.
- Current risk: Running a paired trial or strengthening `CLM-0001` before the readiness verdict passes.
- Minimum next action: Review the `EXP-0002` readiness verdict with method-specialist and PI.
- Parking lot: Manuscript wording, stronger productivity claims, and any new trial before metric/baseline readiness passes.
- Blocked moves today: execute `EXP-0002`, strengthen `CLM-0001`, expand `OUTLINE-0001` into prose, or treat `EXP-0002` as evidence.
- Last user correction: Do not execute `EXP-0002`; only review metric/baseline readiness and keep manuscript/claim work parked.
- Last decision source: `experiments/EXP-0002_brief.md`
- Handoff to read if resuming: `handoffs/HANDOFF-0001.md`
- Known stale links: none.
- State consistency: pass for `EXP-0002` readiness review; handoff is needed only for explicit handoff resume.
- Last mainline check: 2026-05-26, mvp-0.9 action permission example.

## Daily Continue Expected Output

```text
Daily Brief
Mainline: Can the next recovery-quality experiment pass metric/baseline readiness before execution?
Today's Active Item: EXP-0002
Read Now: PROJECT_PROFILE.md, STATE.md, experiments/EXP-0002_brief.md
State-Derived Context: EXP-0001 is a weak demonstration; IDEA-0002 and HYP-0002 define the recovery-quality branch; CLM-0001 must stay weak and outline-only.
Current Risk: A trial or claim could proceed before metric/baseline readiness passes.
Today's Decision: Decide whether EXP-0002 readiness is pass, revise, block, or branch.
Recommended Next Action: Review the Readiness Verdict and resolve rubric anchors, baseline construction, and ambiguity handling.
Do Not Do Today: Do not expand OUTLINE-0001, strengthen CLM-0001, or execute EXP-0002.
May Change After Approval: STATE.md, hypotheses/HYP-0002.md, or experiments/EXP-0002_brief.md
Do Not Touch Today: manuscripts/OUTLINE-0001.md, claims/CLM-0001.md, existing EXP-0001 records
```

## Feedback Trace

The persistent correction is intentionally short in state: review `EXP-0002` readiness only. Read `HANDOFF-0001` only when resuming from handoff or auditing the correction, not for every daily continue.

## Resume Consistency Example

```text
Resume Consistency Verdict
Decision: pass
Checked: STATE.md, experiments/EXP-0002_brief.md
Conflict: none for daily continue; HANDOFF-0001 is required only for explicit handoff resume.
Authoritative Source: STATE.md for today's active item; EXP-0002_brief.md for readiness status; EVD-0001 for claim boundary.
Minimal Fix: none.
Today Do Not Do: Do not execute EXP-0002, strengthen CLM-0001, or edit OUTLINE-0001.
Next Action: Method-specialist review of EXP-0002 readiness.
```

## Action Permission Example

```text
Action Permission Verdict
Decision: ask first
Requested Action: Execute EXP-0002.
Autonomy Level: L1 guided
Risk Level: experiment execution
Blocked Move Check: Blocked today because readiness is still revise.
Required Gate: Metric/Baseline Readiness and explicit user approval.
May Do Now: Review readiness fields and propose required changes.
Must Ask Before: Running the paired mock continuation or writing EXP-0002_decision.md.
Do Not Do: Execute EXP-0002, strengthen CLM-0001, or draft manuscript prose.
Minimum Next Action: Method-specialist review of rubric anchors and baseline construction.
```

## Active Items

| ID | Type | Status | Current Question | Next Action |
| --- | --- | --- | --- | --- |
| IDEA-0002 | idea | active | Should recovery quality become a first-class metric? | Linked to `HYP-0002` and `EXP-0002`; keep as branch origin. |
| HYP-0002 | hypothesis | draft | Can a rubric and baseline make recovery trials interpretable? | Review through `EXP-0002`. |
| EXP-0002 | experiment_brief | draft | Is metric/baseline readiness sufficient for execution? | Resolve readiness verdict before execution. |

## Paused Or Blocked Items

| ID | Type | Status | Blocker | Resume Condition |
| --- | --- | --- | --- | --- |
| HYP-0001 | hypothesis | paused | Only one simulated trial exists. | Resume after at least one additional task type is tested. |
| CLM-0001 | claim | draft | Evidence is weak and no ready metric/baseline trial has run. | Resume after recovery quality is operationalized and another paired trial is recorded. |

## Branch Relationships

| Child | Branch From | Reason |
| --- | --- | --- |
| IDEA-0002 | EXP-0001-DECISION | Experiment exposed an unmeasured recovery-quality variable. |
| HYP-0002 | IDEA-0002 | Metric idea needed a falsifiable readiness hypothesis. |
| EXP-0002 | HYP-0002 | Hypothesis needs metric/baseline readiness review before execution. |
| HANDOFF-0001 | EXP-0002 | User correction must persist into the next readiness-review session. |

## Evidence And Claim Readiness

| Claim | Evidence Level | Readiness | Risk |
| --- | --- | --- | --- |
| CLM-0001 | weak | Outline-only | Based on one mock example. |

## Manuscript Readiness

Ready only for a demonstration outline, not a publication draft.

## Open Risks

- Recovery quality is not yet measured quantitatively.
- The current example may overfit to agent-readable Markdown workflows.

## Latest Decisions

- Preserve `HYP-0001` as paused.
- Create `IDEA-0002` to make recovery quality a first-class object.
- Keep `CLM-0001` weak.
- 2026-05-26 spine review: `EXP-0001` remains a weak demonstration, not a valid test of the comparison in `HYP-0001`, because it lacks a baseline and recovery-quality metric.
- 2026-05-26 readiness review: `EXP-0002` is the active draft. It names a metric and baseline, but remains `revise` until rubric anchors and baseline generation pass method review.
- 2026-05-26 feedback trace: user correction narrows the next session to readiness review only; do not execute `EXP-0002` or strengthen `CLM-0001`.
- 2026-05-26 evidence promotion review: `EVD-0001` promotes only weak audit-path evidence from `EXP-0001-DECISION`; it does not support comparative recovery improvement.
- 2026-05-26 resume consistency review: state and `EXP-0002` agree that the next action is readiness review, not execution.
- 2026-05-26 action permission review: under L1 guided, `EXP-0002` execution, claim strengthening, and manuscript prose require approval and are blocked today by readiness state.
- 2026-05-26 team profile example: `TEAM_PROFILE.md` adds `advisor:recovery-evaluator` for readiness review only; ordinary daily continue should not read it by default.
