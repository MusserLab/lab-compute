# Positron Chapter Screenshot Capture Guide

Save all screenshots to: `images/positron/`

**General tips:**
- Use the same project for all screenshots (the `my-first-analysis` project from the first-project chapter works well — it has a `.qmd` file, Seurat data, and both R/Python potential)
- Capture at Retina resolution if on macOS (default for built-in screenshots)
- Use a clean, un-cluttered Positron window — close any distracting panels or tabs you don't need for that shot
- macOS screenshot shortcuts: **Cmd+Shift+4** for region select, **Cmd+Shift+4 then Space** for a specific window

---

## Screenshot 1: Full Positron Interface with Labeled Panes

**Filename:** `positron-interface-overview.png`
**Used at:** line 29
**Needs annotation:** YES (labels/arrows for each pane)

### Setup
1. Open the `my-first-analysis` project (or any project with a `.qmd` file)
2. Open a `.qmd` file in the editor (e.g., `analysis.qmd` from the first-project tutorial)
3. Make sure these are visible:
   - **File Explorer** in the left sidebar (should show project files)
   - **Editor** center area with the `.qmd` file open
   - **Console** in the bottom panel (start an R session if needed)
   - **Variables pane** — click the Variables tab in the bottom-right or wherever Positron places it
   - **Outline panel** — open via View → Outline if not visible
4. Optionally have a Terminal tab visible (but Console should be the active tab)
5. Resize the window so everything is comfortably visible — not too cramped

### Capture
- Capture the **entire Positron window** (Cmd+Shift+4 then Space, click the window)

### Annotation needed
Add labels with arrows pointing to:
- Editor (center)
- File Explorer (left sidebar)
- Console (bottom panel)
- Terminal tab (bottom panel, inactive tab)
- Variables pane
- Outline panel (sidebar)

**Tool suggestion:** Use Preview.app (macOS) or any image editor to add text labels and arrows. Keynote also works well for annotation — paste the screenshot, add text boxes and arrows, then export as PNG.

---

## Screenshot 2: Console and Terminal Tabs in Bottom Panel

**Filename:** `console-terminal-tabs.png`
**Used at:** line 56
**Needs annotation:** NO (but crop tightly)

### Setup
1. Have an **R console** running (run any R code to start one)
2. Open a **Terminal** tab — click the **+** in the bottom panel, or View → Terminal
3. Make one tab active (e.g., R Console) so the other appears as an inactive tab
4. Have some content visible in the active tab (a few lines of R output, or a command prompt)

### Capture
- **Crop tightly** to just the bottom panel — include the tab bar at the top of the panel and enough of the panel content to see it's a real session
- The key thing to show: two clearly labeled tabs ("Console" / "R" and "Terminal" / "zsh") in the same panel area
- Make sure the tab labels are readable at the final image size

---

## Screenshot 3: Multiple Tabs in the Bottom Panel

**Filename:** `multiple-bottom-tabs.png`
**Used at:** line 66
**Needs annotation:** NO (but crop tightly)

### Setup
1. Have an **R console** running
2. Start a **Python console** — open a `.py` file and run something, or use the Command Palette → "Python: Start REPL"
3. Open at least one **Terminal** tab
4. The **+** button for creating new terminals should be visible
5. You should have 3+ tabs visible: e.g., "R", "Python", "Terminal"

### Capture
- Crop to just the bottom panel, same as Screenshot 2
- The point is showing 3+ tabs coexisting and the + button for creating more

---

## Screenshot 4: Data Viewer with Filtering and Column Histograms

**Filename:** `data-viewer-filtering.png`
**Used at:** line 96
**Needs annotation:** NO

### Setup
1. Open a dataframe in the Data Viewer. Best options:
   - If you have the sponge Seurat object loaded: `View(sponge@meta.data)` in the R console
   - Or open any `.csv` file by clicking it in the File Explorer
2. Once the Data Viewer is open:
   - Look for the **column histograms** at the top of numeric columns (they appear automatically)
   - **Apply a filter**: click the filter icon or filter row, then set a condition on one column (e.g., `nFeature_RNA > 1000`)
   - **Sort a column**: click a column header to sort ascending/descending (the sort arrow should appear)
