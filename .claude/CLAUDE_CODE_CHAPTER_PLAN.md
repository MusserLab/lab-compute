# Claude Code Chapter Improvement Plan — COMPLETED Feb 2026

> **Status: Archived.** All items in this plan were implemented across Feb 2026 sessions. The Claude Code chapters were rewritten (Option A: 4 chapters, revised content), orange callout boxes were added across all book chapters, and project-specific skills were documented. See PLAN.md session notes for details.

This document captures the planning work done to improve the Claude Code sections of the lab_compute book.

---

## Project Goal

Improve the Claude Code chapters to:
1. Focus on the **Positron extension** as the primary interface (not CLI)
2. Build guidance around **actual usage patterns** from the TiHKAL project
3. Add **orange callout boxes** throughout all book chapters showing Claude Code use cases

---

## Current Book Structure

The book is organized into 4 parts + appendices:

```
Part 1: Quick Start
  - intro.qmd
  - installation.qmd
  - first-project.qmd

Part 2: Core Tools
  - positron.qmd
  - project-organization.qmd
  - quarto.qmd
  - renv.qmd
  - conda.qmd
  - git-github.qmd

Part 3: Claude Code (current)
  - intro.qmd
  - project-files.qmd
  - skills.qmd
  - session-walkthrough.qmd

Part 4: Workflows
  - starting-project.qmd
  - collaborating.qmd
  - reproducibility.qmd
  - troubleshooting.qmd

Appendices
  - shortcuts.qmd
  - commands.qmd
  - templates.qmd
```

### Book Style Notes
- Practical, hands-on approach with examples
- Uses callout boxes: `.callout-note` (blue), `.callout-tip` (green), `.callout-important` (yellow), `.callout-warning` (orange/red)
- Includes checklists, tables, quick reference sections
- Written for students with some coding experience
- Focus on reproducibility and collaboration

---

## Current Claude Code Section Assessment

### What's Already Covered

**intro.qmd** (124 lines)
- What Claude Code can do (write code, edit files, run commands, search, explain, debug)
- When to use / when not to use
- Basic interactions (asking questions, writing code, editing files, running commands)
- Mental model (capable assistant, doesn't know your domain, doesn't remember sessions)
- Currently describes CLI usage (`claude` command, `/exit`, `Ctrl+C`)

**project-files.qmd** (187 lines)
- Two levels: user (`~/.claude/CLAUDE.md`) and project (`.claude/CLAUDE.md`)
- Template for project CLAUDE.md
- What makes a good project file
- Example from "Sponge Cell Atlas" project

**skills.qmd** (326 lines)
- How skills work (folders in `~/.claude/skills/` with SKILL.md)
- Anatomy of a skill (frontmatter + instructions)
- Example skills: data-handling, r-plotting-style, git-conventions
- Creating your own skills
- Skill best practices

**session-walkthrough.qmd** (301 lines)
- Complete walkthrough of an RNA-seq QC analysis
- Steps: understand data → create script → run → refine → commit
- Patterns to notice: exploration first, be specific, iterate, review, commit logical units
- Common session patterns: debugging, extending, understanding, refactoring

### What's Missing (Gaps vs TiHKAL Workflow)

