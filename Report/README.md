# CS781 Capstone Project: Report & Results

**Student Name:** Shubham Joshi  
**Roll Number:** 240500  
**Email:** `shubhamj24@iitk.ac.in`  
**Codabench Username:** `s_240500`  
**Institution:** Department of Computer Science and Engineering, IIT Kanpur  
**Project Repository:** [https://github.com/SHUB-1806/CS781_capstone](https://github.com/SHUB-1806/CS781_capstone)  

---

## 1. Overview

This directory contains the final compiled academic report, verified results, and complete LaTeX source files for the **CS781 Capstone Project: In-House Legal Intelligence System**.

- **Official Compiled PDF:** [`CS781-CP-Shubham-Joshi-240500-report.pdf`](./CS781-CP-Shubham-Joshi-240500-report.pdf)
- **Overleaf-Ready Source Package:** [`CS781_Final_Report_LaTeX.zip`](./CS781_Final_Report_LaTeX.zip)
- **LaTeX Source Files:** [`latex/`](./latex/) / [`latex_source/`](./latex_source/)
- **Verified Benchmark Results:** [`results/`](./results/) / [`results_manifest/`](./results_manifest/)

---

## 2. Official Competition Results Summary

All seven phases were executed under strict Kaggle dual-T4 GPU boundaries and the 50M--300M parameter ceiling. Below are our best finished submissions recorded on the official Codabench competition leaderboard:

| Phase | Task Description | Best Variant / Model | Primary Metric | Score | Codabench Submission ID | Status | Valid Submissions |
|:---:|:---|:---|:---|:---:|:---:|:---:|:---:|
| **1** | Legal LM Pretraining | Model A (Rotary Causal Decoder, 200M tokens) | BERTScore F1 | **0.8348** | `958572` | Finished | 4 / 20 |
| **2** | Legal Named Entity Recognition (L-NER) | Model A (Full FT + Window Averaging + BIO Viterbi) | Exact-span Macro-F1 | **0.4851** | `977344` | Finished | 7 / 40 |
| **3** | Rhetorical Role Prediction (RR) | Model A (rsLoRA rank-16, $\alpha=32$) | Macro-F1 | **0.4560** | `993609` | Finished | 5 / 40 |
| **4** | Court Judgment Prediction (CJPE) | Model A (LoRMA rank-16 + Threshold Tuning) | Macro-F1 | **0.7705** | `1009524` | Finished | 5 / 40 |
| **5** | Legal Statute Identification (LSI) | Model A (Full FT + Calibrated Sigmoid Thresholds) | Macro-F1 | **0.3970** | `1013611` | Finished | 4 / 40 |
| **6** | Abstractive Summarization | Model A (LoRA rank-16 + Contrastive Filtering) | BERTScore F1 | **0.8353** | `1043778` | Finished | 6 / 40 |
| **7** | Prior Case Retrieval (PCR) | Model B (Prompt Tuning + BM25 Reciprocal Rank Fusion) | Micro-F1@7 | **0.4365** | `1042346` | Finished | 11 / 40 |

> *Alternative High-Performing Variants:*
> - **Phase 2:** Model A LoRMA Calibrated achieved **0.4839** (Sub ID: `977526`).
> - **Phase 3:** Model A LoRMA achieved **0.4511** (Sub ID: `993608`).
> - **Phase 4:** Model A Full Fast V2 achieved **0.7464** (Sub ID: `1009521`).
> - **Phase 5:** Model A LoRMA achieved **0.3966** (Sub ID: `1013621`).
> - **Phase 6:** Model A LoRMA achieved **0.8345** (Sub ID: `1043777`); Distilled 62M student achieved **0.8237** (Sub ID: `1044525`).
> - **Phase 7:** Model B LoRMA achieved **0.4353** (Sub ID: `1042349`); Sequence Distillation achieved **0.4353** (Sub ID: `1042352`).

---

## 3. Directory Layout

```text
Report/
├── CS781-CP-Shubham-Joshi-240500-report.pdf   # Final compiled 13-page report
├── CS781_Final_Report_LaTeX.zip                # Complete Overleaf upload bundle
├── README.md                                   # This documentation file
├── figures/                                    # High-resolution vector figures
│   ├── saved_learning_curves.pdf              # Pretraining loss curves (Models A, B, C, D)
│   └── per_label.pdf                           # Rhetorical role & NER per-class F1 breakdown
├── latex/                                      # LaTeX source files (Overleaf structure)
│   ├── Report.tex                              # Main LaTeX source document
│   ├── references.bib                          # BibTeX citations
│   └── figures/                                # Embedded PDF figures
├── latex_source/                               # Secondary mirror for compatibility
│   ├── Report.tex
│   ├── references.bib
│   ├── template_original.tex
│   └── figures/
└── results/                                    # Verified benchmark metrics & data
    ├── results_verified.csv                    # Codabench submission history & scores
    ├── results_verified.json                   # Structured JSON records of all submissions
    ├── results_reviewed.csv                    # Comprehensive cross-phase evaluation metrics
    ├── results_reviewed.json                   # Detailed variant analysis
    └── rr_per_label.json                       # Per-class metrics for Rhetorical Role classification
```

---

## 4. Report Structure

The academic report strictly conforms to the course guidelines (11pt type, letter paper, 1-inch margins, standard section structure):

1. **Section 1: Competition Result** — Codabench scores, submission table, and leaderboard rankings across all 7 phases.
2. **Section 2: Introduction and Problem Description** — Legal NLP motivation, confidentiality constraints, on-premise deployment, and phase taxonomy.
3. **Section 3: Data Analysis and Preprocessing** — Corpus statistics (21 GB, 200M tokens), 32,768 BPE legal tokenizer, document length distributions, class imbalance analysis.
4. **Section 4: Approach and Model Evolution** — 4 custom foundation architectures (Rotary Causal Decoder, Enc-Dec, Hybrid Transformer-GRU, Sparse Attention) and PEFT adaptation mechanisms (LoRMA, LoRA, rsLoRA, Bottleneck Adapters, BitFit, $(IA)^3$, Prompt/Prefix Tuning, Distillation).
5. **Section 5: Experiments and Implementation Details** — Dual-T4 DDP setup (`multiprocessing.spawn`), FP16 mixed precision, architecture-calibrated token budgets (A/B: 200M, C: 100M, D: 25M), atomic checkpointing.
6. **Section 6: Results** — Quantitative tables, metric trajectories, compute trade-offs, and PEFT parameter efficiency analysis.
7. **Section 7: Error Analysis and Discussion** — Hard negative retrieval analysis, rhetorical role boundary confusion, court name boilerplate artifacts, and ablation of post-processing heuristics.
8. **Section 8: Conclusion** — Core takeaways, real-world deployment lessons, and future directions.
9. **LLM Usage Declaration** — Detailed compliance statement (Q1--Q4), listing permitted assistance for debugging, conceptual explanations, plotting, and formatting, with an explicit 8--12 sentence personal-contribution statement.
10. **References** — Complete bibliography formatted in IEEE style.

---

## 5. Compiling the LaTeX Source

To compile the LaTeX source into a PDF:

### Option A: Overleaf (Recommended)
1. Download or locate [`CS781_Final_Report_LaTeX.zip`](./CS781_Final_Report_LaTeX.zip).
2. Go to [Overleaf](https://www.overleaf.com), click **New Project** $\to$ **Upload Project**, and select the zip file.
3. Ensure the compiler is set to **pdfLaTeX** and the main file is set to `Report.tex`.
4. Click **Recompile**.

### Option B: Local TeXLive / MacTeX / MikTeX
```bash
cd latex
pdflatex Report.tex
bibtex Report
pdflatex Report.tex
pdflatex Report.tex
```
