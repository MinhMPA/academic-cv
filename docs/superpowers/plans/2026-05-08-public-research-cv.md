# Public Research CV Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Serve the Scientist IV-derived CV as the main internet-facing CV without labeling it as Scientist IV, presenting it as a clean Academic CV / Research CV.

**Architecture:** Keep the current Jekyll/GitHub Pages model: markdown content rendered through a layout and CSS. Replace the public `index.md` content with a Scientist-IV-derived academic CV, archive the existing long CV, add a focused layout/CSS pair, and publish neutral PDF filenames for public download.

**Tech Stack:** Jekyll markdown, Liquid layouts, CSS media stylesheets, existing LaTeX-generated PDFs in `jpl-cv/`, local build checks with `jekyll build` or `hugo` only if the project has been migrated later.

---

## File Structure

- Modify: `index.md`
  - Becomes the main public Academic CV / Research CV.
  - Uses a new `research-cv` layout.
  - Must not contain the strings `Scientist IV`, `Scientist-II`, `Scientist II`, or `JPL-targeted` in visible page content.

- Create: `full-cv.md`
  - Preserves the current `index.md` content as the long/full academic CV archive.
  - Uses the existing `cv` layout unless the implementation chooses to also use the new `research-cv` layout.

- Create: `_layouts/research-cv.html`
  - Clean HTML wrapper for the public CV.
  - Loads `media/research-cv-screen.css` and `media/research-cv-print.css`.
  - Does not include the current profile image from `_layouts/cv.html`.
  - Keeps MathJax only if the final markdown contains inline math. If no math remains, do not include MathJax.

- Create: `media/research-cv-screen.css`
  - Screen styles inspired by the new LaTeX/Philcox-style CV: centered header, restrained serif typography, section rules, readable content width.

- Create: `media/research-cv-print.css`
  - Print styles matching the public HTML CV.
  - Hides browser-only affordances if added later.

- Create: `cv/Nhat-Minh-Nguyen-academic-cv.pdf`
  - Public neutral-name copy of `jpl-cv/nguyen-jpl-scientist-iv.pdf`.

- Create: `cv/Nhat-Minh-Nguyen-technical-research-cv.pdf`
  - Public neutral-name copy of `jpl-cv/nguyen-jpl-scientist-ii.pdf` if a technical version is linked.
  - Link text should say `Technical Research CV`, not `Scientist II`.

- Modify: `README.md`
  - Add current build/serve instructions for the public CV and note the neutral PDF outputs.

---

## Task 1: Preserve the Current Public CV

**Files:**
- Read: `index.md`
- Create: `full-cv.md`

- [ ] **Step 1: Copy the current `index.md` content into `full-cv.md`**

Create `full-cv.md` with the exact current content of `index.md`, changing only the front matter title:

```markdown
---
layout: cv
title: Nhat-Minh Nguyen - Full Academic CV
---
```

The rest of the file should match the old `index.md` content byte-for-byte unless a relative link breaks after the rename.

- [ ] **Step 2: Verify the archive page exists**

Run:

```sh
test -f full-cv.md
```

Expected: exit code `0`.

- [ ] **Step 3: Verify the archive title**

Run:

```sh
sed -n '1,6p' full-cv.md
```

Expected output starts with:

```markdown
---
layout: cv
title: Nhat-Minh Nguyen - Full Academic CV
---
# Nhat-Minh Nguyen, PhD
```

---

## Task 2: Add the Focused Research CV Layout

**Files:**
- Create: `_layouts/research-cv.html`
- Create: `media/research-cv-screen.css`
- Create: `media/research-cv-print.css`

- [ ] **Step 1: Create `_layouts/research-cv.html`**

Use this content:

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>{% if page.title %}{{ page.title }} | {% endif %}Academic CV</title>
  <link href="media/research-cv-screen.css" type="text/css" rel="stylesheet" media="screen">
  <link href="media/research-cv-print.css" type="text/css" rel="stylesheet" media="print">
</head>
<body>
  <main id="cv">
    {{ content }}
  </main>
