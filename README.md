# paper-repo-bootstrap

A reusable Codex Skill for initializing and organizing academic paper repositories from Overleaf or conference LaTeX templates.

## What it does

This Skill turns a raw conference template repository into a clean paper-writing repository.

Typical output structure:

```text
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
└── original conference template/
```

The original conference template is preserved.

The Skill should not modify official `.sty` or `.bst` files.

## Installation

Clone this repository into the Codex user skills directory.

### Windows

```powershell
cd $HOME\.agents\skills
git clone https://github.com/lyJinAoki/paper-repo-bootstrap.git
```

The final path should be:

```text
C:\Users\<username>\.agents\skills\paper-repo-bootstrap\
```

### Linux / macOS

```bash
mkdir -p ~/.agents/skills
cd ~/.agents/skills
git clone https://github.com/lyJinAoki/paper-repo-bootstrap.git
```

## Usage

Open the target paper repository in Codex / VS Code.

Explicitly invoke the Skill:

```text
$paper-repo-bootstrap

Initialize the current paper repository.
Target venue: ICASSP 2027.
Preserve the original conference template.
Do not write manuscript content.
Do not commit or push.
```

A shorter Chinese prompt also works:

```text
$paper-repo-bootstrap

初始化当前论文仓库。
目标会议是 ICASSP 2027。
保留官方模板。
不要写论文正文。
不要 commit，不要 push。
```

## Example

Suppose the repository initially contains:

```text
paper/
└── ICASSP2027_Paper_Templates/
    ├── Template.tex
    ├── spconf.sty
    ├── IEEEbib.bst
    ├── refs.bib
    └── ...
```

After running the Skill, it should become approximately:

```text
paper/
├── main.tex
├── spconf.sty
├── IEEEbib.bst
├── refs.bib
├── AGENTS.md
├── sections/
├── figures/
├── results/
├── code/
├── notes/
└── ICASSP2027_Paper_Templates/
```

The original conference template directory should remain unchanged.

## Recommended test

Create a temporary Git repository containing only an official conference template.

Then run:

```text
$paper-repo-bootstrap

Bootstrap this repository for ICASSP 2027.
Preserve the original template directory.
Do not draft manuscript content.
Do not commit or push.
```

After execution, check:

```bash
git status
```

and inspect the directory tree.

Verify that:

- the original conference template is unchanged;
- `main.tex` is based on the official template;
- required `.sty`, `.bst`, and `.bib` files are available;
- the expected repository structure was created;
- no unexpected files were modified;
- no commit or push was performed automatically.

## Repository structure

```text
paper-repo-bootstrap/
├── README.md
└── SKILL.md
```

- `SKILL.md`: executable workflow and instructions for Codex.
- `README.md`: installation, usage, and testing documentation for humans.

## Design principle

`SKILL.md` defines the reusable paper-repository bootstrap workflow.

Each individual paper repository should have its own `AGENTS.md` containing project-specific information such as:

- target venue;
- page limit;
- paper topic;
- repository conventions;
- compilation requirements;
- files that must not be modified;
- scientific integrity rules.

Detailed paper notes, experiment summaries, and writing plans should go under `notes/` rather than making `AGENTS.md` excessively long.
