# Phase 2: Legal Named Entity Recognition (L-NER)
**Goal:** Sequence labeling over Indian legal judgments identifying entities such as Courts, Judges, Petitioners, Respondents, Statutes, and Precedents.

## Methods & Comparative Results
- **Method A (Full Fine-Tuning, Calibrated):** Fine-tuning all encoder parameters with temperature scaling. **Codabench Score: 0.4851 (ID 977344)**.
- **Method A (LoRMA Matrix Adaptation, Calibrated):** Low-Rank Multiplicative Adaptation. **Score: 0.4839 (ID 977526)**.
- **Ensemble (Validated Rank Ensemble):** Weighted logit aggregation of top calibrated models. **Score: 0.4839 (ID 977669)**.
- **Method D (Partial Layer Freezing):** Freezing bottom 6 transformer layers. **Score: 0.4230 (ID 977521)**.
- **Method C (Houlsby Bottleneck Adapters):** Sequential bottleneck adapters. **Score: 0.4072 (ID 977350)**.
- **Method B (LoRA Fine-Tuning):** Low-Rank Adaptation ($r=16, \alpha=32$). **Score: 0.2019 (ID 977348)**.
- **Method B (Student Distillation):** 6-layer compact distilled student. **Score: 0.1438 (ID 977345)**.

All notebooks in `Notebooks/` are fully executed with entity-level F1 evaluation outputs.
