# Submodule Adoption

Concrete research projects should consume this framework as a git submodule.

## Add Framework To A Project

Use the exact framework URL chosen by the user or project. Do not switch between SSH and HTTPS automatically.

From the consumer project root:

```powershell
git submodule add <framework-url> .auto_research/framework
git submodule update --init --recursive
```

Then create local project files outside the submodule:

```text
.auto_research/
  PROJECT_PROFILE.md
  TEAM_PROFILE.md     # optional project-specific role/advisor profile
  ADOPTION.md
research/
  STATE.md
  ideas/
  literature/
  hypotheses/
  experiments/
  evidence/
  claims/
  manuscripts/
```

## Ownership Rules

- `.auto_research/framework/`: framework submodule; edit in the framework repo, not as local project state.
- `.auto_research/PROJECT_PROFILE.md`: project-specific rules.
- `.auto_research/TEAM_PROFILE.md`: optional project-specific role adaptations and advisory roles.
- `.auto_research/ADOPTION.md`: framework adoption and upgrade record.
- `research/`: actual project state and artifacts.

## Upgrade Workflow

1. Enter `.auto_research/framework`.
2. Fetch or checkout the desired framework commit or tag.
3. Return to the consumer project root.
4. Commit the changed submodule pointer.
5. Update `.auto_research/ADOPTION.md`.
6. Add migration notes if templates or gates changed.

Existing research cards must not be rewritten automatically. Add revision notes only.

## ADOPTION.md Minimum Fields

```yaml
framework_source:
framework_commit:
adopted_at:
local_project:
local_profile:
upgrade_history:
known_incompatibilities:
migration_notes:
```

## Feeding Improvements Back

- Local-only behavior belongs in `PROJECT_PROFILE.md`.
- Project-specific role background belongs in `TEAM_PROFILE.md` when the project uses team calibration.
- Cross-project lessons should become framework issues or framework changes.
- Repeated manual steps may become scripts or CLI commands later.
