<!-- project-type: general -->
# Data Analysis in the Musser Lab

## Overview

A Quarto book teaching Musser Lab students how to set up reproducible data analysis workflows using modern tools: Positron, conda, renv, Git/GitHub, and Claude Code.

**Author:** Jacob Musser, in collaboration with Claude Code
**Live site:** https://MusserLab.github.io/lab-compute/
**Repository:** https://github.com/MusserLab/lab-compute

## Project Structure

```
lab_compute/
├── _quarto.yml           # Book configuration
├── index.qmd             # Welcome page
├── part1/                # Quick Start
│   ├── intro.qmd
│   ├── installation.qmd  # Uses rig for R installation
│   └── first-project.qmd # Hands-on Positron + Seurat tutorial
├── part2/                # Core Tools (deep dives)
│   ├── positron.qmd
│   ├── project-organization.qmd
│   ├── quarto.qmd
│   ├── renv.qmd
│   ├── conda.qmd
│   └── git-github.qmd
├── claude-code/          # Claude Code (Part 3)
│   ├── getting-started.qmd
│   ├── configuring-projects.qmd
│   ├── skills.qmd
│   └── working-effectively.qmd
├── part3/                # Workflows (Part 4)
│   ├── setup-walkthrough.qmd  # Full lab project setup (git, conda, renv, GitHub)
│   ├── starting-project.qmd   # Quick reference/checklist + templates
│   ├── collaborating.qmd
│   ├── reproducibility.qmd
│   └── troubleshooting.qmd
├── appendices/
│   ├── shortcuts.qmd
│   ├── commands.qmd
│   └── templates.qmd
├── images/               # Screenshots (TODO)
└── examples/             # Code examples
```

## Project Document Registry

### Planning Documents

| Document | Topic | Has status table? |
|----------|-------|:-:|
| [PLAN.md](.claude/PLAN.md) | Book roadmap, open items, session notes | Yes |
| [CLAUDE_CODE_CHAPTER_PLAN.md](.claude/CLAUDE_CODE_CHAPTER_PLAN.md) | Claude Code chapter research and outline (COMPLETED) | No |

### Convention/Reference

| Document | Topic |
|----------|-------|
| [CLAUDE.md](.claude/CLAUDE.md) | This file — project overview, conventions, registry |

## Key Decisions

- **Audience:** Students with some coding experience (not complete beginners)
- **Languages:** Both R and Python as first-class citizens
- **Platforms:** macOS and Windows instructions throughout
- **R installation:** Uses `rig` (R Installation Manager), not direct CRAN download
- **Hosting:** GitHub Pages (public), linked from lab website

## Workflows

### Preview locally
```bash
quarto preview
```

### Publish changes
Use the `/publish` skill to commit and publish in one step.

Or manually:
```bash
git add .
git commit -m "Description of changes"
git push
quarto publish gh-pages
```

### Keep README in sync
When making significant changes to the book (title, structure, content scope), update `README.md` to match. The README should reflect:
- Current book title and description
- What the book covers
- Links to the live site

## Available Skills

| Skill | Trigger | Purpose |
|-------|---------|---------|
| `/publish` | User types `/publish` | Commit and publish to GitHub Pages |
| `/done` | User types `/done` | End-of-session wrap-up, update PLAN.md |

### Add screenshots
Place images in `images/` folder and reference with:
```markdown
![Description](../images/filename.png)
```

Screenshots are marked with `[TODO: screenshot]` throughout.

## References

- **TiHKAL** and **Genomic Resources** projects can be referenced as real-world examples
- User's Claude Code setup (skills, CLAUDE.md patterns) documented in the claude-code.qmd chapter

## Writing Conventions

- **Terminal commands** use `` ```default `` fenced blocks — this gives a styled code box with copy button but no syntax coloring. Do NOT use `bash`, `powershell`, or `{.text}` for terminal commands. (`bash` adds unwanted syntax coloring; `{.text}` loses the code box styling and copy button.)
- **Claude Code callout boxes** use `::: {.callout-warning .claude-callout title="Claude Code"}` — orange warning callout with a chat-dots icon (overridden via `.claude-callout` class in `styles.css`). Each box has: (1) a 1–2 sentence intro, (2) a blockquoted example prompt, (3) an explanation of what Claude Code will do. The `.claude-callout` class is required — without it the box gets the default warning triangle icon.
- **macOS + Windows**: Every terminal instruction includes both platforms. Always mention which app to open (Terminal on macOS, PowerShell on Windows).
- **Restart terminal reminders**: After every installation step, remind students to close and reopen their terminal so new commands are available.
- **Homebrew references**: Always briefly explain what Homebrew is when first mentioning `brew` commands, and provide a non-Homebrew alternative (download link).
- **Tone**: Friendly, narrative paragraphs over bullet lists. Write things out rather than listing them. The audience has some coding experience but is not expert.
- **Parts 2–4 are marked "Work in Progress"** in the Welcome page.

## Notes

- The book uses the `cosmo` theme (light) and `darkly` theme (dark)
- Code blocks have copy buttons enabled
- Chapters are numbered automatically