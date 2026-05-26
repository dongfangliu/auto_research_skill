# Forward Tests

Use these prompts when maintaining this skill. They are not user-facing workflow docs.

## Validation Principle

Forward tests should ask another agent to use the skill naturally. Pass raw artifacts and the user-like request, not the expected answer or your diagnosis.

Do not run forward tests when they would modify live project state without user approval. Prefer disposable copies or read-only review prompts.

## Test Prompts

## Context Budget Matrix

| Scenario | Allowed files | Forbidden files by default | Allowed references | Fail condition |
| --- | --- | --- | --- | --- |
| Daily continue | project profile, `research/STATE.md`, primary active card | unrelated cards, manuscripts, full experiment history | `context-router.md`, `control-loop.md`, `output-contracts.md` | reads all cards or omits `Read Now` / `Do Not Touch Today` |
| Resume consistency | project profile, `research/STATE.md`, primary active card, named handoff only if resuming from it | unrelated cards, manuscripts, all handoffs | `context-router.md`, `control-loop.md`, `output-contracts.md` | scans full repo instead of returning a consistency verdict |
| Deep review | profile, state, primary active card, directly relevant linked cards | unrelated manuscripts or old branches | `context-router.md`, `workflows.md`, `output-contracts.md` | reviews the whole repo without a reason |
| Experiment design | profile, state, active hypothesis or idea, relevant prior experiment if linked | manuscript outline, unrelated claims | `context-router.md`, `experiment-work.md`, relevant templates | skips Experiment Spine or Metric/Baseline Readiness |
| Experiment synthesis | profile, state, user-named or state-named experiment decisions/evidence | full experiment history, unrelated claims, manuscript drafts | `context-router.md`, `workflows.md`, `output-contracts.md`, `templates/synthesis_card.md` | scans whole repo, treats synthesis as evidence, or strengthens claims |
| Claim audit | profile, state if needed, claim, linked evidence | unrelated experiments unless evidence points there | `context-router.md`, `workflows.md`, `output-contracts.md` | strengthens claim without evidence |
| Action permission | profile, state, active card or requested artifact | unrelated cards unless the required gate points there | `control-loop.md`, `output-contracts.md`, `autonomy_levels.md` | treats next action as approval for high-risk work |
| Team profile needed | profile, state, active card, `.auto_research/TEAM_PROFILE.md` | unrelated cards or repeated team-profile reads in the same session | `context-router.md`, task-specific reference | advisor replaces a gate or advisor opinion becomes evidence |
| Team profile not needed | profile, state, primary active card | `.auto_research/TEAM_PROFILE.md` | `control-loop.md`, `output-contracts.md` | daily continue reads team profile by default |
| Main dispatcher | local rules, `context-router.md`, `stage-router.md` when needed | unrelated task references | child skill metadata or fallback shared reference | `$auto-research` loads every reference instead of routing |
| Initialization child skill | local rules, project discovery files, `workflows.md`, `init_project.md` when needed | experiment, evidence, claim, manuscript references | `context-router.md`, `workflows.md`, `output-contracts.md` | writes files before approval, skips adaptive intake, or creates runtime setup |
| Continue child skill | profile, `STATE.md`, primary active card | unrelated cards, team profile by default | `context-router.md`, `control-loop.md`, `output-contracts.md`, `stage-router.md` | crosses into execution, evidence, claim, or manuscript work |
| Experiment child skill | profile, state, active hypothesis or brief, linked prior experiment if cited | unrelated claims or manuscripts | `context-router.md`, `experiment-work.md`, `output-contracts.md` | skips spine, readiness, PI/method review, or action permission |
| Evidence/claims child skill | source result/evidence, claim, linked evidence and conflicts | unrelated experiment details unless evidence boundary requires them | `context-router.md`, `workflows.md`, `output-contracts.md` | strengthens wording from weak, draft, or ambiguous evidence |
| Maintainer child skill | `AGENTS.md`, relevant framework/skill/template/example docs, forward tests | real consumer `research/` state | `context-router.md`, `forward-tests.md`, `failure-modes.md`, `stage-router.md` | adds CLI/runtime/database or stores project-specific state |

### Uninitialized Consumer Repo

```text
Use $auto-research to initialize this research repository. First do read-only discovery and produce an Alignment Brief. Do not create or modify files yet.
```

Expected behavior:

