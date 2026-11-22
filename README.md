# MANNeR Reproduction on MINDsmall

This repository contains a bounded reproduction of MANNeR:

> Train Once, Use Flexibly: A Modular Framework for Multi-Aspect
> Neural News Recommendation

## Original Work

- Paper: https://arxiv.org/abs/2307.16089
- Published paper: https://aclanthology.org/2024.findings-emnlp.558/
- Original implementation: https://github.com/andreeaiana/manner
- Pinned original commit:
  `a831482f4d9b4918cb7625aed1c66bb68b6db1fe`

## Submitted Code

- `MANNeR_Final_Submission.ipynb`: cleaned and reproducible Colab workflow

## Scope

The reproduction uses:

- MINDsmall
- news-title input
- MANNeR CR-Module
- Category A-Module
- `roberta-base`
- random seed 42
- NVIDIA Tesla T4
- mixed-precision GPU training

The work is a resource-constrained, single-seed reproduction rather
than an exact replication of every experiment in the paper.

## Confirmed Results

### Pipeline validation

- CR-Module smoke test: passed
- Category A-Module smoke test: passed
- Category smoke train loss: 30.299978
- Category smoke validation loss: 2.943482

The smoke-test loss values are pipeline diagnostics, not final model
performance results.

### Full CR training progress

| Epoch | Global step | Validation loss |
|------:|------------:|----------------:|
| 0 | 15,529 | 3.03542 |
| 1 | 31,058 | 3.01295 |

Validation loss improved by 0.02247, approximately 0.74%, from Epoch 0
to Epoch 1.

Full training and final test evaluation were not completed before the
submission deadline because free Google Colab sessions repeatedly
disconnected. Final AUC, MRR, nDCG@5, and nDCG@10 values are therefore
not claimed.

## Main Configuration

- Batch size: 8
- Maximum epochs: 5
- Learning rate: 1e-5
- CR temperature: 0.36
- Maximum user-history length: 50
- Negative-sampling ratio: 4
- Frozen RoBERTa layers: 0 through 7
- Checkpoint monitor: validation loss
- Early-stopping patience: 3

## Compatibility Adjustments

The notebook documents several adjustments required by the current
Colab environment:

- TorchMetrics `k=` changed to `top_k=`
- scikit-learn TSNE fallback for unavailable MulticoreTSNE
- `.project-root` marker added for pyrootutils
- accessible MINDsmall and GloVe download mirrors
- trusted full-checkpoint loading for newer PyTorch versions

## Data and Checkpoints

The MINDsmall data, GloVe embeddings, and trained checkpoints are not
stored in this repository because of their size and licensing or
distribution considerations.