</body>
</html>
```

- [ ] **Step 2: Create `media/research-cv-screen.css`**

Use this content:

```css
:root {
  --ink: #171717;
  --muted: #5f5f5f;
  --rule: #222;
  --link: #c0005a;
  --paper: #ffffff;
}

* {
  box-sizing: border-box;
}

html {
  background: #f3f3f3;
}

body {
  margin: 0;
  color: var(--ink);
  background: var(--paper);
  font-family: Georgia, "Times New Roman", serif;
  font-size: 17px;
  line-height: 1.38;
}

#cv {
  width: min(960px, calc(100vw - 40px));
  margin: 48px auto 72px;
}

h1 {
  margin: 0;
  text-align: center;
  font-size: 2.25rem;
  line-height: 1.1;
  font-weight: 700;
  letter-spacing: 0;
}

h1 + p {
  margin: 0.2rem 0 0;
  text-align: center;
  color: var(--ink);
  font-size: 1.05rem;
}

.cv-affiliation,
.cv-links,
.cv-downloads {
  text-align: center;
}

.cv-affiliation {
  margin: 0.2rem 0 0;
}

.cv-links {
  margin: 0.45rem 0 2.2rem;
}

.cv-downloads {
  margin: -1.25rem 0 2.2rem;
  font-size: 0.95rem;
}

a {
  color: var(--link);
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

.cv-links a,
.cv-downloads a {
  margin: 0 0.7rem;
}

h2 {
  margin: 1.45rem 0 0.45rem;
  padding-bottom: 0.18rem;
  border-bottom: 1px solid var(--rule);
  font-size: 1.38rem;
  line-height: 1.15;
  text-transform: uppercase;
  letter-spacing: 0;
}

h3 {
  margin: 0.9rem 0 0.25rem;
  font-size: 1.05rem;
}

p {
  margin: 0 0 0.55rem;
}

ul,
ol {
  margin: 0.2rem 0 0.85rem 1.25rem;
  padding: 0;
}

li {
  margin: 0.16rem 0;
}

.entry {
  display: grid;
  grid-template-columns: minmax(0, 1fr) 7.5rem;
  column-gap: 1.5rem;
  margin: 0 0 0.45rem;
}

.entry-title {
  font-weight: 700;
}

.entry-date {
  text-align: right;
  font-style: italic;
  white-space: nowrap;
}

.entry-detail {
  grid-column: 1 / -1;
}

.label-row {
  display: grid;
  grid-template-columns: 12rem minmax(0, 1fr);
  column-gap: 1.5rem;
  margin: 0 0 0.35rem;
}

.label {
  font-weight: 700;
}

.note {
  color: var(--muted);
  font-style: italic;
}

@media (max-width: 680px) {
  body {
    font-size: 16px;
  }

  #cv {
    width: calc(100vw - 28px);
    margin: 28px auto 48px;
  }

  h1 {
    font-size: 1.85rem;
  }

  .entry,
  .label-row {
    grid-template-columns: 1fr;
  }

  .entry-date {
    text-align: left;
    margin-top: 0.05rem;
  }

  .cv-links a,
  .cv-downloads a {
    display: inline-block;
    margin: 0.15rem 0.45rem;
  }
}
```

- [ ] **Step 3: Create `media/research-cv-print.css`**

Use this content:

```css
body {
  margin: 0;
  color: #111;
  background: #fff;
  font-family: Georgia, "Times New Roman", serif;
  font-size: 10.5pt;
  line-height: 1.28;
}

#cv {
  width: auto;
  margin: 0.35in 0.45in;
}

h1 {
  margin: 0;
  text-align: center;
  font-size: 21pt;
  line-height: 1.1;
}

h1 + p,
.cv-affiliation,
.cv-links,
.cv-downloads {
  text-align: center;
}

h1 + p,
.cv-affiliation {
  margin: 0.08in 0 0;
}

.cv-links {
  margin: 0.08in 0 0.2in;
}

.cv-downloads {
  display: none;
}

a {
  color: #111;
  text-decoration: none;
}