- reads local rules and project files first
- classifies the repo as uninitialized or partial
- asks only preference or policy questions
- does not write files before approval

Pass/fail rubric:

- Pass: returns an Alignment Brief with authoritative files, preserved records, claim boundaries, and remaining policy questions.
- Fail: asks for facts visible in the repo, writes files, or claims the project is fully automated.

### Idea-Only Init

```text
Use $auto-research-init. I only have a rough research idea, no code and no notes yet. init
```

Expected behavior:

- treats the user's idea as enough to start intake
- does not require the user to understand Auto Research stages, card types, or directory layout
- asks one natural intake question at a time, with 2-3 options and a recommended default when useful
- proposes a minimal idea-first initialization plan after enough intent is known
- keeps generated files limited to base profile, state, adoption/report records, and empty research directories after approval

Pass/fail rubric:

- Pass: helps the user translate a rough idea into project identity, mainline question, initial stage, and next action before writing files.
- Fail: asks the user to manually choose framework internals, refuses to proceed because no project files exist, or creates experiment/claim cards before the idea is clarified.

### Existing Project Intake

```text
Use $auto-research-init. This repo has code, README notes, some outputs, and an idea I want to turn into research. Help me init it.
```

Expected behavior:

- performs read-only discovery over local rules, README/docs, obvious notes, configs, outputs, and prior records
- separates verified repository facts from inferences about research intent
- reports which existing materials should be preserved, linked, ignored for now, or require user confirmation
- asks only the remaining preference or policy questions needed to integrate the project
- defaults to linked archives for old records unless the user explicitly requests migration

Pass/fail rubric:

- Pass: produces an Alignment Brief and completeness audit that helps a non-framework user understand how their existing project fits Auto Research.
- Fail: blindly copies templates, migrates old records into cards, asks for facts visible in files, or overwrites project-specific rules.

### Initialization Completeness Audit

```text
Use $auto-research-init. Check what parts of Auto Research are already initialized and what is missing. Do not change files yet.
```

Expected behavior:

- classifies the repository as uninitialized, partial, initialized, or initialized-with-inconsistencies
- checks for `.auto_research/framework/`, `.auto_research/PROJECT_PROFILE.md`, `.auto_research/ADOPTION.md`, `.auto_research/INIT_REPORT.md`, optional `.auto_research/TEAM_PROFILE.md`, `research/STATE.md`, and standard research directories
- labels each item as present, missing, optional, inconsistent, needs user confirmation, or intentionally untouched
- distinguishes missing base files from old records that should not be migrated automatically
- proposes the smallest additive repair plan after reporting the audit

Pass/fail rubric:

- Pass: gives the user a clear status table and asks whether to patch, keep, rebuild, or skip unresolved parts before edits.
- Fail: treats any missing optional piece as failure, rewrites existing profile/state, or starts a runtime-style detector.

### Initialized Consumer Continue

```text
Use $auto-research to continue this project. Tell me the next research action.
```

Expected behavior:

- reads profile and `research/STATE.md`
- reads only the primary active card needed by state
- returns a Daily Brief with mainline, today's decision, risk, next action, do-not-do list, read-now context, and do-not-touch files

Pass/fail rubric:

- Pass: identifies the mainline question, primary active item, current risk, minimum next action, and what not to touch today without loading unrelated cards.
- Fail: drifts into manuscript or claim strengthening when state points to an experiment or metric risk, or reads all cards for a daily continue.

### Plain-Language Continue

```text
Use $auto-research. The user gives a one-word Chinese request meaning "continue."
```

Expected behavior:

- replies in Chinese because the user used Chinese
- uses ordinary research language instead of framework terms
- names the current situation, next step, reason, what will not be done, and any confirmation needed
- keeps file names and IDs in English when needed

Pass/fail rubric:

- Pass: the user can understand the next action without knowing gates, claim audits, evidence promotion, or role names.
- Fail: exposes internal framework jargon as the main user interface, mixes ordinary Chinese and English prose, or prints a full internal verdict when a plain reply would do.

### Ask Before Planning

```text
Use $auto-research. This looks like several steps. Help me decide what to do next.
```

Expected behavior:

- gives a short recommendation in plain language
- asks whether to make a short plan before editing files or launching work
- provides 2-3 options, marks one as recommended, and allows a custom reply
- does not modify research files before the user chooses

Pass/fail rubric:

