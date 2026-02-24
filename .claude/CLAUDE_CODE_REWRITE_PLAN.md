# Claude Code Section — Full Rewrite Plan

> Created: 2026-02-24
> Status: APPROVED — ready for implementation

## Overview

Complete rewrite of Part 3 ("Working with AI", formerly "Claude Code") from 4 reference-style chapters to 6 narrative teaching chapters. Current chapters read like feature documentation; new chapters should match the narrative, friendly tone established in the Part 2 rewrites (Ch. 3 first-project is the quality bar).

**Audience:** Students new to data science who have some R experience but are still learning to code and analyze data. They need to build Claude Code into their toolkit *while still learning the basics*. The central tension: Claude Code is too powerful not to use, but students must learn to use it safely, effectively, and as a learning tool — not a crutch.

**Domain focus:** Examples and references throughout should be grounded in single-cell RNA-seq analysis (Seurat, Spongilla dataset from Ch. 3), since this is the primary analysis type students will be doing. Other examples (phylogenetics, DE interpretation) are secondary.

**Critical framing note:** Claude is not just a coding tool. It is equally valuable as a *thinking partner* for the scientific and analytical side of data science. This means: planning analysis approaches, understanding what statistical or methodological choices need to be made and why, identifying and discussing relevant literature, evaluating methods critically, interpreting results biologically, and making sense of unexpected findings. Every chapter should reflect both sides — Claude as a coding collaborator AND Claude as an intellectual collaborator. The "thinking together" side is arguably more important for students who are still developing their analytical judgment.

**Inspiration:** Anthropic's [AI Fluency: Framework & Foundations](https://anthropic.skilljar.com/ai-fluency-framework-foundations) course, particularly the 4D framework (Delegation, Description, Discernment, Diligence). We adapt this for a data science context with concrete lab examples.

**Current files to replace:**
- `claude-code/getting-started.qmd` (145 lines)
- `claude-code/configuring-projects.qmd` (248 lines)
- `claude-code/skills.qmd` (236 lines)
- `claude-code/working-effectively.qmd` (254 lines)

**New file structure:**
```
claude-code/
├── ai-fluency.qmd              # Ch. 1: AI Fluency
├── getting-started.qmd         # Ch. 2: Getting Started (full rewrite)
├── teaching-claude.qmd         # Ch. 3: Teaching Claude About Your Work
├── working-effectively.qmd     # Ch. 4: Working Effectively (full rewrite)
├── musser-lab-toolkit.qmd      # Ch. 5: The Musser Lab Toolkit
└── staying-safe.qmd            # Ch. 6: Staying Safe
```

**_quarto.yml update:**
```yaml
- part: "Working with AI"
  chapters:
    - claude-code/ai-fluency.qmd
    - claude-code/getting-started.qmd
    - claude-code/teaching-claude.qmd
    - claude-code/working-effectively.qmd
    - claude-code/musser-lab-toolkit.qmd
    - claude-code/staying-safe.qmd
```

Note: Part title changes from "Claude Code" to "Working with AI" since Ch. 1 covers AI fluency broadly. File directory stays `claude-code/` to avoid breaking links.

**Files to delete after rewrite:**
- `claude-code/configuring-projects.qmd` (content absorbed into teaching-claude.qmd)
- `claude-code/skills.qmd` (content split between teaching-claude.qmd and musser-lab-toolkit.qmd)

---

## Chapter 1: AI Fluency {#ch1}

**File:** `claude-code/ai-fluency.qmd`
**Tone:** Conceptual and reflective, but grounded in concrete data science examples. More essayistic than hands-on. Jake's personal experiences throughout.
**Target length:** ~400-500 lines

### Opening

Narrative hook: You've just learned the tools of data science (Positron, Quarto, R, conda, Git). Now you have a collaborator that can write code, debug errors, and explain methods — but it's not a person, and working with it well is a skill unto itself. This chapter teaches that skill.

### Section 1: Three Ways to Work with AI

Frame the three interaction modes with data science examples:

1. **Automation** — "Rename all my variables to snake_case." Direct, specific, mechanical. Claude does exactly what you say. Useful but limited — you're just using AI as a fast typist.

2. **Augmentation** — You're thinking together. Claude brings knowledge, you bring judgment. This covers a wide range of activities that go well beyond coding:
   - *Analytical planning:* "I have single-cell data from 4 Spongilla samples. What are the main steps in a standard analysis, and what choices will I need to make at each step?"
   - *Method evaluation:* "What normalization methods should I consider for my count data, and what are the tradeoffs? What does the literature recommend for datasets like mine?"
   - *Literature exploration:* "What papers should I read to understand how people identify cell types in non-model organisms?" or "Find me recent papers on trajectory inference for developmental data."
   - *Result interpretation:* "Here are the top marker genes for cluster 5. What biological processes are these associated with? What cell type might this be?"
   - *Troubleshooting analytical decisions:* "My UMAP shows two clusters merging. What could cause this and how should I think about whether to split or merge them?"
   This is research, planning, interpretation, and learning — the intellectual side of data science, not just the coding side.