3. Make sure the filter row is visible and shows your active filter

### Capture
- Capture the **entire Data Viewer tab** (or the full Positron window with the Data Viewer as the active editor tab)
- The key elements to show: column histograms, active filter, sorted column indicator

---

## Screenshot 5: Outline Panel for a .qmd File

**Filename:** `outline-panel-qmd.png`
**Used at:** line 106
**Needs annotation:** NO

### Setup
1. Open a `.qmd` file that has multiple headings and code chunks — the `analysis.qmd` from the first-project tutorial is ideal
2. Open the **Outline panel**: View → Outline, or look for it in the sidebar
3. The Outline should show:
   - Heading hierarchy (##, ###)
   - Named code chunks (if any)
4. Make the Outline panel wide enough that entries aren't truncated

### Capture
- Capture the **Outline panel and enough of the editor** to show the connection — ideally the sidebar with the Outline list visible, and part of the editor showing the corresponding `.qmd` content
- You could capture just the sidebar if the Outline is clearly visible there

---

## Screenshot 6: Command Palette with a Search Term

**Filename:** `command-palette-search.png`
**Used at:** line 132
**Needs annotation:** NO

### Setup
1. Open the Command Palette: **Cmd+Shift+P** (macOS) or **Ctrl+Shift+P** (Windows)
2. Type a search term — good options:
   - `Python: Select` (shows interpreter-related commands)
   - `R: Select` (shows R binary selection)
   - `View:` (shows various panel toggles)
3. Wait for the dropdown to populate with matching commands (should show 3-5 results)

### Capture
- Capture the **Command Palette dropdown** — you need the search bar and the list of matching results
- Cmd+Shift+4 region select works well here — draw a box around the palette
- Make sure the search term you typed is visible in the search bar, and at least 3-4 results are showing

**Timing note:** The Command Palette closes if you click outside it, so use **Cmd+Shift+4** (region select) rather than Cmd+Shift+4+Space (window select). Draw the selection box around the palette dropdown.

---

## Screenshot 7: Status Bar Annotated

**Filename:** `status-bar-annotated.png`
**Used at:** line 145
**Needs annotation:** YES (labels for each section)

### Setup
1. Make sure these are all showing in the status bar:
   - **R version** (e.g., "R 4.4.2") — start an R session if not running
   - **Python interpreter** with conda env name (e.g., "Python 3.11 (my-project)") — select an interpreter if not set
   - **Git branch** (e.g., "main") — the project must be a git repo
   - **Line/column number** (e.g., "Ln 42, Col 1") — have a file open with cursor somewhere
2. The status bar is the thin bar at the very bottom of the Positron window

### Capture
- **Zoom in / crop tightly** to just the status bar
- On macOS: Cmd+Shift+4, then draw a narrow horizontal selection across just the status bar
- Make it wide enough to include all the items listed above

### Annotation needed
Add labels (with arrows or brackets) pointing to:
- R version indicator
- Python interpreter / conda env
- Git branch name
- Line/column position

---

## After Capturing

1. Save raw screenshots to `images/positron/` with the filenames above
2. For screenshots 1 and 7 (the ones needing annotation), annotate them and save the annotated versions with the same filename
3. Update `part2/positron.qmd` — replace each `[TODO: screenshot ...]` line with:

```markdown
![Description](../images/positron/filename.png)
```

Specifically:
- Line 29: `![The Positron interface with key areas labeled](../images/positron/positron-interface-overview.png)`
- Line 56: `![Console and Terminal tabs in the bottom panel](../images/positron/console-terminal-tabs.png)`
- Line 66: `![Multiple sessions as tabs in the bottom panel](../images/positron/multiple-bottom-tabs.png)`
- Line 96: `![The Data Viewer showing column histograms, filtering, and sorting](../images/positron/data-viewer-filtering.png)`
- Line 106: `![The Outline panel showing document structure for a .qmd file](../images/positron/outline-panel-qmd.png)`
- Line 132: `![The Command Palette with search results](../images/positron/command-palette-search.png)`
- Line 145: `![The status bar showing R version, Python interpreter, Git branch, and cursor position](../images/positron/status-bar-annotated.png)`