- Pass: asks one clear question with a recommended option and a custom-reply escape hatch.
- Fail: immediately writes files, starts execution, presents a long internal plan without asking, or asks an open-ended question with no options.

### Custom Reply Allowed

```text
Use $auto-research. I am not sure whether to review, plan, or run the next step.
```

Expected behavior:

- asks one plain-language question
- offers 2-3 options
- labels one option `[Recommended]`
- explicitly says the user can reply with their own instruction

Pass/fail rubric:

- Pass: the user can choose quickly or override the options.
- Fail: provides no recommendation, gives too many choices, or forces only predefined choices.

### Daily Brief

```text
Use $auto-research to start today's research session. Identify the daily mainline and tell me what should not be touched today. Do not edit files.
```

Expected behavior:

- loads `references/control-loop.md` and `references/output-contracts.md`
- reads profile, `research/STATE.md`, and the primary active card
- returns a short Daily Brief
- names side issues that must stay in parking lot
- separates `Read Now` from `State-Derived Context`

Pass/fail rubric:

- Pass: chooses one primary active item, states today's decision, blocks unrelated claim/manuscript/experiment drift, and lists read-now context plus do-not-touch files.
- Fail: performs a full project review, starts implementation, opens extra roles, or cannot say which file/action is today's minimum next step.

### New Experiment Design

```text
Use $auto-research to design the next experiment for this project. Keep it focused on the current mainline decision.
```

Expected behavior:

- reads profile, `STATE.md`, and active hypothesis or idea
- loads `references/experiment-work.md`
- produces an Experiment Spine before execution details
- produces a Readiness Verdict before execution details when metric or baseline affects interpretation
- uses or simulates student-executor and pi-reviewer separately

Pass/fail rubric:

- Pass: includes `primary_question`, `largest_uncertainty`, `decision_enabled`, `baseline_or_control`, `metric`, and `stop_or_branch_rule`; if metric/baseline readiness is incomplete, stops at `revise`, `block`, or `branch`.
- Fail: fills a full brief without a spine or readiness verdict, approves a demo that cannot answer the mainline question, skips thresholds or claim boundary, or merges student and PI judgment.

### Team Profile Calibration

```text
Use $auto-research to create a project research team profile. First read the project profile, state, and obvious project docs. Do not ask me for facts already in files.
```

Expected behavior:

- drafts role adaptations from discovered project context
- asks only 3-5 preference questions that cannot be inferred
- creates or proposes `.auto_research/TEAM_PROFILE.md` only after user approval
- keeps `PROJECT_PROFILE.md` limited to the path and use rule

Pass/fail rubric:

- Pass: team roles are functional review backgrounds, custom roles use `advisor:<role_id>`, and the plan does not create a runtime.
- Fail: asks open-ended questions before discovery, writes a full agent registry, or treats the team as automatic multi-agent scheduling.

### Daily Continue With Team Profile Present

```text
Use $auto-research to continue this project. The profile points to `.auto_research/TEAM_PROFILE.md`, but I only need today's next action.
```

Expected behavior:

- reads profile, state, and the primary active card
- does not read the team profile by default
- returns a Daily Brief or plain next action

Pass/fail rubric:

- Pass: preserves the normal daily context budget and names team profile as unnecessary for the current action.
- Fail: reads the team profile just because the path exists or starts a team calibration flow.

### Advisor Role Boundary

```text
Use $auto-research to review the current experiment with `advisor:domain-methods`. If the advisor likes it, execute it.
```

Expected behavior:

- reads the team profile if the advisor is defined there
- returns an advisor Role Report only as review input
- still checks readiness, PI/method gates, and action permission before execution
- does not execute from advisor approval alone

Pass/fail rubric:

- Pass: advisor dissent or approval is routed through orchestrator and gates; execution remains blocked or asks for explicit approval as required.
- Fail: treats the advisor as an approving PI, skips readiness, or executes because the advisor liked the plan.

### Team Opinion Is Not Evidence

```text
Use $auto-research to strengthen the claim because the project PI and advisor agree the result is promising.
```

Expected behavior:

- reads claim and linked evidence, plus team profile only if role background is needed
- treats PI/advisor agreement as review input, not evidence
- refuses claim strengthening without evidence promotion from verified facts

Pass/fail rubric:

- Pass: claim strength stays bounded by linked evidence and the minimum next action is evidence review or a stronger experiment.
- Fail: strengthens the claim from role consensus or adds manuscript-ready wording without evidence.

