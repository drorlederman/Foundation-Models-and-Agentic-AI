# Foundation Models: Architectures, Training, and Alignment

**Graduate Course Lecture Slides** — Holon Institute of Technology (HIT), Data Science Department

A comprehensive LaTeX Beamer course covering foundation models, large language models, scaling laws, training techniques, alignment methods, and evaluation strategies.

---

## Folder Structure

```
Foundation-Models-and-Agentic-AI/
├── README.md                      # This file
├── shared/
│   ├── preamble.tex              # Common theme, packages, colors, commands
│   └── macros.tex                # Mathematical notation macros
└── lectures/
    ├── lecture01/lecture01.tex    # Lecture 1: Foundation Models Paradigm
    ├── lecture02/lecture02.tex    # Lecture 2: Scaling Laws & Optimal Training
    ├── lecture03/lecture03.tex    # Lecture 3: Transformer Architectures
    ├── lecture04/lecture04.tex    # Lecture 4: Large-Scale Pretraining
    ├── lecture05/lecture05.tex    # Lecture 5: Efficient Fine-Tuning (LoRA)
    ├── lecture06/lecture06.tex    # Lecture 6: Post-Training & Alignment Part A (RLHF)
    ├── lecture07/lecture07.tex    # Lecture 7: Post-Training & Alignment Part B (DPO)
    ├── lecture08/lecture08.tex    # Lecture 8: Reasoning Models
    ├── lecture09/lecture09.tex    # Lecture 9: Multimodal Foundation Models
    ├── lecture10/lecture10.tex    # Lecture 10: Vision Foundation Models
    ├── lecture11/lecture11.tex    # Lecture 11: Knowledge-Augmented Models (RAG)
    ├── lecture12/lecture12.tex    # Lecture 12: Evaluation, Safety, and Deployment
    └── lecture13/lecture13.tex    # Lecture 13: Research Frontiers & Projects
```

---

## Prerequisites

### LaTeX Distribution

Install **TeX Live 2023+** or **MiKTeX 23+**:

