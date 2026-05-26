# Agent Roles

Roles are activated by task and gate. They are not permanent people and should not be spawned unless the current task benefits from the separation.

## Roles

### orchestrator

Maintains the global view. It reads the project profile and state, frames the mainline question, chooses the next workflow, delegates only when useful, and merges outputs into a coherent decision.

### student-executor

Designs and executes experiments, code changes, analyses, and records. It owns concrete artifacts and reports facts, commands, outputs, deviations, and implementation details. It does not approve its own experiment.

### pi-reviewer

Reviews direction, evidence sufficiency, failure attribution, overclaiming, and next-step strategy. It must give a direct verdict, strongest objection, evidence gap, overclaim risk, and minimum acceptable next action. It does not replace execution records.

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

## Project Team Profiles

Consumer projects may define an optional `.auto_research/TEAM_PROFILE.md` to adapt these generic roles to the project's background, methods, and review risks.

- Applicable stage: experiment design, experiment execution review, result analysis, claim building, manuscript planning, team calibration, or a user request that names a team member or role.
- Trigger condition: a project-specific role background, review focus, or custom advisor can improve the current decision.
- Failure risk: treating a persona or advisor opinion as evidence can over-strengthen claims; using team context during routine organization can waste context; letting a custom advisor approve work can bypass gates.

Team profiles adjust what a role pays attention to. They do not change the role sequence, evidence requirements, action permission, or gate authority.

Custom advisory roles must use `advisor:<role_id>`. They may appear in Role Reports, review notes, and handoff packets, but ordinary card `owner_agent` values should remain framework core roles. Advisors can provide dissent and suggested next actions, but the `orchestrator` resolves their input and the appropriate PI, method, claim, or manuscript gate makes the decision.

## Activation Rules

- Ordinary organization: orchestrator only.
- New idea: orchestrator, optional literature-specialist.
- New hypothesis: orchestrator + pi-reviewer.
- New experiment: student-executor + pi-reviewer.
- Experiment involving metrics, baselines, statistics, controls, numerical stability, or sampling: student-executor + pi-reviewer + method-specialist before execution.
- Failure review: student-executor + pi-reviewer, optional method-specialist.
- Claim recommendation: pi-reviewer + claim-auditor.
- Manuscript outline: writing-agent + claim-auditor + pi-reviewer.
- Framework upgrade in a consumer project: orchestrator + repro-auditor.

## Experiment Collaboration Protocol

For experiment work, use this sequence:

1. `orchestrator` frames the mainline question from profile, state, and active cards.
2. `student-executor` drafts the Experiment Spine and, when relevant, the Metric/Baseline Readiness block.
3. `method-specialist` reviews readiness before execution when the design depends on metrics, baselines, statistics, controls, numerical stability, sampling, or scoring.
4. `pi-reviewer` critiques independently with a direct PI Verdict.
5. `orchestrator` resolves: approve, revise, block, branch, execute, or update state.

When subagents are available and allowed, use separate agents for student and PI roles, and add `method-specialist` before PI when readiness validity depends on measurement or controls. If not, simulate separate role blocks in this order. A simulated PI block must include at least one possible blocking concern or state that none exists with a reason.

## Multi-Agent Limits

Use multiple students only when write scopes and artifacts are disjoint. Use multiple mentors only for high-risk decisions, such as route changes, core claims, major failures, or pre-publication review.

## Handoff Packet

Every delegated agent should return:

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