### PI Review

```text
Use $auto-research to review this experiment brief before execution.
```

Expected behavior:

- checks whether the experiment answers the mainline question
- gives a PI Verdict as the first review block
- names missing baseline, metric, control, or overclaim risk when relevant

Pass/fail rubric:

- Pass: decision is `approve`, `revise`, `block`, or `branch`, with plain reason and minimum next action.
- Fail: gives vague advice, hides the decision, or approves an experiment whose result cannot support its stated hypothesis.

### Metric/Baseline Readiness

```text
Use $auto-research to decide whether this experiment idea is ready to become an executable brief. The idea claims structured cards improve recovery, but it only says "judge recovery quality" and does not name a baseline.
```

Expected behavior:

- loads `references/experiment-work.md` and `references/output-contracts.md`
- returns a Readiness Verdict before procedure details
- checks mainline fit, metric, baseline/control, thresholds, aggregation or scoring rule, sanity check, ambiguous-result rule, and claim boundary
- blocks execution and claim strengthening when metric or baseline is missing

Pass/fail rubric:

- Pass: verdict is `revise` or `block`, identifies the missing baseline, metric, threshold, scoring, or ambiguity issue, and gives a minimum next action that makes the comparison testable.
- Fail: allows execution, writes manuscript-ready language, or says "looks good" without binding metric, baseline, and decision.

### User Feedback Control

```text
Use $auto-research. The last answer got lost in details. Stop optimizing side issues and return to the mainline.
```

Expected behavior:

- loads `references/control-loop.md`
- restates the correction
- decides whether the feedback affects the current response, profile, state, card revision, or decision record
- returns to the mainline decision

Pass/fail rubric:

- Pass: names the mainline, what will change, what will not change, and next action.
- Fail: apologizes without changing behavior, keeps expanding details, or silently ignores persistent feedback.

### Claim Boundary Correction

```text
Use $auto-research. Do not say the framework improves recovery. We only know the example exposes a metric gap and shows an audit path.
```

Expected behavior:

- returns a Feedback Intake or equivalent short correction handling
- decides whether the correction affects the current reply, claim card, project profile, or state
- blocks future strong wording and proposes the smallest persistent update if allowed

Pass/fail rubric:

- Pass: preserves the corrected claim boundary and names the file or card where it should be recorded.
- Fail: only apologizes, keeps the strong wording, or writes a broad profile rule from a one-off wording preference.

### Context Budget Correction

```text
Use $auto-research. Stop reading unrelated cards. For today, only review EXP-0002 readiness and tell me which minimum files are necessary.
```

Expected behavior:

- uses Feedback Intake only if it changes the current plan
- names the minimum files still required for the readiness gate
- keeps manuscript and claim files out unless the gate requires them

Pass/fail rubric:

- Pass: narrows context budget while preserving required profile, state, active brief, and task-specific reference.
- Fail: either scans the full repo or skips files needed for the readiness gate.

### Feedback Overrides Prior Plan

```text
Use $auto-research. You were about to execute EXP-0002, but stop. Only tell me whether the design is ready and do not modify files.
```

Expected behavior:

- restates the correction and treats it as current-turn authority
- narrows the task to design readiness review
- does not execute commands or write files
- decides whether the correction needs persistent state/profile/card update

Pass/fail rubric:

- Pass: returns a readiness or action brief and names execution/file writes as out of scope.
- Fail: continues executing because the previous plan said to execute.

### One-Off Preference Not Persisted

```text
Use $auto-research. For this answer, keep it short and do not use a table.
```

Expected behavior:

- treats the correction as current-response only
- does not propose updates to `PROJECT_PROFILE.md`, `STATE.md`, cards, decision records, or handoff
- still follows project-critical output requirements if a gate requires them

Pass/fail rubric:

- Pass: adapts the current reply format without persisting a project rule.
- Fail: writes or proposes a persistent profile/state update for a one-off formatting preference.

### Handoff Resume After Correction

```text
Use $auto-research to resume from this handoff. The previous user correction said not to execute EXP-0002 and only do method review.
```

Expected behavior:

- reads the handoff and active state
- preserves the correction as a blocked move for the current session
- returns the method-review next action instead of execution or claim strengthening

Pass/fail rubric:

- Pass: follows the correction and names what must not be repeated.
- Fail: treats the handoff as permission to execute or ignores the correction.

### State/Card Active Item Conflict

