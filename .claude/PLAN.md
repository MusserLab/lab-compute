# Lab Compute Guide — Planning Document

> This document tracks next steps and improvements for the book.
> Last updated: 2026-02-02

## Immediate Next Steps

- [ ] Add screenshots throughout (marked with `[TODO: screenshot]`)
- [ ] Review Quick Start section for clarity and completeness
- [ ] Test installation instructions on a fresh machine (macOS and Windows)
- [ ] Have a student test the Quick Start walkthrough

## Content to Expand

### Part 1: Quick Start
- [ ] Review `first-project.qmd` — ensure all steps work end-to-end

### Part 2: Core Tools
- [x] **Positron**: Expand chapter with workflow details (screenshots still needed)
- [ ] **Conda**: Consider adding section on mamba for faster installs
- [ ] **renv**: Add troubleshooting for common Bioconductor issues
- [ ] **Git/GitHub**: Add section on GitHub Classroom (if using for courses)

### Part 3: Claude Code
- [ ] Add more examples from real lab workflows
- [ ] Expand skills chapter with more skill examples

### Part 4: Workflows
- [ ] **Starting Project**: Add template repo link once created
- [ ] **Collaborating**: Add section on code review practices
- [ ] **Reproducibility**: Consider adding Docker basics
- [ ] **Troubleshooting**: Collect common student questions and add answers

### Appendices
- [ ] Add lab-specific templates
- [ ] Add links to external resources

## Ideas for Future Chapters

- [ ] Common bioinformatics workflows

> **Note:** HPC/cluster computing, genomic resources, and data storage info will be in a separate "Lab Resources" reference, not this book.

## Screenshots Needed

- [ ] Positron interface overview (labeled panes)
- [ ] Positron Data Viewer
- [ ] Positron with R and Python sessions
- [ ] GitHub repo creation
- [ ] GitHub Pages settings
- [ ] Claude Code session example

## Completed

- [x] Initial book structure created
- [x] All 16 chapters written with substantive content
- [x] Published to GitHub Pages
- [x] Updated R installation to use rig
- [x] Author attribution added (Jacob Musser + Claude Code)
- [x] Project `.claude/CLAUDE.md` created
- [x] Created `/publish` skill for Quarto publishing
- [x] Created `/quarto-book-setup` skill for new books
- [x] Updated `/done` skill to offer publishing for Quarto books/websites
- [x] Updated book title to "Data Analysis in the Musser Lab"
- [x] Changed rig macOS install to .pkg from GitHub (not Homebrew)
- [x] Moved PLAN.md to .claude/ folder
- [x] Rewrote Part 1 intro — ".qmd as unit of analysis" framing
- [x] Rewrote first-project.qmd — Quarto analysis with penguins dataset
- [x] Created Quarto Documents chapter (part2/quarto.qmd)
- [x] Created Project Organization chapter (part2/project-organization.qmd)
- [x] Expanded Claude Code to full Part with 4 chapters

---

## Session Notes

_Add notes here during working sessions_

### 2026-02-02 (session 3)
- Rewrote Positron chapter (136→365 lines) with "Positron is your home base" framing
- Added sections: Explorer/Outline, Search (regex), Working with Quarto, Source Control Basics
- Expanded Data Viewer, simplified keyboard shortcuts, streamlined extensions
- Added cross-reference anchor to index.qmd

### 2026-02-02 (session 2)
- Added Windows platform coverage to conda chapter:
  - Shell initialization callout (conda init for PowerShell/CMD)
  - Platform-specific prompt examples via tabset
  - Windows troubleshooting sections ("conda not recognized", activation issues)
- Discussed and decided against separate starter-project example (first-project.qmd is sufficient)

### 2026-02-02
- Major restructure: ".qmd as unit of analysis" is now the central framing
- Part 1 intro and first-project rewritten to match this framing
- Created Quarto Documents chapter with mechanics based on TiHKAL patterns
- Created Project Organization chapter — numbered scripts with matching output folders
- Expanded Claude Code from one chapter to full Part (4 chapters)
- Book structure now: Quick Start → Core Tools → Claude Code → Workflows

### 2026-02-01 (session 2)
- Updated book title to "Data Analysis in the Musser Lab"
- Changed rig macOS install to use .pkg from GitHub (not Homebrew)
- Removed "clean uninstall" from rig benefits (keep old R versions!)
- Discussed scope: this book = data science setup; separate resource for HPC/storage/genomic resources
- Moved PLAN.md to .claude/ folder
- Added README sync reminder to project CLAUDE.md

### 2026-02-01 (session 1)
- Created initial book structure
- Published to https://MusserLab.github.io/lab-compute/
- Updated to use rig for R installation
- Created this planning document
- Created `/publish` and `/quarto-book-setup` skills
- Updated `/done` to integrate Quarto publishing