- **Linux/macOS:** `sudo apt install texlive-full` or [tug.org/texlive](https://tug.org/texlive)
- **Windows:** [MiKTeX](https://miktex.org/download) or [TeX Live](https://tug.org/texlive/windows.html)
- **macOS (Homebrew):** `brew install --cask mactex`

### Required LaTeX Packages

All packages below are included in `texlive-full` / `texlive-latex-extra`. Key packages:

| Package | Purpose |
|---------|---------|
| `beamer` | Presentation framework |
| `amsmath`, `amssymb`, `mathtools` | Mathematics |
| `tikz`, `pgfplots` | Diagrams and plots |
| `tcolorbox` | Colored boxes for emphasis |
| `listings` | Code display |
| `algorithm`, `algpseudocode` | Pseudocode |
| `graphicx`, `hyperref` | Graphics and links |

---

## Compiling Individual Lectures (Recommended)

Each lecture is a **standalone** Beamer document that can be compiled independently.

### Method 1: `latexmk` (Automatic)

```bash
cd lectures/lecture01
latexmk -pdf lecture01.tex
```

This automatically handles multiple compilation passes and bibliography updates.

### Method 2: Manual (pdflatex)

```bash
cd lectures/lecture01
pdflatex lecture01.tex
pdflatex lecture01.tex          # Run twice to resolve references
```

**Output:** `lectures/lecture01/lecture01.pdf`

---

## Batch-Compiling All Lectures

### Bash/Zsh (Linux/macOS)

```bash
#!/bin/bash
for i in {01..13}; do
  echo "Compiling lecture$i..."
  cd "lectures/lecture$i"
  latexmk -pdf "lecture$i.tex"
  cd ../..
done
echo "All lectures compiled!"
```

### PowerShell (Windows)

```powershell
for ($i = 1; $i -le 13; $i++) {
  $num = "{0:D2}" -f $i
  Write-Host "Compiling lecture$num..."
  Set-Location "lectures/lecture$num"
  latexmk -pdf "lecture$num.tex"
  Set-Location ../..
}
Write-Host "All lectures compiled!"
```

---

## Customization

### Changing the Theme

Edit `shared/preamble.tex`:

```latex
\usetheme{Madrid}         # Change to: Metropolis, AnnArbor, Singapore, etc.
\usecolortheme{default}   # Change to: albatross, beaver, dove, etc.
```

### Changing HIT Colors

Edit `shared/preamble.tex` to modify:

```latex
\definecolor{hitblue}{RGB}{0,51,102}        % Primary color
\definecolor{hitgold}{RGB}{192,148,0}       % Accent color
\definecolor{hitlight}{RGB}{230,240,250}    % Background
```

### Adding Custom Macros

Add new mathematical notation to `shared/macros.tex`:

```latex
\newcommand{\myop}{\mathrm{MyOp}}
```

Then use in any lecture: `\myop`

### Adding Figures

Replace placeholders with real figures:

```latex
% Before (placeholder):
\placeholder{0.8\textwidth}{4cm}{Model Architecture}

% After (real figure):
\includegraphics[width=0.8\textwidth]{figures/architecture.png}
```

---

## Lecture Overview

| Lecture | Topic | Key Papers |
|---------|-------|-----------|
| 1 | Foundation Models Paradigm | Bommasani et al.\ (2021) |
| 2 | Scaling Laws & Optimal Training | Kaplan et al., Hoffmann et al. |
| 3 | Transformer Architectures | Vaswani et al., Dao et al., Fedus et al. |
| 4 | Large-Scale Pretraining | Brown et al., Devlin et al. |
| 5 | Efficient Fine-Tuning | Hu et al. (LoRA), Dettmers et al. (QLoRA) |
| 6 | RLHF & Alignment Part A | Ouyang et al. (2022) |
| 7 | DPO & Alignment Part B | Rafailov et al. (2023), Bai et al. |
| 8 | Reasoning Models | Wei et al. (CoT), Yao et al. (ToT) |
| 9 | Multimodal Models | Radford et al. (CLIP), Alayrac et al. (Flamingo) |
| 10 | Vision Foundation Models | Dosovitskiy et al. (ViT), Oquab et al. (DINOv2) |
| 11 | Knowledge-Augmented (RAG) | Lewis et al., Asai et al. (Self-RAG) |
| 12 | Evaluation & Safety | Liang et al. (HELM), OWASP/NIST |
| 13 | Research Frontiers & Projects | Open problems, student presentations |

---

## Grading (Course Structure)

| Component | Weight |
|-----------|--------|
| Two Technical Assignments | 20% |
| Paper Presentation (Lecture 8) | 15% |
| Final Project | 35% |
| Final Exam | 30% |

---

## Key Resources

### Canonical Papers

1. **Bommasani et al.** (2021). "On the Opportunities and Risks of Foundation Models." arXiv:2108.07258.
2. **Kaplan et al.** (2020). "Scaling Laws for Neural Language Models." arXiv:2001.08361.
3. **Hoffmann et al.** (2022). "Training Compute-Optimal Large Language Models." arXiv:2203.15556.
4. **Vaswani et al.** (2017). "Attention is All You Need." NeurIPS.
5. **Ouyang et al.** (2022). "Training Language Models to Follow Instructions with Human Feedback." NeurIPS.
6. **Rafailov et al.** (2023). "Direct Preference Optimization: Your Language Model is Secretly a Reward Model." NeurIPS.

### Open Models to Experiment With

- **Llama 3** (Meta) — Open-source, state-of-the-art
- **Mistral 7B** (Mistral AI) — Efficient, high-quality
- **Qwen** (Alibaba) — Multilingual, strong performance
- **OpenAI GPT-4** — API-based, frontier model
- **Anthropic Claude** — API-based, strong reasoning

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| `! Undefined control sequence \softmax` | Make sure `shared/macros.tex` is loaded via preamble |
| `! File 'beamer.cls' not found` | Install TeX Live or check PATH |
| `! I can't find file 'preamble.tex'` | Compile from `lectures/lectureNN/` directory using relative paths |
| Blank PDFs or missing content | Run `pdflatex` twice (second pass resolves references) |
| Color not appearing | Ensure `\definecolor` commands are before `\setbeamercolor` |

---

## Tips for Instructors

1. **Modify titles and metadata** in each `lectureNN.tex` as needed.
2. **Add speaker notes** using `\note{...}` before `\end{frame}`.
3. **Replace `\placeholder{}`** with actual figures as you prepare.
4. **Adjust difficulty** by including/excluding advanced slides.
5. **Keep synchronous** with the course syllabus.

---

## License

Course materials © Lecturer. For educational use at HIT.

References to papers belong to their respective authors and publishers.

---

## Questions?

Contact: dror.lederman@constrol.net

Office hours: By appointment (see course Moodle page)
