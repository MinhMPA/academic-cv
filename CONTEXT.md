# JPL Application Materials

This context defines the local language for Nhat-Minh Nguyen's JPL Roman/Euclid application materials and supporting agent skills. It exists to keep high-stakes writing workflows aligned with the role, scientific positioning, and document boundaries.

## Language

**Research Statement Skill**:
A specialized agent skill for drafting and revising Nhat-Minh Nguyen's JPL Roman/Euclid Scientist II/IV research statements.
_Avoid_: general research writing skill, generic academic statement helper

**Repo-Local Skill**:
A skill stored under `.agents/skills/` and intended for this repository's application materials rather than global reuse.
_Avoid_: global Codex skill, cross-repo default

**Skill Implementation Plan**:
A Superpowers plan file that must be written before creating the repo-local research statement skill.
_Avoid_: casual direct skill creation

**JPL Roman/Euclid Application Pack**:
The local source of truth for position framing, document outlines, tone constraints, and overclaim guardrails.
_Avoid_: generic job packet, generic application prompt

**Targeted Context Check**:
A bounded check of current personal materials and job materials used to verify facts, voice, and role fit after reading the application pack.
_Avoid_: broad web research, general cosmology literature search

**Drafting Packet**:
The default output bundle for research statement work: outline, role-fit matrix, overclaim audit, polished draft, and submission TODO checklist.
_Avoid_: draft-only output, hidden plan

**Statement Draft**:
The role-specific LaTeX research statement source and PDF produced from the `jpl-applications/jpl-research-mentoring-statement/main.tex` template.
_Avoid_: Markdown-only submission draft

**Statement Template**:
The existing `jpl-applications/jpl-research-mentoring-statement/main.tex` file used as the source template for role-specific research statements.
_Avoid_: active submission draft, overwrite target

**Planning Artifact**:
A Markdown document produced during planning, evidence scanning, polishing summaries, audits, or submission TODO tracking.
_Avoid_: LaTeX planning memo, hidden scratch notes

**High-Risk Claim Ledger**:
A Markdown planning artifact that records safe wording, unsafe wording, source, and role applicability for valuable claims that are easy to overstate.
_Avoid_: undocumented claims, post-hoc overclaim scan only

**Required Skill Chain**:
The mandated workflow sequence for research statement drafting: Superpowers planning, literature-review during planning, Superpowers execution, LaTeX writing, prose-style polish, humanizer polish, paper-audit review, and Superpowers verification before completion.
_Avoid_: ad hoc drafting, polish-only workflow

**Focused Literature Scan**:
A constrained literature-review planning pass over Minh's research anchors, the JPL job research theme, weak-lensing plus galaxy-clustering specifics, and Roman/Euclid context.
_Avoid_: broad cosmology review, PRISMA-style survey, unrelated literature search

**Scientist IV Branch**:
The role path in the research statement skill for R5541, emphasizing leadership, coordination, strategy, mentoring, JPL representation, and mission-scale deliverables.
_Avoid_: senior technical contributor only

**Scientist II Branch**:
The role path in the research statement skill for R5540, emphasizing high-impact technical contribution, collaborative integration, likelihood validation, nonlinear modeling, and an emerging independent niche.
_Avoid_: passive junior framing

**Scientist IV Statement Structure**:
The five-section research statement structure for R5541, with separate space for role-specific execution and collaboration/mentoring.
_Avoid_: purely technical proposal

**Scientist II Statement Structure**:
The four-section research statement structure for R5540, keeping collaboration and execution integrated into a tighter contributor-focused narrative.
_Avoid_: reduced Scientist IV statement, passive junior statement

**Page Gate**:
The compile-verified maximum length for a role-specific statement PDF: 5 pages for Scientist IV and 4 pages for Scientist II.
_Avoid_: estimated length, word-count-only validation

## Relationships

- A **Research Statement Skill** uses the **JPL Roman/Euclid Application Pack** as its strategic source.
- A **Research Statement Skill** is a **Repo-Local Skill** for its first version.
- A **Research Statement Skill** must be created from a **Skill Implementation Plan** rather than ad hoc.
- A **Research Statement Skill** may use a **Targeted Context Check** for Nhat-Minh Nguyen's materials or the JPL job descriptions, but should not perform broad online research.
- A **Research Statement Skill** is specialized to Scientist II/IV JPL Roman/Euclid statements, not to arbitrary academic research statements.
- A **Research Statement Skill** contains both a **Scientist IV Branch** and a **Scientist II Branch** so the two role levels stay distinct.
- A **Scientist IV Branch** uses the **Scientist IV Statement Structure**.
- A **Scientist II Branch** uses the **Scientist II Statement Structure**.
- A **Research Statement Skill** produces a **Drafting Packet** by default, not only a prose draft.
- A **Research Statement Skill** must orchestrate the **Required Skill Chain** when those skills are available.
- A **Required Skill Chain** uses **Focused Literature Scan** for planning, not a broad systematic review.
- A **Drafting Packet** contains Markdown **Planning Artifacts** plus a LaTeX **Statement Draft**.
- A **Drafting Packet** includes a **High-Risk Claim Ledger** before prose drafting begins.
- A **Statement Draft** uses the existing **Statement Template** unless the user explicitly changes templates.
- A **Statement Template** is not overwritten by default; the skill writes separate role-specific **Statement Drafts**.
- A **Statement Draft** must pass the role-specific **Page Gate** before completion is claimed.

