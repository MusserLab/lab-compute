# Claude Code Chapters: Detailed Outline

This outline details the structure and content for the revised Claude Code section (Part 3) and the orange callout boxes to be added throughout the book.

---

## Part 3: Claude Code (Revised Structure)

Recommend **Option A**: Keep 4 chapters, revise content to be more focused and practical.

---

### Chapter 1: Getting Started with Claude Code

**File:** `part3/getting-started.qmd` (rename from `intro.qmd`)

**Purpose:** Get students up and running with Claude Code in Positron, understand what it can do, and learn the mental model for effective use.

#### 1.1 What Is Claude Code?

- AI assistant that understands code, can read/edit files, run commands
- Runs in your project directory with full context
- Not a chatbot — a coding partner with real capabilities

#### 1.2 Accessing Claude Code

**Primary: Positron Extension (Focus here)**
- Opening Claude Code panel in Positron
- Starting a conversation
- Using `@` mentions to reference files
- Keyboard shortcuts: submit (Enter vs Ctrl+Enter), new conversation

**Alternatives (Brief mentions with links)**
- CLI: `claude` command (link to Anthropic docs)
- Desktop apps: Claude.app, Claude for Mac (link)
- Web: claude.ai (link)

*Why Positron? Your code, terminal, and Claude in one window. No context switching.*

#### 1.3 What Claude Code Can Do

| Capability | Examples |
|------------|----------|
| **Understand code** | Explain functions, trace data flow, find patterns |
| **Write code** | Create scripts, write functions, generate boilerplate |
| **Edit files** | Fix bugs, refactor, add features to existing files |
| **Run commands** | Execute R/Python scripts, git operations, file management |
| **Search** | Find where things are defined, grep for patterns |
| **Debug** | Trace errors, explain stack traces, fix issues |

#### 1.4 When to Use Claude Code (and When Not To)

**Good for:**
- Setting up project structure
- Debugging cryptic errors
- Understanding unfamiliar code
- Writing boilerplate (data loading, plotting templates)
- Troubleshooting environment issues
- Explaining what code does

**Not good for:**
- Making analytical decisions (you should decide normalization, thresholds)
- Replacing your domain knowledge (you know biology, Claude knows code)
- Complex statistical reasoning without verification
- Production code without review

#### 1.5 Mental Model for Working with Claude

Three key concepts:

1. **Capable but not omniscient** — Claude can write code but doesn't know your specific data, conventions, or project history
2. **Context matters** — Claude only knows what's in the current project and what you tell it
3. **Sessions are ephemeral** — Each new conversation starts fresh; use project files to persist knowledge

**Box: "Claude reads your project"**
- `.claude/CLAUDE.md` is read at every conversation start
- Put important context, conventions, gotchas there
- More on this in Chapter 2

---

### Chapter 2: Configuring Your Project for Claude

**File:** `part3/configuring-projects.qmd` (rename from `project-files.qmd`)

**Purpose:** Teach students how to set up Claude to work effectively on their project — from basic CLAUDE.md to plan files for complex projects.

#### 2.1 The Two Configuration Levels

| Level | Location | Purpose |
|-------|----------|---------|
| **User** | `~/.claude/CLAUDE.md` | Preferences that apply to all projects |
| **Project** | `.claude/CLAUDE.md` | Project-specific context, conventions, gotchas |

*Project settings are loaded automatically when you open Claude Code in that directory.*

#### 2.2 Creating Your Project CLAUDE.md

**Essential sections for a data analysis project:**

```markdown
# Project Name

## Overview
[1-2 sentences: what is this project analyzing?]

## Repository Layout
[Key folders and what's in them]

## Data
[Where raw data lives, key file formats, any conventions]

## Workflows
[How to run analyses, render documents, etc.]

## Conventions
[Coding style, naming patterns, etc.]

## Gotchas
[Things that have tripped you up — add as you discover them]
```

**Example: Minimal CLAUDE.md for a course project**

```markdown
# Stats 101 Final Project

## Overview
Analysis of penguin body measurements to predict species.

## Data
- Raw data: `data/penguins.csv` (from palmerpenguins package)
- Cleaned data: `data/penguins_clean.rds`

## Workflows
Render the analysis: `quarto render analysis.qmd`

## Conventions
- Use tidyverse style
- theme_classic() for all plots
```

#### 2.3 Evolving Your Project Documentation

Your CLAUDE.md should grow with your project:

| When | What to add |
|------|-------------|
| **After debugging** | Add the gotcha to prevent future confusion |
| **After decisions** | Document analytical choices and rationale |
| **After refactoring** | Update folder structure and conventions |
| **After collaboration** | Note team conventions and workflow |

