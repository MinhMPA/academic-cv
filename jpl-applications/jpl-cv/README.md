# JPL-Targeted CV Drafts

This directory contains two role-specific LaTeX CV drafts:

- `nguyen-jpl-scientist-iv.tex`
- `nguyen-jpl-scientist-ii.tex`

The shared style file is `cvstyle.tex`. It is inspired by the Northeastern University COS Faculty CV Template by Zoe Kearney, licensed under LPPL 1.3c, and tuned toward the compact academic style of the Philcox CV example.

Build from this directory:

```sh
latexmk -pdf nguyen-jpl-scientist-iv.tex
latexmk -pdf nguyen-jpl-scientist-ii.tex
```

Clean auxiliary files:

```sh
latexmk -c
```
