# Research Statement Skill Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Create a repo-local `research-statement` skill for drafting and auditing JPL Roman/Euclid Scientist IV and Scientist II research statements for Nhat-Minh Nguyen.

**Architecture:** The skill lives under `.agents/skills/research-statement/`. `SKILL.md` contains the trigger rules and core workflow; focused reference files hold role-branch details, output packet requirements, and audit checklists. The skill must produce Markdown planning/review artifacts and LaTeX role-specific statement drafts derived from `jpl-applications/jpl-research-mentoring-statement/main.tex`.

**Tech Stack:** Codex skills (`SKILL.md`), Markdown references, LaTeX (`latexmk`), repository-local JPL application files, Superpowers workflow skills, `literature-review`, `latex-paper-en`, `prose-style`, `humanizer`, and `paper-audit`.

---

## Files

- Create: `.agents/skills/research-statement/SKILL.md`
- Create: `.agents/skills/research-statement/references/role-branches.md`
- Create: `.agents/skills/research-statement/references/output-packet.md`
- Create: `.agents/skills/research-statement/references/audit-checklists.md`
- Modify only if validation reveals drift: `CONTEXT.md`

Do not create global files under `/Users/nguyenmn/.codex/skills/`. This is a repo-local skill.

## Task 1: Create the Skill Skeleton

**Files:**
- Create: `.agents/skills/research-statement/SKILL.md`

- [ ] **Step 1: Create the skill directory**

Run:

```bash
mkdir -p .agents/skills/research-statement/references
```

Expected: directory exists at `.agents/skills/research-statement/`.

- [ ] **Step 2: Add `SKILL.md`**

Create `.agents/skills/research-statement/SKILL.md` with this content:

```markdown
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
```

- [ ] **Step 3: Verify skeleton trigger coverage**

Run:

```bash
rg -n "research-statement|R5541|R5540|Scientist IV|Scientist II|Required Skill Chain|Output Contract|Hard Gates" .agents/skills/research-statement/SKILL.md
```

Expected: every searched phrase appears in `SKILL.md`.

## Task 2: Add Role Branch Reference

**Files:**
- Create: `.agents/skills/research-statement/references/role-branches.md`

- [ ] **Step 1: Create `role-branches.md`**

Create `.agents/skills/research-statement/references/role-branches.md` with this content:

```markdown
# Role branches

## Scientist IV: R5541

Use this branch when drafting or revising `research_statement_R5541_Scientist_IV.tex`.

Core posture:

- candidate can help lead and coordinate Roman/Euclid joint-probe cosmology;
- strategic scientific leadership, not only technical contribution;
- nonlinear modeling, systematics strategy, cross-survey calibration, and dark-sector interpretation;
- mentoring, coordination, JPL representation, and mission-scale deliverables.

Required five-section structure:

1. Research vision.
2. Preparation: growth, field-level inference, and survey realism.
3. Proposed JPL research program.
4. Scientist IV leadership and execution plan.
5. Collaboration, mentoring, and inclusive team science.

Scientist IV page gate:

- compiled PDF must be no more than 5 pages.

## Scientist II: R5540

Use this branch when drafting or revising `research_statement_R5540_Scientist_II.tex`.

Core posture:

- high-impact contributor with an emerging independent niche;
- technical execution and collaborative integration;
- nonlinear modeling, likelihood/model validation, weak lensing plus clustering interpretation;
- focused independent contribution without junior/passive framing.

Required four-section structure:

1. Research vision.
2. Preparation: methods and science background.
3. Proposed JPL contribution.
4. Three-year integration and independent niche.

Scientist II page gate:

- compiled PDF must be no more than 4 pages.

## Shared scientific thesis

Use this thesis, adapted to the role:

> I develop field-level and forward-modeling methods that help galaxy surveys extract robust dark-sector information from weak lensing and clustering, with applications to cosmic growth, gravity, dark energy, and primordial physics.

## Positioning guardrails

Allowed:

- "I contributed to evidence for late-time suppression in the growth of large-scale structure."
- "I developed field-level Bayesian inference methods for galaxy surveys."
- "This work was recognized by the 2024 Buchalter Cosmology Prize."
- "Field-level inference can validate, stress-test, and extend mission-ready summary-statistic analyses."

Avoid:

- claiming to have invented field-level inference;
- implying sole credit for the growth suppression result;
- implying Roman/Euclid internal mission membership unless sourced;
- making every proposed analysis sound fully field-level;
- weakening Scientist II into a passive or junior role.
```

- [ ] **Step 2: Verify role branch content**

Run:

