# Failure Modes

Use this reference when behavior feels ambiguous or risky.

## Real Project State In Framework Repo

Risk: writing actual research progress into the framework source repository.

Guardrail: in `framework_repo`, edit only generic framework files, templates, examples, prompts, or skill files. Real research state belongs in consumer repo `research/`.

## Loading Too Much Context

Risk: reading the full framework and all cards for a small task.

Guardrail: read `context-router.md`, then only the task-specific reference and active files from `STATE.md`.

## Relying On Chat Memory

Risk: after a long conversation or context compaction, the agent continues from remembered chat details that were never written to project files.

Guardrail: use Long Context Recovery. Re-read profile, `STATE.md`, and the primary active card before high-risk actions. If a user correction must persist, write or propose the smallest update to existing state, card, decision record, or handoff.

## Card Filling Without Decision

Risk: filling every template section while losing the decision the card should support.

Guardrail: identify the mainline question, decision needed, and minimum next action before adding details. Put non-decisive details in a parking lot.

## Mainline Drift

Risk: moving between claim, metric, experiment, and manuscript work without choosing the active decision.

Guardrail: use `control-loop.md` when active items compete. Pick the item that reduces the largest current risk and state the assumption.

## Daily Drift

Risk: a daily `continue` session expands into new branches, manuscript wording, claim strengthening, or method details without advancing the primary decision.

Guardrail: produce a Daily Brief first. Work on one primary active item. Put side issues in parking lot unless a branch gate is explicitly requested.

## Leaking Framework Internals

Risk: the user asks a normal research question and receives framework terms such as gate, evidence promotion, claim audit, role sequence, or state machine jargon.

Guardrail: use Plain Research Reply. Explain the research action in ordinary language first. Reveal framework terms only when the user asks how the system works or when an exact durable record needs the term.

## Mixed Visible Language

Risk: the reply mixes languages in ordinary prose and feels inconsistent or hard to read.

Guardrail: match the user's conversation language for visible prose. Keep file names, IDs, commands, schema fields, and quoted source text in their original form. Framework-source files and templates default to English.

## Open-Ended User Choice

Risk: the agent asks a vague question such as "What do you want to do?" and makes the user design the next step from scratch.

Guardrail: ask one concrete question with 2-3 options, mark one as `[Recommended]`, and say the user can reply with a custom instruction.

## Multi-Step Action Drift

Risk: a focused request turns into a chain of experiment execution, evidence promotion, claim strengthening, and manuscript drafting in one response.

Guardrail: use the one-decision rule. Finish or block the current decision first, then name the next gated decision. Do not cross into the next action class without permission and the required gate.

## Feedback Not Captured

Risk: the user corrects direction, PI style, claim wording, context budget, or experiment interpretation, but the next session repeats the same mistake.

Guardrail: use Feedback Intake. Decide whether the correction is current-response only or belongs in profile, state, a card revision, a decision record, or a handoff packet.

## Over-Persisting Feedback

Risk: a one-off wording or formatting preference is written into persistent project policy and pollutes future research behavior.

Guardrail: persist only feedback that changes future decisions, claim boundaries, experiment interpretation, blocked moves, context budget, or default review style.

## Asking Discoverable Questions

Risk: asking where the profile, state, templates, or active item are before searching.

Guardrail: inspect the repository first. Ask only preference, policy, or direction questions after discovery.

## Overwriting History

Risk: replacing old cards, decisions, experiment records, or manuscript notes.

Guardrail: append a revision, branch, or migration note. Preserve old wording unless the user explicitly asks for a destructive cleanup.

## Overclaiming

Risk: turning weak evidence into strong claims or manuscript-ready language.

Guardrail: keep facts, inferences, limitations, and competing explanations separate. Mark unsupported claims as `speculative`; bind every claim to evidence before manuscript use.

## Raw Result As Evidence

Risk: treating an experiment brief, readiness verdict, handoff, PI opinion, or unreviewed decision record as evidence that can strengthen a claim.

Guardrail: use the Result-to-Evidence Gate. Promote only verified facts with limitations and claim-use boundaries. Ambiguous, failed, draft, or readiness-only records cannot become positive evidence.

## Metric/Baseline Readiness Gap

Risk: running an experiment or strengthening a comparative claim when the metric, baseline/control, thresholds, or ambiguity rule cannot support the decision.

Guardrail: use the Metric/Baseline Readiness Gate. Missing metric or baseline means `revise` or `block`; missing threshold or ambiguity rule means `revise`. Do not treat a qualitative demo as comparative evidence.

## PI Jargon Feedback

Risk: PI review becomes vague academic prose that the user cannot act on.

Guardrail: use a PI Verdict with `Decision`, `Plain Reason`, `Blocking Issues`, `Required Changes`, `Overclaim Risk`, and `Minimum Next Action`.

## Premature Multi-Agent Work

Risk: spawning or simulating many roles for routine organization.

Guardrail: default to one orchestrator. Add roles only for experiments, failures, claim/manuscript work, or framework upgrades.

## Runtime Creep

Risk: adding CLI, databases, task queues, migrations, or web UI while trying to improve the file-first MVP.

Guardrail: document repeated pain as a future candidate. Do not implement runtime unless the user explicitly changes scope.

## Autonomy Bypass

Risk: treating a recommended next action as permission to execute, edit claims, draft manuscript prose, open specialist agents, or upgrade framework state.

Guardrail: use Action Permission. Under `L1 guided`, propose high-risk actions and ask first. Blocked moves from profile, state, handoff, or user correction override convenience.

## Vague Execution Approval

Risk: interpreting "continue", "next", or a stale state recommendation as approval to run experiments or change research artifacts.

Guardrail: approval must name the action class closely enough to audit: design, execute, promote evidence, strengthen claim, draft manuscript, update state, update profile, open specialist roles, or upgrade framework.

## Route Escalation Creep

Risk: a light daily continue escalates into deep review, experiment execution, claim strengthening, or manuscript drafting because the next action sounds obvious.

Guardrail: keep Daily Brief short. Print a permission verdict only when an action crosses a risk boundary; otherwise name `May Change After Approval` and `Do Not Do Today`.

## Consumer Upgrade Damage

Risk: changing submodule pointer or templates and silently rewriting existing cards.

Guardrail: record framework commits in `ADOPTION.md`, summarize changes, and add migration notes. Existing research cards remain intact.

## Weak Initialization

Risk: copying templates into a project before understanding it.

Guardrail: produce an Alignment Brief first, confirm project identity and policy choices, then present an implementation plan before writing files.

## Premature Manuscript Mode

Risk: drafting polished paper language before the claim ledger is ready.

Guardrail: draft outlines from claim cards only. Weak or speculative claims stay tentative or are omitted.
