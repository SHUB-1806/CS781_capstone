# Phase 4: Court Judgment Prediction (CJPE)
**Goal:** Binary classification predicting the outcome of High Court civil and criminal appeals based on case facts and precedent arguments.

## Methods & Comparative Results
- **Method A (LoRMA Fast V2):** Low-Rank Multiplicative Adaptation with chunk-level attention aggregation. **Codabench Score: 0.7705 (ID 1009524 - Best Variant)**.
- **Method A (Full Fine-Tuning Fast V2):** End-to-end classification. **Score: 0.7464 (ID 1009521)**.
- **Method C (Houlsby Bottleneck Adapters Fast V2):** Intermediate adapter projection. **Score: 0.7285 (ID 1009525)**.
- **Method B (Task-Specific Distillation Fast V2):** Compact student classifier. **Score: 0.6294 (ID 1009526)**.
- **Method B (BitFit):** Bias-only parameter fine-tuning. **Score: 0.5779 (ID 1007811)**.
- **Method D (Partial Layer Freezing):** Freezing lower encoder representations. Executed on Kaggle dual-T4 GPUs (`05-d-partial-fast.ipynb`).

Each model includes full execution logs, observations, and submission files.
