# Workflow Gates

Gates decide whether research can move forward, should branch, or needs more evidence. Gates are lightweight but mandatory at important transitions.

## Ideation Gate

Before creating a hypothesis, check:

- Is the idea specific enough to test?
- What is the likely contribution?
- What would make the idea uninteresting or false?
- What literature questions must be answered first?

## Literature Gate

Before hypothesis design, check:

- Which prior work is directly relevant?
- Which findings conflict?
- What gap remains after reading?
- Are there known failure modes or baseline methods?

## Hypothesis Gate

Before experiment design, check:

- Is the hypothesis falsifiable?
- What prediction follows if it is true?
- What result would refute or weaken it?
- What minimum experiment can reduce the largest uncertainty?

## Experiment Spine Gate

Before writing a full experiment brief, check:

- `primary_question`: What mainline question is this experiment answering?
- `largest_uncertainty`: What uncertainty does it reduce?
- `decision_enabled`: What decision can be made from the result?
- `minimum_test`: What is the smallest valid test?
- `baseline_or_control`: What comparison or control is required?
- `metric`: What will be measured or judged?
- `will_not_answer`: What will remain outside scope?
- `stop_or_branch_rule`: What result stops, revises, or branches the line?

If the spine does not answer the mainline question, decide `revise` or `block`. Do not approve a vague demonstration as support for a stronger hypothesis.

## Metric/Baseline Readiness Gate

Before writing execution details, running a trial, strengthening a claim, or drafting manuscript text from an experiment, check:

- `mainline_question`: The metric and baseline answer the active research question, not a side demonstration.
- `baseline_or_control`: The comparison or control is named and fits the decision.
- `metric`: The primary metric has a unit, source, or rubric anchor that another reviewer can apply.
- `decision_thresholds`: Success, failure, and ambiguous results lead to different decisions.
- `aggregation_rule`: Repeated samples, rubric items, or qualitative ratings have an interpretation rule.
- `sanity_check`: A negative control, baseline check, or diagnostic can catch obvious measurement failure.
- `claim_boundary`: The result states what claim may be weakened, held, or tentatively strengthened.

Decision values:

- `pass`: Mainline fit, metric anchor, baseline/control, decision thresholds, aggregation or scoring rule, sanity check, ambiguous-result rule, and claim boundary are all sufficient for the minimum test.
- `revise`: The direction is valid, but a missing metric detail, baseline detail, threshold, or ambiguity rule blocks execution.
- `block`: The proposed measurement cannot answer the mainline question.
- `branch`: Readiness review exposes a different question that should become a new idea or hypothesis.

If this gate does not pass, do not execute the experiment, strengthen the claim, or draft publication-ready language. Return the minimum next action needed to make the metric and baseline decision-ready.

## Resume Consistency Gate

Before daily continue, resume, handoff resume, stage transition, experiment execution, evidence promotion, claim strengthening, or manuscript work, check the smallest state/card set needed:

- `STATE.md` names one primary active item and path.
- The primary active card ID, status, and `next_action` do not contradict state.
- Latest decision, evidence promotion, claim boundary, or user correction that changes today's work is reflected in state or the active card.
- Failure or result attribution matches the next action: measurement error leads to metric/procedure review, implementation error leads to implementation fix, hypothesis failure leads to revise/branch/stop, and ambiguous results lead to hold/review.
- Handoff is read only when state names it, the user asks to resume from it, or a direct conflict points to it.
- Blocked moves and do-not-touch files are consistent with the active card and latest correction.
- State-derived context is not treated as directly verified evidence unless the source card was read.

Decision values:

- `pass`: State, primary active card, and required handoff/decision context agree enough to continue.
- `revise`: A small state/card/handoff update is needed before continuing.
- `block`: Continuing would execute the wrong task, strengthen an invalid claim, or use stale evidence.

If this gate does not pass, return a consistency issue and the minimal additive fix. Do not scan the whole repository to compensate for stale state.

## Action Permission / Blocked Moves Gate

