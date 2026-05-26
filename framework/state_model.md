# State Model

The framework uses Markdown cards with structured headers. Cards are human-readable, git-friendly, and easy for agents to resume from.

## Common Header

Every card should start with this header:

```yaml
id:
type:
status:
created_at:
updated_at:
parent:
branch_from:
linked_items:
owner_agent:
evidence_level:
confidence:
next_action:
```

## Status Values

- `draft`: created but not yet reviewed.
- `active`: currently being worked on.
- `paused`: intentionally stopped but may resume.
- `blocked`: cannot continue without external input or missing artifact.
- `revised`: superseded by a later version, but still retained.
- `rejected`: judged not worth pursuing under current evidence.
- `accepted`: accepted for the current project stage.
- `archived`: retained for provenance but no longer active.

## Evidence Levels

- `none`: no supporting evidence yet.
- `speculative`: plausible but unsupported.
- `weak`: limited or indirect support.
- `moderate`: reproducible or convergent support with known limits.
- `strong`: robust support across relevant checks.
- `contradicted`: evidence currently argues against the item.

## STATE.md Responsibilities

`STATE.md` is the project dashboard. It should show:

- Active items.
- Paused or blocked items.
- Branch relationships.
- Current risks.
- Next recommended action.
- Claim readiness.
- Manuscript readiness.
- Current framework commit or version.

`STATE.md` should summarize; it should not replace detailed cards.

## Synthesis Pointers

Experiment synthesis cards summarize a bounded experiment thread after one or more experiment decisions or experiment-derived evidence cards exist. `STATE.md` should keep only pointers and short status fields:

- `latest_synthesis`: most recent `SYN-0000` card relevant to the current mainline.
- `pending_synthesis_items`: experiment decisions or evidence that may need synthesis.
- `active_experiment_threads`: current experiment branches or batches.
- `synthesis_needed`: `none`, `suggested`, `requested`, or `completed`.
- `mainline_impact_from_latest_synthesis`: one-sentence impact summary.

Synthesis cards do not replace evidence cards, claim cards, or detailed experiment records.

## ID Policy

MVP uses manually assigned IDs:

- `IDEA-0001`
- `LQ-0001`
- `LIT-0001`
- `HYP-0001`
- `EXP-0001`
- `EVD-0001`
- `SYN-0001`
- `CLM-0001`
- `OUTLINE-0001`

If manual IDs become error-prone, add a lightweight CLI later.
