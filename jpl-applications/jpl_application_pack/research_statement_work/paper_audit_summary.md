# Paper Audit Summary

Last updated: 2026-05-11 03:35 JST.

## Files Audited

- `jpl-applications/jpl-research-mentoring-statement/research_statement_R5541_Scientist_IV.tex`
- `jpl-applications/jpl-research-mentoring-statement/research_statement_R5540_Scientist_II.tex`

## Audit Mode

The `paper-audit` quick-audit workflow was run on both LaTeX drafts. This is a reviewer-style paper audit, so several findings are expected to be false positives for an application research statement.

## Result

- Scientist IV: no critical issues and no submission blockers were reported.
- Scientist II: no critical issues and no submission blockers were reported.
- The audit did flag style and paper-genre issues, mostly long sentences, missing abstract, and missing figure/table material.
- A stricter `paper-audit --mode gate` pass now reports `PASS` for both statements.

## Addressed Findings

- Undefined-acronym risks were reduced by expanding first uses of Jet Propulsion Laboratory, Physical Review Letters, cosmic microwave background, effective-field-theory, Dark Energy Spectroscopic Instrument, Prime Focus Spectrograph, Sloan Digital Sky Survey III Baryon Oscillation Spectroscopic Survey, and photometric-redshift language where needed.
- Formulaic prose flagged by humanizer-style checks was removed.
- Scientist IV leadership wording was narrowed from broad "lead Roman/Euclid" language to "help lead JPL contributions to Roman and Euclid joint-probe cosmology."

## Findings Treated as Not Applicable

- Missing abstract: not applicable because the artifact is an application research statement.
- Missing figures/tables: not applicable because the active application asks for a statement and imposes a short page limit.
- Missing bibliography/citation apparatus: currently intentional; citations are tracked in the planning memo rather than inserted into the upload draft.

## Residual Risks

- Some sentences remain technically dense. They are acceptable for a specialist JPL review but can be shortened if the final packet needs a broader panel style.
- Claims about survey memberships, OpenUniverse involvement, and mission-team language should be verified before upload.
- The Workday posting text states a 3-page limit; both PDFs are under that limit, but upload instructions and application availability should still be checked at submission time.

## Sample-Informed Risk Update

- The revised plan should reduce the highest Scientist IV risk by replacing broad leadership language with a concrete Roman--Euclid overlap mock challenge or likelihood-validation work package.
- The revised plan should reduce the weak-lensing-adjacency risk by explicitly stating that Minh's role is not shear-pipeline ownership, but likelihood validation and systematics propagation from calibrated products.
- The revised plan should reduce the "robust but underspecified" risk by naming validation tests: matched mocks, scale-cut sweeps, covariance/cross-covariance checks, prior sensitivity, and null tests.

## Final Verification Pass

- `latexmk -g -pdf -interaction=nonstopmode -file-line-error` succeeded for both role-specific drafts.
- `pdfinfo` reports 2 pages for the Scientist IV PDF and 2 pages for the Scientist II PDF.
- `latex-paper-en` de-AI analysis produced no detailed trace findings for either draft.
- `latex-paper-en` logic analysis reported no rule-based coherence issues for either draft.
- `paper-audit --mode gate` returned `PASS` for both drafts; its remaining abstract/figure/table notes are not applicable to this application statement format.
- Grep checks found the required likelihood-validation, Roman--Euclid mock-challenge, working-group qualifier, and modular mentoring language, and found no matches for the plan's forbidden overclaim/sample-leakage phrases.