3. **Agency** — "Here's my count matrix and metadata. Write a QC script that flags outlier samples and generates diagnostic plots." Claude reads your data, makes decisions, writes code, runs it. Powerful but requires trust and verification.

Key insight: Most students default to mode 1 (tell it what to type) or jump straight to mode 3 (do it for me). Mode 2 — *thinking together* — is where the real power is, and it's also where you learn the most.

**Jake's examples:** Brief, concrete stories of how Jake actually uses each mode in his research. Mode 1 example: "rename all the cluster labels in my Seurat object to match the new naming convention." Mode 2 example: "I have a set of differentially expressed genes from my single-cell clusters — help me make sense of what these cell types are doing" (using deep research to interpret DE results — better than GO enrichment for building biological narratives). Mode 3 example: having Claude write and iterate on a complex multi-panel figure comparing marker gene expression across cell types.

**Deep research preview:** Briefly introduce the concept of asking Claude to do extended research — this needs to be explained concretely (what it is, how to access it) since students won't know the term. Example: generating curated gene lists for signaling pathways (Wnt, Notch, TGF-beta) that you then explore in your single-cell data with FeaturePlot. Or: interpreting a list of DE genes by reading the literature and producing a narrative synthesis. Full workflow covered in Ch. 4.

### Section 2: The Learning Paradox

**This is a major section, not a sidebar.** Directly addresses the tension:

- You're learning to code AND using a tool that can write code for you
- The temptation: let Claude do everything, copy-paste, move on
- The problem: you don't learn, you can't evaluate the output, you can't troubleshoot when things break
- The solution: use Claude as a *teacher*, not just a *producer*

**Concrete patterns for learning mode:**
- After Claude writes a script, ask it to walk you through every line
- Before accepting a statistical method, ask *why* it chose that approach — then ask for the counterargument and alternative methods
- Ask Claude to find you the key papers on a method, then actually read them
- Run scripts interactively (line by line in Positron console), not just `quarto render`
- When Claude suggests a package, ask what it does and whether alternatives exist
- Dissect the output: "Why did 200 genes get filtered out? What would happen if I changed the threshold?"
- When Claude gives a confident recommendation, ask: "What would someone who disagrees with this approach say? Find me papers that argue for a different method."

**The rule of thumb:** If you can't explain what the code does *and why you chose this approach over alternatives* to a labmate, you accepted it too quickly.

### Section 3: The 4D Framework (adapted from Anthropic)

Introduce the four core competencies for working with AI. Credit the Anthropic AI Fluency course as inspiration. Each principle includes "what this looks like in data science" examples.

**1. Clear Communication (Description)**
- Background: what your data looks like, what you've tried, what the project is about
- What you want: specific, concrete requests
- What a good outcome looks like: expected output format, dimensions, style

LLM context woven in here: *Why* being specific matters. Claude doesn't have memory between sessions. Each conversation starts from your CLAUDE.md and what you tell it. It's predicting helpful responses based on what you've provided — the more precise your request, the better the prediction. (This naturally introduces context windows without a standalone architecture lecture.)

**2. Evaluating Output Critically (Discernment)**
- Claude produces plausible-looking code that may have subtle bugs
- Statistical methods: Claude may choose a method that's technically valid but inappropriate for your data
- Biological interpretation: Claude doesn't know your organism, your experimental design, or your scientific question the way you do
- **Claude gives clean, confident answers — but science is messy.** Train yourself to ask: "What's the argument against this? What would a reviewer object to? Find me papers that take a different approach." Claude is remarkably good at presenting counterarguments when you ask for them. This is one of the most powerful habits you can develop.

LLM limitations woven in here: *Why* Claude sometimes gets things wrong. It's a language model — it predicts likely continuations of text. It can't run the code in its head, doesn't truly "understand" statistics, and sometimes produces confident-sounding nonsense ("hallucination"). This isn't a bug to be fixed; it's a fundamental property to work around.

Concrete checks for code: verify row counts at each step, spot-check join results, compare statistical output to published methods, run a sanity check on a few genes by hand.

