---
name: auto-research-experiment
description: Thin Auto Research experiment harness. Use only after $auto-research is active or when the user explicitly invokes $auto-research-experiment, asks Auto Research to design, review, execute, or analyze experiments, readiness, metrics, baselines, controls, deviations, or failure attribution.
---

# Auto Research Experiment

## Purpose

Keep experiment design, review, execution, and failure analysis tied to the mainline question, readiness gates, role separation, and reproducible records.

## Applicable Stages

- Applicable stage: `hypothesis_design`, `experiment_design`, `experiment_execution`, and experiment-related `result_analysis`.
- Trigger condition: the user asks to design, review, execute, diagnose, or interpret an experiment after `$auto-research` is active or by invoking `$auto-research-experiment`.
- Failure risk: writing procedure details before the experiment spine, executing without readiness and approval, merging student and PI judgment, or turning results directly into claim support.

## Minimum Context

1. Read local `AGENTS.md` or equivalent.
2. Load shared `../auto-research/references/context-router.md`.
3. Read project profile, `research/STATE.md`, and the active idea, hypothesis, or experiment brief named by state.
4. Read linked prior experiments only when cited by the active card or needed for failure attribution.
5. Read `.auto_research/TEAM_PROFILE.md` only when a high-risk decision needs project-specific role background or an explicitly named advisor.
6. Read procedure files only when execution has been explicitly requested and permission checks allow it.

## Reference Loading

- Load `../auto-research/references/experiment-work.md` for experiment design, readiness, execution, PI review, method review, or failure review.
- Load `../auto-research/references/output-contracts.md` for Experiment Spine, Readiness Verdict, PI Verdict, Role Report, Action Permission Verdict, or Execution Report.
- Load `templates/experiment_brief.md` and `templates/decision_record.md` only when creating or checking those artifacts.
- Load `framework/workflow_gates.md` when exact gate criteria are needed.

## Workflow

1. Frame the mainline question from profile, state, and active card.
2. Draft or check the Experiment Spine before execution details.
3. Run Metric/Baseline Readiness before procedure details when measurement, comparison, controls, statistics, sampling, or claim boundaries affect the decision.
4. Keep `student-executor`, `method-specialist`, and `pi-reviewer` perspectives separate; simulate role blocks if subagents are not available.
5. Before execution, check Resume Consistency, readiness pass, required PI/method review, blocked moves, and Action Permission.
6. After approved execution, record commands, inputs, outputs, deviations, verified facts, limitations, competing explanations, and evidence boundary.

## Blocked Actions

- Do not execute an experiment unless readiness passes and the user or project policy approves the action class.
- Do not treat an advisor report as execution approval.
- Do not promote evidence, strengthen claims, or draft manuscript wording from execution approval.
- Do not approve demonstrations that cannot answer the mainline question.
- Do not hide failed sanity checks, deviations, ambiguous results, or competing explanations.

## Output Contract

Use `Readiness Verdict` before execution when metric or baseline matters. Use `PI Verdict` for experiment review. Use `Role Report` for delegated, simulated, or advisory roles. Use `Execution Report` only after approved execution. Use `Evidence Promotion Verdict` only by routing to `$auto-research-evidence-claims`.