**Good habit:** At the end of each session, ask yourself: "What did I learn that future sessions should know?"

#### 2.4 Plan Files for Complex Projects

For projects with many tasks, use dedicated plan files:

| File | Purpose |
|------|---------|
| `PLOTTING_PLAN.md` | Track figures to create, status, decisions |
| `ANALYSIS_PLAN.md` | Analytical steps, what's done/pending |
| `DATA_NOTES.md` | Data dictionary, preprocessing decisions |

**Plan file structure:**

```markdown
# Plotting Plan

## Quick Reference
- Input data: `data/results.rds`
- Output directory: `figures/`

## Figures

### Figure 1: Sample Overview
- Status: DONE
- Script: `scripts/01_sample_overview.R`
- Notes: Used log scale for y-axis

### Figure 2: Differential Expression Volcano
- Status: TODO
- Requirements: Need to decide FDR threshold

## Technical Decisions
| Decision | Resolution |
|----------|------------|
| Color palette | viridis for continuous, Set1 for categorical |
| Figure dimensions | 8x6 inches for main, 4x4 for supplementary |
```

**Why plan files?**
- Claude sees them and understands project status
- Track decisions so you don't repeat discussions
- Review what's done when returning after a break

#### 2.5 Multi-File .claude/ for Larger Projects

As projects grow, you might organize like this:

```
.claude/
├── CLAUDE.md              # Main project overview
├── PLOTTING_PLAN.md       # Figure tracking
├── DATA_NOTES.md          # Data documentation
├── ANALYSIS_DECISIONS.md  # Analytical choices with rationale
└── settings.local.json    # Claude Code settings
```

*Each file can be referenced from CLAUDE.md so Claude knows where to look.*

---

### Chapter 3: Skills

**File:** `part3/skills.qmd` (keep name)

**Purpose:** Explain how skills extend Claude's behavior and show students how to use existing skills and create their own.

#### 3.1 What Are Skills?

Skills are specialized instructions that:
- Load automatically when relevant (based on trigger conditions)
- Can be invoked manually with `/skillname`
- Customize Claude's behavior for specific tasks

*Think of skills as "expert modes" — when you're doing git work, the git skill loads. When you're plotting in R, the plotting skill loads.*

#### 3.2 User-Level Skills

Located at `~/.claude/skills/`, these apply across all projects. There are two types:

