# Research State: Mini Project

```yaml
project_id: mini_project
framework_commit: mvp-0.1-example
updated_at: 2026-05-18
active_stage: claim_building
active_items:
  - CLM-0001
next_recommended_action: Run a second recovery trial before strengthening any claim.
```

## Snapshot

The project started with an idea that structured research cards may help agents resume interrupted work. A first mock experiment partially supported the workflow but exposed an unmeasured failure mode: recovery quality needs an explicit metric. This generated a branch idea, `IDEA-0002`.

## Active Items

| ID | Type | Status | Current Question | Next Action |
| --- | --- | --- | --- | --- |
| CLM-0001 | claim | draft | What can be safely claimed from one mock trial? | Keep wording weak and request another trial. |
| IDEA-0002 | idea | active | Should recovery quality become a first-class metric? | Create a hypothesis or experiment around recovery scoring. |

## Paused Or Blocked Items

| ID | Type | Status | Blocker | Resume Condition |
| --- | --- | --- | --- | --- |
| HYP-0001 | hypothesis | paused | Only one simulated trial exists. | Resume after at least one additional task type is tested. |

## Branch Relationships

| Child | Branch From | Reason |
| --- | --- | --- |
| IDEA-0002 | EXP-0001-DECISION | Experiment exposed an unmeasured recovery-quality variable. |

## Evidence And Claim Readiness

| Claim | Evidence Level | Readiness | Risk |
| --- | --- | --- | --- |
| CLM-0001 | weak | Outline-only | Based on one mock example. |

## Manuscript Readiness

Ready only for a demonstration outline, not a publication draft.

## Open Risks

- Recovery quality is not yet measured quantitatively.
- The current example may overfit to agent-readable Markdown workflows.

## Latest Decisions

- Preserve `HYP-0001` as paused.
- Create `IDEA-0002` to make recovery quality a first-class object.
- Keep `CLM-0001` weak.

