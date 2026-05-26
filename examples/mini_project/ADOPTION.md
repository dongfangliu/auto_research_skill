# Adoption Record: Mini Project

```yaml
framework_source: auto_research local example
framework_commit: mvp-0.13-example
adopted_at: 2026-05-18
local_project: mini_project
local_profile: PROJECT_PROFILE.md
upgrade_history: []
known_incompatibilities:
  - This example is not a real empirical project.
migration_notes:
  - Initial example created directly inside the framework repo.
```

## Current Framework Version

This example uses the `mvp-0.13` team profile shape.

## Adoption Reason

Demonstrate a complete research trail without requiring a real consumer project.

## Local Integration

The example keeps profile, team profile, state, and cards directly under `examples/mini_project/`.

## Upgrade History

| Date | Old Commit | New Commit | Reason | Migration Needed |
| --- | --- | --- | --- | --- |
| 2026-05-18 | none | mvp-0.1-example | Initial example | No |
| 2026-05-26 | mvp-0.1-example | mvp-0.4-example | Demonstrate Daily Brief and primary active item discipline | Additive state/profile notes only |
| 2026-05-26 | mvp-0.4-example | mvp-0.5-example | Demonstrate metric/baseline readiness before experiment execution | Add `HYP-0002` and draft `EXP-0002`; keep `EXP-0001` historical |
| 2026-05-26 | mvp-0.5-example | mvp-0.6-example | Demonstrate feedback intake and handoff trace | Add `HANDOFF-0001` and `last_user_correction`; no experiment execution |
| 2026-05-26 | mvp-0.6-example | mvp-0.7-example | Demonstrate result-to-evidence promotion boundaries | Add promotion verdict to `EVD-0001`; no claim strengthening |
| 2026-05-26 | mvp-0.7-example | mvp-0.8-example | Demonstrate resume consistency before action | Add state consistency fields and handoff resume readiness |
| 2026-05-26 | mvp-0.8-example | mvp-0.9-example | Demonstrate action permission and blocked moves | Add blocked moves today and Action Permission example; no execution |
| 2026-05-26 | mvp-0.9-example | mvp-0.13-example | Demonstrate optional team profile and advisor boundary | Add `TEAM_PROFILE.md` and an advisory Role Report; no execution or claim strengthening |

## Known Incompatibilities

- No real submodule pointer exists inside the example.
- No real literature review was performed.

## Migration Notes

- `STATE.md` now records `primary_active_item`, `primary_active_path`, current risk, parking lot, and last mainline check for daily continue.
- `EXP-0002` is a draft readiness example, not an executed experiment.
- `HANDOFF-0001` records the correction that the next session should review readiness only.
- `EVD-0001` records that `EXP-0001` supports only weak audit-path wording.
- State records consistency fields so daily continue can stop at minimal context.
- State records blocked moves today so next action is not mistaken for permission.
- `TEAM_PROFILE.md` demonstrates `advisor:recovery-evaluator` as review input only.
- Historical cards were not rewritten.