Before writing files, opening specialist agents or custom advisors, executing experiments, promoting evidence, strengthening claims, drafting manuscript text, resolving state/handoff conflicts, changing project policy, or upgrading the framework, check:

- Requested action and immediate output.
- Project autonomy level and local profile policy.
- Blocked moves from profile, state, handoff, and latest user correction.
- Required upstream gate: readiness, resume consistency, failure attribution, evidence promotion, claim audit, or manuscript readiness.
- Risk level: low-risk organization, draft-only research work, experiment execution, claim/manuscript change, project-policy change, or framework upgrade.
- Whether the action is allowed now, needs explicit approval, or is blocked.

Decision values:

- `allowed`: May proceed now within the current scope.
- `ask first`: Must ask for approval before taking the action.
- `blocked`: Must not take the action; return the minimum safe next action.

High-risk actions default to `ask first` or `blocked` under `L0` and `L1`: experiment execution, evidence promotion from ambiguous results, claim strengthening, manuscript drafting, framework upgrades, profile policy changes, custom advisor work for high-risk decisions, expensive experiments, and mainline direction changes.

## Experiment Brief Gate

Before execution, check:

- Experiment Spine.
- Metric/Baseline Readiness.
- Research question.
- Background facts.
- Fixed settings.
- New variables.
- Success criteria tied to the metric and decision.
- Failure branches.
- Diagnostics.
- PI Verdict.

## Decision Record Gate

After execution, check:

- Commands, configs, inputs, and outputs are recorded.
- Facts are separated from inferences.
- Failures and regressions are preserved.
- Competing explanations are listed.
- Deviations from the brief are recorded.
- What remains unknown is explicit.
- Minimum next step is explicit.

## Result-to-Evidence Gate

Before a decision record, literature note, artifact, or result is turned into an evidence card or used by a claim, check:

- Verified facts are separated from inferences and impressions.
- Metric, baseline/control, threshold, aggregation, sanity check, and deviation interpretation are carried forward when relevant.
- Ambiguous, partial, failed, or deviated results are not written as positive support.
- Draft briefs, readiness verdicts, handoffs, PI opinions, and unexecuted plans are not treated as evidence.
- Evidence strength is no stronger than the source record permits.
- The evidence states what it supports and what it does not support.
- Claim-use boundary and forbidden wording are explicit.

Decision values:

- `promote`: Create or update an evidence card with the allowed strength and boundaries.
- `hold`: Preserve the result, but do not use it to strengthen a claim.
- `revise`: Fix missing interpretation, limitations, links, or wording before promotion.
- `block`: Do not create positive evidence from this source.
- `branch`: The result changes direction or creates a new question.

Claim strengthening must wait until evidence has passed this gate. A direct jump from experiment brief, readiness verdict, handoff, or unreviewed decision record to claim wording is not allowed.

## Decision Trace / Feedback Gate

After a gate verdict, PI dissent, user correction, claim-boundary change, failed review, or handoff, check:

- The final decision is written in one sentence.
- The plain reason is recoverable without reading the whole conversation.
- Rejected alternatives are named when they are likely to recur.
- User correction or dissent is preserved if it changes future behavior.
- Any changed claim, experiment, autonomy, or context boundary has a durable location.
- The next reviewer knows what to check and what not to repeat.

If the trace is missing for a persistent correction, update the smallest durable artifact: state, profile, affected card, decision record, or handoff packet. Do not persist one-off style preferences unless they affect future work.

## Claim Gate

Before a claim enters manuscript planning, check:

- Supporting evidence is linked.
- Conflicting evidence is linked.
- Evidence strength is assigned.
- Required metric and baseline/control are satisfied for any comparative wording.
- Allowed and forbidden wording are written.
- The claim does not exceed the evidence.

## Manuscript Gate

Before drafting, check:

- Each section maps to claim cards.
- Weak claims are marked as tentative or omitted.
- Limitations are explicit.
- Missing experiments are listed.

## Framework Upgrade Gate

When a consumer project updates the submodule, check:

- Old and new framework commits are recorded.
- Template or gate changes are summarized.
- Existing research cards are not overwritten.
- Any migration is additive.
