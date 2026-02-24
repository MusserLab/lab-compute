# Lab Compute Guide — Planning Document

> This document tracks next steps and improvements for the book.
> Last updated: 2026-02-24

## Still Open

### Part 2: Polishing (priority order)

Assessed all 6 Part 2 chapters (Feb 2026). Common issue: they read like reference documentation, not teaching guides. The first-project chapter (Ch. 3) sets a high bar with narrative tone and 14 screenshots. Part 2 chapters need to move toward that quality.

**Claude Code callouts**: Target is 2-3 per Part 2 chapter. All chapters now meet target: Ch. 4 (3), Ch. 6 (2), Ch. 7 (3), Ch. 8 (3), Ch. 9 (3).

#### Ch. 4 — Positron (REWRITE DONE — screenshots pending)

Full rewrite completed Feb 2026. See plan: `.claude/plans/parsed-strolling-hoare.md`

Completed:
- [x] Restructure around daily workflow, not UI element tour
- [x] Add "Console vs Terminal" section — when to use which, with examples
- [x] Add "Managing Multiple Sessions" — tabs, switching, which console receives Cmd+Enter code
- [x] Add "Status Bar" section — what it shows, why to check it
- [x] Add "When Things Go Wrong" — panel recovery, session restart, Output panel
- [x] Rewrite "Restarting R" — clean environment testing, not a rendering prerequisite
- [x] Note: R/Python version only needs to be set once per project via Command Palette; /new-project skill does this automatically
- [x] Add Jupyter extension to Extensions section
- [x] Mention that Terminal opens to project root
- [x] Remove JSON settings examples (too advanced for this stage)
- [x] Match narrative tone of Ch. 3 and Ch. 9 (Git)
- [x] ~7 screenshot TODOs placed throughout
- [x] Note: needs future link to Musser Lab-specific Claude Code skills chapter (doesn't exist yet)
- [x] Windows terminal callout (PowerShell vs Unix, conda init, file paths)
- [x] Data Viewer: opens CSV/TSV from File Explorer
- [x] File Explorer: project scope, + buttons for new files/folders
- [x] 3 Claude Code callout boxes
- [x] Fixed .vscode → .positron throughout
- [x] Interpreter settings: described as internally remembered (no visible settings file)

#### Ch. 6 — Quarto (REWRITE DONE — screenshot pending)

Full rewrite completed Feb 2026 (942 → 786 lines). Restructured from reference doc to teaching guide with Python as first-class citizen. Added: "Compared to Jupyter Notebooks" subsection, 7 R/Python tabsets throughout, new Claude Code callout (2 total). Dissolved standalone "Working with Python" section — Python integrated everywhere via tabsets. Cut ~160 lines of duplicated templates, replaced with @sec-templates cross-references. Reference tables moved to end.

- [x] Restructure: teaching content first, reference tables at end
- [x] Cut duplicate templates (already in Appendix C)
- [ ] Positron with .qmd, console, and Data Viewer screenshot (`quarto.qmd:60`)

#### Ch. 5 — Project Organization (REWRITE DONE)

Full rewrite completed Feb 2026 (496 → 458 lines). Restructured from reference spec to narrative teaching guide. Added: motivating opening, "Two Rules" framing, `.claude/` in project tree, `.qmd` as analysis format, exploratory directory section, "start flat, grow sectioned" guidance, cross-language Parquet examples, `/new-project` reference. Reduced to one Mermaid diagram. Fixed quarto.qmd cross-reference (`#output-files` → `#housekeeping`).

- [x] Add narrative intro paragraph
- [x] Soften tone throughout

#### Ch. 7 — R: rig & renv (REWRITE DONE — screenshots pending)

Full rewrite completed Feb 2026 (580 → ~340 lines). Restructured from reference documentation to narrative teaching guide built around Ch. 3 callbacks. Package reference content (tidyverse, Bioconductor tables, RNA-seq/single-cell package lists) moved to new Appendix D (`appendices/r-packages.qmd`).

- [x] Tie renv workflow section back to Ch. 3 experience
- [x] Narrative tone throughout (scenarios, explanations, not bullet lists)
- [x] Fixed outdated `.vscode/settings.json` → Command Palette approach
- [x] 3 Claude Code callout boxes (package discovery, renv status, installation errors)
- [x] 4 screenshot TODOs placed throughout
- [x] "How rig and renv Work Together" section with Bioconductor version story
- [x] Created Appendix D: R Packages for Biology

#### Ch. 8 — Conda (REWRITE DONE — screenshots pending)

Full rewrite completed Feb 2026 (476 → 444 lines). Restructured from command reference to narrative teaching guide. Added: Miniforge installation section (macOS + Windows), one-time setup section (solver, channels, shell init), narrative environment walkthrough, Positron integration section with screenshot TODOs. `/new-project` skill referenced as automating environment creation and Positron configuration. Bioconda moved to advanced section at end.

- [x] Narrative tone throughout (scenarios, explanations, not bullet lists)
- [x] Added Miniforge installation section (was missing — installation.qmd deferred to this chapter)
- [x] One-time setup: libmamba solver, conda-forge channel, Windows shell init
- [x] "Creating your first environment" walkthrough with package explanations
- [x] Positron integration section: Command Palette → Select Interpreter workflow
- [x] 3 Claude Code callout boxes (package recommendations, environment diagnosis, Positron interpreter issues)
- [x] 3 screenshot TODOs (terminal prompt, Select Interpreter, status bar)
- [x] `/new-project` skill noted as automating env creation + package installation + Positron config
- [x] Bioconda/channels moved to later section (not beginner-critical)
- [x] Cut .condarc display, absorbed "Configuring Conda" into one-time setup
- [x] Best practices woven into narrative (never use base, pin Python, meaningful names)

#### Ch. 9 — Git & GitHub (REWRITE DONE — screenshots pending)

Full rewrite completed Feb 2026 (353 → 429 lines). Restructured from reference doc to narrative teaching guide. Added: Git installation section (macOS/Windows), GitHub setup (account, CLI, `gh auth login`), `git config` identity, "Your First Commit" hands-on walkthrough, "Exploring GitHub" web interface tour (Issues, README, file browsing), friendlier branches/PRs preview. Setup-walkthrough updated to cross-reference Ch. 9 for GitHub CLI auth.

- [x] Opening callback to Ch. 3 (matching pattern from Chs. 4, 6, 7, 8)
- [x] Git installation (macOS Xcode CLT/Homebrew, Windows git-scm.com, tabsets)
- [x] GitHub setup: account, CLI install, `gh auth login`, `git config`, joining MusserLab org
- [x] Narrative core concepts (not definition list)
- [x] "Your First Commit" hands-on walkthrough in Positron Source Control
- [x] "Exploring GitHub" section: web interface, file browsing, commit history, Issues
- [x] README as project landing page
- [x] Replaced "Beyond the Basics" with "As Your Projects Grow" framing
- [x] 3 Claude Code callout boxes (commit messages, .gitignore, confusing Git messages)
- [x] 5 screenshot TODOs placed throughout
- [x] Setup-walkthrough cross-references Ch. 9 for `gh auth login` (removed duplication)

### Screenshots

first-project.qmd is done (14 images in `images/first-project/`).

Positron chapter will need ~7 new screenshots after rewrite:
- [ ] Full interface with labeled panes
- [ ] Console and terminal tabs side by side
- [ ] Multiple tabs in bottom panel (R, Python, Terminal)
- [ ] Data Viewer with filtering active
- [ ] Outline panel with a .qmd file
- [ ] Command Palette with a search term
- [ ] Status bar annotated

Quarto chapter:
- [ ] Positron with .qmd, console, and Data Viewer (`quarto.qmd:60`)

Git chapter will need ~5 new screenshots after rewrite:
- [ ] `gh auth login` terminal prompts and successful authentication
- [ ] GitHub repo page showing file listing, recent commit, and README (MusserLab example)
- [ ] Positron Source Control panel showing a modified file and diff view
- [ ] GitHub Issue showing title, description, and linked commit
- [ ] Positron Source Control panel during first commit walkthrough

Conda chapter will need ~3 new screenshots after rewrite:
- [ ] Terminal showing `(my-project)` prompt after activation
- [ ] Positron Command Palette → Python: Select Interpreter with conda environments
- [ ] Positron status bar showing active Python environment

### Part 3: Working with AI (FULL REWRITE PLANNED — was "Claude Code")

Detailed plan: `.claude/CLAUDE_CODE_REWRITE_PLAN.md`

Expanding from 4 reference-style chapters to 6 narrative teaching chapters. Inspired by Anthropic's 4D AI Fluency Framework (Delegation, Description, Discernment, Diligence), adapted for data science students. Examples grounded in single-cell RNA-seq analysis. Includes deep research workflows for gene interpretation.

| Ch. | File | Title | Status |
|-----|------|-------|--------|
| 1 | `ai-fluency.qmd` | AI Fluency | TODO |
| 2 | `getting-started.qmd` | Getting Started | TODO (full rewrite) |
| 3 | `teaching-claude.qmd` | Teaching Claude About Your Work | TODO |
| 4 | `working-effectively.qmd` | Working Effectively | TODO (full rewrite) |
| 5 | `musser-lab-toolkit.qmd` | The Musser Lab Toolkit | TODO |
| 6 | `staying-safe.qmd` | Staying Safe | TODO |

Files to delete after rewrite: `configuring-projects.qmd`, `skills.qmd` (content absorbed into Chs. 3 and 5).

New appendix needed: Lab Skills Reference (complete table of all Musser Lab skills).

### Other Content
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
- [ ] **New Appendix E: Lab Skills Reference** — complete table of all Musser Lab Claude Code skills (part of Part 3 rewrite)

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

### 2026-02-24
- **Part 3 full rewrite planning session** — created `CLAUDE_CODE_REWRITE_PLAN.md` with detailed outlines for 6 new chapters
  - Expanding from 4 reference-style chapters to 6 narrative teaching chapters
  - Part renamed "Working with AI" (was "Claude Code"); directory stays `claude-code/`
  - Inspired by Anthropic's 4D AI Fluency Framework (Delegation, Description, Discernment, Diligence)
  - Ch. 1: AI Fluency — three interaction modes (automation/augmentation/agency), learning paradox, 4D framework adapted for data science
  - Ch. 2: Getting Started — narrative first session with Spongilla project (thinking + coding interactions)
  - Ch. 3: Teaching Claude About Your Work — CLAUDE.md, plan files, skills (simple → complex)
  - Ch. 4: Working Effectively — "Thinking Together" and "Coding Together" session patterns, deep research for gene interpretation, challenging Claude's recommendations
  - Ch. 5: The Musser Lab Toolkit — lab skills repo walkthrough, key skills, example CLAUDE.md files
  - Ch. 6: Staying Safe — permissions, hooks, settings.json, data protection, prompt injection
  - Cross-cutting: "Claude as thinking partner" framing in every chapter; learning paradox thread throughout
  - Domain focus: single-cell RNA-seq examples (Seurat, Spongilla) throughout all chapters
  - New Appendix E: Lab Skills Reference (complete table of all lab skills)
  - Registered plan in CLAUDE.md Project Document Registry

### 2026-02-23 (session 5)
- **Git & GitHub chapter (Ch. 9) full rewrite** — 353→429 lines, restructured from reference doc to narrative teaching guide
  - Opening callback to Ch. 3: "what happens when you want to go back to yesterday's version?"
  - NEW: Git installation section — macOS (Xcode CLT/Homebrew) and Windows (git-scm.com) with tabsets
  - NEW: GitHub setup — account creation, GitHub CLI install (macOS/Windows tabset), `gh auth login` walkthrough, joining MusserLab org
  - NEW: `git config --global user.name/email` identity setup
  - Core concepts rewritten as narrative flow (not definition list), with staging analogy
  - "Your First Commit" hands-on walkthrough in Positron Source Control panel
  - Expanded MusserLab section: README as landing page, public vs private explained with publication workflow
  - NEW: "Exploring GitHub" section: web interface tour, file browsing, commit history, Issues (creating + linking with `closes #12`)
  - Replaced "Beyond the Basics" with friendlier "As Your Projects Grow" — branches and PRs as concepts, cross-ref to Collaborating chapter
  - 3 Claude Code callouts (was 1): commit message writing, .gitignore generation, confusing Git messages
  - 5 screenshot TODOs: gh auth login, GitHub repo page, Positron diff view, GitHub Issue, first commit walkthrough
  - `setup-walkthrough.qmd`: replaced duplicated `gh auth login` instructions with cross-reference to Ch. 9

### 2026-02-23 (session 4)
- **Conda chapter (Ch. 8) full rewrite** — 476→444 lines, restructured from command reference to narrative teaching guide
  - New opening: renv callback, "conda does the same thing for Python" framing for someone with no Python experience
  - NEW: Miniforge installation section (macOS via Homebrew + direct download, Windows via installer) — fills gap where installation.qmd deferred to this chapter
  - One-time setup section: conda-forge channel priority, libmamba solver, Windows shell init — framed as "do this once, forget about it"
  - "Creating your first environment" walkthrough: explains every flag (`-n`, `python=3.11`, package list), ipykernel rationale woven into narrative
  - Positron integration section: Command Palette → Python: Select Interpreter workflow, with 3 screenshot TODOs
  - `/new-project` skill referenced as automating env creation, package installation, and Positron configuration
  - 3 Claude Code callouts: package recommendations for new analysis types, ModuleNotFoundError diagnosis, Positron interpreter detection issues
  - Best practices section rewritten narratively: "never install into base" with explanation, one env per project, pin Python version
  - Bioconda/channels moved to later section (not beginner-critical), shortened
  - Cut: .condarc YAML display, standalone "Configuring Conda" section, "Basic Commands" heading (commands woven into narrative)
  - Troubleshooting tightened, merged duplicate Windows init content

### 2026-02-23 (session 3)
- **R: rig & renv chapter (Ch. 7) full rewrite** — 580→~340 lines, restructured from reference documentation to narrative teaching guide
  - Opens with Ch. 3 callbacks: "what renv::init() actually did"
  - rig section: concrete scenario (upgrading R, old project breaks), Bioconductor tie-in
  - Fixed outdated `.vscode/settings.json` per-project R version → Command Palette approach
  - renv section built on Ch. 3 experience: walks through files created, explains snapshot/restore cycle as a story
  - 3 Claude Code callouts: package discovery for new analysis types, interpreting renv::status(), debugging installation errors
  - 4 screenshot TODOs: rig list, Command Palette R: Select R Binary, renv activation message, renv::status() output
  - "How rig and renv Work Together" section: renv.lock records R version + Bioconductor version + packages
  - Cut ~200 lines of package reference content → moved to new Appendix D: R Packages for Biology
  - Appendix D (`appendices/r-packages.qmd`): tidyverse, Bioconductor (with version table), RNA-seq packages, single-cell packages
  - Added `appendices/r-packages.qmd` to `_quarto.yml`

### 2026-02-23 (session 2)
- **Quarto chapter (Ch. 6) full rewrite** — 942→786 lines, restructured from reference doc to teaching guide
  - New "Compared to Jupyter Notebooks" subsection (plain text diffs, fresh-session rendering, Positron integration)
  - "Compared to Plain Scripts" reframed for both .R and .py
  - 7 R/Python tabsets: YAML header, setup chunk, inputs, saving outputs, working directory, rendering, provenance
  - New Claude Code callout for scaffolding QMD files (2 total in chapter)
  - Dissolved standalone "Working with Python" section — Python integrated everywhere
  - Cut ~160 lines of duplicated templates (Quick Reference), replaced with @sec-templates cross-refs
  - "Python-Specific Notes" short section at end (conda gotchas, ipykernel, session-info, no mixing)
  - Reference tables (YAML options, chunk options, R-vs-Python comparison) moved to Quick Reference at end

### 2026-02-23
- **Project Organization chapter (Ch. 5) full rewrite** — 496→458 lines, restructured from reference spec to narrative teaching guide
  - New opening: narrative hook about returning to a project after 6 months
  - "Two Rules" framing: inputs are sacred, outputs are disposable
  - `.claude/` introduced in project tree with forward ref to Claude Code chapters
  - `.qmd` as analysis format explained (was missing)
  - Exploratory directory elevated to its own section with one-way dependency rule
  - "Start flat, grow sectioned" guidance for project growth
  - Cross-language Parquet examples (R and Python)
  - `/new-project` referenced as the scaffolding tool
  - Reduced from two Mermaid diagrams to one
  - Complete example includes narrative walkthrough ("how would you find X?")
  - Fixed quarto.qmd cross-reference (`#output-files` → `#housekeeping`)

### 2026-02-22
- **Positron chapter (Ch. 4) full rewrite** — 385→~290 lines, restructured from UI-element tour to daily-workflow guide
  - New sections: Console vs Terminal, Managing Multiple Sessions, Status Bar, When Things Go Wrong
  - Windows terminal callout (PowerShell vs Unix differences, conda init, file paths)
  - Data Viewer: added CSV/TSV opening from File Explorer
  - File Explorer: project scope, + buttons for new files/folders
  - Restart R reframed: clean environment testing, NOT a rendering prerequisite
  - All `.vscode` → `.positron` (Positron uses its own settings directory)
  - Interpreter settings: internally remembered by Positron (no visible file written)
  - 3 Claude Code callout boxes, 7 screenshot TODOs
  - Preserved cross-reference anchors (#setting-the-r-version, #rstudio-positron-translation)
- Assessed all 6 Part 2 chapters; added priority-ordered polishing roadmap to PLAN.md
- Archived CLAUDE_CODE_CHAPTER_PLAN.md (marked COMPLETED Feb 2026)

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
