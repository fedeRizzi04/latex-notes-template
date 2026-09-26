# LaTeX Notes Template

[![Compile LaTeX](https://github.com/fedeRizzi04/latex-notes-template/actions/workflows/latex.yml/badge.svg)](https://github.com/fedeRizzi04/latex-notes-template/actions/workflows/latex.yml)
[![Made with LaTeX](https://img.shields.io/badge/Made%20with-LaTeX-008080.svg)](https://www.latex-project.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A minimal LaTeX template for lecture/course notes (`notes.tex`), built with `scrbook` and supporting both Italian and English labels (switch via `\dispensalingua` in the preamble).

## How it works

On every push or pull request, the [`latex.yml`](.github/workflows/latex.yml) GitHub Action compiles `notes.tex` and publishes `notes.pdf` as a build artifact.

## Examples

Styled boxes for notes, theorems, proofs and algorithms — ready to use out of the box:

<p align="center">
  <img src="assets/img1.png" width="47%" alt="Example page: note and theorem boxes"/>
  &nbsp;&nbsp;
  <img src="assets/img2.png" width="47%" alt="Example page: algorithm and theorem boxes"/>
</p>

## Adding new folders (e.g. images)

The workflow only triggers on changes to specific paths:

```yaml
on:
  push:
    paths:
      - "notes.tex"
      - ".github/workflows/latex.yml"
```

If you add a new folder to the repo (e.g. `images/` for figures included in the document), **you must add that path to `latex.yml`** under both `push.paths` and `pull_request.paths`. Otherwise, changes to files in that folder won't trigger a recompilation.

Example:

```yaml
on:
  push:
    paths:
      - "notes.tex"
      - "images/**"
      - ".github/workflows/latex.yml"
  pull_request:
    paths:
      - "notes.tex"
      - "images/**"
      - ".github/workflows/latex.yml"
```