```bash
rg -n "five-section|four-section|5 pages|4 pages|do not|Avoid|Buchalter|growth suppression|field-level" .agents/skills/research-statement/references/role-branches.md
```

Expected: role structure, page gates, and guardrails are present.

## Task 3: Add Output Packet Reference

**Files:**
- Create: `.agents/skills/research-statement/references/output-packet.md`

- [ ] **Step 1: Create `output-packet.md`**

Create `.agents/skills/research-statement/references/output-packet.md` with this content:

```markdown
# Output packet

All planning and review artifacts are Markdown. The submission draft is LaTeX.

## Planning artifacts

Create artifacts under:

`jpl-applications/jpl_application_pack/research_statement_work/`

Use these filenames:

- `focused_literature_scan.md`
- `role_fit_matrix_R5541_Scientist_IV.md`
- `role_fit_matrix_R5540_Scientist_II.md`
- `high_risk_claim_ledger.md`
- `outline_R5541_Scientist_IV.md`
- `outline_R5540_Scientist_II.md`
- `polish_notes.md`
- `paper_audit_summary.md`
- `TODO_before_submission.md`

Create only the role-specific files needed for the requested role(s).

## LaTeX drafts

Use:

- `jpl-applications/jpl-research-mentoring-statement/research_statement_R5541_Scientist_IV.tex`
- `jpl-applications/jpl-research-mentoring-statement/research_statement_R5540_Scientist_II.tex`

Use `jpl-applications/jpl-research-mentoring-statement/main.tex` as the template source. Preserve local class/style dependencies.

## Focused literature scan

Use `literature-review` as a focused evidence scan, not a systematic review.

Cover only:

- Minh's relevant research anchors;
- job research themes;
- weak lensing plus galaxy clustering specifics;
- Roman/Euclid specifics needed for the statement;
- OpenUniverse/simulation validation only when role-relevant.

Do not create PRISMA diagrams or broad literature-review figures for this application statement workflow.

## High-risk claim ledger

Required before drafting. Include columns:

| Claim category | Safe wording | Avoid wording | Source | Role applicability |
| --- | --- | --- | --- | --- |

Required categories:

- growth suppression;
- Buchalter Prize;
- field-level inference contribution;
- weak-lensing bridge;
- Roman/Euclid fit;
- OpenUniverse or simulation-validation relevance;
- PI grants or leadership;
- mentoring and organizing;
- DESI/PFS/HSC or other survey affiliations.
```

- [ ] **Step 2: Verify output contract**

Run:

```bash
rg -n "research_statement_work|focused_literature_scan|high_risk_claim_ledger|research_statement_R5541|research_statement_R5540|main.tex|PRISMA" .agents/skills/research-statement/references/output-packet.md
```

Expected: artifact paths, role-specific TeX files, template rule, and PRISMA exclusion are present.

## Task 4: Add Audit Checklist Reference

**Files:**
- Create: `.agents/skills/research-statement/references/audit-checklists.md`

- [ ] **Step 1: Create `audit-checklists.md`**

Create `.agents/skills/research-statement/references/audit-checklists.md` with this content:

```markdown
# Audit checklists

## Pre-drafting checklist

- [ ] Application pack read.
- [ ] `CONTEXT.md` read.
- [ ] Target role selected.
- [ ] Focused literature scan completed.
- [ ] Role-fit matrix completed.
- [ ] High-risk claim ledger completed.
- [ ] Outline completed.

## Drafting checklist

- [ ] Role-specific section structure followed.
- [ ] Statement draft written in role-specific `.tex` file.
- [ ] `main.tex` was not overwritten unless explicitly requested.
- [ ] Scientist IV uses leadership/coordination/mentoring language.
- [ ] Scientist II uses high-impact contributor language without passive or junior framing.
- [ ] Field-level inference is framed as validation, information accounting, and next-generation likelihood support.
- [ ] Weak lensing bridge is explicit through galaxy shapes, intrinsic alignments, matter clustering, cross-probe covariance, or joint lensing-clustering inference.

## Polish checklist

- [ ] `latex-paper-en` used for LaTeX-aware writing and compile checks.
- [ ] `prose-style` used after structure is stable.
- [ ] `humanizer` used with Minh's writing samples when available.
- [ ] Visible prose avoids generic AI tells: "crucial", "pivotal", "underscores", "serves as", "stands as", "delve", "landscape", "not only ... but", and mechanical rule-of-three phrasing.

## Audit checklist

- [ ] `paper-audit` run on the statement source or PDF.
- [ ] Major findings summarized in Markdown.
- [ ] High-risk claim ledger checked against final draft.
- [ ] Page gate checked with compiled PDF.
- [ ] Superpowers verification-before-completion run fresh before final status.

## Page gates

- Scientist IV: `pdfinfo <pdf>` must report no more than 5 pages.
- Scientist II: `pdfinfo <pdf>` must report no more than 4 pages.
```

