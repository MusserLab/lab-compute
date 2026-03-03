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

### Part 3: Working with AI (REWRITE DONE — was "Claude Code")

Detailed plan: `.claude/CLAUDE_CODE_REWRITE_PLAN.md`

Full rewrite completed Feb 2026. Expanded from 4 reference-style chapters to 6 narrative teaching chapters. Inspired by Anthropic's 4D AI Fluency Framework, adapted for data science students. Examples grounded in single-cell RNA-seq analysis. Includes deep research workflows for gene interpretation.

| Ch. | File | Title | Status |
|-----|------|-------|--------|
| 1 | `ai-fluency.qmd` | AI Fluency | DONE |
| 2 | `getting-started.qmd` | Getting Started | DONE (full rewrite) |
| 3 | `teaching-claude.qmd` | Teaching Claude About Your Work | DONE |
| 4 | `working-effectively.qmd` | Working Effectively | DONE (full rewrite) |
| 5 | `musser-lab-toolkit.qmd` | The Musser Lab Toolkit | DONE |
| 6 | `staying-safe.qmd` | Staying Safe | DONE |

Completed:
- [x] All 6 chapters written with narrative tone matching Parts 1-2 quality bar
- [x] Old `configuring-projects.qmd` and `skills.qmd` deleted (content absorbed into Chs. 3 and 5)
- [x] `_quarto.yml` updated: part renamed "Working with AI", 6 new chapters
- [x] Appendix E (Lab Skills Reference) created
- [x] `index.qmd` updated: Part 3 description and Work in Progress callout

Screenshots pending:
- [ ] Ch. 2: Positron sidebar with Claude Code icon (~4 screenshots)
- [ ] Ch. 6: Permission prompt, hook blocking a command (~2 screenshots)

### Other Content
- [x] Update "Work in Progress" callout in `index.qmd` — updated to "Parts 1–3 complete, Part 4 still being written"
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
- [x] **Appendix E: Lab Skills Reference** — complete table of all Musser Lab Claude Code skills

## Ideas for Future Chapters

- [ ] Common bioinformatics workflows

> **Note:** HPC/cluster computing, genomic resources, and data storage info will be in a separate "Lab Resources" reference, not this book.

## Completed

Major milestones (Feb 2026): Initial book created and published to GitHub Pages. All 26 chapters written across 4 parts + 5 appendices. Part 1 rewritten as hands-on Spongilla scRNA-seq tutorial with 14 screenshots. All 6 Part 2 chapters rewritten from reference docs to narrative teaching guides. Part 3 expanded from 4 reference-style Claude Code chapters to 6 narrative "Working with AI" chapters (AI fluency, getting started, teaching Claude, working effectively, Musser Lab toolkit, staying safe). Convention alignment pass reconciled all chapters with Claude Code skills. Code blocks standardized to `default`, callout boxes to `.callout-warning .claude-callout`. Cross-references audited clean. Appendices C (templates), D (R packages), and E (lab skills) created.

---

## Session Notes

_Add notes here during working sessions_

