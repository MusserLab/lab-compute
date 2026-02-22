# Lab Compute Guide — Planning Document

> This document tracks next steps and improvements for the book.
> Last updated: 2026-02-20

## Still Open

### Screenshots (3 remaining)

first-project.qmd is done (14 images in `images/first-project/`).

- [ ] Positron interface with labeled panes (`positron.qmd:29`)
- [ ] Positron Data Viewer with dataframe open (`positron.qmd:80`)
- [ ] Positron with .qmd, console, and Data Viewer (`quarto.qmd:60`)

### Content
- [ ] Update "Work in Progress" callout in `index.qmd:19-22` — all 21 chapters are substantive now, no stubs or placeholders remain. Soften or remove.
- [ ] Review Quick Start section for clarity and completeness
- [ ] Test installation instructions on a fresh machine (macOS and Windows)
- [ ] Have a student test the Quick Start walkthrough
- [ ] Review `first-project.qmd` — ensure all steps work end-to-end
- [ ] Consider subsetting Spongilla data more aggressively (~10K cells → ~2-3K) to get matrix.mtx.gz under 50 MB (GitHub recommended limit; currently 94 MB)
- [ ] **Git/GitHub**: Add section on GitHub Classroom (if using for courses)

### Part 4: Workflows
- [ ] **Starting Project**: Add template repo link once created
- [ ] **Collaborating**: Add section on code review practices

### Appendices
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
- [x] **Book Restructure** (Feb 2026): Rewrote Part 1 as hands-on Seurat tutorial
  - first-project.qmd: Spongilla scRNA-seq analysis (replaced project scaffolding)
  - setup-walkthrough.qmd: Old first-project content moved to Workflows
  - starting-project.qmd: Trimmed to quick reference/checklist
  - intro.qmd: Rewritten with narrative style, ASCII tools diagram
  - installation.qmd: Terminal instructions, rig optional, OAuth auth, Homebrew explanation
  - index.qmd: "How to Use This Book" section, honest audience description
  - Spongilla dataset added to examples/data/spongilla_counts/
- [x] Replaced custom .callout-claude CSS with built-in .callout-warning title="Claude Code" (14 files)
- [x] Standardized all terminal code blocks to `default` (styled box + copy button, no syntax coloring)
- [x] README rewritten to be reader-focused (example data, scripts, reference outputs)
- [x] Cleared styles.css (custom callout CSS removed)
- [x] Added RStudio-to-Positron translation table in positron.qmd
- [x] Orange "Ask Claude" callout boxes — CSS + 14 boxes across all chapters
- [x] Claude Code callout icon: chat-dots (speech bubble) instead of warning triangle via `.claude-callout` CSS class
- [x] Convention alignment: reconciled book with Claude Code skills (script-organization, quarto-docs, conda-env, new-project)
  - Ch. 5: Added subdirectories, exploratory/, lifecycle, BUILD_INFO, helpers, ~/lib, Parquet
  - Ch. 6: Updated YAML/setup templates, expanded Python QMD to first-class, added R vs Python table
  - Ch. 8: Added ipykernel/seaborn/session-info to core packages
  - Ch. 14: Full rewrite — outs/ not output/, flat data/ not data/raw+processed/
  - Appendix C: All templates updated to match skills
  - Consistency fixes across 5 additional files (zero remaining old-pattern references)
- [x] Cross-references audit — all internal links and heading anchors verified clean (Feb 2026 audit)
- [x] Reproducibility chapter: Docker basics section added (`reproducibility.qmd:222`)
- [x] Troubleshooting chapter: substantive content (323 lines, common tasks and answers)
- [x] Appendix C (Templates): lab-specific templates added (432 lines)

---

## Session Notes

_Add notes here during working sessions_

### 2026-02-21
- Claude Code callout icon: replaced warning triangle with chat-dots (speech bubble) via CSS override in `styles.css`
- Added `.claude-callout` class to all 15 Claude Code boxes across 14 files; 2 plain `.callout-warning` boxes unchanged
- Fixed intro text in first-project.qmd that introduced boxes as if for the first time (a box already appeared in installation.qmd)
- Updated CLAUDE.md writing convention with new callout syntax
- `getting-started.qmd`: Added "Before You Start" prerequisites section with checklist and link back to installation chapter; reorganized access methods (Positron primary, terminal secondary)
- `installation.qmd`: Clarified Claude Code authentication — explicitly warns to choose OAuth not API key, explains billing difference, includes `claude logout` recovery

### 2026-02-20
- Session wrap-up and commit: all first-project work from Feb 18-19 sessions
- Published to GitHub Pages

### 2026-02-19
- Rewrote README.md to be reader-focused — highlights example dataset (Spongilla), analysis script, and reference outputs with direct repo links
- Previous README was developer-oriented (build instructions, contributing); new version prioritizes what readers can download and use

### 2026-02-18 (session 2)
- **Major first-project.qmd revision** — incorporated detailed biology and pedagogy feedback
  - Added GitHub download instructions for example data/scripts
  - Annotated example QMD script: YAML header comments, chunk option explanations, Quarto/Markdown tutorial elements
  - Revised QC section: nCount_RNA varies by cell type, doublets, clustering-based QC, DoubletFinder
  - Revised normalization: not always technical, biological RNA abundance differences, Casey Dunn's count-space methods
  - Revised variable features: SAM as alternative, "standard pipeline" is one convention not gospel
  - Revised PCA: pick more PCs than elbow suggests, rare cell types in later PCs
  - Reframed UMAP as one visualization, not the analysis endpoint
  - Added Step 9: Identifying Cell Types — unbiased DE (FindMarkers, DotPlot) + candidate gene approach (Piwi)
  - Updated Claude Code example: muscle genes (myosins) in pinacocytes
  - Screenshot count: 14 needed for first-project chapter (detailed descriptions provided to user)
- Created `practical-comparative-single-cell/single-cell-analysis-notes.md` — seed for future single-cell book project

### 2026-02-18
- **Code block standardization** — switched all terminal command fences to `default`
- Discovered `{.text}` produces invisible code blocks (no `sourceCode` class → no Quarto CSS styling or copy button)
- Tested 4 approaches: `{.text}`, `bash`, `default`, bare fences — `default` is the only one with styled box + copy button + no syntax coloring
- Converted 108 blocks across 15 files; 3 `bash` blocks intentionally kept in `templates.qmd` (literal template content)
- Updated CLAUDE.md writing convention to document `default` standard

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