- [ ] **Step 2: Verify audit checklist**

Run:

```bash
rg -n "Pre-drafting|Drafting|Polish|paper-audit|latex-paper-en|prose-style|humanizer|verification-before-completion|pdfinfo" .agents/skills/research-statement/references/audit-checklists.md
```

Expected: each phase and required skill appears.

## Task 5: Validate the Skill Package

**Files:**
- Read: `.agents/skills/research-statement/SKILL.md`
- Read: `.agents/skills/research-statement/references/role-branches.md`
- Read: `.agents/skills/research-statement/references/output-packet.md`
- Read: `.agents/skills/research-statement/references/audit-checklists.md`

- [ ] **Step 1: Verify required files exist**

Run:

```bash
test -f .agents/skills/research-statement/SKILL.md
test -f .agents/skills/research-statement/references/role-branches.md
test -f .agents/skills/research-statement/references/output-packet.md
test -f .agents/skills/research-statement/references/audit-checklists.md
```

Expected: all commands exit with code 0.

- [ ] **Step 2: Verify required workflow skills are named**

Run:

```bash
rg -n "superpowers:writing-plans|literature-review|superpowers:executing-plans|superpowers:subagent-driven-development|latex-paper-en|prose-style|humanizer|paper-audit|verification-before-completion" .agents/skills/research-statement
```

Expected: every required workflow skill appears at least once.

- [ ] **Step 3: Verify role-specific output paths are named**

Run:

```bash
rg -n "research_statement_R5541_Scientist_IV|research_statement_R5540_Scientist_II|jpl-applications/jpl-research-mentoring-statement/main.tex|jpl-applications/jpl_application_pack/research_statement_work" .agents/skills/research-statement
```

Expected: role-specific TeX output paths, template path, and Markdown work directory appear.

- [ ] **Step 4: Verify context consistency**

Run:

```bash
rg -n "Research Statement Skill|Drafting Packet|High-Risk Claim Ledger|Page Gate|Repo-Local Skill|Skill Implementation Plan" CONTEXT.md
```

Expected: all resolved domain terms appear in `CONTEXT.md`.

- [ ] **Step 5: Check git diff**

Run:

```bash
git diff -- .agents/skills/research-statement CONTEXT.md docs/superpowers/plans/2026-05-11-research-statement-skill.md
```

Expected: diff shows only the new research-statement skill files, this plan, and the accepted context terms.

## Task 6: Commit Checkpoint

**Files:**
- Stage: `.agents/skills/research-statement/`
- Stage: `CONTEXT.md`
- Stage: `docs/superpowers/plans/2026-05-11-research-statement-skill.md`

- [ ] **Step 1: Run whitespace check**

Run:

```bash
git diff --check
```

Expected: no output and exit code 0.

- [ ] **Step 2: Stage files**

Run:

```bash
git add .agents/skills/research-statement CONTEXT.md docs/superpowers/plans/2026-05-11-research-statement-skill.md
```

Expected: files are staged.

- [ ] **Step 3: Inspect staged stat**

Run:

```bash
git diff --cached --stat
```

Expected: staged files are limited to the research-statement skill, `CONTEXT.md`, and this plan.

- [ ] **Step 4: Commit**

Run:

```bash
git commit -m "Add JPL research statement skill"
```

Expected: commit succeeds.

---

## Self-Review

Spec coverage:

- Repo-local skill: covered by Task 1.
- Required skill chain: covered by Task 1 and Task 4.
- Literature-review during planning as focused scan: covered by Task 3.
- Markdown planning/audit artifacts: covered by Task 3.
- LaTeX statement drafts from `main.tex`: covered by Task 1 and Task 3.
- Scientist IV and Scientist II branches: covered by Task 2.
- Page gates: covered by Task 2 and Task 4.
- Claim ledger: covered by Task 3.
- Verification before completion: covered by Task 1, Task 4, and Task 5.

Placeholder scan:

- No `TBD`, `TODO`, or "fill in later" placeholders are used as implementation instructions.
- All file paths and validation commands are concrete.

Type/path consistency:

- Skill path is consistently `.agents/skills/research-statement/`.
- Planning artifact directory is consistently `jpl-applications/jpl_application_pack/research_statement_work/`.
- Role-specific TeX files are consistently under `jpl-applications/jpl-research-mentoring-statement/`.
