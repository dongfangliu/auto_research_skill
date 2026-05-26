---
name: auto-research-evidence-claims
description: Thin Auto Research evidence and claim harness. Use only after $auto-research is active or when the user explicitly invokes $auto-research-evidence-claims, asks Auto Research to promote evidence, audit claims, strengthen wording, check evidence boundaries, or assess manuscript readiness.
---

# Auto Research Evidence Claims

## Purpose

Bind results, synthesis context, evidence cards, claims, allowed wording, forbidden wording, and manuscript readiness without overstating what the evidence supports.

## Applicable Stages

- Applicable stage: `result_analysis`, `claim_building`, and `manuscript_drafting`.
- Trigger condition: the user asks to turn a result into evidence, consume synthesis evidence candidates, audit a claim, strengthen a claim, decide whether wording is allowed, or draft from claim cards after `$auto-research` is active or by invoking `$auto-research-evidence-claims`.
- Failure risk: treating drafts, readiness verdicts, handoffs, synthesis cards, PI opinions, or ambiguous results as positive evidence; strengthening claims beyond linked evidence; drafting manuscript prose from weak claims.

## Minimum Context

1. Read local `AGENTS.md` or equivalent.
2. Load shared `../auto-research/references/context-router.md`.
3. For evidence work, read the source decision/result/literature note and any linked evidence card.
4. For synthesis-informed evidence work, read only the synthesis evidence candidates and their directly named source records.
5. For claim work, read the claim card, linked supporting evidence, linked conflicting evidence, and state only when readiness or active priority matters.
6. For synthesis-informed claim work, read claim warnings and mainline impact, but verify all claim strength against linked evidence.
7. Read experiment records only when the evidence boundary depends on experiment interpretation.
8. Read `.auto_research/TEAM_PROFILE.md` only when claim review needs project-specific role background or an explicitly named advisor.

## Reference Loading

- Load `../auto-research/references/workflows.md` for result-to-evidence, claim, and manuscript workflows.
- Load `../auto-research/references/output-contracts.md` for Evidence Promotion Verdict, Claim Audit, Gate Review, or Plain Research Reply.
- Load `templates/evidence_card.md`, `templates/claim_card.md`, `templates/synthesis_card.md`, or `templates/manuscript_outline.md` only when creating or checking those artifacts.
- Load `../auto-research/references/experiment-work.md` only if the claim depends on experiment details that the evidence card does not already summarize.
- Load `framework/workflow_gates.md` when exact gate criteria are needed.

## Workflow

1. Separate verified facts from inferences, limitations, competing explanations, and next steps.
2. Treat synthesis cards as routing and interpretation context only.
3. Before creating or upgrading evidence, run Result-to-Evidence review and assign allowed/forbidden wording.
4. Before strengthening a claim, check linked evidence, conflicting evidence, evidence strength, metric/baseline readiness for comparative wording, and Action Permission.
5. Before manuscript work, map sections to claim cards and omit or mark weak/speculative claims as tentative.
6. Keep role opinions and synthesis verdicts as review input only; they do not create evidence or strengthen claims.
7. Stop at the first missing evidence boundary or permission issue and name the minimum next action.

## Blocked Actions

- Do not use draft briefs, readiness verdicts, handoffs, PI opinions, or unreviewed decision records as claim-supporting evidence.
- Do not use synthesis cards as claim-supporting evidence.
- Do not promote ambiguous, failed, deviated, or sanity-check-failed results as positive support without resolving the ambiguity.
- Do not strengthen claims under `L1 guided` without explicit approval after gates pass.
- Do not produce publication-ready manuscript prose from weak, speculative, unsupported, or contradicted claims.
- Do not let team or advisor consensus substitute for evidence.

## Output Contract

Use `Evidence Promotion Verdict` before evidence affects a claim. Use `Claim Audit` for claim strength and wording. Use `Gate Review` for manuscript readiness or blocked transitions. Use `Plain Research Reply` when the user only needs a short wording boundary. When starting from a synthesis card, consume only `Evidence Candidates`, `Claim Warnings`, and `Mainline Impact`; route missing experiment interpretation back to `$auto-research-experiment`.
