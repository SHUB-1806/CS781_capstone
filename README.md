# CS781: Special Topics in NLP — Capstone Project (Legal NLP)

**Student:** Shubham Joshi  
**Roll Number:** 240500  
**Email:** `shubhamj24@iitk.ac.in` / `shubhammaheshjoshi@gmail.com`  
**Codabench Username:** `s_240500`  
**Official Repository:** [https://github.com/SHUB-1806/CS781_capstone](https://github.com/SHUB-1806/CS781_capstone)  

---

## 📌 Executive Summary

This repository contains the complete code, models, parameter-efficient fine-tuning (PEFT) pipelines, executed Jupyter notebooks, raw observation logs, official Codabench submission archives, and the final 10-page academic report for the **CS781 Natural Language Processing Capstone Project**.

The project investigates the entire life cycle of domain-specific legal language modeling across **seven competitive phases**:
1. **Pretraining from Scratch:** 4 distinct architectures (Encoder, Causal Decoder, Recurrent-Hybrid, Sparse Decoder) trained on raw Indian legal corpora with custom BPE tokenizers.
2. **Legal Named Entity Recognition (L-NER):** Entity sequence tagging with full parameter fine-tuning, LoRA, LoRMA, and temperature calibration.
3. **Rhetorical Role Prediction (RR):** Multi-class discourse classification using Rank-Stabilized LoRA (rsLoRA), LoRMA, (IA)³, and Prompt Tuning.
4. **Court Judgment Prediction (CJPE):** Long-document appeal outcome prediction utilizing LoRMA matrix scaling and dual-T4 distributed data parallel training.
5. **Legal Statute Identification (LSI):** Extreme multi-label statutory section classification under class imbalance.
6. **Abstractive Summarization:** Generating legal headnotes using low-rank adaptation (LoRA), bottleneck adapters, and sequence distillation.
7. **Prior Case Retrieval (PCR):** Two-stage dense-sparse hybrid retrieval combining dense bi-encoders with BM25 lexical search via Reciprocal Rank Fusion (RRF).

---

## 🏆 Official Finished Results Across All Seven Phases

| Phase | Task Domain | Best Performing Method | Codabench ID | Finished Score | Primary Evaluation Metric |
| :---: | :--- | :--- | :---: | :---: | :--- |
| **P1** | Legal LM Pretraining | **Model A (Modern RoBERTa 200M, AdamW)** | `958572` | **0.8348** | Pretraining Accuracy (Rank 1) |
| **P2** | Legal Named Entity Recognition | **Method A Full Fine-Tuning (Calibrated)** | `977344` | **0.4851** | Strict Micro Macro F1 |
| **P3** | Rhetorical Role Prediction | **Method A rsLoRA (Rank-Stabilized LoRA)** | `993609` | **0.4560** | Macro F1 |
| **P4** | Court Judgment Prediction | **Method A LoRMA Fast V2** | `1009524` | **0.7705** | Macro F1 |
| **P5** | Legal Statute Identification | **Method A Full Fine-Tuning** | `1013611` | **0.3970** | Macro F1 |
| **P6** | Abstractive Summarization | **Method A LoRA Fine-Tuning** | `1043778` | **0.8353** | Mean ROUGE-1 |
| **P7** | Prior Case Retrieval | **Method B Prompt Tuning (Hybrid RRF)** | `1042346` | **0.4365** | Top-$k$ Retrieval MAP |

---

## 📂 Repository Organization

```
CS781_capstone/
├── README.md                                    <-- Master documentation & benchmark results
├── LICENSE                                      <-- MIT Open-Source License
├── requirements.txt                             <-- Pinned dependencies
├── NOTEBOOK_EXECUTION_AUDIT.md                  <-- Audit of all 67 notebooks
├── MANIFEST_FILES.json                          <-- Machine-readable checksums & file inventory
│
├── Report/                                      <-- Submission-Ready Report Package
│   ├── CS781-CP-Shubham-Joshi-240500-report.pdf <-- Compiled 10-page final report PDF
│   ├── Report.tex                               <-- Main report LaTeX source
│   ├── references.bib                           <-- Complete BibTeX bibliography
│   ├── template_original.tex                    <-- Official course template
│   ├── CS781_Report_Draft_LaTeX.zip             <-- Overleaf-ready ZIP archive
│   ├── figures/saved_learning_curves.pdf        <-- Vector pretraining curves
│   └── results_manifest/                        <-- Verified CSV and JSON results matrices
│
├── Phase1_Pretraining/                          <-- Pretraining (Models A, B, C, D)
├── Phase2_LNER/                                 <-- Legal NER (00 through 06)
├── Phase3_RhetoricalRoles/                      <-- Rhetorical Roles (01 through 10)
├── Phase4_CourtJudgmentPrediction/              <-- CJPE Binary Classification
├── Phase5_LegalStatuteIdentification/           <-- Multi-label Statute Classification
├── Phase6_AbstractiveSummarization/             <-- Abstractive Summarization & Distillation
└── Phase7_PriorCaseRetrieval/                   <-- Dense & Hybrid RRF Prior Case Retrieval
```

---

## 🚀 Environment Setup & Reproducibility

### 1. Installation
Clone this repository and install the dependencies:
```bash
git clone https://github.com/SHUB-1806/CS781_capstone.git
cd CS781_capstone
pip install -r requirements.txt
```

### 2. Dual NVIDIA T4 GPU Training on Kaggle
Training was optimized for dual NVIDIA T4 GPUs using:
- **PyTorch DistributedDataParallel (DDP):** Spawned across both GPUs (`CUDA_VISIBLE_DEVICES=0,1`).
- **Mixed Precision (`fp16`):** Native `torch.cuda.amp.autocast()` to conserve VRAM.
- **Dynamic Padding & Gradient Accumulation:** Minimizing wasted FLOPs on batch padding.
- **Token Budget Allocation:** High-capacity Model A & B on 200M tokenizers, Model C on 100M tokenizers, and Model D on 25M tokenizers to resolve hardware OOM constraints.

---

For questions or inquiries, please contact:  
**Shubham Joshi** (`shubhamj24@iitk.ac.in` / `shubhammaheshjoshi@gmail.com`)
