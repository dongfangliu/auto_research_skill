# Changelog

## mvp-0.14 - Harness skill suite

- Added five thin child skills: `auto-research-init`, `auto-research-continue`, `auto-research-experiment`, `auto-research-evidence-claims`, and `auto-research-maintainer`.
- Kept `$auto-research` as the explicit compatibility entry while routing active Auto Research sessions to narrower child skills when available.
- Added `stage-router.md` to map lifecycle stages and stage actions to child skills, minimum context, stop conditions, output contracts, and failure risks.
- Updated README install guidance for the full skill suite while preserving legacy single-skill installation.
- Extended forward tests and local checks for child-skill routing, stage navigation, evidence/claim boundaries, maintainer behavior, and runtime-creep prevention.

## mvp-0.13 - Optional project team profiles

- Added `templates/team_profile.md` for project-specific role adaptations and advisory roles.
- Added `team_profile` and `team_profile_use` guidance to project profiles, initialization, submodule adoption, and README docs.
- Updated skill routing so team profiles are loaded only for high-risk gates, team calibration, or explicit team/role requests, not ordinary daily continue.
- Added advisor boundaries: custom roles use `advisor:<role_id>`, return Role Reports only, and cannot approve gates or create evidence.
- Extended forward tests, failure modes, and the mini project with a minimal `TEAM_PROFILE.md` and advisory review example.

## mvp-0.12 - Guided user choices

- Required user questions at meaningful choice points to include 2-3 options, one `[Recommended]` option, and an explicit custom-reply escape hatch.
- Updated plain reply and control-loop guidance so planning, review, execution, file changes, durable corrections, stronger wording, and paper-like prose are presented as easy user choices.
- Added failure-mode and forward-test coverage for vague open-ended questions.

## mvp-0.11 - Plain-language user layer

- Added a user-facing mode that hides framework internals behind ordinary research actions.
- Added a Plain Research Reply contract for short, understandable responses.
- Added choice-point guidance so agents ask before planning, execution, file writes, durable corrections, stronger conclusions, or paper-like prose.
- Set framework-source and default template files to English by default while keeping chat replies aligned to the user's language.
- Added failure modes and forward tests for leaking framework internals and mixed visible language.

## mvp-0.10 - High-control research loop

- Added an operating kernel to the skill for route, focus, design, permission, action, record, and report decisions.
- Strengthened experiment design and execution guidance with a compact control loop, execution preflight, stop conditions, and recording requirements.
- Added Action Brief and Execution Report contracts for token-efficient communication around focused work.
- Tightened feedback and autonomy guidance so user corrections override stale plans and vague next-action recommendations do not count as execution approval.
- Added failure modes for multi-step action drift and vague execution approval.

## mvp-0.9 - Action permission and risk routing

- Added an Action Permission / Blocked Moves Gate for experiment execution, evidence promotion, claim strengthening, manuscript prose, profile changes, framework upgrades, and specialist work.
- Updated autonomy rules, control-loop guidance, context routing, output contracts, failure modes, and forward tests to catch over-read, over-write, and approval-bypass regressions.
- Added `blocked_moves_today` to state and clearer blocked-move prompts to project profiles.
- Extended the mini project so `EXP-0002` execution, `CLM-0001` strengthening, and manuscript prose remain blocked under `L1 guided`.

## mvp-0.8 - Resume consistency

- Added a Resume Consistency Gate for state, primary active card, handoff, latest decision, evidence boundary, and claim boundary conflicts.
- Updated control-loop and context-router rules so stale state returns a consistency verdict instead of triggering a full repo scan.
- Added resume-readiness fields to state and handoff templates, plus state-impact fields to decision, evidence, and claim templates.
- Extended forward tests and the mini project to preserve token-light resume while blocking stale execution, evidence, and claim paths.

## mvp-0.7 - Result-to-evidence promotion

- Added a Result-to-Evidence Gate between decision records and claim use.
- Added Evidence Promotion Verdict fields and output contracts to separate verified facts, inferences, limitations, ambiguity, and claim-use boundaries.
- Updated workflows and forward tests to block draft briefs, readiness verdicts, handoffs, PI opinions, and ambiguous results from becoming positive evidence.
- Revised the mini project's `EVD-0001` to show weak audit-path evidence that cannot support comparative recovery-improvement claims.

## mvp-0.6 - Feedback-to-state decision trace

- Added Feedback Intake and Decision Trace rules for user corrections, PI dissent, claim-boundary changes, and handoffs.
- Updated handoff, decision, state, project profile, and claim templates to preserve only high-value persistent corrections.
- Added forward tests for mainline corrections, claim-boundary corrections, context-budget corrections, and handoff resume after correction.
- Extended the mini project with a handoff trace that preserves the instruction not to execute `EXP-0002` or strengthen `CLM-0001`.

## mvp-0.5 - Metric and baseline readiness

- Added a Metric/Baseline Readiness Gate before experiment execution, claim strengthening, or manuscript drafting.
- Added a Readiness Verdict contract and experiment brief fields for metric, baseline/control, thresholds, ambiguity handling, sanity checks, and claim boundaries.
- Updated forward tests and failure modes to block experiments and comparative claims when metric or baseline readiness is missing.
- Extended the mini project with a draft second experiment that keeps readiness review separate from execution.

## mvp-0.4 - Daily mainline discipline

- Added Daily Brief and Daily Mainline Discipline rules for ordinary continue/resume sessions.
- Updated state templates and the mini project to identify a single primary active item, minimum next action, and do-not-touch parking lot.
- Updated workflows and forward tests so daily continue stays token-light and avoids claim/manuscript drift.

## mvp-0.3 - Token-efficient experiment control

- Added task-specific skill references for experiment work and control-loop decisions.
- Added Experiment Spine and direct PI Verdict contracts for experiment design, execution, and failure review.
- Expanded agent role rules, autonomy levels, output contracts, and forward-test rubrics.
- Updated templates for experiment briefs, decision records, hypothesis review, literature impact, state mainline tracking, and handoff packets.
- Revised the mini project trail to show that a demo without baseline or metric cannot strengthen a comparative claim.

## mvp-0.2 - Alignment-first initialization guide

- Added `prompts/init_project.md` for Codex, Claude Code, or similar agents to guide project initialization.
- Added `framework/initialization.md` to document discovery, alignment, and implementation phases.
- Added `templates/init_report.md` for auditable initialization records.
- Updated README with the prompt-first initialization entry point.

## mvp-0.1 - Initial file-first framework

- Added research lifecycle, state model, agent roles, workflow gates, autonomy levels, profile guide, submodule adoption guide, and upgrade path.
- Added reusable Markdown templates for project profiles, state, cards, handoff packets, evidence, claims, and manuscript outlines.
- Added `examples/mini_project` to demonstrate a full trail from idea to manuscript outline, including an experiment-stage branch back to ideation.
