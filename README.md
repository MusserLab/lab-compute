# Data Analysis in the Musser Lab

A practical guide to reproducible research using modern tools and workflows.

**Read the book:** https://MusserLab.github.io/lab-compute/

## For Readers

This repository contains the source for the book plus **example datasets and scripts** you can download and use directly. You don't need to clone the whole repo — grab just what you need.

### Example Dataset: Spongilla Single-Cell RNA-Seq

A real single-cell RNA-seq dataset from freshwater sponge (*Spongilla lacustris*) in standard 10X Genomics format. This is the same format you'll receive from a sequencing core facility.

**Location:** [`examples/data/spongilla_counts/`](examples/data/spongilla_counts/)

| File | Description |
|------|-------------|
| `barcodes.tsv.gz` | Cell barcodes |
| `features.tsv.gz` | Gene names |
| `matrix.mtx.gz` | Sparse count matrix |

About 10,000 cells across 4 samples — large enough to be realistic, small enough to run quickly on a laptop.

To download, navigate to the folder above on GitHub and download each file, or clone the repo:

```
git clone https://github.com/MusserLab/lab-compute.git
```

### Example Script: Seurat Analysis Workflow

A fully annotated Quarto document that walks through a standard Seurat single-cell analysis pipeline.

**Location:** [`examples/scripts/01_seurat_basics.qmd`](examples/scripts/01_seurat_basics.qmd)

The script covers loading 10X data, quality control, normalization, PCA, clustering, and UMAP visualization. It's designed to be run interactively in Positron, chunk by chunk.

### Reference Outputs

Pre-rendered plots from the analysis script so you can check your results against expected output.

**Location:** [`examples/outs/01_seurat_basics/`](examples/outs/01_seurat_basics/)

Includes QC violin plots, variable feature plots, an elbow plot, UMAP, and gene expression feature plots — all as publication-ready PDFs.

## What the Book Covers

| Part | Description |
|------|-------------|
| **Quick Start** | Install tools and run your first analysis in 30 minutes |
| **Core Tools** | Deep dives into Positron, conda, renv, Quarto, and Git |
| **Claude Code** | AI-assisted coding with Claude Code |
| **Workflows** | Setting up projects, collaborating, reproducibility |
| **Appendices** | Keyboard shortcuts, commands, templates |

Start with the [Quick Start](https://MusserLab.github.io/lab-compute/part1/intro.html) to install everything and work through the Spongilla example.

## Building the Book Locally

This book is built with [Quarto](https://quarto.org/).

```
# Preview with live reload
quarto preview

# Build static site
quarto render
```

## Contributing

To suggest changes, open an issue or submit a pull request.

## Author

Jacob Musser, in collaboration with [Claude Code](https://code.claude.com/docs/en/overview)

## License

This work is licensed for educational use within the Musser Lab.
