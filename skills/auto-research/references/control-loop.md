# Control Loop

Use this reference for user feedback, mainline drift, context budget decisions, and autonomy checks.

## Context Budget

Load context in this order:

1. Local rules: `AGENTS.md` or equivalent.
2. Project profile.
3. `research/STATE.md`.
4. Active cards named by state.
5. Optional `.auto_research/TEAM_PROFILE.md` only for high-risk gates, team calibration, or explicit team/role requests.
6. Task-specific reference file.
7. Framework files only when a gate, template, or rule is needed.

For a normal `continue`, stop after profile, state, and active cards unless a gate or missing template requires more. Do not load the team profile for ordinary daily continue. For a claim audit, do not load experiment-work unless the claim depends on an experiment record that must be inspected.

If the optional team profile has already been read in the same continuous session, reuse that context unless the file changed, the user asks to reload it, or context recovery after compaction makes high-risk work depend on it.

## Long Context Recovery

Use this when the conversation is long, a session resumes after compaction, or the agent is unsure whether an important instruction came from chat memory or durable project state.

1. Re-read only project profile, `research/STATE.md`, and the primary active card before acting.
2. Treat chat memory as volatile until it is confirmed by those files or by a named handoff, decision record, or active card.
3. Do not execute experiments, promote evidence, strengthen claims, or draft manuscript prose from chat memory alone.
4. If an important user correction is not yet durable, say which existing place should capture it: `STATE.md`, the active card, a decision record, or a handoff packet.
5. For high-risk role/advisor work after compaction, re-read the team profile if the task depends on it.
6. Do not create a new checkpoint artifact. Use existing state, cards, decision records, and handoffs.

## Daily Mainline Discipline

Use for daily brief, today, continue, resume, start session, or when active items compete.

Daily open:

1. Read project profile, `research/STATE.md`, and the primary active card only.
2. Confirm `mainline_question`, `primary_active_item`, `primary_active_path`, `primary_decision`, `current_risk`, `next_recommended_action`, `parking_lot`, `last_user_correction`, and `last_mainline_check`.
3. Run a Resume Consistency check: primary card ID and status, card `next_action`, state `next_recommended_action`, blocked moves, last user correction, and any latest failure/result attribution must not contradict each other.
4. If several active items exist, choose one primary active item that reduces the largest current risk. Put the rest in parking lot, paused, or a branch gate.
5. If state is insufficient, stale, or conflicts with the primary active card, report `Revise STATE first`, name the missing or conflicting field, and suggest a `STATE.md` or active-card update instead of scanning the full repository.
6. Treat facts copied from `STATE.md` as state-derived context unless you read the source card or evidence directly.

Daily close:

1. State whether `STATE.md` needs an additive update.
2. If yes, name the fields to update: mainline, primary active item, current risk, next action, parking lot, or last user correction.
3. Keep side issues in parking lot unless they need a branch gate.

Daily Brief is an output contract, not a persistent card. It should not start experiments, strengthen claims, or draft manuscript text.

## Resume Consistency

Use this when daily open, handoff resume, or a gate finds that state and cards may disagree:

```text
Resume Consistency Verdict
Decision: pass | revise | block
Checked
Conflict
Authoritative Source
Minimal Fix
Today Do Not Do
Next Action
```

For ordinary daily continue, check only profile, state, and the primary active card. Read a handoff only when the user asks to resume from it, state names it as required for resume, or a direct conflict points to it. If a conflict remains, stop at the verdict; do not perform a full repo audit.

Attribution consistency rule: measurement error should route to metric/procedure review; implementation error to implementation fix; hypothesis failure to revise, branch, or stop; ambiguous result to hold or review. If state points to a different next action, return `revise`.

## Mainline Control

Before substantial work, identify:

```text
mainline_question
active_item
decision_needed
current_risk
parking_lot
```

If the conversation drifts into details that do not affect the decision, return to the mainline and put side issues in `parking_lot`. If `STATE.md` lists competing active items, choose the one that reduces the largest current risk and state the assumption.

Use a one-decision rule: unless the user asks for a deep review, advance only the decision named by `primary_decision` or the decision needed by the primary active card. Do not combine experiment execution, evidence promotion, claim strengthening, and manuscript drafting in one response unless a gate explicitly requires a handoff between them.

When the next action is unclear, choose the smallest action that can reduce the current risk without changing research direction. If no such action exists, return a Resume Consistency Verdict or Action Permission Verdict instead of scanning wider history.

## Feedback Handling

When the user corrects direction, terminology, experiment judgment, PI style, or autonomy:

1. Restate the correction in plain language.
2. Classify the correction:
   - current-response preference: tone, format, or local emphasis for this reply
   - persistent style rule: repeated PI style, language, or review directness preference
   - mainline correction: active item, priority, parking lot, or context budget
   - research judgment correction: metric, baseline, claim boundary, experiment interpretation, or evidence status
   - autonomy correction: what may be read, written, executed, delegated, or drafted
3. Decide whether it changes current response only, `PROJECT_PROFILE.md`, `STATE.md`, a card revision, a decision record, or a handoff packet.
4. If it changes persistent research state, propose or write an additive update according to the project autonomy level.
5. Do not silently ignore high-value feedback.

User corrections outrank the agent's prior plan for the current turn. After a correction, restate the new constraint, name what work is now out of scope, and continue only with the minimum action still allowed.

Use persistent updates for repeated preferences, project-specific terms, changed claim boundaries, changed active stage, or corrected experimental interpretation.

Do not persist every correction. One-off wording or response-format preferences usually affect only the current reply. Persistent updates are justified when the feedback changes future decisions, blocked moves, claim boundaries, experiment interpretation, or the project's default review style.

## Feedback Intake

Use this compact intake only when the user corrects the agent or when a correction must survive the current response:

```text
Feedback Intake
Correction
Applies To: current response | PROJECT_PROFILE | STATE | active card | decision record | handoff | parking lot
Mainline Impact
Context Budget Impact
Persistent Update Needed: yes | no
Proposed Minimal Change
Next Action
Will Not Do
```

If the correction says "return to the mainline", identify the primary active item and put side issues in parking lot. If the correction changes claim boundaries or experiment interpretation, update or propose an additive card/decision revision rather than rewriting history. If the correction narrows context budget, name the minimum files that still must be read for the current gate.

## Decision Trace

For gate verdicts, PI dissent, user corrections, claim-boundary changes, and handoffs, preserve a short trace:

```text
Decision Trace
Decision
Why
Rejected Alternatives
Dissent Or User Correction
Boundary Changed
Do Not Repeat
Next Reviewer Should Check
```

Record the trace in the smallest durable place that future agents will read: `STATE.md` for active mainline changes, project profile for persistent policy or style, the affected card for local claim/experiment boundaries, a decision record for experiment interpretation, or a handoff packet when another agent/session must resume.

## Autonomy Check

Before writing files, running experiments, opening subagents, strengthening claims, or drafting manuscript text, check the project autonomy level and blocked moves. If unspecified, use `L1 guided`.

High-risk actions always need explicit approval unless the profile says otherwise:

- changing the mainline research direction
- launching expensive or long-running experiments
- replacing a core hypothesis
- strengthening a core claim
- producing publication-ready language
- changing framework submodule version

Use an Action Permission Verdict when the next action crosses a risk boundary:

```text
Action Permission Verdict
Decision: allowed | ask first | blocked
Requested Action
Autonomy Level
Risk Level
Blocked Move Check
Required Gate
May Do Now
Must Ask Before
Do Not Do
Minimum Next Action
```

Ordinary Daily Briefs should stay short. Use the permission check to fill `May Change After Approval` and `Do Not Do Today`; print the full verdict only when the user asks to act or when permission is unclear.

For high-control execution, approval must name the action class closely enough to audit later: design, execute, promote evidence, strengthen claim, draft manuscript, update state, update profile, open specialist roles, or upgrade framework. A general next-action recommendation in `STATE.md` is not execution approval under `L1 guided`.

## User-Facing Output

Keep control-loop replies short. For ordinary user-facing work, prefer `Plain Research Reply` from `output-contracts.md`. Use `Daily Brief` when the user asks for a daily start, resume summary, or what to avoid today. For other control-loop cases, use:

```text
Mainline
Decision Needed
What I Will Change
What I Will Not Change
Next Action
```

Use this only when it clarifies the work. Do not wrap every small reply in a template.

## Ask At Choice Points

Ask one short question before crossing a meaningful boundary:

- planning a multi-step change
- executing an experiment or command
- writing or modifying research files
- recording a user correction for future sessions
- making a result available for future writing
- saying a conclusion more strongly
- drafting paper-like prose

Use plain wording. Provide 2-3 options, mark one as `[Recommended]`, and say the user may reply with a custom instruction. If a structured planning or user-input tool is available, use it for these choices; otherwise ask directly in chat.

Example:

```text
Do you want me to plan this first?
1. [Recommended] Make a short plan before editing files.
2. Only review and point out risks.
3. Proceed with the smallest safe change now.
You can also reply with your own instruction.
```