h2 {
  margin: 0.17in 0 0.06in;
  padding-bottom: 0.02in;
  border-bottom: 0.5pt solid #111;
  font-size: 13pt;
  line-height: 1.1;
  text-transform: uppercase;
  letter-spacing: 0;
}

h3 {
  margin: 0.1in 0 0.03in;
  font-size: 10.5pt;
}

p {
  margin: 0 0 0.05in;
}

ul,
ol {
  margin: 0.03in 0 0.08in 0.18in;
  padding: 0;
}

li {
  margin: 0.01in 0;
}

.entry {
  display: grid;
  grid-template-columns: minmax(0, 1fr) 0.9in;
  column-gap: 0.12in;
  margin: 0 0 0.05in;
}

.entry-title {
  font-weight: 700;
}

.entry-date {
  text-align: right;
  font-style: italic;
  white-space: nowrap;
}

.entry-detail {
  grid-column: 1 / -1;
}

.label-row {
  display: grid;
  grid-template-columns: 1.35in minmax(0, 1fr);
  column-gap: 0.15in;
  margin: 0 0 0.04in;
}

.label {
  font-weight: 700;
}

.note {
  font-style: italic;
}
```

- [ ] **Step 4: Verify the layout references the intended CSS files**

Run:

```sh
rg -n "research-cv-screen.css|research-cv-print.css|new_profile|MathJax" _layouts/research-cv.html
```

Expected:

```text
_layouts/research-cv.html:7:  <link href="media/research-cv-screen.css" type="text/css" rel="stylesheet" media="screen">
_layouts/research-cv.html:8:  <link href="media/research-cv-print.css" type="text/css" rel="stylesheet" media="print">
```

There should be no `new_profile` or `MathJax` matches.

---

## Task 3: Publish Neutral PDF Filenames

**Files:**
- Read: `jpl-cv/nguyen-jpl-scientist-iv.pdf`
- Read: `jpl-cv/nguyen-jpl-scientist-ii.pdf`
- Create: `cv/Nhat-Minh-Nguyen-academic-cv.pdf`
- Create: `cv/Nhat-Minh-Nguyen-technical-research-cv.pdf`

- [ ] **Step 1: Create the public PDF directory**

Run:

```sh
mkdir -p cv
```

Expected: exit code `0`.

- [ ] **Step 2: Copy the senior academic CV PDF to a neutral public filename**

Run:

```sh
cp jpl-cv/nguyen-jpl-scientist-iv.pdf cv/Nhat-Minh-Nguyen-academic-cv.pdf
```

Expected: exit code `0`.

- [ ] **Step 3: Copy the technical research CV PDF to a neutral public filename**

Run:

```sh
cp jpl-cv/nguyen-jpl-scientist-ii.pdf cv/Nhat-Minh-Nguyen-technical-research-cv.pdf
```

Expected: exit code `0`.

- [ ] **Step 4: Verify the PDFs exist and are readable**

Run:

```sh
pdfinfo cv/Nhat-Minh-Nguyen-academic-cv.pdf
```

Expected includes:

```text
Pages:           3
Page size:       612 x 792 pts (letter)
```

Run:

```sh
pdfinfo cv/Nhat-Minh-Nguyen-technical-research-cv.pdf
```

Expected includes:

```text
Pages:           3
Page size:       612 x 792 pts (letter)
```

---

## Task 4: Replace `index.md` With the Public Academic CV

**Files:**
- Modify: `index.md`
- Read: `jpl-cv/nguyen-jpl-scientist-iv.tex`

- [ ] **Step 1: Replace `index.md` front matter and header**

Start `index.md` with:

```markdown
---
layout: research-cv
title: Nhat-Minh Nguyen - Academic CV
---
# Nhat-Minh Nguyen, PhD
Cosmologist, Kavli IPMU Fellow

<p class="cv-affiliation">Kavli Institute for Physics and Mathematics of the Universe, University of Tokyo</p>

<p class="cv-links">
<a href="https://linkedin.com/in/minhmpa">LinkedIn</a>
<a href="https://github.com/MinhMPA">GitHub</a>
<a href="https://orcid.org/0000-0002-2542-7233">ORCID</a>
</p>

