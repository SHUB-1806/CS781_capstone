# Phase 5: Legal Statute Identification (LSI)
**Goal:** Extreme multi-label classification predicting relevant sections of the Indian Penal Code (IPC) and other statutory acts cited in judgment narratives.

## Methods & Comparative Results
- **Method A (Full Fine-Tuning):** Full parameter optimization with binary cross-entropy with logits. **Codabench Score: 0.3970 (ID 1013611 - Best Variant)**.
- **Method A (LoRMA):** Low-Rank Multiplicative Adaptation. **Score: 0.3966 (ID 1013621)**.
- **Method C (Houlsby Adapters):** Bottleneck adapter modules. **Score: 0.3618 (ID 1013620)**.
- **Method D (Partial Layer Freezing):** Top-layer fine-tuning. **Score: 0.395+ (ID 1013608)**.
- **Method B (Prompt Tuning):** Virtual soft prompt prefixing. **Score: 0.2783 (ID 1013618)**.
- **Method B (Distillation):** Compact student multi-label classifier.

All 6 methods are accompanied by executed training notebooks and observation files.