Concrete checks for scientific claims: ask Claude for the primary literature supporting its recommendation, ask for the counterargument, read the actual papers (not just Claude's summary), compare to what established researchers in your field recommend.

**3. Delegation (Delegation)**
- What to give Claude: boilerplate, repetitive code, debugging, code explanation, scaffolding
- What to keep for yourself: analytical decisions, biological interpretation, method selection for key analyses, understanding what the code does
- The gray zone: Claude can suggest methods, but you decide. Claude can write the statistics, but you verify the assumptions

This principle benefits from some experience to fully appreciate, which is why it comes third. By now the student understands *how* to communicate and *why* to verify — they can start thinking about *what* to hand off.

**4. Ethics and Acknowledgment (Diligence)**
- Be transparent about AI use: tell collaborators, note it in methods sections
- Lab convention: co-author line in git commits (already established in Git chapter)
- Don't pass off AI-generated analysis as your own intellectual work
- When Claude helps with writing (manuscripts, reports), disclose it
- Data privacy: don't paste sensitive/unpublished data into web-based AI without considering implications (forward-reference to Ch. 6 security)

### Closing

These four principles aren't rules to memorize — they're habits to build. The rest of this section shows you how to put them into practice with Claude Code specifically. Refer back to this chapter when things feel off in a Claude Code session; usually one of these four principles will point to the issue.

---

## Chapter 2: Getting Started with Claude Code {#ch2}

**File:** `claude-code/getting-started.qmd`
**Tone:** Hands-on, narrative walk-through. "Your first real session." Similar feel to Ch. 3 (first-project).
**Target length:** ~300-350 lines

### Opening

Callback to the first-project chapter: "In Chapter 3, you built a single-cell analysis with Seurat. You probably noticed Claude Code callout boxes throughout the book suggesting things you could ask Claude. Now you're going to actually use it."

### Section 1: Before You Start (brief)

Prerequisites checklist linking back to installation chapter. Keep this short — 10-15 lines max. Students who followed the book already have everything installed.

### Section 2: Opening Claude Code in Positron

Narrative walk-through of opening the extension, seeing the chat panel, understanding what Claude can see (your project files). Screenshot TODOs.

Key shortcuts: submitting messages, new conversations, `@` file references. Keep this practical, not a table dump.

### Section 3: Your First Conversation

Walk through a realistic first interaction. Not a contrived demo — something a student would actually do.

**Decided:** Two short interactions, back to back, to show both sides of Claude from the start:

**Interaction 1 (thinking together):** Student has the Spongilla project from Ch. 3 open. Ask Claude a conceptual question: "In the analysis script, we filter cells based on nFeature_RNA. How do I know what threshold to use? What are people typically looking for here?" Claude explains the biology (dying cells, doublets, empty droplets), discusses how thresholds depend on the data, and suggests looking at a violin plot to decide. This models Mode 2 — no code is written, but the student understands a decision they previously just copied.

**Interaction 2 (coding together):** Following directly from the conversation: "Can you add a violin plot of nFeature_RNA to the QC section so I can see the distribution before filtering?" Claude reads the script, proposes an edit, shows the diff. Student reviews and accepts. This models Mode 3 — Claude writes code, student verifies.

Together these immediately demonstrate that Claude is both a thinking partner and a coding partner.

The walk-throughs should show:
- What the student types (realistic prompt, not perfect)
- What Claude does (explains reasoning; reads files and proposes changes)
- The student reviewing and accepting/modifying
- The diff view and approval flow

### Section 4: What Claude Code Can Actually Do

Brief capabilities overview — but framed as a story, not a table. "You just saw Claude read your script and explain it. It can also edit files directly — here's what that looks like..." Walk through each capability with a one-sentence example tied to their Spongilla project.

### Section 5: The Terminal Alternative

Brief mention that Claude Code also works in the terminal. Some people prefer it. Show the command. Don't belabor it — Positron is the primary interface for this audience.

### Section 6: Three Things to Remember

Reinforce Ch. 1 principles, now that they've experienced Claude firsthand:
1. Be specific (they just saw how their prompt shaped the response)
2. Verify the output (they just reviewed a diff)
3. Claude doesn't remember — each new conversation starts fresh (sets up Ch. 3)

---

## Chapter 3: Teaching Claude About Your Work {#ch3}

**File:** `claude-code/teaching-claude.qmd`
**Tone:** Mix of conceptual (why persistent context matters) and hands-on (creating files, writing skills). Progressive complexity: simple → advanced.
**Target length:** ~450-550 lines

### Opening

"You just experienced the limitation: Claude doesn't remember yesterday's session. But there's a solution. You can teach Claude about your project — your data, your conventions, your analytical decisions — so that every new conversation starts with shared understanding."

### Section 1: Your Project CLAUDE.md

The foundation. What it is, where it lives (`.claude/CLAUDE.md`), what to put in it.

Walk through creating one for a hypothetical single-cell project, building it up progressively:
1. Start with 5 lines: project name, what the data is, how to render
2. Add the scientific context: organism, experimental design, key questions ("comparing developmental stages X and Y")
3. Add analytical decisions as you make them ("chose SCTransform over LogNormalize because [reason]"; "excluded Sample S23 — failed QC, low gene counts")
4. Add conventions (theme_classic, tidyverse style) and key files as the project grows

**Key point:** CLAUDE.md isn't just about code — it's about the scientific context too. When Claude knows your organism, your experimental design, and the questions you're asking, its suggestions for both analysis approaches *and* code are dramatically better.

**Template:** Provide the research project template (similar to current chapter but narrative, not just a code block).

**The habit:** "At the end of each session, ask yourself: what did I learn that future sessions should know?" Show how Claude Code can help with this — ask Claude to summarize what was decided in the session and suggest additions to CLAUDE.md.

### Section 2: User-Level Configuration

Brief section on `~/.claude/CLAUDE.md` — preferences that apply everywhere. Keep it short. This is where conda sourcing, quarto paths, and universal preferences live.

Explain the two-level system: user config + project config, project takes precedence.

### Section 3: Plan Files for Complex Projects

When a project gets complex enough that CLAUDE.md alone isn't sufficient. Introduce plan files as living documents that track status, decisions, and pending work.

Start with a simple, relatable example for beginners:
- ANALYSIS_PLAN.md — "where am I in the pipeline?" A simple checklist: QC done, normalization done, clustering in progress, DE not started. Decisions recorded along the way ("chose 20 PCs because elbow plot showed diminishing variance after ~15").

Then show how plan files scale for more complex projects:
- PLOTTING_PLAN.md — figure tracking with status table (for a project with many figures)
- DATA_NOTES.md — data provenance and known issues (for projects with multiple data sources)

Show how to reference plan files from CLAUDE.md. Explain that Claude reads the `.claude/` folder and uses plan files to understand project status.

**Key point:** Plan files aren't just for Claude — they're good science practice. When you come back to a project after a month, the plan file tells you where you left off.

### Section 4: Skills — Teaching Claude How to Work

Progressive introduction:

**What skills are:** Reusable instruction sets that customize Claude's behavior. They live in folders with a SKILL.md file. Claude loads them based on context (file types, keywords, task type).

**Simple skills:** A skill that says "use theme_classic() for all ggplot2 plots" or "always show data dimensions after loading." Just a few lines of markdown with code examples. Walk through creating one.

**Background vs. slash command skills:** Background skills load automatically when relevant. Slash commands (like `/done`) are invoked explicitly. Explain the difference with examples.

**Complex skills:** Skills that carry associated files, reference external scripts, or contain detailed multi-step workflows. Example: the `protein-phylogeny` skill that generates a full `.qmd` analysis pipeline. Don't go into exhaustive detail — the point is that skills can be as simple or sophisticated as needed.

**Anatomy of a skill file:** Frontmatter (name, description, user-invocable) and instructions body. Show a real example.

### Section 5: How Claude Code Can Help Build These Files

Concrete prompts showing how to ask Claude to:
- Draft an initial CLAUDE.md based on the current project structure
- Create a plan file for tracking figures
- Write a simple skill based on conventions you describe
- Update CLAUDE.md with decisions from the current session

This section reinforces that Claude Code is a tool for managing its own configuration.

### Brief forward-reference

"There are other ways to customize Claude Code's behavior — hooks that run automatically, permission settings that control what Claude can do. We'll cover those in [Staying Safe](#ch6)."

---

## Chapter 4: Working Effectively with Claude {#ch4}

**File:** `claude-code/working-effectively.qmd`
**Tone:** Practical, pattern-oriented. Mix of conceptual framing and concrete examples. This is the "art of collaboration" chapter.
**Target length:** ~500-600 lines (largest chapter — includes the deep research section)

### Opening

"You know what Claude Code is (Ch. 2), and you've taught it about your project (Ch. 3). Now let's talk about how to actually work together productively. This isn't about memorizing commands — it's about developing instincts for when to ask, what to ask, and how to evaluate what you get back."

### Section 1: The Exploration-First Pattern

The most important workflow pattern. Before asking Claude to *do* something, ask it to *explain* or *plan*:

```
You: What does the normalization section of analysis.qmd do?
Claude: [explains]
You: I want to try a different method. What are my options?
Claude: [discusses tradeoffs]
You: Let's go with method X. Implement it.
Claude: [edits]
```

Why this works: catches misunderstandings before they become wrong code. Also exercises the learning mode from Ch. 1.

### Section 2: Session Patterns for Common Tasks

Narrative walk-throughs organized into two categories: thinking together and coding together. Both are equally important parts of working with Claude.

#### Thinking Together (Mode 2)

**Planning an analysis approach:**
- "I have 4 single-cell samples from different developmental stages. What's the best strategy for integrating them? What methods exist and when should I use each one?"
- Claude discusses options (Seurat integration, Harmony, scVI), tradeoffs, and what to look for when evaluating results
- You read the papers Claude references, then decide which method to use
- This is where students develop analytical judgment — by discussing options *before* writing code

**Evaluating a method choice:**
- "The tutorial I'm following uses SCTransform for normalization. Is that the right choice for my data? What are the alternatives?"
- Claude explains the assumptions behind each method and what makes them appropriate or not
- Key pattern: don't just follow tutorials blindly — ask Claude to help you understand *why* each step exists

**Challenging Claude's recommendations (critical thinking):**
- Claude tends to give you a clean answer. But science is full of debate. Students should learn to push back:
- "What's the argument *against* this approach? What would a skeptic say?"
- "Are there papers that disagree with this method? Find them for me."
- "Give me the counterargument — why might someone choose a different approach?"
- "What are the limitations of this method that you haven't mentioned?"
- This is one of the most valuable skills students can develop: treating Claude as a knowledgeable colleague who you can ask to play devil's advocate, present alternative viewpoints, or find dissenting literature. It trains scientific thinking — the habit of considering multiple perspectives before committing to a decision.

**Interpreting results:**
- "Here are my cluster markers. What do these genes suggest about cell type identity?"
- "My differential expression found 500 significant genes between these two conditions. How do I make sense of this?"
- Claude synthesizes biological knowledge to help you form hypotheses — which you then verify against literature and your own domain knowledge

**Finding relevant literature:**
- "What are the key papers on cell type deconvolution in sponges?"
- "I'm seeing unexpected Wnt pathway expression in my pinacocytes. Is this known in the literature?"
- Claude identifies papers and summarizes their relevance — you read the actual papers

#### Coding Together (Mode 3)

**Debugging an error:**
- Paste the actual error message (not a paraphrase)
- Point to where it happens (file, line number)
- Include context on what you were trying to do
- Example: a realistic Seurat error with the full conversation flow

**Understanding code you didn't write:**
- "Walk me through this function line by line"
- "Why does this use `left_join` instead of `inner_join`?"
- Connect to the learning paradox: this is how you learn from Claude

**Building something new:**
- Start small, build up. Don't ask for an entire analysis at once
- Each step: verify, then continue
- Example: building a QC script piece by piece

**Extending existing code:**
- Reference the file explicitly
- Point to the existing pattern you want to match ("use the same style as...")
- Example: adding a plot to an existing analysis

#### The Natural Flow

In practice, thinking and coding interleave constantly. A typical session might look like: discuss what analysis to do → Claude writes the code → you run it and examine the output → discuss what the results mean → decide the next step → Claude writes more code. The plan-think-code-interpret cycle is the core rhythm of working with Claude in data science.

### Section 3: Managing Conversations

When to start fresh vs. continue:
- Fresh: switching tasks, context feels cluttered, Claude seems confused, after a break
- Continue: building on recent work, fixing issues, iterating

Keep sessions focused — one main task per conversation. The plan file picks up where you leave off.

**The `/done` command:** End productive sessions with `/done`. Walk through what it does: summarizes work, checks renv, offers to commit, optionally publishes. This ensures work is saved before closing.

### Section 4: Deep Research — Extended Reports and Biological Interpretation

Section 2 covered quick back-and-forth analytical conversations. This section covers a more powerful mode: asking Claude to conduct extended research — reading literature, synthesizing information, and producing structured reports. This is Mode 2 (augmentation) at its most powerful, and it's where Claude can transform how students approach the *scientific* side of data analysis.

**Important for beginners:** This section must open by explaining *what deep research actually is* and *how to access it* (e.g., using Claude on the web with the research feature, or asking Claude Code to do extended investigation with web search). Don't assume students know what "deep research" means — explain the mechanics before showing the workflow.

**Generating curated gene lists:**
Walk through a concrete example: you need a list of Wnt signaling pathway genes to check expression in your single-cell data. Instead of manually searching databases, ask Claude (or use deep research) to compile a curated list with gene symbols, brief functional descriptions, and key references. Then use these in FeaturePlot/DotPlot to explore pathway activity across your clusters.

Other pathway examples: Notch, TGF-beta, cell cycle genes, apoptosis markers. The gene lists Claude generates become inputs to your Seurat analysis.

**Interpreting differentially expressed genes:**
The traditional approach: run FindMarkers, get a gene list, throw it at GO enrichment, get back generic terms like "signal transduction" and "protein binding." Jake's approach: give Claude the top DE genes from a cluster comparison and ask it to synthesize a biological narrative. What cell type does this look like? What processes are active? What's surprising?

Walk through a realistic example: you've identified a cluster in the Spongilla data. FindMarkers gives you 50 DE genes. Instead of (or in addition to) GO enrichment, you ask Claude to interpret the list biologically. Claude reads the literature, identifies that the combination of markers suggests a specific cell type, and provides references you can check.

**Critical evaluation:** This section must reinforce the Discernment principle. Claude's interpretations are hypotheses, not conclusions. Always:
- Check key claims against primary literature
- Verify gene symbols are correct for your organism
- Cross-reference with known marker databases
- Treat it as a starting point for your own investigation, not an endpoint

**The workflow:** Generate gene lists / interpret DE results → verify with literature → explore in your data → iterate. This is the augmentation loop in practice.

### Section 5: When Things Go Wrong

Important for students who are new to both coding and AI:

- **Claude gets stuck in a loop** — It keeps trying the same failing approach. Start a new conversation, describe the problem differently.
- **Claude misunderstands your project** — Check your CLAUDE.md. Is it accurate? Is it misleading?
- **The code runs but the output looks wrong** — Don't just ask Claude to "fix it." Describe what you expected vs. what you got. Paste the specific output.
- **You don't understand what Claude did** — Ask. "Explain what you just changed and why." This is not a sign of weakness; it's the learning mode from Ch. 1.
- **When to ask a human** — Sometimes Claude can't help. If you've been going in circles for 20 minutes, ask your PI, a labmate, or post on the lab Slack. Knowing when to escalate is a real skill.

### Section 6: Iterating on Your Workflow

Brief closing section on developing your own Claude Code style over time. What to add to CLAUDE.md after sessions. How your skills evolve. The feedback loop: better context → better responses → better context.

---

## Chapter 5: The Musser Lab Toolkit {#ch5}

**File:** `claude-code/musser-lab-toolkit.qmd`
**Tone:** Practical, tour-style but narrative. "Here's what we've built for the lab and how to use it."
**Target length:** ~350-450 lines

### Opening

"The Musser Lab maintains a shared set of Claude Code skills, configuration examples, and conventions. This chapter walks you through the toolkit — what's available, how to install it, and how the key skills work in practice."

### Section 1: The Lab Skills Repository

What it is: a GitHub repo of shared skills that any lab member can install. How to install: clone/download to `~/.claude/skills/`. How updates work.

Repo link: `MusserLab/lab-claude-skills` (or wherever it lives at publication time).

### Section 2: Key Background Skills

Walk through the most important background skills with narrative explanations and examples of what they do in practice. For each: what it does, when it activates, a concrete "before and after" showing how Claude behaves differently with the skill loaded.

**Essential skills to cover (subset — not exhaustive):**

- **`data-handling`** — Shows data dimensions after loading, validates joins, asks before analytical decisions. Example: Claude loads a CSV and immediately reports "Loaded 10,234 rows × 8 columns" instead of silently moving on.

- **`debugging-before-patching`** — Diagnoses before fixing. Claude investigates root causes instead of slapping on a quick fix. Example: instead of adding `na.rm = TRUE` everywhere, Claude asks why NAs are present.

- **`file-safety`** — Prevents overwriting raw data or collaborator outputs. Example: Claude refuses to write to `data/` and explains why.

- **`git-conventions`** — Co-author line, reviews staged changes, avoids committing secrets. Students have already seen this in the Git chapter.

- **`script-organization`** — Numbered scripts, outs/ directories, lifecycle status. Ties back to the Project Organization chapter in Part 2.

- **`r-plotting-style`** — Lab-standard ggplot2 theme and conventions. Example: consistent theme_classic() base across all lab figures.

### Section 3: Key Slash Commands

Walk through the most-used slash commands:

- **`/done`** — Already introduced in Ch. 4; reiterate briefly with the full feature set
- **`/new-project`** — Scaffolds a complete project (directory structure, conda env, renv, CLAUDE.md, git). Show what it creates. Reference the Setup Walkthrough chapter in Part 4.
- **`/new-plan`** — Creates a planning document. When to use it.
- **`/publish`** — For Quarto book/website projects

### Section 4: Specialized Skills

Briefly introduce the domain-specific skills that students may encounter as their work deepens. Don't explain in detail — just enough that they know these exist:

- **`protein-phylogeny`** — Generates a full phylogenetics pipeline (.qmd with MAFFT, IQ-TREE)
- **`gene-lookup`** — Looks up gene/protein information from database IDs
- **`tree-formatting`** — Phylogenetic tree visualization with ggtree
- **`scientific-manuscript`** — Writing guidance for high-impact journals
- **`figure-export`** — Publication-quality figure saving (PDF/PNG/SVG)

### Section 5: Example CLAUDE.md Files

Show 2-3 real (or realistic) CLAUDE.md files from lab projects at different stages:

1. **New project** — minimal, just started. ~15 lines.
2. **Mid-project** — active analysis with conventions, gotchas, key files. ~40 lines.
3. **Mature project** — full documentation with plan file references, decisions recorded. ~60 lines.

These serve as practical templates students can adapt.

### Note on appendix

A complete table of all lab skills (name, type, one-line description) should go in a new appendix. This chapter covers only the important ones narratively.

---

## Chapter 6: Staying Safe {#ch6}

**File:** `claude-code/staying-safe.qmd`
**Tone:** Practical and direct. Not fear-mongering, but honest about risks. "Here's how the guardrails work and why they matter."
**Target length:** ~300-400 lines

### Opening

"Claude Code is powerful — it can read your files, edit your code, and run commands in your terminal. That power comes with responsibility. This chapter covers how Claude Code's safety features work, how the lab configures them, and what you should know to protect your data and your work."

### Section 1: The Permission System

What happens when Claude wants to do something: the approval prompt. Walk through what students see:

- **File edits** — Claude shows a diff, you approve or reject
- **Commands** — Claude shows the command, you approve or reject
- **Allow once vs. allow for session** — what each means, when to use which

The mental model: Claude always asks before acting. You're the gatekeeper. This is by design.

**Common permissions students will encounter:** reading files (usually auto-allowed), editing files, running `quarto render`, running git commands, installing packages.

### Section 2: Hooks — Automatic Guardrails

What hooks are: shell commands that run automatically in response to Claude Code events (before/after tool calls). The lab uses hooks to prevent common mistakes.

**Examples of safety hooks:**
- Blocking `git push --force` (prevents overwriting shared history)
- Blocking writes to `data/` directories (raw data is sacred)
- Blocking `rm -rf` or other destructive commands
- Warning before committing files over a certain size

How to see what hooks are active: `~/.claude/hooks.json` and project-level `.claude/hooks.json`.

Students don't need to write hooks (the lab provides them), but they should understand what they are and why a command might be blocked.

### Section 3: Settings and Configuration

`settings.json` files that control Claude Code behavior:

- **User-level:** `~/.claude/settings.json` — your personal defaults
- **Project-level:** `.claude/settings.json` — shared project settings (committed to git)
- **Local overrides:** `.claude/settings.local.json` — personal project overrides (not committed)

Key settings students should know about:
- Allowed/denied tools and commands (permission patterns for common operations)
- Model selection (if applicable)

Note for writing: be careful about "directory restrictions" — Claude Code doesn't have a simple toggle for this. Frame what's actually configurable honestly; don't imply features that don't exist or would confuse beginners trying to find a setting that isn't there.

### Section 4: Protecting Your Data

Practical guidance:
- **Don't paste sensitive data into web-based AI chat** — Claude Code runs locally, but be aware of the difference between local CLI and web interfaces
- **Training opt-out** — How to ensure your data isn't used for model training. Walk through the setting. Link to Anthropic's data usage policy.
- **What Claude Code sends** — Brief, honest explanation of what data leaves your machine (your prompts and file contents go to Anthropic's API; results come back; nothing is stored for training if opted out)
- **Credentials and secrets** — Never commit `.env` files, API keys, passwords. The `git-conventions` skill catches this, but understand why.

### Section 5: Prompt Injection (Brief)

Keep this short — one or two paragraphs plus an example. The concept:
- When Claude reads external content (web pages, downloaded files, data from APIs), that content could contain instructions that try to manipulate Claude's behavior
- This is called "prompt injection"
- For students, the main risk is: if you ask Claude to read a file you downloaded from the internet, be aware that the file's content could influence Claude's behavior
- Claude Code has built-in protections, but awareness is the best defense

Not a deep dive — just enough that they know the concept exists.

### Closing

"Security isn't about being paranoid — it's about building good habits early. The permission system, hooks, and settings work together to make Claude Code safe by default. Your job is to pay attention to the approval prompts and keep sensitive information out of places it shouldn't be."

---

## Cross-Cutting Concerns

### Claude as Thinking Partner (not just coding tool)

This framing must permeate every chapter. Claude is equally valuable for the intellectual/scientific side of data science as for writing code. Every chapter should include examples of both:

- **Ch. 1:** Mode 2 (augmentation) is the most detailed of the three modes, covering analytical planning, method evaluation, literature exploration, and result interpretation — all before any code is discussed
- **Ch. 2:** First interaction is a conceptual question (QC thresholds), second is a coding request — both sides from the start
- **Ch. 3:** CLAUDE.md should capture analytical decisions and scientific context, not just code conventions. Plan files track scientific questions and hypotheses, not just figure status
- **Ch. 4:** Session patterns split explicitly into "Thinking Together" and "Coding Together" halves, with a note on how they interleave. Deep research section covers extended scientific investigation
- **Ch. 5:** Lab skills include analytical tools (data-handling surfaces data dimensions to support scientific judgment, not just as a code convenience)
- **Ch. 6:** Evaluating Claude's scientific claims requires the same critical thinking as evaluating its code

### The Learning Paradox Thread

Per Jake's request, this theme is prominent in Ch. 1 and reinforced throughout:

- **Ch. 1:** Major section introducing the concept and concrete patterns
- **Ch. 2:** The first conversation walk-through models learning behavior (asking Claude about QC thresholds, not just producing code)
- **Ch. 3:** When creating skills, emphasize that skills should encode *understanding* not just rules
- **Ch. 4:** "Understanding code you didn't write" section; deep research section emphasizes verifying Claude's biological interpretations against literature; "When to ask a human" section
- **Ch. 5:** Lab skills are designed to surface information (data-handling shows dimensions, debugging-before-patching explains root causes)
- **Ch. 6:** Security awareness itself is a form of critical evaluation — understanding what Claude can access and why guardrails exist

### Callbacks to Earlier Chapters

Following the pattern established in Part 2, each chapter should open with a callback to something the student has already experienced:

- **Ch. 1:** "You've learned the tools. Now meet your collaborator."
- **Ch. 2:** "Remember the Claude Code callout boxes throughout the book? Now you'll actually use it."
- **Ch. 3:** "Remember how each conversation started fresh? Here's how to fix that."
- **Ch. 4:** "You know the tool and its configuration. Now let's talk about the art of working together."
- **Ch. 5:** "You've been writing your own configuration. Here's what the lab has already built for you."
- **Ch. 6:** "You've seen Claude ask permission before editing files. Here's the full safety system."

### Screenshots

Each chapter will need screenshot TODOs. Estimate:
- Ch. 1: 0-1 (conceptual chapter, mostly text)
- Ch. 2: 3-5 (Positron extension, chat panel, diff view, approval prompt)
- Ch. 3: 2-3 (.claude/ folder structure, CLAUDE.md in editor, skill folder)
- Ch. 4: 1-2 (session flow, /done output)
- Ch. 5: 2-3 (skills repo, /new-project output, example CLAUDE.md)
- Ch. 6: 2-3 (permission prompt, hook blocking a command, settings file)

### New Appendix: Lab Skills Reference

Complete table of all Musser Lab skills:

| Skill | Type | Description |
|-------|------|-------------|
| `data-handling` | Background | Data validation, summaries, surfacing analytical decisions |
| `debugging-before-patching` | Background | Diagnose before fixing, never blind-patch |
| `file-safety` | Background | Prevents overwriting raw data and important files |
| `git-conventions` | Background | Commit practices, co-author line, secret detection |
| `conda-env` | Background | Conda activation patterns |
| `r-renv` | Background | renv status, snapshot reminders |
| `r-plotting-style` | Background | Lab ggplot2 theme and conventions |
| `quarto-docs` | Background | QMD analysis script conventions |
| `script-organization` | Background | Numbered scripts, outs/ directories, lifecycle |
| `figure-export` | Background | Publication-quality figure saving |
| `scientific-manuscript` | Background | High-impact manuscript development |
| `protein-phylogeny` | Background | Phylogenetics pipeline generation |
| `gene-lookup` | Background | Gene/protein ID lookup |
| `tree-formatting` | Background | Phylogenetic tree visualization |
| `/done` | Slash command | End-of-session wrap-up and commit |
| `/new-project` | Slash command | Scaffold new project with full structure |
| `/new-plan` | Slash command | Create planning document |
| `/publish` | Slash command | Commit and publish Quarto sites |
| `/quarto-book-setup` | Slash command | Initialize Quarto book with GitHub Pages |
| `/audit` | Slash command | Project health check |
| `/new-skill` | Slash command | Create a new skill |
| `/security-setup` | Slash command | Configure security protections |

---

## Implementation Order

Suggested order for writing the chapters:

1. **Ch. 2 (Getting Started)** — Establishes the hands-on experience that other chapters reference back to
2. **Ch. 1 (AI Fluency)** — Benefits from knowing exactly what Ch. 2 covers, so callbacks are accurate
3. **Ch. 3 (Teaching Claude)** — Builds on "Claude doesn't remember" from Ch. 2
4. **Ch. 4 (Working Effectively)** — Assumes Ch. 2 and Ch. 3 content
5. **Ch. 5 (Musser Lab Toolkit)** — Requires Ch. 3 (skills concept) as prerequisite
6. **Ch. 6 (Staying Safe)** — Standalone enough to write in any order, but benefits from Ch. 2 (permission prompts)

Each chapter is a full session of work (similar to Part 2 rewrites). Could also batch Ch. 1+2 or Ch. 5+6 if sessions are long.

---

## Resolved Decisions

1. **Ch. 2 first conversation:** Two interactions — (1) conceptual: ask about nFeature_RNA QC thresholds (Mode 2 / thinking), (2) coding: ask Claude to add a violin plot (Mode 3 / coding)
2. **Ch. 5 lab repo:** `MusserLab/lab-claude-skills` confirmed as public repo name
3. **Skills appendix:** New Appendix E (Lab Skills Reference). Will be revisited/cleaned up later.
4. **Part title:** "Working with AI" (broader than just Claude Code since Ch. 1 covers AI fluency generally). Directory stays `claude-code/`.
5. **Deep research:** Introduced briefly in Ch. 1 (Mode 2 examples), full workflow in Ch. 4 Section 4. Primary examples: curated gene lists for pathway analysis, interpreting DE results (better than GO enrichment for biological narrative).
6. **Domain focus:** Single-cell RNA-seq examples throughout (Seurat, Spongilla dataset, marker genes, clustering, DE analysis). Other domains (phylogenetics, manuscript writing) appear as secondary examples in specialized skills.
