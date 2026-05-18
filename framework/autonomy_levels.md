# Autonomy Levels

Each project should declare an autonomy level in its project profile.

## L0 manual

Agents organize, summarize, and suggest. They do not decide next steps or modify research artifacts without explicit instruction.

## L1 guided

Agents propose plans and wait for human approval before executing meaningful research steps. This is the MVP default.

## L2 delegated

Agents may execute low-risk tasks without approval, such as creating draft cards, summarizing known notes, or updating state. High-risk gates still require approval.

## L3 autonomous_draft

Agents may proceed through multiple research stages and produce manuscript drafts. All claims must remain evidence-labeled and publication readiness is not implied.

## L4 publication_ready

Future target only. Requires mature audit, reproducibility, statistics, ethics, and publication review infrastructure. MVP projects should not use this level.

## High-Risk Actions

The following require human approval unless the project profile explicitly says otherwise:

- Changing research direction.
- Launching expensive or long-running experiments.
- Replacing core hypotheses.
- Recommending final claims.
- Producing publication-ready language.
- Updating framework submodule version in a consumer project.