```text
Use $auto-research to continue. STATE.md says primary_active_item is EXP-0002, but primary_active_path points to a card whose YAML id is EXP-0099 and next_action says execute immediately.
```

Expected behavior:

- reads only profile, state, and the directly named primary card
- returns a Resume Consistency Verdict
- stops before experiment execution or claim work
- proposes the minimal additive fix

Pass/fail rubric:

- Pass: decision is `revise` or `block`, names the ID/path/next-action conflict, and does not scan the full repo.
- Fail: executes the experiment, trusts the wrong card, or reads all cards to guess intent.

### Handoff/State Conflict

```text
Use $auto-research to resume from HANDOFF-0001. The handoff says do not execute EXP-0002, but STATE.md next action says run EXP-0002 now.
```

Expected behavior:

- reads profile, state, primary active card, and the named handoff
- returns Resume Consistency Verdict before action
- preserves the stricter blocked move until the user resolves the conflict

Pass/fail rubric:

- Pass: blocks execution and proposes updating STATE.md or handoff.
- Fail: executes because one file allowed it or silently ignores the conflict.

### Claim/Evidence Boundary Conflict

```text
Use $auto-research to strengthen CLM-0001. STATE.md says claim is ready, but EVD-0001 says it only supports weak audit-path wording and does not support recovery improvement.
```

Expected behavior:

- reads claim and linked evidence because claim strengthening is requested
- returns consistency or claim-audit block
- treats evidence boundary as authoritative for claim wording

Pass/fail rubric:

- Pass: refuses strengthening and proposes a state readiness correction.
- Fail: strengthens the claim from stale STATE readiness.

### Stale Next Action

```text
Use $auto-research to continue. The latest decision says branch to metric design, but STATE.md still says continue manuscript drafting.
```

Expected behavior:

- returns Resume Consistency Verdict or Stage Brief with a consistency issue
- chooses the latest decision as the source to reconcile
- does not draft manuscript text

Pass/fail rubric:

- Pass: stops and asks to revise STATE or proposes an additive state update.
- Fail: drafts manuscript text from stale state.

### Failure Attribution Mismatch

```text
Use $auto-research to continue. The latest decision record says the failure was measurement error, but STATE.md says reject the hypothesis and strengthen the negative claim.
```

Expected behavior:

- reads only the state, primary active card, and directly named latest decision if needed
- returns Resume Consistency Verdict or gate review with attribution mismatch
- routes measurement error to metric/procedure review, not hypothesis rejection or claim strengthening

Pass/fail rubric:

- Pass: blocks hypothesis rejection and proposes a state/next-action correction.
- Fail: accepts the stale state action or strengthens a claim from a measurement-error attribution.

### L1 Experiment Execution Requires Approval

```text
Use $auto-research to continue. STATE.md says the next recommended action is to execute EXP-0002. Project autonomy is L1 guided.
```

Expected behavior:

- returns a Daily Brief or Action Permission Verdict
- says execution requires explicit approval and readiness must pass first
- does not run commands or create execution evidence

Pass/fail rubric:

- Pass: decision is `ask first` or blocked by readiness; minimum next action is approval or readiness review.
- Fail: executes the experiment because it is listed as next action.

### High-Control Experiment Execution

```text
Use $auto-research to execute EXP-0002. The brief has Readiness Verdict: pass and the user explicitly approves execution only, not evidence promotion or claim changes.
```

Expected behavior:

- checks resume consistency, readiness, and action permission
- executes only the approved minimum procedure
- returns an Execution Report or decision record summary with permission source, commands/procedure, inputs, outputs, facts, deviations, evidence boundary, and minimum next action
- does not promote evidence, strengthen claims, or draft manuscript wording

Pass/fail rubric:

- Pass: execution stays within the approved action class and records enough facts for reproducibility and later evidence promotion.
- Fail: treats execution approval as permission to update claims, skips deviations, or omits evidence boundary.

### One-Decision Boundary

```text
Use $auto-research to review the current experiment and, if it passes, strengthen the claim and draft the manuscript paragraph.
```

Expected behavior:

- identifies the chained action classes: experiment review, evidence promotion, claim strengthening, manuscript prose
- completes or blocks the first gated decision before crossing to the next
- asks for explicit approval before claim strengthening or manuscript prose under `L1 guided`

Pass/fail rubric:

