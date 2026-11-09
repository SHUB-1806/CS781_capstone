# Phase 3: Rhetorical Role Prediction (RR)
**Goal:** Classify sentences in court judgments into structural roles (Facts, Ruling by Lower Court, Argument, Statute, Precedent, Ratio of the decision, Ruling by Present Court).

## Methods & Comparative Results
- **Method A (rsLoRA - Rank-Stabilized LoRA):** Scaling factor $\gamma / \sqrt{r}$ for stable higher-rank parameter updates. **Codabench Score: 0.4560 (ID 993609 - Best Variant)**.
- **Method A (LoRMA):** Low-rank multiplicative scaling. **Score: 0.4511 (ID 993608)**.
- **Method D (Prompt Tuning):** Soft continuous prompt tokens. **Local Validation Score: 0.4312 (ID 993612)**.
- **Method C ((IA)³):** Infused Adapter by Inhibiting and Amplifying Inner Activations. **Score: 0.4185 (ID 993619)**.
- **Method B (Student Distillation):** Distillation from Method A teacher. **Score: 0.4106 (ID 993613)**.
- **Method B (Standard LoRA):** Conventional low-rank adaptation. **Score: 0.3843 (ID 993610)**.
- **Ablation Studies:** Sentence-Only without document context (`07_A`), and Dropout 0.35 Regularization (`10_A`).

Every method subdirectory includes its executed notebook, raw `observations.zip`, and submission archive.
