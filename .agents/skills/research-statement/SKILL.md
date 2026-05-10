---
name: research-statement
description: Draft and revise Nhat-Minh Nguyen's JPL Roman/Euclid Scientist IV and Scientist II research statements. Use for high-stakes research statement planning, drafting, polishing, and auditing when the work involves `jpl-applications/jpl_application_pack/`, Roman/Euclid weak lensing and galaxy clustering, field-level or forward-modeling inference, dark-sector cosmology, or the R5541/R5540 JPL roles.
---

# Research Statement

## Scope

This is a repo-local skill for Nhat-Minh Nguyen's JPL Roman/Euclid application materials. It is not a generic faculty research statement skill.

Use it to create a full drafting packet for:

- `R5541 Scientist IV`
- `R5540 Scientist II`

## Required Skill Chain

When available, invoke these skills in this order:

1. `superpowers:writing-plans` for the execution plan.
2. `literature-review` during planning, limited to a focused scan.
3. `superpowers:executing-plans` or `superpowers:subagent-driven-development` for execution.
4. `latex-paper-en` for LaTeX statement drafting, compilation, and source-aware writing checks.
5. `prose-style` after structure is stable.
6. `humanizer` after prose-style, using Minh's homepage/Kakenhi/blog voice samples when available.
7. `paper-audit` for reviewer-style audit before finalizing.
8. `superpowers:verification-before-completion` before any completion claim.

If a required skill is unavailable, state the missing skill and continue with the closest fallback. Do not silently skip the stage.

## Source Hierarchy

Read local sources first:

1. `jpl-applications/jpl_application_pack/agent_prompt.md`
2. `jpl-applications/jpl_application_pack/README_for_agent.md`
3. `jpl-applications/jpl_application_pack/research_statement_outline.md`
4. `CONTEXT.md`
5. current CV/application materials in this repository

Use online lookup only for targeted checks related to:

- Nhat-Minh Nguyen's public materials;
- R5541/R5540 job descriptions;
- Roman/Euclid job-specific context;
- weak lensing plus galaxy clustering specifics directly needed for the statement.

Do not run a broad cosmology literature review unless the user explicitly asks.

## Output Contract

The default output is a drafting packet, not only a prose draft.

Markdown planning artifacts:

- focused literature scan memo;
- role-fit matrix;
- high-risk claim ledger;
- statement outline;
- audit and polish notes;
- TODO before submission.

LaTeX statement drafts:

- `jpl-applications/jpl-research-mentoring-statement/research_statement_R5541_Scientist_IV.tex`
- `jpl-applications/jpl-research-mentoring-statement/research_statement_R5540_Scientist_II.tex`

Use `jpl-applications/jpl-research-mentoring-statement/main.tex` as the template source. Do not overwrite `main.tex` unless the user explicitly asks.

## Role Routing

Before drafting, identify the target role. If the user does not specify a role, ask whether to draft Scientist IV, Scientist II, or both.

For role-specific structure and emphasis, read `references/role-branches.md`.

For required artifacts and file naming, read `references/output-packet.md`.

For final checks and overclaim risks, read `references/audit-checklists.md`.

## Hard Gates

No completion claim until all relevant gates pass:

- LaTeX builds successfully.
- Scientist IV PDF is no more than 5 pages.
- Scientist II PDF is no more than 4 pages.
- High-risk claim ledger exists before drafting.
- `paper-audit` has been run or its absence has been explicitly reported.
- Superpowers verification has been run fresh in the same turn.
