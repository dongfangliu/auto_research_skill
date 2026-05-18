# Project Profile: Research Continuity Mini Project

```yaml
project_id: mini_project
project_name: Research Continuity Mini Project
autonomy_level: L1 guided
default_language: English
framework_commit: mvp-0.1-example
updated_at: 2026-05-18
```

## Project Identity

This mini project explores whether structured research cards help agents resume interrupted research tasks with fewer missing context errors.

## Research Goal

Create a small demonstration trail that tests whether a structured state file plus linked cards improves task resumption.

## Research Boundaries

This example does not claim statistical validity, real human productivity improvement, or publication-ready evidence.

## Claim Boundaries

Do not claim that the framework improves all research workflows. Only claim that this example demonstrates a plausible audit path and highlights the need for a recovery metric.

## Required Context

- `STATE.md`
- Relevant card files linked from `STATE.md`
- Framework lifecycle and state model

## Artifact Policy

Use manual IDs. Do not rewrite earlier cards; append revision notes.

## Evidence Standards

- Weak: single simulated trial or qualitative observation.
- Moderate: repeated trials across different task types.
- Strong: controlled evaluation with independent raters or quantitative recovery metrics.

## Agent Policy

- New experiment: student-executor + pi-reviewer.
- Failure review: student-executor + pi-reviewer.
- Claim recommendation: pi-reviewer + claim-auditor.
- Manuscript: writing-agent + claim-auditor + pi-reviewer.

## Blocked Moves

- Do not turn the example into a real empirical claim.
- Do not write publication-ready language from the current evidence.

## Publish Standards

At least moderate evidence is required before writing a real paper draft. This example may only produce a manuscript outline.

## Profile Update Triggers

Update if a new card type is required or if recovery metrics become central.

