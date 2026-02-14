# Lab Compute Guide — Planning Document

> This document tracks next steps and improvements for the book.
> Last updated: 2026-02-14

## Still Open

### Screenshots (5 remaining)
These are marked with `[TODO: screenshot]` in the source files:

- [ ] Positron interface with empty folder open (`first-project.qmd:34`)
- [ ] Rendered HTML output (`first-project.qmd:295`)
- [ ] Positron interface with labeled panes (`positron.qmd:17`)
- [ ] Positron Data Viewer with dataframe open (`positron.qmd:68`)
- [ ] Positron with .qmd, console, and Data Viewer (`quarto.qmd:58`)

### Content
- [ ] Review Quick Start section for clarity and completeness
- [ ] Test installation instructions on a fresh machine (macOS and Windows)
- [ ] Have a student test the Quick Start walkthrough
- [ ] Review `first-project.qmd` — ensure all steps work end-to-end
- [ ] **Git/GitHub**: Add section on GitHub Classroom (if using for courses)

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
- [x] Positron chapter expanded (365 lines, "home base" framing)
- [x] Conda chapter expanded (456 lines, core packages, channels, lab policies)
- [x] renv chapter expanded → "R: rig & renv" (570 lines, Bioconductor, tidyverse)
- [x] Quarto chapter expanded (676 lines, interactive workflow, setup patterns, cheatsheets)
- [x] Claude Code: Major revision — 4 chapters rewritten (getting-started, configuring-projects, skills, working-effectively)
- [x] Claude Code: Positron extension as primary interface
- [x] Claude Code: Plan files pattern (PLOTTING_PLAN.md, DATA_NOTES.md)
- [x] Claude Code: Context management guidance
- [x] Claude Code: Prompt patterns for data science
- [x] Claude Code: Project-specific skills (gene-naming example)
- [x] Orange "Ask Claude" callout boxes — CSS + 14 boxes across all chapters
- [x] Convention alignment: reconciled book with Claude Code skills (script-organization, quarto-docs, conda-env, new-project)
  - Ch. 5: Added subdirectories, exploratory/, lifecycle, BUILD_INFO, helpers, ~/lib, Parquet
  - Ch. 6: Updated YAML/setup templates, expanded Python QMD to first-class, added R vs Python table
  - Ch. 8: Added ipykernel/seaborn/session-info to core packages
  - Ch. 14: Full rewrite — outs/ not output/, flat data/ not data/raw+processed/
  - Appendix C: All templates updated to match skills
  - Consistency fixes across 5 additional files (zero remaining old-pattern references)

---

## Session Notes

_Add notes here during working sessions_

### 2026-02-14
- **Convention alignment session** — reconciled book with current Claude Code skills
- Source of truth: `~/.claude/skills/` (script-organization, quarto-docs, conda-env, new-project)
- Followed instructions from `~/.claude/plans/book-update-instructions.md`
- 10 files modified across 5 primary chapters + 5 consistency fixes
- Key theme: Python QMD as first-class data science format alongside R
- All `data/raw/`, `data/processed/`, `output/` references eliminated
- All templates now include: status field, git hash, BUILD_INFO.txt, set.seed(42)

### 2026-02-03 (session 2)
- **Claude Code chapter improvement planning session**
- Read entire book to understand structure and style
- Analyzed TiHKAL project for workflow patterns:
  - Multi-file .claude/ structure (CLAUDE.md + plan files)
  - PLOTTING_PLAN.md pattern for status tracking
  - Project-specific skills (gene-naming)
  - Evolving documentation
- Identified gaps vs actual workflow: Positron extension, plan files, context management, prompt patterns
- Created `CLAUDE_CODE_CHAPTER_PLAN.md` with detailed research and next steps
- User feedback on callouts:
  - Use Claude orange (custom Anthropic-style class)
  - Simple examples: troubleshooting or setting up one specific thing
  - Detailed but concise prompts showing how to provide specific information
- Next: Read user-level skills, create detailed outline for review

### 2026-02-03
- Expanded renv chapter → "R: rig & renv" (253→570 lines):
  - rig section: why multiple R versions, essential commands, per-project R version pinning
  - Tidyverse section: importance in data science, pandas parallel, link to R4DS
  - Bioconductor expansion: what it is, version synchronization table, RNA-seq packages (DESeq2, limma, edgeR, tximport, tximeta, goseq), single-cell packages (Seurat, SingleCellExperiment, scran, scater, Monocle3)
- Expanded Quarto chapter (377→676 lines):
  - Why Quarto: compared to R scripts, compared to R Markdown
  - Detailed interactive development workflow walkthrough
  - Setup chunk patterns based on TiHKAL project
  - Documenting inputs/outputs pattern
  - Cheatsheets moved to end (YAML header, setup chunk template, chunk options, commands, shortcuts)

### 2026-02-02 (session 4)
- Expanded Conda chapter (311→456 lines):
  - Core data science packages section (numpy, pandas, matplotlib, ipykernel)
  - Expanded channels (priority, bioconda, .condarc configuration)
  - Libmamba solver setup
  - Lab policies (never use base, both conda+renv)
  - Dependency conflicts troubleshooting

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
