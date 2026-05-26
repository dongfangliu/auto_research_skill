# Experiment Work

Use this reference only for experiment design, execution, failure review, and PI review. Keep ordinary `continue` and claim work on `workflows.md`.

## Experiment Spine First

Before writing an experiment brief, lock the spine:

```text
primary_question
largest_uncertainty
decision_enabled
minimum_test
baseline_or_control
metric
will_not_answer
stop_or_branch_rule
```

If the spine cannot show how the result answers the main question, return `revise` or `block`. Do not approve a vague demo as an experiment that supports the hypothesis.

## Experiment Control Loop

Use this sequence for design, execution, and review:

1. Frame the mainline question and current decision from profile, state, and the active card.
2. Draft the smallest experiment spine that can change that decision.
3. Run Metric/Baseline Readiness before procedure details when measurement, comparison, scoring, sampling, or claim impact matters.
4. Check action permission before execution, long-running commands, file writes, specialist roles, evidence promotion, claim changes, or manuscript language.
5. Execute only the approved minimum test. Record exact commands, inputs, fixed settings, environment details that affect interpretation, outputs, and deviations.
6. Stop on broken preconditions, missing artifacts, failed sanity checks, non-comparable baselines, or unexpected scope expansion. Preserve the failure instead of repairing the question after the run.
7. Convert results to a decision record before evidence. Use an Evidence Promotion Verdict before any claim impact.

Keep the loop token-light: report only the fields that affect the next decision, reproducibility, evidence boundary, or user approval.

## Metric/Baseline Readiness Before Details

After the spine and before execution details, issue a compact readiness verdict when the task involves metric choice, baseline/control choice, comparative claims, statistics, controls, numerical stability, or measurement quality:

```text
Readiness Verdict
Decision: pass | revise | block | branch
Mainline Fit
Metric
Baseline Or Control
Decision Thresholds
Aggregation Rule
Sanity Check
Ambiguous Result Rule
Claim Boundary
Minimum Next Action
```

The verdict cannot be `pass` if any of these are missing:

- metric or qualitative rubric anchor
- baseline or control needed for the stated comparison
- success, failure, and ambiguous-result interpretation
- aggregation or scoring rule when multiple items, samples, or raters are involved
- link from the metric result to `decision_enabled`
- claim boundary for what the experiment may and may not support

If readiness is `revise`, `block`, or `branch`, stop before detailed procedure unless the procedure is needed to explain the missing piece. Do not approve claim strengthening or manuscript drafting from a non-ready experiment.

## Role Sequence

For experiment work, use this order:

1. `orchestrator`: frame the mainline question and active item from profile, `STATE.md`, and active cards.
2. `student-executor`: draft the spine and readiness block before detailed procedure when measurement or comparison affects the decision.
3. `method-specialist`: review readiness before execution when metrics, baselines, statistics, controls, numerical stability, sampling, or scoring matter.
4. `pi-reviewer`: critique independently with a direct PI Verdict.
5. `orchestrator`: resolve conflicts and decide whether to write, revise, branch, execute, or stop.

When subagents are available and allowed, use separate agents for `student-executor` and `pi-reviewer`, and add `method-specialist` before PI when readiness validity depends on measurement or controls. If not, write separate role blocks in the same response and do not let the PI block merely confirm the student plan.

Add `method-specialist` before execution when validity depends on metrics, baselines, statistics, controls, numerical stability, or sampling.

## Brief Requirements

An experiment brief must include:

- Experiment Spine.
- Metric/Baseline Readiness verdict when measurement or comparison affects the decision.
- Execution preflight: required files, commands, permissions, runtime cost, and stop conditions.
- Background facts needed to interpret the result.
- Fixed settings that affect interpretation.
- New variables.
- Success criteria tied to the metric and decision.
- Failure branches.
- Diagnostics.
- Commands or procedure.
- Expected outputs.
- PI Verdict.

Omit details that do not affect interpretation, reproducibility, or the decision enabled by the result.

If the readiness verdict is not `pass`, the PI Verdict should usually be `revise`, `block`, or `branch`. The minimum next action should name the missing metric, baseline, threshold, aggregation rule, or ambiguity rule.

## Execution Record

After execution, write or update a decision record with:

- execution permission or approval source
- decision made
- verified facts
- exact commands, configs, inputs, outputs, artifacts, and runtime-relevant environment notes
- deviations from brief
- inferences
- limitations
- failures or regressions
- competing explanations
- what remains unknown
- minimum next action
- linked evidence
- PI Verdict

Facts are direct observations, commands, configs, inputs, outputs, and artifacts. Inferences must stay weaker than the facts.

## Result-to-Evidence Review

Before creating or updating an evidence card from an execution result, issue an Evidence Promotion Verdict:

- verified facts that can be carried forward
- inferences that must stay weaker than facts
- metric, threshold, baseline/control, sanity check, and deviation interpretation
- ambiguity or failure status
- allowed evidence level
- claim impact and forbidden wording
- minimum next action

If the verdict is `hold`, `revise`, `block`, or `branch`, do not strengthen a claim from that result. A readiness verdict, handoff, draft brief, or PI opinion can explain a plan or boundary, but it is not evidence.

## PI Verdict

Use direct language:

```text
Decision: approve | revise | block | branch
Plain Reason
Blocking Issues
Required Changes
Overclaim Risk
Minimum Next Action
```

Start with the decision. Avoid vague advice such as "more research is needed" unless it is attached to a concrete next action.

## Failure Review

When an experiment fails, preserve the failure. Decide whether it implies:

- implementation error
- measurement error
- weak metric
- missing control or baseline
- hypothesis revision
- new branch idea
- stop condition

Do not silently convert a failed experiment into a success by changing the question after the fact.
