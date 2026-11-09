# Phase 7: Prior Case Retrieval (PCR)
**Goal:** Retrieve precedent cases relevant to a target query judgment from a candidate corpus of thousands of legal opinions.

## Two-Stage Architecture & Breakthrough
1. **Stage 1 (Dense Baselines):** Initial bi-encoder embedding retrieval yielded MAP scores between `0.2451` and `0.2676` (IDs 1041957–1041962).
2. **Stage 2 (Improved Hybrid BM25 + Dense + Reciprocal Rank Fusion):** Combining lexical sparse BM25 retrieval with fine-tuned dense embeddings via Reciprocal Rank Fusion ($k=60$) yielded a massive **+63% performance jump**:
   - **Method B (Prompt Tuning + Hybrid RRF): Codabench Score: 0.4365 (ID 1042346 - Best Variant)**.
   - **Method A (LoRMA + Hybrid RRF): Score: 0.4353 (ID 1042349)**.
   - **Method B (Automatic Distillation): Score: 0.4353 (ID 1042352)**.
   - **Method A (Partial Freezing + Hybrid RRF): Score: 0.4347 (ID 1042347)**.
   - **Method D (Prefix Tuning + Hybrid RRF): Score: 0.4335 (ID 1042343)**.
   - **Method C ((IA)³ + Hybrid RRF): Score: 0.4330 (ID 1042344)**.

All baseline and improved hybrid notebooks are fully executed with retrieval evaluation rankings.