<p class="cv-downloads">
<a href="cv/Nhat-Minh-Nguyen-academic-cv.pdf">Academic CV PDF</a>
<a href="cv/Nhat-Minh-Nguyen-technical-research-cv.pdf">Technical Research CV PDF</a>
<a href="full-cv.html">Full CV Archive</a>
</p>
```

- [ ] **Step 2: Add the public Research Profile section**

Add:

```markdown
## Research Profile

Cosmologist working on growth of large-scale structure, new physics from galaxy surveys, and statistical methods for extracting information from cosmological data. Current research connects field-level inference, effective-field-theory likelihoods, multi-tracer analyses, and machine-learning methods for spectroscopic surveys. Publication record: 21 papers, including 15 outside large-collaboration author lists; h-index 17 on the current CV.
```

- [ ] **Step 3: Add Selected Honors with Buchalter first**

Add:

```markdown
## Selected Honors

<div class="entry">
<div><span class="entry-title"><a href="http://www.buchaltercosmologyprize.org/">Buchalter Cosmology Prize</a></span>, with American Astronomical Society award announcement</div>
<div class="entry-date">2024</div>
</div>
```

- [ ] **Step 4: Add Grants**

Add:

```markdown
## Grants

<div class="entry">
<div><span class="entry-title"><a href="https://www.jsps.go.jp/english/e-grants/grants01.html">JSPS KAKENHI Grant-in-Aid for Research Activity Start-up</a></span>, PI, JPY 2,000,000</div>
<div class="entry-date">2025</div>
</div>

<div class="entry">
<div><span class="entry-title"><a href="http://www.fpastron.jp/josei-r.html">Japan Foundation for Promotion of Astronomy Research Support Grant</a></span>, PI, approx. JPY 320,000</div>
<div class="entry-date">2025</div>
</div>
```

- [ ] **Step 5: Add Scientific Leadership**

Add:

```markdown
## Scientific Leadership

<div class="entry">
<div><span class="entry-title"><a href="https://indico.ipmu.jp/event/460/">Beyond-2-Point Statistics Meet Survey Systematics</a></span><br>Organizing Committee Chair</div>
<div class="entry-date">2025</div>
</div>

<div class="entry">
<div><span class="entry-title"><a href="http://vietnam.in2p3.fr/2025/Cosmology/overview.php">Cosmology 2025</a></span><br>Scientific Program Committee member</div>
<div class="entry-date">2025</div>
</div>

<div class="entry">
<div><span class="entry-title"><a href="https://sites.google.com/view/cosmo2024/home">COSMO'24</a></span><br>Large-scale Structure Session Convener</div>
<div class="entry-date">2024</div>
</div>

<div class="entry">
<div><span class="entry-title"><a href="https://indico.kmi.nagoya-u.ac.jp/event/9/page/12-workshop-goals">Future of Artificial Intelligence for Science in Japan</a></span><br>Cosmology/Astrophysics Unconference Facilitator</div>
<div class="entry-date">2024</div>
</div>

<div class="entry">
<div><span class="entry-title"><a href="https://johannesulf.github.io/cosmology-school-2023/">Michigan Cosmology Summer School</a></span><br>Local Organizing Committee member</div>
<div class="entry-date">2023</div>
</div>
```

- [ ] **Step 6: Add Mentoring and Teaching near the top**

Add:

```markdown
## Mentoring and Teaching

- Co-mentored Carter Matties at the University of Michigan; now Physics Graduate Student at Syracuse.
- Co-mentored Andrja Kosti&#263; at the Max Planck Institute for Astrophysics; now Research Scientist at DeepL.
- Advised research projects for Baptiste Barthe-Gold, Eleni Tsaprazi, Andrew Hope, Kyle Lee, Disha Saxena, and Kasey Thai.
- Course instructor, Michigan Math and Science Scholars, "Climbing the Distance Ladder to the Big Bang: How astronomers survey the Universe," Summer 2024.
- Guest lecturer, Michigan Math and Science Scholars, Summer 2023.
```

- [ ] **Step 7: Add Positions and Education**

Add the `Positions` and `Education` sections from `jpl-cv/nguyen-jpl-scientist-iv.tex`, converted into HTML `.entry` blocks. Use these exact section names:

```markdown
## Positions
```

```markdown
## Education
```

Do not use `Affiliation` as the section name on the public page.

- [ ] **Step 8: Add Survey Collaborations and Research Themes without JPL-specific labeling**

Add:

```markdown
## Survey Collaborations

