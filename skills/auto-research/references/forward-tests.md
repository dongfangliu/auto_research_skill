# Forward Tests

Use these prompts when maintaining this skill. They are not user-facing workflow docs.

## Validation Principle

Forward tests should ask another agent to use the skill naturally. Pass raw artifacts and the user-like request, not the expected answer or your diagnosis.

Do not run forward tests when they would modify live project state without user approval. Prefer disposable copies or read-only review prompts.

## Test Prompts

### Uninitialized Consumer Repo

```text
Use $auto-research to initialize this research repository. First do read-only discovery and produce an Alignment Brief. Do not create or modify files yet.
```

Expected behavior:

- reads local rules and project files first
- classifies the repo as uninitialized or partial
- asks only preference or policy questions
- does not write files before approval

### Initialized Consumer Continue

```text
Use $auto-research to continue this project. Tell me the next research action.
```

Expected behavior:

- reads profile and `research/STATE.md`
- reads only active cards needed by state
- returns a Stage Brief with risks and next action

### Claim Audit

```text
Use $auto-research to audit whether the current claim can enter the manuscript outline.
```

Expected behavior:

- reads the claim and linked evidence
- separates support, conflicts, limits, and wording
- refuses strong wording for weak or missing evidence

### Framework Repo Maintenance

```text
Use $auto-research to improve the framework docs for experiment failure review.
```

Expected behavior:

- recognizes framework source repo
- edits only generic framework docs or templates
- does not create real project `research/` state

### Partial Initialization

```text
Use $auto-research to repair this half-initialized project.
```

Expected behavior:

- reports existing Auto Research files
- asks whether to keep, rebuild, or patch missing pieces
- preserves existing profile, adoption, and state unless approved

## Local Checks

Run the skill validator after edits:

```powershell
python C:\Users\dxf\.codex\skills\.system\skill-creator\scripts\quick_validate.py skills\auto-research
```

Check that:

- `SKILL.md` frontmatter has only `name` and `description`
- `agents/openai.yaml` has `policy.allow_implicit_invocation: false`
- references are linked directly from `SKILL.md`
- no real project state is stored in the skill
