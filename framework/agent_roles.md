# Agent Roles

Roles are activated by task and gate. They are not permanent people and should not be spawned unless the current task benefits from the separation.

## Roles

### orchestrator

Maintains the global view. It reads the project profile and state, chooses the next workflow, delegates only when useful, and merges outputs into a coherent decision.

### student-executor

Executes experiments, code changes, analyses, and records. It owns concrete artifacts and reports facts, commands, outputs, deviations, and implementation details.

### pi-reviewer

Reviews direction, evidence sufficiency, failure attribution, overclaiming, and next-step strategy. It does not replace execution records.

### literature-specialist

Turns ideas into literature questions, compares prior work, extracts disputes, and identifies evidence gaps. It should distinguish paper claims from verified project facts.

### method-specialist

Reviews methods, statistics, numerical stability, experimental design, controls, and alternative explanations.

### claim-auditor

Checks whether claims are supported by evidence cards, whether wording is too strong, and whether conflicting evidence is represented.

### repro-auditor

Checks whether a research trail can be resumed, reproduced, and audited from files alone. It focuses on required context, commands, artifacts, framework version, profile compatibility, and migration notes.

### writing-agent

Builds outlines or drafts from approved claim cards. It must not create unsupported claims to improve narrative flow.

## Activation Rules

- Ordinary organization: orchestrator only.
- New idea: orchestrator, optional literature-specialist.
- New hypothesis: orchestrator + pi-reviewer.
- New experiment: student-executor + pi-reviewer.
- Failure review: student-executor + pi-reviewer, optional method-specialist.
- Claim recommendation: pi-reviewer + claim-auditor.
- Manuscript outline: writing-agent + claim-auditor + pi-reviewer.
- Framework upgrade in a consumer project: orchestrator + repro-auditor.

## Multi-Agent Limits

Use multiple students only when write scopes and artifacts are disjoint. Use multiple mentors only for high-risk decisions, such as route changes, core claims, major failures, or pre-publication review.

## Handoff Packet

Every delegated agent should return:

```text
Facts
Inferences
Risks
Open Questions
Recommended Next Action
Files / Commands / Outputs
```
