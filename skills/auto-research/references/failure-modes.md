# Failure Modes

Use this reference when behavior feels ambiguous or risky.

## Real Project State In Framework Repo

Risk: writing actual research progress into the framework source repository.

Guardrail: in `framework_repo`, edit only generic framework files, templates, examples, prompts, or skill files. Real research state belongs in consumer repo `research/`.

## Loading Too Much Context

Risk: reading the full framework and all cards for a small task.

Guardrail: read `context-router.md`, then only the task-specific reference and active files from `STATE.md`.

## Asking Discoverable Questions

Risk: asking where the profile, state, templates, or active item are before searching.

Guardrail: inspect the repository first. Ask only preference, policy, or direction questions after discovery.

## Overwriting History

Risk: replacing old cards, decisions, experiment records, or manuscript notes.

Guardrail: append a revision, branch, or migration note. Preserve old wording unless the user explicitly asks for a destructive cleanup.

## Overclaiming

Risk: turning weak evidence into strong claims or manuscript-ready language.

Guardrail: keep facts, inferences, limitations, and competing explanations separate. Mark unsupported claims as `speculative`; bind every claim to evidence before manuscript use.

## Premature Multi-Agent Work

Risk: spawning or simulating many roles for routine organization.

Guardrail: default to one orchestrator. Add roles only for experiments, failures, claim/manuscript work, or framework upgrades.

## Runtime Creep

Risk: adding CLI, databases, task queues, migrations, or web UI while trying to improve the file-first MVP.

Guardrail: document repeated pain as a future candidate. Do not implement runtime unless the user explicitly changes scope.

## Consumer Upgrade Damage

Risk: changing submodule pointer or templates and silently rewriting existing cards.

Guardrail: record framework commits in `ADOPTION.md`, summarize changes, and add migration notes. Existing research cards remain intact.

## Weak Initialization

Risk: copying templates into a project before understanding it.

Guardrail: produce an Alignment Brief first, confirm project identity and policy choices, then present an implementation plan before writing files.
