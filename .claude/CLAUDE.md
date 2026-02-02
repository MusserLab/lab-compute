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
├── part1/                # Quick Start (get running in 30 min)
│   ├── intro.qmd
│   ├── installation.qmd  # Uses rig for R installation
│   └── first-project.qmd
├── part2/                # Core Tools (deep dives)
│   ├── positron.qmd
│   ├── conda.qmd
│   ├── renv.qmd
│   ├── git-github.qmd
│   └── claude-code.qmd
├── part3/                # Workflows
│   ├── starting-project.qmd
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

## Notes

- The book uses the `cosmo` theme (light) and `darkly` theme (dark)
- Code blocks have copy buttons enabled
- Chapters are numbered automatically