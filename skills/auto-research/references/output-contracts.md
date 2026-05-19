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

## Gate Review

Use before moving stages, executing experiments, strengthening claims, or drafting manuscript text:

```text
Gate
Decision: pass | fail | branch | revise
Facts
Inferences
Risks
Missing Evidence
Required Next Action
```

## Role Report

Use for delegated or simulated roles:

```text
Facts
Inferences
Risks
Open Questions
Recommended Next Action
Files / Commands / Outputs
```

## Claim Audit

Use when evaluating claim strength:

```text
Claim
Supporting Evidence
Conflicting Evidence
Evidence Strength
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