### 2026-02-24 (session 3)
- **Part 3 full rewrite — all 6 chapters written** in one session
  - Ch. 1 (AI Fluency, ~220 lines): Three interaction modes (automation/augmentation/agency), learning paradox as major section, 4D framework adapted for data science. Essayistic tone with concrete Spongilla examples.
  - Ch. 2 (Getting Started, ~120 lines): Two walk-through interactions — (1) thinking together about QC thresholds, (2) coding together to add violin plot. Approval flow taught through experience. 4 screenshot TODOs.
  - Ch. 3 (Teaching Claude, ~280 lines): CLAUDE.md built progressively from 5 lines to full mid-project example. Plan files from simple checklist to multi-file setup. Skills introduction (simple → slash commands → complex). Absorbs old configuring-projects.qmd and skills.qmd.
  - Ch. 4 (Working Effectively, ~330 lines): Exploration-first pattern, "Thinking Together" and "Coding Together" halves, deep research section (gene lists, DE interpretation), managing conversations, `/done` command, when things go wrong.
  - Ch. 5 (Musser Lab Toolkit, ~250 lines): Lab skills repo installation, 6 key background skills narratively explained, 4 slash commands, specialized skills preview, 3 example CLAUDE.md files at different project stages.
  - Ch. 6 (Staying Safe, ~180 lines): Permission system (diffs, commands, allow once vs session), hooks as automatic guardrails, settings at three levels, data protection (what Claude sends, credentials, web vs CLI), prompt injection brief.
  - `_quarto.yml`: Part renamed "Working with AI", 6 chapters listed, old configuring-projects and skills removed
  - Deleted: `configuring-projects.qmd`, `skills.qmd` (content absorbed into Chs. 3 and 5)
  - Created: Appendix E (`appendices/lab-skills.qmd`) — complete table of all lab background skills and slash commands
  - Updated: `index.qmd` Part 3 description and Work in Progress callout (Parts 1–3 complete)
  - Updated: `.claude/CLAUDE.md` project structure tree (new chapter list, new appendix)
  - Updated: `PLAN.md` status table (all 6 chapters DONE), session notes

### 2026-02-24 (session 2)
- **Cross-chapter consistency and beginner review** — read all Part 1 + Part 2 chapters, identified 20 issues, fixed all
  - Broken link: `project-organization.qmd` → `configuring-projects.qmd` (will be deleted in Part 3 rewrite) → updated to `getting-started.qmd`
  - Forward references: 6 `/new-project` mentions across 4 chapters now say "(covered in Part 3)"
  - Ordering: Quarto Python sections now note "read the Conda chapter first"; setup chunk template has "These Templates Require Git" callout
  - Git chapter: "Your First Commit" now walks through `git init` on the first-project folder; push section notes remote is required; `.gitignore` harmonized with project-organization chapter (removed redundant `*.rds`, added `renv/staging/` and `.positron/`)
  - Beginner fixes: added "Creating a New Document" paragraph in Quarto; Python setup chunk has inline comments; Parquet section explains type preservation and notes `arrow` install; `sys.path.insert` explained; `session-info` dash/underscore note
  - Minor: `.positron/` folder clarified; "Both Conda and renv" justified for single-language projects; Bioconductor release history link added; renv forward references softened; first-project mentions BUILD_INFO.txt as a Part 2 convention

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

### Earlier sessions (collapsed)
- **2026-02-23 (session 3):** R: rig & renv chapter (Ch. 7) full rewrite (580→~340 lines). Created Appendix D: R Packages for Biology.
- **2026-02-23 (session 2):** Quarto chapter (Ch. 6) full rewrite (942→786 lines). Added 7 R/Python tabsets, cut duplicated templates.
- **2026-02-23:** Project Organization chapter (Ch. 5) full rewrite (496→458 lines). "Two Rules" framing, narrative tone.
- **2026-02-22:** Positron chapter (Ch. 4) full rewrite (385→~290 lines). Assessed all Part 2 chapters, created polishing roadmap.
- **2026-02-21:** Claude Code callout icon (chat-dots), `.claude-callout` class on all 15 boxes. Getting-started and installation updates.
- **2026-02-20:** Wrap-up and publish of first-project work.
- **2026-02-19:** README rewritten to be reader-focused.
- **2026-02-18:** first-project.qmd major revision (biology/pedagogy feedback, 14 screenshots). Code block standardization to `default` (108 blocks, 15 files).
- **2026-02-14:** Convention alignment — reconciled book with Claude Code skills (10 files, 5 chapters).
- **2026-02-03:** Claude Code chapter planning session (TiHKAL analysis, gaps identified). renv chapter expanded (253→570 lines), Quarto chapter expanded (377→676 lines).
- **2026-02-02:** Major restructure (".qmd as unit of analysis"), Positron chapter rewrite (136→365 lines), Conda chapter expanded (311→456 lines), Windows platform coverage added.
- **2026-02-01:** Initial book created and published. Title set, rig installation, `/publish` and `/quarto-book-setup` skills created.
