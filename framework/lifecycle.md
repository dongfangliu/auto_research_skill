# Research Lifecycle

Auto Research treats research as a recoverable, branching state machine rather than a linear pipeline.

## Stages

1. `ideation`: create, merge, reject, and rank research ideas.
2. `literature_review`: map existing work, conflicts, gaps, and evidence quality.
3. `hypothesis_design`: turn an idea into falsifiable hypotheses and predictions.
4. `experiment_design`: define minimum experiments, controls, variables, success criteria, and failure branches.
5. `experiment_execution`: run experiments and preserve commands, configs, outputs, and deviations.
6. `result_analysis`: separate facts, inferences, limits, failures, and next steps.
7. `claim_building`: bind candidate claims to evidence and allowed wording.
8. `manuscript_drafting`: assemble outline or draft from claim ledger only.

## Experiment Branch Synthesis

Experiment branch synthesis is a user-triggered post-experiment action, not a new lifecycle stage. Use it after `result_analysis` and before claim strengthening when a bounded experiment thread needs to be digested like a PR or merge summary.

- Applicable stage: experiment-related `result_analysis`, before evidence candidates are promoted or claims are strengthened.
- Trigger condition: the user asks to digest, synthesize, consolidate, or summarize a recent experiment branch; or the agent reaches a low-frequency reminder point such as a long experiment thread, conflicting results, unclear mainline impact, or pre-claim/manuscript work.
- Failure risk: treating synthesis as evidence, using it to strengthen claims directly, or making it a generic project summary detached from experiment records.

An experiment synthesis must bind to at least one experiment decision record or experiment-derived evidence card. It may recommend evidence promotion, claim audit, another experiment branch, parking a branch, or stopping a line, but it cannot replace the gates for those actions.

## Stage Actions

Every stage supports five actions:

- `continue`: continue active work without changing the branch.
- `review`: inspect previous cards, decisions, and evidence.
- `branch`: create a new card from current findings while preserving the source record.
- `revise`: append a revision section without overwriting old content.
- `gate`: request PI, auditor, or specialist review before moving forward.

## Nonlinear Research Rules

- An experiment can remain active while a new idea or literature branch is created.
- A failed experiment can produce a new idea, hypothesis, method concern, or literature question.
- Revised hypotheses must preserve old versions and explain why the revision exists.
- Manuscripts must not invent claims outside the claim ledger.
- A branch is not a failure. It is a first-class research object with provenance.

## Minimum Progression Gate

Before moving to the next stage, record:

- Current item ID.
- Evidence level.
- Main risk or uncertainty.
- Recommended next action.
- Whether PI/auditor/specialist review is required.
