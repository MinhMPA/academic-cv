# Repository Guidelines

## Project Structure & Module Organization
This repository maintains a Markdown academic CV site rendered with Jekyll.

- `index.md` is the public, internet-facing research CV.
- `full-cv.md` preserves the longer-form CV.
- `_layouts/` contains Jekyll HTML templates.
- `media/` contains print and screen CSS plus image assets such as `new_profile.jpg`.
- `cv/` stores generated public PDF exports. Treat these as build artifacts that should match the Markdown source.
- `jpl-applications/` contains role-specific JPL material, including LaTeX CV sources and PDFs under `jpl-cv/`.
- `docs/` and `.agents/` hold agent/planning metadata and are excluded from the Jekyll build.

## Build, Test, and Development Commands
Install Jekyll prerequisites if needed:

```sh
gem install bundler jekyll
```

Build the site without writing into the repository:

```sh
bundle exec jekyll build --destination /tmp/academic-cv-site
```

Serve locally with live reload at `http://localhost:4000`:

```sh
bundle exec jekyll serve
```

For JPL LaTeX CVs, work from `jpl-applications/jpl-cv/` and compile the relevant `.tex` file, for example `latexmk -pdf nguyen-jpl-scientist-iv.tex`.

## Coding Style & Naming Conventions
Use Markdown for CV content and keep entries concise, factual, and chronologically consistent. Prefer semantic headings and simple lists over embedded HTML. Use two-space indentation for nested Markdown lists and YAML-style config alignment in `_config.yml`.

CSS files in `media/` are split by style and target: `*-screen.css` for web rendering and `*-print.css` for PDF/print output. Keep new filenames lowercase with hyphens, for example `research-cv-print.css`.

## Testing Guidelines
There is no automated test suite. Validate changes by running a Jekyll build and reviewing the generated page locally. For content edits, check links, dates, publication titles, and PDF filenames. For CSS/layout edits, inspect screen output and browser print preview before updating files in `cv/`.

## Commit & Pull Request Guidelines
Recent history uses short imperative or descriptive commit messages such as `Update CV`, `Add public academic CV`, and `Update publications and citation counts`. Keep commits focused on one content or layout change.

Pull requests should include a brief description, validation command, and screenshots or PDF previews when layout or print output changes. Link relevant issues or job/application context when applicable, but avoid committing private notes unless they belong in `jpl-applications/`.

## Agent-Specific Instructions
Do not rewrite generated PDFs without confirming the corresponding Markdown or LaTeX source change. Avoid broad formatting churn in CV content; preserve wording and ordering unless the task explicitly asks for editorial revision.
