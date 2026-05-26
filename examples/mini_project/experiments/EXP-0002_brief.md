# EXP-0002 Brief: Recovery Quality Readiness Trial

```yaml
id: EXP-0002
type: experiment_brief
status: draft
created_at: 2026-05-26
updated_at: 2026-05-26
parent: HYP-0002
branch_from: EXP-0001-DECISION
linked_items:
  - IDEA-0002
  - HYP-0002
  - EXP-0001-DECISION
owner_agent: student-executor
evidence_level: none
confidence:
next_action: Resolve the readiness verdict before execution.
```

## Research Question

Can a recovery-quality metric and unstructured-note baseline make the next resumption trial interpretable?

## Experiment Spine

```yaml
primary_question: Does the next experiment have enough metric and baseline structure to test recovery quality?
largest_uncertainty: Whether recovery quality can be judged against a comparable unstructured-note baseline.
decision_enabled: Decide whether to execute a paired mock continuation or revise the metric/baseline first.
minimum_test: One paired mock continuation from the same source scenario.
baseline_or_control: Unstructured one-page note created from the same source scenario.
metric: Recovery Quality Score across active item, next action, evidence boundary, and branch provenance.
will_not_answer: Whether structured cards improve real researcher productivity or generalize across domains.
stop_or_branch_rule: If the metric or baseline is ambiguous, revise the rubric; if the structured condition does not beat baseline, keep claims weak.
```

## Metric/Baseline Readiness

```text
Readiness Verdict
Decision: revise
Mainline Fit: The metric and baseline target the current mainline question about recovery quality.
Metric: Recovery Quality Score with four rubric items: active item recovered, next action recovered, evidence boundary preserved, branch provenance preserved.
Baseline Or Control: An unstructured one-page note from the same scenario.
Decision Thresholds: Structured condition must score higher than baseline to support only a weak comparative claim.
Aggregation Rule: Sum four binary rubric items; ties are not positive evidence.
Sanity Check: A reviewer should be able to score both outputs without opening unrelated project files.
Ambiguous Result Rule: If the outputs tie, the rubric is unclear, or scoring requires extra context, revise the metric before another trial.
Claim Boundary: At most weak support for `CLM-0001`; no productivity or publication-ready claim.
Minimum Next Action: Ask method-specialist to review the rubric anchors and baseline generation rule.
```

## Background Facts

`EXP-0001` showed that a structured trail can support one mock continuation, but it lacked a baseline and explicit recovery metric.

## Core Hypothesis

`HYP-0002`: A recovery-quality rubric plus an unstructured-note baseline can make the next resumption trial interpretable.

## Fixed Settings

- Same source scenario for both conditions.
- Same continuation prompt style.
- Same four rubric items for both outputs.
- No manuscript or claim strengthening during this trial.

## New Variables

- Condition A: structured research cards.
- Condition B: unstructured one-page note.
- Recovery Quality Score.

## Success Criteria

The structured-card condition scores higher than the unstructured-note baseline on the Recovery Quality Score without scoring ambiguity.

## Failure Branches

- If the baseline note is not comparable, revise baseline generation.
- If the rubric cannot be applied consistently, revise `HYP-0002`.
- If both conditions tie, keep `CLM-0001` weak and review whether the schema adds value.

## Diagnostics Plan

Check scorer independence, rubric ambiguity, missing provenance, and any unsupported claim introduced by the continuation output.

## Commands Or Procedure

Manual paired mock continuation after the readiness verdict passes. Do not execute while this brief remains in `revise`.

## Expected Outputs

- Updated readiness verdict.
- `EXP-0002_decision.md` only after execution is approved.
- Evidence card only if a paired trial is actually run.

## PI Review

```text
Decision: revise
Plain Reason: The brief now names a metric and baseline, but the rubric anchors and baseline generation rule need method review before execution.
Blocking Issues: Independent scoring rule is underspecified. Baseline note generation could leak structured-card advantages.
Required Changes: Method-specialist must review rubric anchors, baseline construction, and ambiguous-result handling.
Overclaim Risk: Do not use this draft to strengthen `CLM-0001`.
Minimum Next Action: Review Metric/Baseline Readiness, then either revise the brief or approve execution.
```

## Advisor Review Example

This is a project-team advisory report, not evidence and not approval to execute.

```text
Role
advisor:recovery-evaluator

Scope
Review whether the Recovery Quality Score and unstructured-note baseline are likely to produce an interpretable readiness decision.

Facts
- `EXP-0002` remains a draft with Readiness Verdict: revise.
- The current metric has four binary rubric items.
- The baseline is an unstructured one-page note from the same scenario.

Inferences
- The rubric may still be too coarse if outputs preserve different kinds of partial provenance.
- Baseline generation could leak structured-card information unless the note creation rule is fixed before execution.

Risks
- A tie or scorer disagreement could be misread as support for `CLM-0001`.

Dissent Or Blocking Concern
Do not execute until baseline generation and scorer independence are specified.

Open Questions
- Who creates the unstructured baseline note?
- Can a reviewer score both conditions without opening unrelated files?

Recommended Next Action
Method-specialist should review rubric anchors and baseline construction before PI approval.

Files / Commands / Outputs
- Read: `TEAM_PROFILE.md`, `experiments/EXP-0002_brief.md`
- Commands: none
- Outputs: advisory review only
```
