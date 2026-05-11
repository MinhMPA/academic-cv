# Polish Notes

Last updated: 2026-05-11 03:55 JST.

## Scope

Polish was applied to the role-specific research statement drafts:

- `jpl-applications/jpl-research-mentoring-statement/research_statement_R5541_Scientist_IV.tex`
- `jpl-applications/jpl-research-mentoring-statement/research_statement_R5540_Scientist_II.tex`

The drafts follow the user's current internal page targets: up to 5 pages for Scientist IV and up to 4 pages for Scientist II. The current versions remain shorter than those caps.

## Voice and Positioning

- Scientist IV draft: emphasizes independent scientific leadership, JPL-facing mission execution, cross-probe Roman/Euclid cosmology, mentoring, and calibration/validation responsibility.
- Scientist II draft: emphasizes technical contribution, likelihood validation, Roman/Euclid readiness, and a compact four-section structure.
- Both drafts use direct first-person statements and avoid inflated role claims.
- Homepage and KAKENHI-style samples were used as voice anchors: precise, research-forward, and confident without marketing language.

## Prose-Style and Humanizer Pass

- Replaced one formulaic construction: "not only technical" became "technical and institutional."
- Avoided generic AI-signature phrases such as "pivotal," "delve," "tapestry," "testament," "fostering," and "landscape."
- Preserved technical density where it carries role fit, especially in the sections connecting field-level inference, weak lensing, galaxy clustering, and mission validation.
- Expanded several acronyms on first use to make the statements readable outside a narrow subfield review panel.

## LaTeX-Paper-EN Checks

The `latex-paper-en` compile, sentence, and de-AI modules were used as the relevant subset for these LaTeX statements.

- `uv` is not installed in this environment, so the helper scripts were run with direct `python3` fallback.
- The LaTeX build was run directly with `latexmk`.
- Sentence analysis flagged several long technical sentences as P2 readability issues. I kept the ones that compactly carry technical fit and role alignment; these are revision candidates only if the final upload must feel less technical.
- The de-AI check reported no detailed trace findings after the humanizer/prose pass.

## Page-Fit Strategy

- The Scientist IV statement uses five compact sections, matching the user's requested structure while staying under the 5-page internal cap and keeping the final PDF to 3 pages.
- The Scientist II statement uses four compact sections and keeps mentoring/leadership material lighter, keeping the final PDF to 2 pages under the 4-page internal cap.
- The Scientist IV draft includes the provided field-level-inference figure as a visual anchor; the Scientist II draft remains text-only because the figure made the shorter statement feel visually sparse rather than stronger.

## Remaining Polish Options

- Shorten one or two high-density sentences in each draft if the target reader is expected to be less technical.
- Decide whether the final upload should include explicit citations. The current drafts are citation-free because the application asks for a research statement, not a paper-style document.
- Reconfirm exact upload instructions before submission; the local template has letter-like metadata, while JPL may only need the statement body as a PDF.
- Reconfirm application availability before submission: on 2026-05-11 the canonical `jpl.jobs` pages reported the jobs as filled, while the Workday posting text remained accessible for tailoring.

## Sample-Informed Revision Pass

- The CU Boulder research/mentoring sample supports a clearer "optimal data representation" thesis and a modular mentoring model.
- The KAKENHI grant sample supports a more operational validation plan: simulation suites, systematics injections, mock validation, and milestone-driven deliverables.
- The revised statements should preserve the current risk control: no claim of Roman/Euclid team membership, no claim of OpenUniverse contribution, and no claim of shear-pipeline leadership.

## Final Polish Pass

- Replaced the soft Scientist IV phrasing "I have tried to keep methods connected" with "I keep methods connected to survey conditions."
- Replaced a generic mentoring-performance sentence with a more concrete description of explicit expectations, shared credit, and mission-scale context.
- Removed avoidable SDSS/BOSS acronym burden from both drafts while preserving the intrinsic-alignment evidence.

## Humanizer and Prose-Style Pass

- Calibrated the voice against the CU Boulder research/mentoring statement and KAKENHI grant sample without copying their sentence patterns wholesale.
- Kept the central question about the right data representation, but rebuilt the flow around reader-facing hooks: science driver, technical path, practical bridge, JPL work package, and mentoring model.
- Replaced generic mission-fit prose with concrete technical objects: likelihood validation, information accounting, scale-cut tests, covariance checks, cross-calibration mocks, and dark-sector interpretation.
- Corrected the DESI+PFS work description from "current first-author work" to "current single-author work" in both role-specific drafts.
- Final automated prose checks found no de-AI trace listings and no rule-based logic/coherence issues.
