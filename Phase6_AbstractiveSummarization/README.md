# Phase 6: Abstractive Summarization
**Goal:** Generate concise, legally accurate abstractive headnotes and summaries from verbose multi-page legal opinions.

## Methods & Comparative Results
- **Method A (LoRA Fine-Tuning):** Low-Rank Adaptation on query/value projections. **Codabench Score: 0.8353 (ID 1043778 - Best Variant)**.
- **Method A (LoRMA):** Multiplicative low-rank scaling. **Score: 0.8345 (ID 1043777)**.
- **Method C (Houlsby Bottleneck Adapters):** Dual-bottleneck insertion. **Score: 0.8277 (ID 1043780)**.
- **Method B (Sequence-Level Distillation):** Student sequence distillation trained on Kaggle dual-T4 GPUs. **Score: 0.8237 (ID 1044525)**.
- **Method D (Pfeiffer Adapters):** Single post-FFN bottleneck adapters. **Score: 0.8206 (ID 1043781)**.
- **Method B (Prompt Tuning):** Prefix prompt vectors. **Score: 0.8133 (ID 1043779)**.

All executed notebooks, ROUGE metric logs, raw observations, and submission files are archived.
