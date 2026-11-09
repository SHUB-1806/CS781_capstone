# Phase 1: Legal Language Model Pretraining
**Goal:** Pretrain custom language models from scratch on raw Indian legal corpora (Court judgments and acts).

## Architectures Explored
- **Model A (Modern RoBERTa Encoder-Only, 200M Tokenizer):** 12-layer bidirectional Transformer encoder with rotary position embeddings (RoPE), pre-layer normalization (RMSNorm), GeLU activation, and AdamW optimizer. Achieved **0.8348 Pretraining Accuracy (Rank 1)** on Codabench (ID `958572`).
- **Model B (LLaMA/Mistral Causal Decoder, 200M Tokenizer):** 12-layer autoregressive causal decoder with SwiGLU activation, RoPE embeddings, and causal self-attention. Score: `0.7977` (ID `958564`).
- **Model C (GRU-Transformer Hybrid, 100M Tokenizer):** Recurrent-attention hybrid with interleaved gated recurrent unit layers and multi-head self-attention to optimize sequential inductive bias under reduced tokenizer budgets. Score: `0.8308` (ID `958568`).
- **Model D (Sparse Longformer-Style Decoder, 25M Tokenizer):** Dilated sparse causal decoder designed for extended legal contexts with memory-efficient local window attention. Score: `0.8264` (ID `960903`).

## Subdirectory Structure
- `Preprocessing/`: Custom byte-pair encoding (BPE) tokenizer training scripts for 25M, 50M, 100M, and 200M vocabularies.
- `Training_Notebooks/`: Fully executed training runs with consumed-token history, loss curves, and optimizer trajectories.
- `Submission_Notebooks/`: Inference scripts formatting output tensors to official competition specs.
- `Submissions/`: Validated submission ZIP archives for Models A, B, C, and D.
