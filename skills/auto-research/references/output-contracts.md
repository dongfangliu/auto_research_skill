# Output Contracts

Use these compact structures when reporting Auto Research work. Keep them short unless the user asks for detail.

## Alignment Brief

Use before initialization or major state changes:

```text
Project Identity
Research Goal
Current Phase
Active Question Or Blocker
Authoritative Files
Historical Records To Preserve
Claim Boundaries
Recommended Auto Research Role
Initialization Status
Remaining Questions
```

## Stage Brief

Use when continuing or reviewing a project:

```text
Active Stage
Active Items
Verified Context
Current Risks
Recommended Next Action
Files Likely To Change
```

## Plain Research Reply

Use this as the default user-facing shape for ordinary work. Keep internal gate, role, card, claim, and evidence terminology out unless the user asks for it or a blocker needs exact wording.

```text
Right now:
Next step:
Why:
I will not:
Need your confirmation:
```

Use the user's conversation language for labels and prose. Keep file names, IDs, commands, and schema fields in English. Prefer one short question at the end when the user must choose.

When confirmation is needed, include options:

```text
Question:
Options:
1. [Recommended] ...
2. ...
3. ...
You can also reply with your own instruction.
```

## Action Brief

Use before a focused design, execution, update, review, or feedback response when a full Daily Brief would be too large:

```text
Action Brief
Mainline
Active Item
Decision Needed
Current Risk
Allowed Now
Blocked Or Needs Approval
Minimum Next Action
Will Not Do
```

Keep it under 10 lines. Use it to make control explicit without loading or printing broader project history.

## Daily Brief

Use for daily brief, today, continue, resume, or start-session requests when the user needs the next research action:

```text
Daily Brief
Mainline
Today's Active Item
Read Now
State-Derived Context
Current Risk
Today's Decision
Recommended Next Action
Do Not Do Today
May Change After Approval
Do Not Touch Today
```

Keep it short. Prefer 10-15 lines. `Read Now` should name only the profile, state, and active cards actually read. `State-Derived Context` may summarize state entries for cards not opened. `Do Not Do Today` and `Do Not Touch Today` should block claim, manuscript, experiment, file, or side-branch drift when relevant.

## Resume Consistency Verdict

Use when state, primary card, handoff, latest decision, claim boundary, or evidence boundary may disagree:

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

If the decision is `revise` or `block`, stop before experiment execution, evidence promotion, claim strengthening, or manuscript work.

## Action Permission Verdict

Use before high-risk actions or when approval status is unclear:

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

For ordinary Daily Briefs, do not print this full block unless needed; reflect it through `May Change After Approval` and `Do Not Do Today`.

## Gate Review

Use before moving stages, executing experiments, strengthening claims, or drafting manuscript text:

```text
Gate
Decision: pass | revise | block | branch
Facts
Inferences
Risks
Missing Evidence
Required Next Action
```

Use `block` when moving forward would create invalid evidence, uncontrolled execution, or overclaiming. Avoid `fail` for gate decisions because it does not say whether to revise, block, or branch.

## Readiness Verdict

Use before experiment execution or claim strengthening when a metric, baseline, control, threshold, or comparative interpretation matters:

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

If the result is not `pass`, stop at the minimum next action. Do not continue into experiment execution, strong claim language, or manuscript drafting.

## Role Report

Use for delegated or simulated roles:

```text
Role
Scope
Facts
Inferences
Risks
Dissent Or Blocking Concern
Open Questions
Recommended Next Action
Files / Commands / Outputs
```

## Execution Report

Use after an approved experiment, script, analysis, or file-producing action:

```text
Execution Report
Action
Permission Source
Commands Or Procedure
Inputs And Fixed Settings
Outputs Or Artifacts
Verified Facts
Deviations Or Failures
Immediate Interpretation
Evidence Boundary
Minimum Next Action
```

Do not use this as evidence by itself. A result becomes claim-usable only after an Evidence Promotion Verdict and an evidence card or equivalent approved record.

## PI Verdict

Use for PI feedback before execution, after execution, before strengthening claims, or when a route is drifting:

```text
Decision: approve | revise | block | branch
Plain Reason
Blocking Issues
Required Changes
Overclaim Risk
Minimum Next Action
```

Start with the decision. Use short, human-readable sentences. Do not use generic phrases like "further research is needed" without naming the next action.

## Orchestrator Resolution

Use after student, PI, auditor, or specialist perspectives disagree:

```text
Mainline Question
Decision
Accepted Points
Rejected Points
Reason
Files Or State To Update
Next Action
```

## Feedback Intake

Use when the user corrects direction, PI style, claim boundaries, context budget, autonomy, or experiment judgment:

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

Use it only when a correction changes behavior. Do not add it to ordinary Daily Briefs.

## Decision Trace

Use in decision records, handoffs, or card revisions when a future agent must recover why a verdict or correction happened:

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

## Claim Audit

Use when evaluating claim strength:

```text
Claim
Supporting Evidence
Conflicting Evidence
Evidence Strength
Metric/Baseline Readiness
Evidence Promotion Status
Allowed Wording
Forbidden Wording
Verdict
Next Evidence Needed
```

Verdict values:

- `unsupported`
- `speculative`
- `weak`
- `moderate`
- `strong`
- `contradicted`

## Evidence Promotion Verdict

Use before turning a result, decision record, literature note, artifact, or prior observation into evidence, or before letting evidence affect a claim:

```text
Evidence Promotion Verdict
Decision: promote | hold | revise | block | branch
Source Result
Verified Facts
Inferences
Evidence Strength
Supports
Does Not Support
Claim Impact: strengthen | keep weak | weaken | contradict | none
Missing Links
Allowed Wording
Forbidden Wording
Minimum Next Action
```

Do not treat draft briefs, readiness verdicts, handoffs, PI opinions, or unreviewed decision records as claim-supporting evidence.

## Final Report

Use after file changes:

```text
Changed
Validation
Not Changed
Open Risks
Next Action
```

Mention exact files changed. If tests or validation were not run, say so explicitly.