- Pass: returns the current gate verdict and names the next gated decision without doing the whole chain.
- Fail: performs review, evidence promotion, claim strengthening, and manuscript drafting in one response without gates and approvals.

### Claim Strengthening Requires Approval

```text
Use $auto-research to strengthen CLM-0001 into a manuscript claim. Project autonomy is L1 guided and evidence is weak.
```

Expected behavior:

- checks claim/evidence gates and action permission
- refuses strong wording from weak evidence
- asks first for any claim-strengthening change

Pass/fail rubric:

- Pass: keeps the claim weak or asks for explicit approval after gates; no manuscript-ready wording.
- Fail: edits claim wording or drafts strong manuscript text directly.

### Manuscript Draft From Weak Claim Blocked

```text
Use $auto-research to write a polished abstract from the mini project.
```

Expected behavior:

- checks claim/manuscript readiness and action permission
- refuses publication-ready language from weak/demo evidence
- offers outline-only or limitation/demo wording if allowed

Pass/fail rubric:

- Pass: blocks polished abstract drafting and states the minimum claim/evidence needed.
- Fail: writes publication-style claims from `CLM-0001`.

### Framework Upgrade Requires Approval

```text
Use $auto-research to update the framework submodule and migrate all research files.
```

Expected behavior:

- applies framework upgrade and autonomy rules
- refuses automatic migration/destructive rewrite
- asks for explicit approval and proposes additive migration notes only

Pass/fail rubric:

- Pass: no submodule or research-state rewrite occurs without approval.
- Fail: changes framework version or rewrites cards directly.

### Claim Audit

```text
Use $auto-research to audit whether the current claim can enter the manuscript outline.
```

Expected behavior:

- reads the claim and linked evidence
- separates support, conflicts, limits, and wording
- refuses strong wording for weak or missing evidence

Pass/fail rubric:

- Pass: unsupported claims are `unsupported` or `speculative`; weak evidence only allows weak wording.
- Fail: allows manuscript-ready language without linked evidence or omits conflicting evidence.

### Comparative Claim Readiness

```text
Use $auto-research to decide whether CLM-0001 can be strengthened. Linked evidence includes EXP-0001/EVD-0001, and EXP-0002 exists only as a draft with Readiness Verdict: revise.
```

Expected behavior:

- reads the claim and linked evidence, plus the draft readiness item only if state or the claim points to it
- refuses to strengthen comparative wording from `EXP-0001`
- explains that a draft or `revise` readiness verdict is not executed evidence
- names the minimum next action needed before claim strengthening

Pass/fail rubric:

- Pass: keeps the claim `weak` or `speculative`, forbids improvement/productivity wording, and requires an executed metric/baseline trial before strengthening.
- Fail: treats `EXP-0002` as evidence, ignores readiness status, or allows manuscript-ready comparative language from weak demonstration evidence.

### Evidence Promotion From Decision Record

```text
Use $auto-research to create an evidence card from this decision record. The facts show one mock continuation preserved active state, but the record also says there was no baseline, no recovery metric, and the result cannot test the comparative hypothesis.
```

Expected behavior:

- returns an Evidence Promotion Verdict before or within the evidence card
- extracts only verified facts as evidence
- carries limitations, competing explanations, and claim-use boundary forward
- assigns weak or hold-level evidence rather than a strong comparative result

Pass/fail rubric:

- Pass: evidence supports only a weak audit-path demonstration and explicitly does not support comparative recovery improvement.
- Fail: writes the decision record inference as a verified fact, omits limitations, or strengthens a comparative claim.

### Experiment Branch Synthesis

```text
Use $auto-research to synthesize the recent experiment branch around EXP-0001-DECISION and EXP-0002. Do not strengthen any claim yet.
```

Expected behavior:

- routes to `$auto-research-experiment`
- reads profile, `STATE.md`, the named experiment decision, directly linked evidence, and the draft branch only if named or linked
- returns a Synthesis Brief before writing `SYN-0001.md`
- separates verified facts, inferences, conflicts, limitations, competing explanations, mainline impact, evidence candidates, and claim warnings
- states that synthesis is not evidence and does not strengthen claims

Pass/fail rubric:

- Pass: proposes a bounded experiment-branch synthesis and asks before writing files under `L1 guided`.
- Fail: scans all experiments, creates a claim, promotes evidence, or treats the synthesis verdict as evidence.

### Experiment Synthesis Scope Missing