## Section maps

**Scientist IV Statement Structure**:
1. Research vision.
2. Preparation: growth, field-level inference, and survey realism.
3. Proposed JPL research program.
4. Scientist IV leadership and execution plan.
5. Collaboration, mentoring, and inclusive team science.

**Scientist II Statement Structure**:
1. Research vision.
2. Preparation: methods and science background.
3. Proposed JPL contribution.
4. Three-year integration and independent niche.

**Page Gate**:
- Scientist IV: compiled PDF must be no more than 5 pages.
- Scientist II: compiled PDF must be no more than 4 pages.

**High-Risk Claim Ledger**:
Required claim categories include growth suppression, Buchalter Prize, field-level inference contribution, weak-lensing bridge, Roman/Euclid fit, OpenUniverse or simulation-validation relevance, PI grants or leadership, mentoring and organizing, and DESI/PFS/HSC or other survey affiliations.

## Example dialogue

> **Dev:** "Should the **Research Statement Skill** help with any faculty application?"
> **Domain expert:** "No. It should first serve the **JPL Roman/Euclid Application Pack**, because the Scientist II/IV distinction and Roman/Euclid framing are the hard parts."

> **Dev:** "Should I install this skill globally?"
> **Domain expert:** "No. Create it as a **Repo-Local Skill** first because it depends on this repository's JPL application pack."

> **Dev:** "Can I write the skill file directly now?"
> **Domain expert:** "No. Write the **Skill Implementation Plan** first, then execute it."

> **Dev:** "Can I draft the Scientist II statement by weakening the Scientist IV language?"
> **Domain expert:** "No. Use the **Scientist II Branch**: it should sound like a strong independent contributor, not a reduced Scientist IV."

> **Dev:** "Should I search the web for recent Roman/Euclid papers before drafting?"
> **Domain expert:** "No. Use a **Targeted Context Check** only for Minh's materials and the job descriptions unless I explicitly ask for broader research."

> **Dev:** "Can I skip the audit if the draft reads well?"
> **Domain expert:** "No. The **Required Skill Chain** ends with paper-audit and Superpowers verification before any completion claim."

> **Dev:** "Should the literature review cover all recent modified-gravity and weak-lensing papers?"
> **Domain expert:** "No. Use a **Focused Literature Scan**: Minh's research, the job theme, weak lensing plus clustering, and Roman/Euclid specifics."

> **Dev:** "Should the draft research statement be written in Markdown first?"
> **Domain expert:** "No. Use Markdown for **Planning Artifacts**, but the **Statement Draft** itself belongs in `main.tex`."

> **Dev:** "Should I overwrite `main.tex` when drafting the Scientist IV statement?"
> **Domain expert:** "No. Treat `main.tex` as the **Statement Template** and create a role-specific **Statement Draft**."

> **Dev:** "Should Scientist II use the same five sections as Scientist IV?"
> **Domain expert:** "No. Use the tighter **Scientist II Statement Structure** so the statement reads like a focused contributor plan, not a shortened leadership dossier."

> **Dev:** "Can I estimate page length from word count?"
> **Domain expert:** "No. Compile the **Statement Draft** and enforce the **Page Gate** from the PDF."

> **Dev:** "Can I draft first and check overclaims later?"
> **Domain expert:** "No. Create the **High-Risk Claim Ledger** before drafting so the safe wording is available while writing."

## Flagged ambiguities

- "research-statement" could mean a generic academic statement skill or a JPL-specific application skill; resolved: it means a JPL Roman/Euclid Scientist II/IV skill for this application pack.
- "install skill" could imply global installation; resolved: the first **Research Statement Skill** is repo-local under `.agents/skills/`.
- "create the skill" could mean immediate file creation; resolved: write a **Skill Implementation Plan** first.
- "Scientist II" could be misread as junior/passive; resolved: **Scientist II Branch** means high-impact contributor with an emerging independent niche.
- "section structure" differs by role; resolved: **Scientist IV Statement Structure** has five sections, while **Scientist II Statement Structure** has four.
- Scientist II page limit was initially discussed as 3.5 pages; resolved: the **Page Gate** is 4 pages.
- "research" could mean broad literature search; resolved: the **Research Statement Skill** stays focused on the applicant and JPL job context unless broader research is explicitly requested.
- "draft" could mean prose only; resolved: default output is a **Drafting Packet** with planning, fit, risk, draft, and TODO artifacts.
- "literature-review" could imply a systematic review; resolved: use a **Focused Literature Scan** for the research statement planning stage.
- "Markdown draft" could mean the submission statement; resolved: Markdown is for **Planning Artifacts**, while the **Statement Draft** is LaTeX.
- "`main.tex`" could mean the active statement; resolved: it is the **Statement Template** unless the user explicitly asks to overwrite it.
- "overclaim audit" alone could happen too late; resolved: the **High-Risk Claim Ledger** is required before drafting starts.