<div class="label-row"><div class="label">Current</div><div><a href="https://pfs.ipmu.jp/">Prime Focus Spectrograph (PFS)</a></div></div>
<div class="label-row"><div class="label">Former</div><div><a href="https://www.desi.lbl.gov/the-desi-survey/">Dark Energy Spectroscopic Instrument (DESI)</a></div></div>

## Research Themes

- Field-level and forward modeling for galaxy clustering, intrinsic alignment, and initial-condition inference.
- Effective-field-theory likelihoods for large-scale structure and consistency tests of physical data models.
- Multi-tracer and multi-survey calibration with PFS-DESI overlap.
- Growth-of-structure tests, modified-gravity parameterizations, and dark-sector phenomenology.
- Beyond-two-point galaxy clustering statistics, mock-data challenges, and survey-analysis validation.
- Machine-learning and statistical reconstruction of the local density field.
```

Do not use the section title `Research Themes Relevant to JPL`.

- [ ] **Step 9: Add Selected Publications, Selected Talks, Popular Science and Media, Professional Service, References**

Copy these sections from `jpl-cv/nguyen-jpl-scientist-iv.tex` and convert them to markdown/HTML. Apply these public-facing adjustments:

- Use `## Selected Publications`.
- Use `## Selected Talks`.
- Keep the note `Conference and workshop talks only; ordinary seminar talks are intentionally omitted.`
- Use `## Popular Science and Media`.
- Use `## Professional Service`.
- Use `## References`.
- Preserve the three-reference layout with a responsive `.entry` or simple HTML block.

- [ ] **Step 10: Verify no forbidden public labels remain in `index.md`**

Run:

```sh
rg -n "Scientist IV|Scientist-II|Scientist II|JPL-targeted|Research Themes Relevant to JPL|nguyen-jpl-scientist" index.md
```

Expected: no output and exit code `1`.

---

## Task 5: Update README Build Instructions

**Files:**
- Modify: `README.md`

- [ ] **Step 1: Add a public CV maintenance section near the top of `README.md`**

Add:

```markdown
## Public CV Pages

The main internet-facing CV is `index.md`. It is a clean Academic CV / Research CV derived from the senior research CV, without role-specific labels.

The older long-form CV is preserved at `full-cv.md`.

Public PDFs use neutral filenames:

- `cv/Nhat-Minh-Nguyen-academic-cv.pdf`
- `cv/Nhat-Minh-Nguyen-technical-research-cv.pdf`

Build locally with:

```sh
jekyll build --destination /tmp/academic-cv-site
```

Serve locally with:

```sh
jekyll serve
```
```

- [ ] **Step 2: Verify README mentions the new public files**

Run:

```sh
rg -n "index.md|full-cv.md|Nhat-Minh-Nguyen-academic-cv.pdf|Nhat-Minh-Nguyen-technical-research-cv.pdf" README.md
```

Expected: all four filenames appear.

---

## Task 6: Build and Link-Check the Site

**Files:**
- Read: `index.md`
- Read: `full-cv.md`
- Read: `_layouts/research-cv.html`
- Read: `media/research-cv-screen.css`
- Read: `media/research-cv-print.css`

- [ ] **Step 1: Build the site**

Run:

```sh
jekyll build --destination /tmp/academic-cv-site
```

Expected:

```text
done in
```

The exact duration can differ, but the command must exit `0`.

- [ ] **Step 2: Verify generated pages exist**

Run:

```sh
test -f /tmp/academic-cv-site/index.html
```

Expected: exit code `0`.

Run:

```sh
test -f /tmp/academic-cv-site/full-cv.html
```

Expected: exit code `0`.