**Background Skills** — Load automatically based on context (you don't invoke them):

| Skill | When It Activates | What It Does |
|-------|-------------------|--------------|
| `data-handling` | Writing R/Python analysis code | Shows data summaries at key steps (`glimpse()`, row counts), annotates analytical decisions in comments, validates joins to prevent silent data loss, asks user before making important analytical choices |
| `r-plotting-style` | Creating ggplot2 visualizations | Applies `theme_classic()` base, no grid lines, uses ggrepel for labels, consistent sizing across related plots |
| `file-safety` | Creating or modifying files | Prevents overwriting collaborator outputs or raw data, creates versioned filenames instead, asks before uncertain overwrites |
| `git-conventions` | Git operations (commit, status, etc.) | Adds co-author line to commits, checks what will be committed, avoids committing secrets or large files |
| `conda-env` | Running Python scripts or pip commands | Sources conda profile script before activating environments (required in Claude's non-interactive shell) |
| `r-renv` | Working in R projects with renv.lock | Explains "out-of-sync" warnings, reminds about `renv::snapshot()` after installing packages |
| `quarto-docs` | Rendering .qmd files | Uses `quarto render` CLI (not `rmarkdown::render()`), knows format options and common errors |

**User-Invocable Skills** — You call these explicitly with `/command`:

| Command | When to Use | What It Does |
|---------|-------------|--------------|
| `/done` | End of a working session | Summarizes accomplishments, checks if renv needs updating, offers to commit changes with descriptive message, optionally publishes Quarto sites |
| `/publish` | After making changes to a Quarto book/website | Commits current changes and runs `quarto publish gh-pages` |
| `/quarto-book-setup` | Starting a new documentation project | Creates Quarto book structure with GitHub Pages configuration |

#### 3.3 Anatomy of a Skill

Skills live in folders with a `SKILL.md` file:

```
~/.claude/skills/
└── my-skill/
    └── SKILL.md
```

**SKILL.md structure:**

```markdown
---
name: skill-name
description: When to use this skill
user-invocable: false  # or true if it's a /command
---

# Skill Title

## When This Applies
[Conditions when Claude should follow these instructions]

## Instructions
[What Claude should do]

## Examples
[Code patterns, templates]
```

**Example: The data-handling skill**

Key instructions:
- Show `glimpse()` or row counts after loading/transforming data
- Annotate analytical decisions with comments explaining "why"
- Check for data loss after joins
- **Ask the user** before making important analytical choices

#### 3.4 User-Invocable Skills (Slash Commands)

Some skills are commands you invoke explicitly:

| Command | What It Does |
|---------|--------------|
| `/done` | End-of-session wrap-up: summarize, check renv, commit |
| `/publish` | Commit changes and publish Quarto site to GitHub Pages |
| `/quarto-book-setup` | Initialize new Quarto book with GitHub Pages |

*These are invoked by typing the command in Claude Code.*

#### 3.5 Project-Specific Skills

For domain-specific knowledge, create project skills:

```
.claude/
└── skills/
    └── gene-naming/
        └── SKILL.md
```

**When to create a project skill:**
- Repeated conventions specific to this project
- Domain knowledge Claude needs to apply correctly
- Code patterns that should be consistent

**Example: Gene naming skill for a transcriptomics project**

```markdown
---
name: gene-naming
description: Gene ID conventions for this project
user-invocable: false
---

# Gene Naming Conventions

## ID Formats
- Trinity IDs: `TRINITY_DN12345_c0_g1_i1`
- Short gene names: stored in `Gene.short` column
- Official symbols: stored in `Gene.symbol` column

## Joining Pattern
Always join on `trinity_gene_id`, not `Gene.short`:

```r
# CORRECT
data %>% left_join(annotations, by = "trinity_gene_id")

# WRONG - Gene.short may have duplicates
data %>% left_join(annotations, by = "Gene.short")
```

## Common Pitfall
Gene short names may contain apostrophes (5'→3' exonuclease).
Always normalize: `mutate(Gene.short = str_replace_all(Gene.short, "'", "'"))`
```

#### 3.6 Creating Your Own Skills

**Steps:**

1. Identify repeated guidance you give Claude
2. Create folder: `~/.claude/skills/my-skill/` (or `.claude/skills/` for project-specific)
3. Write `SKILL.md` with frontmatter and instructions
4. Test by starting a new conversation

**Best practices:**
- Keep skills focused on one topic
- Include concrete code examples
- Specify when the skill applies
- Update as you learn better patterns

---

### Chapter 4: Working Effectively with Claude

**File:** `part3/working-effectively.qmd` (rename from `session-walkthrough.qmd`)

**Purpose:** Teach practical patterns for effective Claude Code sessions — prompting, context management, and iterative refinement.

#### 4.1 Prompt Patterns That Work

**Be specific about what you want:**

| Less Effective | More Effective |
|----------------|----------------|
| "Fix this error" | "I'm getting this error when I run the script: [paste error]. The issue seems to be in the data loading section." |
| "Make a plot" | "Create a volcano plot of differential expression results. X-axis: log2 fold change. Y-axis: -log10 adjusted p-value. Highlight genes with adjP < 0.05 and |log2FC| > 1." |
| "Clean this up" | "Refactor this function to: 1) separate data loading from processing, 2) add error handling for missing files, 3) return a tibble instead of a list." |

**Provide context that helps:**
- What you're trying to accomplish (the goal)
- What you've already tried (saves time)
- Relevant file names or data structures
- Constraints (must use existing function, avoid dependencies, etc.)

#### 4.2 The Exploration-First Pattern

For unfamiliar code or complex tasks:

1. **Explore first** — Ask Claude to explain what exists before making changes
2. **Plan the approach** — Have Claude outline steps before implementing
3. **Implement incrementally** — One change at a time, verify each works
4. **Review and refine** — Check output, iterate on issues

**Example session flow:**

```
You: What does scripts/process_data.R do? Walk me through the main steps.

Claude: [explains the script]

You: I need to add a quality filter step after line 45. Before you write
code, what's your approach?

Claude: [describes approach]

You: That sounds right. Go ahead and implement it.

Claude: [makes the edit]

You: Run the script and show me the output.

Claude: [runs and shows result]

You: The counts look wrong. Why are we losing 80% of the data?

Claude: [investigates and explains]
```

#### 4.3 Managing Session Context

**When to start a new conversation:**
- Switching to a completely different task
- Context is getting cluttered with irrelevant history
- Claude seems confused or stuck in a wrong direction

**When to continue the current conversation:**
- Building on work you just did
- Fixing issues with recent changes
- Refining an approach

**Keep sessions focused:**
- One main task per conversation
- If a tangent becomes substantial, consider a new session
- Use plan files to track across sessions

#### 4.4 Reviewing Claude's Work

**Always review changes before accepting:**

| What to Check | Why |
|---------------|-----|
| Diffs shown in UI | See exactly what changed |
| Run the code | Verify it works |
| Check edge cases | Does it handle empty data, errors? |
| Read the logic | Does the approach make sense? |

**For analytical code, extra scrutiny:**
- Verify data counts at each step
- Check that joins matched as expected
- Confirm statistical choices are what you intended

#### 4.5 Common Session Patterns

**Debugging Pattern:**
1. Share the error message and relevant code
2. Ask Claude to explain what's happening
3. Let Claude propose a fix
4. Test the fix
5. If it fails, share the new error

**Understanding Pattern:**
1. Ask Claude to explain a function/file
2. Ask follow-up questions about specific parts
3. Ask how components connect

**Building Pattern:**
1. Describe what you want to create
2. Have Claude outline the approach
3. Implement piece by piece
4. Test and refine

**Refactoring Pattern:**
1. Explain what's wrong with current code
2. State goals for refactoring
3. Have Claude propose structure
4. Implement incrementally with testing

#### 4.6 Using the /done Command

End productive sessions with `/done`:

1. Summarizes what was accomplished
2. Checks if renv needs updating (R projects)
3. Offers to commit changes with descriptive message
4. Optionally publishes Quarto sites

*This ensures work is saved and documented.*

---

## Orange Callout Boxes: Content Plan

### Style Implementation

**Decision: Use custom CSS for true Claude orange.**

**Step 1:** Create or update `styles.css` in the project root:

```css
/* Claude orange callout - custom callout type */
.callout-claude {
  border-left: 4px solid #E87B35;  /* Claude/Anthropic orange */
  background-color: #FEF3EB;       /* Light orange tint */
}

.callout-claude .callout-header {
  background-color: transparent;
}

.callout-claude .callout-icon::before {
  background-image: none;  /* Remove default icon if desired */
}

.callout-claude .callout-title {
  color: #E87B35;
  font-weight: 600;
}

/* Dark mode support */
.quarto-dark .callout-claude {
  background-color: rgba(232, 123, 53, 0.15);
}
```

**Step 2:** Reference in `_quarto.yml`:

```yaml
format:
  html:
    css: styles.css
```

**Step 3:** Use in chapters:

```markdown
::: {.callout-claude title="Ask Claude"}
Your prompt example here...
:::
```

---

### Callout Content by Chapter

Each callout should:
- Focus on ONE specific problem/task
- Show a concise but specific prompt
- Demonstrate how to give useful context

---

#### Part 1: Quick Start

**installation.qmd**

::: {.callout-warning title="Ask Claude"}
**Verify your R installation:**

> I ran `R --version` and got this output: [paste output]. I also ran `which R` which shows [path]. Is this set up correctly, or do I need to fix something?

*Claude can verify paths are correct and diagnose common installation issues.*
:::

---

**first-project.qmd**

::: {.callout-warning title="Ask Claude"}
**Create a gitignore for your project:**

> I'm starting an R project for data analysis. What should go in my .gitignore? I'll have CSV files in data/, and I'm using renv.

*Claude can generate a .gitignore tailored to your specific project type.*
:::

---

#### Part 2: Core Tools

**positron.qmd**

::: {.callout-warning title="Ask Claude"}
**Fix interpreter issues:**

> Positron isn't finding my R installation. When I try to run code, I get "R interpreter not found." I installed R using rig and it works in terminal. What should I check?

*Describe what you expected vs what happened. Include any error messages.*
:::

---

**project-organization.qmd**

::: {.callout-warning title="Ask Claude"}
**Review your project structure:**

> Here's my project folder structure: [paste tree output or describe]. I'm analyzing RNA-seq data from three conditions. Does this organization make sense, or should I restructure anything?

*Ask for a review with specifics about your project type.*
:::

---

**quarto.qmd**

::: {.callout-warning title="Ask Claude"}
**Debug a render error:**

> When I run `quarto render analysis.qmd`, I get this error:
>
> [paste error]
>
> The code runs fine in the console. What's going wrong?

*Include the exact error. Mention if it works interactively — that's a useful clue.*
:::

---

**renv.qmd**

::: {.callout-warning title="Ask Claude"}
**Fix renv sync issues:**

> I'm getting this warning when I start R:
>
> `* Project 'myproject' is out-of-sync -- use renv::status() for details`
>
> I ran `renv::status()` and it shows: [paste output]. What should I do?

*Include the status output — it tells Claude exactly what's out of sync.*
:::

---

**conda.qmd**

::: {.callout-warning title="Ask Claude"}
**Fix conda environment issues:**

> I'm trying to run a Python script but getting "ModuleNotFoundError: No module named 'pandas'". I thought I installed it. Here's my environment: [paste `conda list` output or env name]. What's wrong?

*Include the environment name and what you tried.*
:::

---

**git-github.qmd**

::: {.callout-warning title="Ask Claude"}
**Understand a git message:**

> Git is showing me this message and I'm not sure what to do:
>
> ```
> Your branch and 'origin/main' have diverged,
> and have 2 and 3 different commits each, respectively.
> ```
>
> What does this mean and how do I fix it?

*Paste the exact git output. Claude can explain what happened and suggest safe next steps.*
:::

---

#### Part 4: Workflows

**starting-project.qmd**

::: {.callout-warning title="Ask Claude"}
**Set up your CLAUDE.md:**

> I'm starting a new project analyzing proteomics data from cell cultures. Can you create a starter .claude/CLAUDE.md for this project? The data is in data/raw/, I'm using R with renv, and rendering with Quarto.

*Tell Claude the project type, data location, and tools you're using.*
:::

---

**collaborating.qmd**

::: {.callout-warning title="Ask Claude"}
**Understand a merge conflict:**

> I have a merge conflict in `analysis.qmd`. Here are the conflict markers:
>
> ```
> <<<<<<< HEAD
> threshold <- 0.05
> =======
> threshold <- 0.01
> >>>>>>> feature-branch
> ```
>
> My collaborator changed the threshold. Which should I keep?

*Show the conflict. Explain the context so Claude can help you decide.*
:::

---

**reproducibility.qmd**

::: {.callout-warning title="Ask Claude"}
**Check reproducibility:**

> I need to make sure my analysis is reproducible. Can you check `analysis.qmd` for any issues? Things like hardcoded paths, missing package declarations, or code that might behave differently on another machine.

*Ask Claude to audit a specific file for reproducibility issues.*
:::

---

**troubleshooting.qmd**

(This chapter should integrate multiple callout examples as it's about getting help.)

::: {.callout-warning title="Ask Claude"}
**Debug a cryptic error:**

> I'm getting this error and don't understand it:
>
> ```
> Error in `mutate()`:
> ℹ In argument: `value = as.numeric(value)`.
> Caused by error:
> ! NAs introduced by coercion
> ```
>
> This is the code: [paste relevant code]. What's happening?

*Include both the error AND the code that caused it.*
:::

::: {.callout-warning title="Ask Claude"}
**Figure out why code stopped working:**

> This script was working yesterday and now fails with: [error]. I didn't change anything. What could have changed? Here's the script: [filename or paste].

*Mention what changed (or didn't). Claude can help trace environment or dependency issues.*
:::

---

## Summary of Proposed Changes

### Renamed/Restructured Files

| Current | New | Notes |
|---------|-----|-------|
| `part3/intro.qmd` | `part3/getting-started.qmd` | Positron focus, cleaner intro |
| `part3/project-files.qmd` | `part3/configuring-projects.qmd` | Add plan files, multi-file patterns |
| `part3/skills.qmd` | `part3/skills.qmd` | Add project skills section |
| `part3/session-walkthrough.qmd` | `part3/working-effectively.qmd` | Prompt patterns, context management |

### New Content by Chapter

| Chapter | Major Additions |
|---------|-----------------|
| getting-started | Positron extension as primary, alternatives as brief mentions |
| configuring-projects | Plan files, evolving docs, multi-file structure |
| skills | Project-specific skills, user-level skill details |
| working-effectively | Prompt patterns, context management, /done usage |

### Callout Boxes to Add

- **Part 1:** 2 callouts (installation, first-project)
- **Part 2:** 6 callouts (positron, project-organization, quarto, renv, conda, git-github)
- **Part 4:** 5 callouts (starting-project, collaborating, reproducibility, troubleshooting×2)

**Total: 13 orange callout boxes across the book**

---

## Next Steps

1. **Get approval on this outline**
2. Design/test the callout styling (CSS or built-in)
3. Revise Chapter 1 (getting-started.qmd)
4. Revise Chapter 2 (configuring-projects.qmd)
5. Revise Chapter 3 (skills.qmd)
6. Revise Chapter 4 (working-effectively.qmd)
7. Add callout boxes to all other chapters
8. Update `_quarto.yml` with new chapter names