| Gap | Description |
|-----|-------------|
| **Positron extension** | Current chapters describe CLI; students will use the Positron extension |
| **Plan files** | TiHKAL uses PLOTTING_PLAN.md, TRANSCRIPTOMICS_DATA.md, etc. for tracking complex work |
| **Multi-file .claude/** | TiHKAL has 7+ markdown files in .claude/ for different concerns |
| **Project-specific skills** | TiHKAL has a `gene-naming` skill with domain-specific knowledge |
| **Context management** | When to start new chats, keeping sessions task-focused, avoiding bloat |
| **Prompt patterns** | Types of prompts that work well for data science |
| **Evolving documentation** | How to update CLAUDE.md and plan files as project progresses |
| **Status tracking** | Using plan files to track what's done/pending |

---

## TiHKAL Project Analysis

### .claude/ Directory Structure
```
TiHKAL/.claude/
├── CLAUDE.md                      # Main project instructions (340 lines)
├── PLOTTING_PLAN.md               # Figure-making plan with status tracking (502 lines)
├── TRANSCRIPTOMICS_DATA.md        # Specialized data documentation
├── CROSS_DATASET_COMPARISONS.md   # Comparison tracking
├── GENE_NAMING_PLAN.md            # Gene naming conventions
├── PDB_CONTACT_ANALYSIS_PLAN.md   # Structural analysis plan
├── SIGNALING_PATHWAY_REPORTS.md   # Pathway analysis tracking
├── TRANSCRIPTOMICS_PLOTTING_PLAN.md
├── settings.local.json
└── skills/
    └── gene-naming/SKILL.md       # Project-specific skill
```

### CLAUDE.md Patterns from TiHKAL

1. **Biological Context Section** — "What the phosphoproteomics is meant to test" with working interpretation
2. **Repository Layout** — Detailed folder structure with file descriptions
3. **Analysis Pipeline** — Key toggles, pipeline steps, key outputs
4. **Plotting Pipeline** — Scripts table, input/output structure, conventions
5. **Data Validation Notes** — Project-specific validation practices
6. **Common Failure Points** — Known gotchas specific to this project
7. **Links to Plan Files** — References to PLOTTING_PLAN.md, TRANSCRIPTOMICS_DATA.md, etc.
8. **Quick Start** — Steps to get up and running

### PLOTTING_PLAN.md Patterns

1. **Quick Reference** — Key inputs, sample types, scripts, output directories
2. **Technical Decisions Table** — Decisions with resolutions
3. **Figure Plan** — Prioritized list with status (DONE/TODO/WAITING)
4. **Implementation Notes** — How to implement each figure type
5. **Status Tracking Tables** — Per-figure status with notes

### Project-Specific Skill (gene-naming)

- Domain-specific knowledge (Trinity ID formats, join patterns)
- Correct code patterns with examples
- Warnings about common mistakes (apostrophe normalization, column mapping)
- Helper function documentation

---

## User-Level Skills to Document

Located at `~/.claude/skills/`:

| Skill | Purpose |
|-------|---------|
| `data-handling` | Data validation, summaries, show data at key steps, annotate decisions, ask before deciding |
| `r-plotting-style` | ggplot2 theme and conventions |
| `file-safety` | Rules for not overwriting important files |
| `conda-env` | Conda activation patterns |
| `r-renv` | R package management with renv |
| `quarto-docs` | Quarto rendering and formatting |
| `git-conventions` | Git commit practices |
| `quarto-publish` | Commit and publish Quarto projects to GitHub Pages |
| `quarto-book-setup` | Initialize a new Quarto book with GitHub Pages |
| `done` | End-of-session wrap-up and commit |
| `scientific-manuscript` | High-impact paper writing guidance |

**NOTE**: Next session should read the full content of these skills to understand what's valuable for the book.

---

## Orange Callout Boxes Plan

### Style Decision Needed
- User wants "Claude orange"
- Consider custom callout class in Anthropic/Claude style
- Need to define CSS or Quarto configuration

### Content Approach (User Feedback)
- **Simpler examples** — troubleshooting or helping set up one specific thing
- **More detailed prompts** — demonstrate how to be concise but provide specific/important information
- NOT complex multi-step workflows

### Proposed Callout Locations

| Chapter | Focus Area | Example Prompt Style |
|---------|------------|---------------------|
| installation.qmd | Verify setup | Specific error + what you tried |
| first-project.qmd | Create one component | Describe the specific thing needed |
| positron.qmd | Fix interpreter issue | Error message + what's happening |
| project-organization.qmd | Review structure | Ask about specific concern |
| quarto.qmd | Debug render error | Error message + relevant code |
| renv.qmd | Fix sync issue | Warning message + context |
| conda.qmd | Fix environment | Specific error + environment name |
| git-github.qmd | Resolve one issue | Describe the problem state |
| starting-project.qmd | Set up one piece | What you're trying to create |
| collaborating.qmd | Understand conflict | Show the conflict markers |
| reproducibility.qmd | Find one issue | Ask about specific file |
| troubleshooting.qmd | Enhance existing section | Add more specific examples |

---

## Proposed Claude Code Section Restructure

### Option A: Keep 4 chapters, revise content

| Current | Revised Focus |
|---------|---------------|
| intro.qmd → **getting-started.qmd** | Positron extension focus; CLI/apps as alternatives |
| project-files.qmd → **configuring-projects.qmd** | Add plan files, multi-file .claude/ pattern |
| skills.qmd | Add project-specific skills section |
| session-walkthrough.qmd → **working-effectively.qmd** | Context management, prompt patterns, evolving docs |

### Option B: Expand to 5-6 chapters

1. **Getting Started** — Positron extension, basic setup
2. **Project Configuration** — CLAUDE.md, plan files, multi-file structure
3. **Skills** — Global skills, project-specific skills
4. **Effective Prompting** — Prompt patterns for data science
5. **Managing Sessions** — Context, when to start fresh, task focus
6. **Real-World Example** — Extended walkthrough with TiHKAL-inspired patterns

---

## Next Steps for New Conversation

1. **Read user-level skills** at `~/.claude/skills/*/SKILL.md` to understand valuable patterns
2. **Create detailed outline** for revised Claude Code chapters
3. **Design orange callout style** — custom CSS/Quarto config
4. **Draft specific callout content** for each chapter with detailed but concise prompts
5. **Get user approval** on outline before writing full content

---

## Key Files to Reference

### Book files
- `_quarto.yml` — Book configuration
- All `.qmd` files in the book (listed above)

### TiHKAL reference
- `/Users/jm284/Dropbox/Documents-Db-Work/Research/Projects-primary/Roy_neurotransmitters/TiHKAL/.claude/CLAUDE.md`
- `/Users/jm284/Dropbox/Documents-Db-Work/Research/Projects-primary/Roy_neurotransmitters/TiHKAL/.claude/PLOTTING_PLAN.md`
- `/Users/jm284/Dropbox/Documents-Db-Work/Research/Projects-primary/Roy_neurotransmitters/TiHKAL/.claude/skills/gene-naming/SKILL.md`

### User skills to read
- `/Users/jm284/.claude/skills/data-handling/SKILL.md` (already read)
- `/Users/jm284/.claude/skills/r-plotting-style/SKILL.md`
- `/Users/jm284/.claude/skills/file-safety/SKILL.md`
- `/Users/jm284/.claude/skills/conda-env/SKILL.md`
- `/Users/jm284/.claude/skills/r-renv/SKILL.md`
- `/Users/jm284/.claude/skills/quarto-docs/SKILL.md`
- `/Users/jm284/.claude/skills/git-conventions/SKILL.md`
- `/Users/jm284/.claude/skills/done/SKILL.md`
- `/Users/jm284/.claude/skills/scientific-manuscript/SKILL.md`

---

## User Preferences Summary

1. **Primary interface**: Positron extension (mention CLI/apps exist, point to resources)
2. **Callout style**: Claude orange, possibly custom Anthropic-style class
3. **Callout content**: Simple, specific troubleshooting or setup help; detailed but concise prompts
4. **Examples**: Generic data science (informed by TiHKAL patterns, not TiHKAL-specific)
5. **Deliverable**: Detailed outline first, then implementation after approval