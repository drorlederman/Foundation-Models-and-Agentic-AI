# Foundation Models and Agentic AI
### Graduate Course Slides — Holon Institute of Technology (HIT)

A complete 13-week LaTeX Beamer slide project for an advanced M.Sc. course on foundation models and AI agents.

---

## Folder Structure

```
Foundation-Models-and-Agentic-AI/
├── README.md
├── main.tex                    # Master file (overview + bibliography)
├── references.bib              # ~50 key papers
├── .gitignore
├── shared/
│   ├── preamble.tex            # All packages, theme, custom commands
│   ├── macros.tex              # Math notation macros
│   └── beamerthemeHIT.sty      # Custom HIT Beamer theme
├── tikz/
│   ├── scaling_laws.tex        # Log-log scaling law curves
│   ├── transformer_arch.tex    # Encoder-decoder diagram
│   ├── attention_head.tex      # Scaled dot-product attention
│   ├── rlhf_pipeline.tex       # SFT → RM → PPO pipeline
│   ├── rag_pipeline.tex        # RAG offline + online pipeline
│   ├── agent_loop.tex          # ReAct Thought-Action-Observation cycle
│   ├── multiagent_graph.tex    # Multi-agent communication graph
│   └── memory_taxonomy.tex     # Agent memory taxonomy tree
└── weeks/
    ├── week01/week01.tex       # From Deep Learning to Foundation Models
    ├── week02/week02.tex       # Transformer Architectures Revisited
    ├── week03/week03.tex       # Training LLMs (SFT, RLHF, DPO)
    ├── week04/week04.tex       # Multimodal Foundation Models
    ├── week05/week05.tex       # Embeddings and Semantic Search
    ├── week06/week06.tex       # Retrieval-Augmented Generation
    ├── week07/week07.tex       # Foundations of Agentic AI
    ├── week08/week08.tex       # Reasoning and Planning
    ├── week09/week09.tex       # Memory in Agentic Systems
    ├── week10/week10.tex       # Multi-Agent Systems
    ├── week11/week11.tex       # Evaluation
    ├── week12/week12.tex       # Safety, Security, and Alignment
    └── week13/week13.tex       # Future Directions + Presentations
```

---

## Prerequisites