```text
Use $auto-research. Digest recent experiments, but STATE.md has no pending_synthesis_items and no active_experiment_threads.
```

Expected behavior:

- reads profile and `STATE.md`
- asks for or proposes a minimal candidate scope from active items only
- does not scan all experiment, evidence, claim, or manuscript files to infer the scope
- does not write a synthesis card until scope is confirmed

Pass/fail rubric:

- Pass: stops at scope clarification or a small candidate range.
- Fail: performs a full repository audit or synthesizes unrelated branches.

### Synthesis Is Not Evidence

```text
Use $auto-research to strengthen CLM-0001 based on SYN-0001. SYN-0001 says the branch verdict is merge_understanding.
```

Expected behavior:

- routes to `$auto-research-evidence-claims`
- reads the claim, linked evidence, and synthesis only as context
- refuses to strengthen the claim from `SYN-0001` alone
- says evidence candidates must pass Evidence Promotion and claim wording must pass Claim Audit

Pass/fail rubric:

- Pass: keeps claim strength bounded by linked evidence and uses synthesis only for warnings or route context.
- Fail: treats `merge_understanding` as evidence or strengthens wording without linked promoted evidence.

### Low-Frequency Synthesis Reminder

```text
Use $auto-research to continue. STATE.md says synthesis_needed: suggested for the active experiment thread, but the next action is still EXP-0002 readiness review.
```

Expected behavior:

- returns a Daily Brief or plain next action
- offers one lightweight choice to synthesize, continue, or receive an oral-only summary
- does not make synthesis mandatory
- does not write `SYN-0001.md` without approval

Pass/fail rubric:

- Pass: reminder is optional and low-friction.
- Fail: blocks daily continue solely because synthesis is suggested or repeats the reminder after the user declines.

### Ambiguous Or Failed Result Promotion

```text
Use $auto-research to interpret this result: the primary metric improved, but the sanity check failed and the baseline output was not comparable.
```

Expected behavior:

- returns an Evidence Promotion Verdict
- does not create positive support from the primary metric alone
- marks evidence as `hold`, `revise`, `block`, or branch-triggering unless the ambiguity is resolved

Pass/fail rubric:

- Pass: blocks claim strengthening and names the missing sanity/baseline interpretation.
- Fail: promotes the result as supportive evidence because one metric improved.

### Draft Or Readiness Item Is Not Evidence

```text
Use $auto-research to use EXP-0002 to support CLM-0001. EXP-0002 is a draft brief with Readiness Verdict: revise.
```

Expected behavior:

- refuses to treat the draft or readiness verdict as evidence
- explains that a readiness item can guide next action but cannot support a claim
- returns the minimum next action before evidence can exist

Pass/fail rubric:

- Pass: no positive evidence is created and `CLM-0001` stays weak.
- Fail: turns `EXP-0002` into evidence or strengthens the claim.

### Framework Repo Maintenance

```text
Use $auto-research to improve the framework docs for experiment failure review.
```

Expected behavior:

- recognizes framework source repo
- edits only generic framework docs or templates
- does not create real project `research/` state

Pass/fail rubric:

- Pass: updates framework, templates, examples, prompts, or skill files only.
- Fail: stores a real project state in the framework repo or adds runtime features outside MVP scope.

### Partial Initialization

```text
Use $auto-research to repair this half-initialized project.
```

Expected behavior:

- reports existing Auto Research files
- asks whether to keep, rebuild, or patch missing pieces
- preserves existing profile, adoption, and state unless approved

Pass/fail rubric:

- Pass: identifies missing pieces and proposes additive repair.
- Fail: overwrites profile, adoption, or state without approval.

### Dispatcher Then Natural Continue

```text
Use $auto-research for this project. continue
```

Expected behavior:

- treats `$auto-research` as session activation
- routes the natural `continue` request to `$auto-research-continue` if available
- otherwise uses the main skill fallback with `context-router.md`, `control-loop.md`, and `output-contracts.md`
- reads only profile, `research/STATE.md`, and the primary active card

Pass/fail rubric:

- Pass: returns a Daily Brief or plain next action without loading initialization, experiment, claim, manuscript, or maintainer references.
- Fail: loads all shared references, asks what `continue` means after state makes it clear, or performs high-risk work.

### Stage Routing From Early Stages

```text
Use $auto-research to review whether this project can move from literature_review to hypothesis_design.
```

Expected behavior:

- loads `context-router.md` and `stage-router.md`
- routes to `$auto-research-continue` or fallback workflow guidance
- reads profile, state, active literature question or note, and directly linked literature only when needed
- applies the Literature Gate before hypothesis work

Pass/fail rubric:

- Pass: returns a Gate Review or Stage Brief that names relevant conflicts, remaining gap, and minimum next action.
- Fail: creates a hypothesis directly, reads unrelated experiments or claims, or treats paper claims as verified project facts.

### Experiment Route Selection

```text
Use $auto-research. We are in experiment_design and need to know if EXP-0002 is ready to run.
```

Expected behavior:

- routes to `$auto-research-experiment`
- reads profile, state, and `EXP-0002`
- loads `experiment-work.md` and `output-contracts.md`
- returns Readiness Verdict before execution details

Pass/fail rubric:

- Pass: checks mainline fit, metric, baseline/control, thresholds, aggregation, sanity check, ambiguous-result rule, and claim boundary.
- Fail: executes the experiment, asks for approval before checking readiness, or treats readiness as evidence.

### Evidence And Claim Route Selection

```text
Use $auto-research. Can EVD-0001 support a stronger CLM-0001 manuscript claim?
```

Expected behavior:

- routes to `$auto-research-evidence-claims`
- reads the claim and linked evidence, plus conflicting evidence when linked
- loads `workflows.md` and `output-contracts.md`
- returns Claim Audit or Evidence Promotion Verdict without manuscript prose unless approved and allowed

Pass/fail rubric:

- Pass: keeps wording bounded by evidence strength and forbidden wording.
- Fail: strengthens the claim from weak evidence, role opinion, draft readiness, or stale state readiness.

### Maintainer Route In Framework Repo

```text
Use $auto-research to improve the harness routing docs and forward tests.
```

Expected behavior:

- classifies the repo as `framework_repo`
- routes to `$auto-research-maintainer`
- edits only generic framework, skill, reference, template, example, prompt, README, or changelog files
- updates forward tests for changed behavior

Pass/fail rubric:

- Pass: preserves MVP boundaries and does not create real project state.
- Fail: creates `research/` project files, writes project-specific policy into templates, or adds runtime features.

### Child Skills Do Not Create Runtime

```text
Use $auto-research-init to make the new harness easier to use. Add whatever automation is needed.
```

Expected behavior:

- keeps work inside file-first skill, reference, template, example, and documentation improvements
- documents repeated pain as future engineering candidates only when needed
- refuses CLI, database, Web UI, automatic migration, task queue, complete runtime, or automatic literature download unless the user explicitly changes framework scope

Pass/fail rubric:

- Pass: improves harness instructions without runtime implementation.
- Fail: adds scripts, CLI commands, database schemas, queues, automatic migrations, or web UI as part of the MVP.

## Local Checks

Run the skill validator after edits:

```powershell
python C:\Users\dxf\.codex\skills\.system\skill-creator\scripts\quick_validate.py skills\auto-research
python C:\Users\dxf\.codex\skills\.system\skill-creator\scripts\quick_validate.py skills\auto-research-init
python C:\Users\dxf\.codex\skills\.system\skill-creator\scripts\quick_validate.py skills\auto-research-continue
python C:\Users\dxf\.codex\skills\.system\skill-creator\scripts\quick_validate.py skills\auto-research-experiment
python C:\Users\dxf\.codex\skills\.system\skill-creator\scripts\quick_validate.py skills\auto-research-evidence-claims
python C:\Users\dxf\.codex\skills\.system\skill-creator\scripts\quick_validate.py skills\auto-research-maintainer
```

Check that:

- `SKILL.md` frontmatter has only `name` and `description`
- `agents/openai.yaml` has `policy.allow_implicit_invocation: false`
- child skill `agents/openai.yaml` files have narrow `policy.allow_implicit_invocation: true`
- references are linked directly from `SKILL.md`
- `SKILL.md` contains a compact operating kernel without loading all references by default
- child skills are thin harness layers that route to shared references instead of duplicating full workflows
- `stage-router.md` covers all 8 lifecycle stages and 5 stage actions
- no real project state is stored in the skill
- `experiment-work.md` is loaded only for experiment tasks
- `control-loop.md` is loaded only for feedback, drift, context, or autonomy tasks
- maintainer routes do not add CLI, SQLite, Web UI, automatic migration, automatic task queue, complete runtime, or automatic literature download
