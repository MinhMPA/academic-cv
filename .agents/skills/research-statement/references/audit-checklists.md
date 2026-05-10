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