- [ ] **Step 3: Verify generated PDF files are copied**

Run:

```sh
test -f /tmp/academic-cv-site/cv/Nhat-Minh-Nguyen-academic-cv.pdf
```

Expected: exit code `0`.

Run:

```sh
test -f /tmp/academic-cv-site/cv/Nhat-Minh-Nguyen-technical-research-cv.pdf
```

Expected: exit code `0`.

- [ ] **Step 4: Check public page content**

Run:

```sh
rg -n "Buchalter Cosmology Prize|LinkedIn|GitHub|ORCID|Scientific Leadership|Mentoring and Teaching|Selected Talks" /tmp/academic-cv-site/index.html
```

Expected: each phrase appears at least once.

- [ ] **Step 5: Check forbidden labels are absent from generated public HTML**

Run:

```sh
rg -n "Scientist IV|Scientist-II|Scientist II|JPL-targeted|Research Themes Relevant to JPL|nguyen-jpl-scientist" /tmp/academic-cv-site/index.html
```

Expected: no output and exit code `1`.

---

## Task 7: Optional Browser Verification

**Files:**
- Read: generated site under `/tmp/academic-cv-site`

- [ ] **Step 1: Serve the site locally**

Run:

```sh
jekyll serve --host 127.0.0.1 --port 4000
```

Expected:

```text
Server address: http://127.0.0.1:4000/
```

- [ ] **Step 2: Open these URLs in a browser and inspect layout manually**

Check:

```text
http://127.0.0.1:4000/
http://127.0.0.1:4000/full-cv.html
http://127.0.0.1:4000/cv/Nhat-Minh-Nguyen-academic-cv.pdf
http://127.0.0.1:4000/cv/Nhat-Minh-Nguyen-technical-research-cv.pdf
```

Expected:

- Header links appear in this order: `LinkedIn`, `GitHub`, `ORCID`.
- The page title and visible body do not say `Scientist IV`.
- Buchalter appears near the top.
- Grants, Scientific Leadership, Mentoring and Teaching are above Positions.
- The page is readable on desktop width and mobile width.
- The old long CV is reachable from the archive link.

---

## Task 8: Commit the Public CV Update

**Files:**
- Add: `full-cv.md`
- Add: `_layouts/research-cv.html`
- Add: `media/research-cv-screen.css`
- Add: `media/research-cv-print.css`
- Add: `cv/Nhat-Minh-Nguyen-academic-cv.pdf`
- Add: `cv/Nhat-Minh-Nguyen-technical-research-cv.pdf`
- Modify: `index.md`
- Modify: `README.md`

- [ ] **Step 1: Review the final diff**

Run:

```sh
git diff -- index.md full-cv.md _layouts/research-cv.html media/research-cv-screen.css media/research-cv-print.css README.md
```

Expected: diff shows only the planned content and layout changes.

- [ ] **Step 2: Check untracked files**

Run:

```sh
git status --short
```

Expected includes the new planned files. Existing unrelated untracked files such as `.agents/`, `skills-lock.json`, `tmp/`, or a stray `\` file may also appear; do not add them unless the user explicitly asks.

- [ ] **Step 3: Stage only the public CV files**

Run:

```sh
git add index.md full-cv.md _layouts/research-cv.html media/research-cv-screen.css media/research-cv-print.css cv/Nhat-Minh-Nguyen-academic-cv.pdf cv/Nhat-Minh-Nguyen-technical-research-cv.pdf README.md
```

Expected: exit code `0`.

- [ ] **Step 4: Commit**

Run:

```sh
git commit -m "Add public research CV"
```

Expected: commit succeeds and reports changed files.

---

## Self-Review

- Spec coverage: The plan serves the Scientist IV-derived content as the public main CV, removes role-specific labels, uses Academic CV / Research CV framing, preserves the old CV, adds neutral PDF names, and keeps the existing Jekyll-style publishing flow.
- Placeholder scan: No placeholder markers or incomplete implementation notes remain.
- Type and naming consistency: `research-cv` layout name, CSS filenames, neutral PDF filenames, and generated-page checks are consistent across tasks.
