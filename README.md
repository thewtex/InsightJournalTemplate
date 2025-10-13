# Insight Journal Article Template

[![Build MyST Document](https://github.com/InsightSoftwareConsortium/InsightJournalTemplate/actions/workflows/build-myst.yml/badge.svg)](https://github.com/InsightSoftwareConsortium/InsightJournalTemplate/actions/workflows/build-myst.yml)

This repository contains a modern template for open science publications for the
[Insight Journal]:

    https://insight-journal.org

## Features

- 🚀 **Modern authoring** with [MyST Markdown]
- 📦 **Dependency management** with [Pixi]
- 🔄 **Reproducible builds** and environments
- 📄 **Multiple export formats** (PDF, HTML, DOCX, [MECA])
- 🧪 **Integrated source code** testing and validation support
- 📚 **Rich scientific features** (figures, equations, citations, cross-references)

## Quick Start

### Prerequisites

1. Install [Pixi](https://pixi.sh/latest/):

```bash
curl -fsSL https://pixi.sh/install.sh | bash
```

2. Clone this repository:

```bash
git clone https://github.com/InsightSoftwareConsortium/InsightJournalTemplate
cd InsightJournalTemplate
```

2. Build the manuscript, source code, and run tests:

```bash
pixi run build
```

## Repository Structure

```
InsightJournalTemplate/
├── docs/                           # MyST Markdown manuscript
│   ├── index.md                   # Main article content
│   ├── references.bib             # Bibliography database
│   └── assets/                    # Images and figures
│
├── src/                           # C++ source code examples
│   ├── CMakeLists.txt            # Modern CMake configuration
│   ├── ImageCopy.cxx             # ITK image copying example
│   ├── ImageCompare.cxx          # ITK image comparison example
│
├── data/                          # Input datasets and test data
│   └── img1.png                  # Sample image data
│
├── build/                         # Build artifacts (auto-generated)
│   ├── ITK/                      # ITK source code (if using C++ features)
│   ├── ITK-build/                # ITK build artifacts
│   └── project-build/            # Project build artifacts
│
├── _build/                        # MyST build outputs
│   ├── html/                     # HTML documentation
│   └── exports/                  # PDF, DOCX, MECA exports
│
├── .github/workflows/             # CI/CD automation
├── myst.yml                       # MyST project configuration
├── pixi.toml                      # Dependency and task management
├── pixi.lock                      # Locked dependency versions
└── README.md                      # This file
```

## Build Tasks

The project uses [Pixi](https://pixi.sh) for dependency management and task automation. All tasks can be run with `pixi run <task-name>`:

### Core Manuscript Tasks

| Task | Description |
|------|-------------|
| `build-html` | Generate interactive HTML documentation |
| `build-pdf` | Build PDF using Typst (no LaTeX required) |
| `build-arxiv` | Build PDF with arXiv formatting (requires LaTeX distribution) |
| `build-tex` | Generate LaTeX source files |
| `build-docx` | Export to Microsoft Word format |
| `build-cff` | Generate [CITATION.cff] file |

### Combined Build Tasks

| Task | Description |
|------|-------------|
| `build-manuscript` | Build HTML, PDF, and citation file |
| `build-pdfs` | Build both Typst and arXiv PDFs |
| `build-meca` | Create complete [MECA] archive for journal submission |
| `verify-meca` | Build MECA and verify bundle reproducibility |
| `build` | **Main build task** - builds manuscript and tests project |

### Development Tasks

| Task | Description |
|------|-------------|
| `start` | Start live development server with hot reload |
| `dev` | Alias for development server |
| `clean` | Remove all build artifacts |

### C++ Source Code Tasks (Environment: `cxx`)

To work with the ITK C++ examples, use the `cxx` environment:

```bash
# Activate C++ environment
pixi shell -e cxx

# Or run tasks directly in C++ environment
pixi run -e cxx <task-name>
```

| Task | Description |
|------|-------------|
| `clone-itk` | Download ITK source code |
| `configure-itk` | Configure ITK build with CMake |
| `build-itk` | Compile ITK libraries |
| `configure-project` | Configure project against built ITK |
| `build-src` | Compile project executables |
| `test-src` | Run project test suite |

### Example Workflows

**Build manuscript only:**
```bash
pixi run build-manuscript
```

**Full development cycle:**
```bash
# Start development server
pixi run start

# In another terminal, build and test everything
pixi run build
```

**Work with C++ code:**
```bash
# Build ITK and project code
pixi run -e cxx build-src

# Run tests
pixi run -e cxx test-src
```

**Create journal submission:**
```bash
# Generate complete MECA package
pixi run build-meca
```

**Verify MECA bundle reproducibility:**
```bash
# Build MECA, unpack it, and verify the bundle builds correctly
pixi run verify-meca
```

## License

All source code in this repository is distributed under the Apache 2.0
License. Please see the [LICENSE](./LICENSE) file for details.

All documents and works of art in this repository are distributed under the
[Creative Commons by Attribution License 4.0].

[Insight Journal]: https://insight-journal.org
[MyST Markdown]: https://mystmd.org
[Pixi]: https://pixi.sh/latest/
[MECA]: https://www.niso.org/standards-committees/meca
[Creative Commons by Attribution License 4.0]: https://creativecommons.org/licenses/by/4.0/
[CITATION.cff]: https://citation-file-format.github.io/