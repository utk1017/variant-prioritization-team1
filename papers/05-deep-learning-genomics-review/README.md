# Deep learning: new computational modelling techniques for genomics (review)

**Assigned to:** Aditya
**Paper:** Eraslan, Avsec, Gagneur & Theis, *Nature Reviews Genetics* 20, 389–403 (2019)
**Codebase:** — (review paper; surveys many tools rather than shipping one)

## About
Review of deep-learning methods across genomics — one-hot sequence encoding, CNNs, RNNs,
multitask / transfer learning, model interpretation, autoencoders and GANs. Useful as shared
background for the whole team, and part of Aditya's assignment.

Because it surveys the field rather than shipping one tool, the approach here is to
**demonstrate one representative method end to end** and connect it to the team's
variant-prioritization goal.

## How to run

**Notebook:** [`deep_learning_genomics_review_demo.ipynb`](./deep_learning_genomics_review_demo.ipynb)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/adtyapnda/variant-prioritization-team1/blob/main/papers/05-deep-learning-genomics-review/deep_learning_genomics_review_demo.ipynb)

Fully self-contained — no downloads, runs in seconds on CPU (Colab or local). It:
1. One-hot encodes DNA sequence.
2. Trains a small **DeepBind / Basset / Akita-style CNN** to detect a CTCF-like binding motif
   on synthetic data.
3. Runs **in-silico saturation mutagenesis (ISM)** to score every possible single-nucleotide
   variant.
4. **Ranks variants by predicted effect** — the same interpretation technique Akita (paper 04)
   applies to Hi-C contact maps.

## Output
The notebook already contains its executed outputs:
- Training-loss curve (BCE **0.69 → 0.16** over 15 epochs)
- Test **accuracy 0.993**, **ROC-AUC 1.000**
- **ISM variant-effect heatmap** + per-position importance track — the model localises the
  planted motif on its own, without being told where it is
- **Top-10 ranked single-nucleotide variants** by |Δ score|

Everything uses synthetic data with a fixed seed, so it is an *illustrative reproduction of the
workflow* the review describes — not the real Akita model (see [`../04-akita/`](../04-akita/)
for the notebook that runs the actual pre-trained Akita).

## Status
🟢 Done — notebook runs end-to-end with outputs saved inside it
