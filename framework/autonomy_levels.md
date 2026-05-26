# Autonomy Levels

Each project should declare an autonomy level in its project profile.

## L0 manual

Agents organize, summarize, and suggest. They do not decide next steps or modify research artifacts without explicit instruction.

## L1 guided

Agents propose plans and wait for human approval before executing meaningful research steps. This is the MVP default.

## L2 delegated

Agents may execute low-risk tasks without approval, such as creating draft cards, summarizing known notes, or updating state. High-risk gates still require approval.

## L3 autonomous_draft

Agents may proceed through multiple research stages and produce manuscript drafts. All claims must remain evidence-labeled and publication readiness is not implied.

## L4 publication_ready

Future target only. Requires mature audit, reproducibility, statistics, ethics, and publication review infrastructure. MVP projects should not use this level.

## Autonomy Matrix

Use the project profile first when it is more specific. Otherwise apply this matrix:

| Action | L0 manual | L1 guided | L2 delegated | L3 autonomous_draft |
| --- | --- | --- | --- | --- |
| Read files and summarize | allowed | allowed | allowed | allowed |
| Create draft cards | ask first | ask first | allowed for low-risk cards | allowed |
| Update `STATE.md` | ask first | ask first | allowed for factual summaries | allowed with revision notes |
| Open specialist agents or advisors | ask first | ask first for meaningful work | allowed for low-risk review | allowed |
| Design experiment brief | suggest only | propose and wait | allowed for low-risk draft | allowed |
| Execute experiment | explicit approval | explicit approval | allowed only if low-cost and pre-approved by profile | allowed unless high-risk |
| Resolve state/handoff conflict | ask first | propose minimal fix | allowed for factual consistency notes | allowed with revision notes |
| Promote result to evidence | explicit approval if claim-impacting | ask first unless profile allows draft evidence | allowed for low-risk weak evidence | allowed with evidence gate |
| Strengthen claim | explicit approval | explicit approval | explicit approval | PI + claim-auditor gate required |
| Draft manuscript outline | ask first | allowed from approved/weak claim cards | allowed from claim ledger only | allowed from claim ledger only |
| Draft manuscript prose | explicit approval | explicit approval | ask first unless profile allows | draft from claim ledger only |
| Change project profile policy | explicit approval | explicit approval | ask first | ask first unless pre-approved |
| Upgrade framework version | explicit approval | explicit approval | explicit approval | explicit approval |

## Action Permission Workflow

Before a high-risk action, return or internally apply:

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

For ordinary daily continue, do not print the full verdict unless the next action crosses a risk boundary. Use it to populate `May Change After Approval` and `Do Not Do Today`.

## High-Risk Actions

The following require human approval unless the project profile explicitly says otherwise:

- Changing research direction.
- Launching expensive or long-running experiments.
- Replacing core hypotheses.
- Recommending final claims.
- Promoting ambiguous results into evidence.
- Producing publication-ready language.
- Opening custom advisory roles for high-risk decisions.
- Resolving state/handoff conflicts by editing files.
- Updating framework submodule version in a consumer project.

If the autonomy level is missing or ambiguous, use `L1 guided`.