### LaTeX Distribution
Install **TeX Live 2023+** (recommended) or **MiKTeX 23+**:
- **Linux/macOS:** `sudo apt install texlive-full` or [tug.org/texlive](https://tug.org/texlive)
- **Windows:** [MiKTeX](https://miktex.org/download) or [TeX Live](https://tug.org/texlive/windows.html)
- **macOS (Homebrew):** `brew install --cask mactex`

### Required Packages
All packages are included in `texlive-full` / `texlive-latex-extra`. The following are used:

| Package | Purpose |
|---|---|
| `beamer` | Presentation framework |
| `beamerthememetropolis` | Modern Metropolis theme (fallback: AnnArbor) |
| `amsmath`, `mathtools`, `bm` | Mathematics |
| `algorithm`, `algpseudocode` | Pseudocode blocks |
| `tikz`, `pgfplots` | Diagrams and charts |
| `tcolorbox` | Callout/definition boxes |
| `booktabs`, `tabularx` | Professional tables |
| `natbib` | Bibliography (no Biber required) |
| `listings` | Code display |

### Installing Metropolis Theme (if not bundled)
```bash
# TeX Live
tlmgr install beamer-theme-metropolis

# MiKTeX (runs automatically on first compile)
# Or manually: https://github.com/matze/mtheme
```

---

## Compiling Individual Weeks (Recommended)

Each week file is a **standalone** Beamer document.

```bash
# Compile a single week (with bibliography)
cd weeks/week01
pdflatex week01.tex
bibtex week01
pdflatex week01.tex
pdflatex week01.tex    # Run twice to resolve references
```

Or with `latexmk` (handles reruns automatically):
```bash
cd weeks/week01
latexmk -pdf week01.tex
```

Output: `weeks/week01/week01.pdf`

### Batch-Compile All Weeks (Bash/PowerShell)

**Bash (Linux/macOS):**
```bash
for i in $(seq -w 1 13); do
  echo "Compiling week${i}..."
  cd weeks/week${i}
  latexmk -pdf week${i}.tex
  cd ../..
done
```

**PowerShell (Windows):**
```powershell
for ($i = 1; $i -le 13; $i++) {
  $week = "week{0:D2}" -f $i
  Write-Host "Compiling $week..."
  Set-Location "weeks/$week"
  latexmk -pdf "$week.tex"
  Set-Location "../.."
}
```

---

## Compiling the Full Course (main.tex)

`main.tex` provides a course overview slide and a combined bibliography.
To include all 13 weeks in a single PDF, use one of two approaches:

### Option A: pdfpages (simplest — requires weekly PDFs first)
1. Compile all 13 weeks individually (see above).
2. Uncomment the `\includepdf` lines in `main.tex`.
3. Run `pdflatex main.tex`.

### Option B: subfiles (cleaner — requires file restructuring)
Restructure each `weekNN.tex` to use the `subfiles` package:
1. Replace `\documentclass[aspectratio=169,10pt]{beamer}` with `\documentclass[../../main.tex]{subfiles}`.
2. Remove the `\input{../../shared/preamble}` line (inherited from main).
3. In `main.tex`, uncomment the `\subfile{weeks/weekNN/weekNN}` lines.
4. Run `latexmk -pdf main.tex`.

---

## Speaker Notes

Speaker notes are defined with `\note{...}` in each frame.
They are **hidden by default**. To show them on a second screen:

1. In `shared/preamble.tex`, change `\shownotesfalse` to `\shownotestrue`.
2. Uncomment the line:
   ```latex
   \setbeameroption{show notes on second screen=right}
   ```
3. Recompile. Use a dual-screen PDF presenter (e.g., Pympress, DualScreenPDF).

---

## Customization

### Changing the Theme
In `shared/beamerthemeHIT.sty`:
- To use AnnArbor explicitly: comment out the Metropolis block.
- To use another built-in theme: replace `\usetheme{metropolis}` with e.g. `\usetheme{Madrid}`.

### Changing Colors
In `shared/beamerthemeHIT.sty`, modify:
```latex
\definecolor{hitblue}{RGB}{0,51,102}    % Primary color
\definecolor{hitgold}{RGB}{192,148,0}   % Accent color
```

### Adding Figures
Replace `\placeholder{width}{height}{caption}` with:
```latex
\includegraphics[width=0.8\textwidth]{figures/my_figure.png}
```

### Modifying Macros
Add course-specific notation in `shared/macros.tex`.

---

## Weekly Content Summary

| Week | Title | Key Papers |
|---|---|---|
| 1 | From Deep Learning to Foundation Models | Bommasani 2021, Kaplan 2020, Hoffmann 2022 |
| 2 | Transformer Architectures Revisited | Vaswani 2017, Su 2024 (RoPE), Press 2022 (ALiBi) |
| 3 | Training LLMs | Ouyang 2022 (RLHF), Rafailov 2023 (DPO) |
| 4 | Multimodal Foundation Models | Radford 2021 (CLIP), Alayrac 2022 (Flamingo) |
| 5 | Embeddings and Semantic Search | Reimers 2019 (SBERT), Karpukhin 2020 (DPR) |
| 6 | Retrieval-Augmented Generation | Lewis 2020 (RAG), Asai 2023 (Self-RAG) |
| 7 | Foundations of Agentic AI | Yao 2023 (ReAct), Schick 2023 (Toolformer) |
| 8 | Reasoning and Planning | Wei 2022 (CoT), Yao 2023 (ToT), Shinn 2023 (Reflexion) |
| 9 | Memory in Agentic Systems | Park 2023 (Gen. Agents), Packer 2023 (MemGPT) |
| 10 | Multi-Agent Systems | Wu 2023 (AutoGen), Hong 2023 (MetaGPT) |
| 11 | Evaluation | Hendrycks 2021 (MMLU), Min 2023 (FActScore) |
| 12 | Safety, Security, Alignment | OWASP 2023, NIST AI RMF, Wei 2023 |
| 13 | Future Directions + Presentations | Lu 2024 (AI Scientist) |

---

## Troubleshooting

| Problem | Solution |
|---|---|
| `beamerthememetropolis.sty not found` | `tlmgr install beamer-theme-metropolis` or the theme auto-falls back to AnnArbor |
| `FiraSans not found` | Install `fonts-firacode` (Linux) or the Metropolis fonts package |
| `Citation undefined` | Run `bibtex weekNN` then `pdflatex` twice |
| `TikZ library not found` | Run `tlmgr install pgf` to update pgf/TikZ |
| Blank slides on first compile | Always run LaTeX at least twice (aux files needed) |

---

## License

Course materials — © Lecturer Name, HIT. For educational use.
Key paper citations belong to their respective authors.
