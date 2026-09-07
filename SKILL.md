---
name: paper-repo-bootstrap
description: Initialize or reorganize an academic paper repository from an Overleaf or conference LaTeX template. Use when the user asks to set up, scaffold, initialize, or organize a paper repo for venues such as ICASSP, ISMIR, INTERSPEECH, NeurIPS, ICML, or similar conferences.
---

# Paper Repository Bootstrap

Initialize a clean academic paper repository while preserving the original
conference template.

The user's explicit instructions always take precedence over this skill.

## Goal

Turn an existing cloned Overleaf / LaTeX conference repository into a clean
paper-working repository suitable for writing with Codex and syncing with
Overleaf.

## Before making changes

1. Inspect the current repository structure.
2. Confirm that the current directory is the intended Git repository.
3. Identify:
   - the original conference template directory;
   - the primary template `.tex` file;
   - required `.sty` files;
   - bibliography `.bib` files;
   - bibliography style `.bst` files;
   - any other files required for compilation.
4. Do not assume filenames such as `Template.tex`, `spconf.sty`, or
   `IEEEbib.bst`; inspect the repository first.
5. Never move or modify `.git`.

## Preserve the original template

Keep the original conference template directory intact as a reference.

Do not:
- delete it;
- modify its `.sty` files;
- overwrite its original template files.

Copy required working files from the template into the repository root when
necessary.

## Default working structure

Prefer the following structure unless the repository or user requires
otherwise:

paper-root/
├── main.tex
├── references.bib
├── AGENTS.md
├── sections/
│   ├── introduction.tex
│   ├── method.tex
│   ├── experiments.tex
│   └── conclusion.tex
├── figures/
├── results/
├── code/
├── notes/
│   └── paper_plan.md
└── original conference template directory/

Do not create directories that clearly do not make sense for the project.

## main.tex

Use the official conference template as the basis for `main.tex`.

Preserve:
- document class;
- conference style;
- margins;
- font configuration;
- bibliography style;
- mandatory conference formatting.

Do not modify conference `.sty` or `.bst` files.

When useful, split manuscript content into files under `sections/` and include
them from `main.tex` using `\input{...}`.

Avoid duplicate `\section{...}` declarations between `main.tex` and section
files.

## Directory purposes

### sections/

Formal manuscript source.

Typical files:
- introduction.tex
- method.tex
- experiments.tex
- conclusion.tex

Adapt section names to the actual paper.

### figures/

Only figures intended for or potentially used in the manuscript.

Prefer PDF for vector figures when appropriate.

### results/

Paper-facing experiment results, such as:
- CSV
- JSON
- XLSX

Do not copy checkpoints, training logs, or large experiment outputs here unless
explicitly requested.

### code/

Scripts or notebooks used to produce paper figures, tables, or analyses.

### notes/

Working material that is not manuscript text.

Typical contents:
- story / narrative
- experiment summary
- TODOs
- advisor feedback
- writing plan

Start with `notes/paper_plan.md` unless more files are clearly useful.

## AGENTS.md

Create a short repository-specific `AGENTS.md`.

It should describe:
- target venue;
- page limit if known;
- paper topic if known;
- repository layout;
- compilation rules;
- files Codex must not modify;
- scientific integrity rules.

Always include:

- Do not invent experimental results.
- Do not invent citations.
- Do not modify official conference style files.
- Mark uncertain scientific claims or missing information as TODO.
- Preserve existing manuscript content unless the user asks for rewriting.

Do not put the entire project history in AGENTS.md.
Use `notes/` for detailed project knowledge.

## Existing repositories

Never overwrite an existing non-empty file simply to impose this structure.

If files such as:
- main.tex
- references.bib
- AGENTS.md
- section files

already exist, inspect and preserve them.

Reorganize only when safe.

## Verification

After changes:

1. Print or inspect the resulting directory tree.
2. Run `git status`.
3. Check that only expected files changed.
4. Verify all paths referenced by `main.tex`.
5. If a local LaTeX environment is available, compile the paper.
6. If local LaTeX is unavailable, do not install it unless requested.

Report:
- files created;
- files copied;
- files modified;
- anything intentionally left unchanged;
- any remaining TODOs or compile concerns.

## Git / Overleaf safety

Do not commit or push automatically unless the user explicitly asks.

Do not pull automatically if there are uncommitted local edits unless it is
clearly safe.

Remember that this repository may synchronize with Overleaf through Git.