# Review of the six final Phase 2 runs

All six local prediction ZIPs pass the official schema plus exact test-ID/text-bound checks. The saved notebooks report completed jobs with matching delivered runtime code, shape/gradient checks and best-checkpoint selection. No saved exception or hardcoded-answer modification was found.

The important limitation is model quality: B LoRA and B distillation remain weak. These baseline/rebuild jobs did not run notebook 07's stronger character-context candidates. Completing the methods does not mean the 0.4 floor or 0.6–0.7 target was achieved.

| Method | Native validation F1 | Selected epoch | Local ZIP |
|---|---:|---:|---|
| A full | 0.5347 | 8 | [submission_Final_A_full_calibrated.zip](submission_Final_A_full_calibrated.zip) |
| B LoRA | 0.1572 | 9 | [submission_Rebuild_B_lora_calibrated.zip](submission_Rebuild_B_lora_calibrated.zip) |
| C adapters | 0.3593 | 14 | [submission_Rebuild_C_adapters_calibrated.zip](submission_Rebuild_C_adapters_calibrated.zip) |
| D partial | 0.4534 | 15 | [submission_Rebuild_D_partial_calibrated.zip](submission_Rebuild_D_partial_calibrated.zip) |
| A LoRMA | 0.5401 | 10 | [submission_Rebuild_A_lorma_calibrated.zip](submission_Rebuild_A_lorma_calibrated.zip) |
| B distillation | 0.1425 | 9 | [submission_Final_B_distillation_calibrated.zip](submission_Final_B_distillation_calibrated.zip) |

These are original development selection scores, not recomputed private Codabench scores. Larger fitted calibration scores in notebook output reuse the ten validation documents and must not be presented as an independent test score.

## Important file-selection discrepancy

A full and B distillation both completed a separate final refit on all 70 released training documents. This folder contains their calibrated **development** candidates, not the selected public-refit predictions. The current files are valid submissions, but they do not represent those final refits. Download the exact saved files below if you intend to submit the refitted models; no retraining is required:

**A full:**

`/kaggle/working/cs781_phase2_final/Final_A_full/refit70/submission_Final_A_full_refit70.zip`

Expected ZIP SHA-256: `120bc6a3976d68aa7402bf2b921bb62b8277b0e3237d2d35a70ead9dc9af0e0d`

**B distillation:**

`/kaggle/working/cs781_phase2_final/Final_B_distillation/refit70/submission_Final_B_distillation_refit70.zip`

Expected ZIP SHA-256: `a2cfc1c1b78d039546513067dbb60851adab2836710008c6c54984dc3c6e253a`

B LoRA, C adapters, D partial and A LoRMA local ZIPs match the output *variant/name* selected by their completed development jobs. They have not undergone the separate all-70 refit in these runs. Their calibration changes the predictions, so a native checkpoint prediction checksum need not match a calibrated ZIP.

## What to submit or improve

- A full, A LoRMA and D partial are reasonable learned submission candidates. Retain both development/refit variants when available; private performance of the new refits is unmeasured.
- C adapters is a valid learned experiment, but native F1 is below 0.4. Modest further held-out training/context experiments are reasonable; there is no guaranteed gain.
- B LoRA and B distillation are valid method-completion submissions but weak score candidates. Their completed curves peaked at epoch 9 and then plateaued; simply repeating the same training is not supported as a solution.
- If time remains, run the existing 07 controlled candidate comparisons for B first, using its completed output as baseline. Keep the stronger completed native validation model. D was still improving at epoch 15, so a five-epoch held-out extension is more justified for D than for plateaued B.
- Exporter 00 also produced an older LoRMA candidate with native F1 0.541746 versus the rebuilt 0.540054. Its prediction ZIP is not in this folder. That small validation difference does not prove a better private score.

## Evidence and limits

The folder contains executed notebooks and prediction ZIPs, not the actual .pt checkpoint tensors or full training_summary.json/metric histories. Remote states were verified by the saved Kaggle runtime, but were not independently loaded on this computer. For four calibrated ZIPs, saved final reports do not contain a calibrated prediction checksum; format/content checks pass, but weights-to-calibrated-prediction reproduction requires the complete saved Kaggle outputs.

A full development prediction bytes match the earlier confirmed A checkpoint receipt. B distillation development prediction bytes match its executed development receipt. Neither matches its completed public-refit prediction receipt, confirming the file-selection discrepancy.

Keep all complete Kaggle checkpoint outputs for recovery and academic evidence. No private test labels were read or used in this audit. Detailed hashes, epoch logs, parameter counts, teacher receipt and per-label metrics are in `../qa/Final_Submission_Review/review.json`.
