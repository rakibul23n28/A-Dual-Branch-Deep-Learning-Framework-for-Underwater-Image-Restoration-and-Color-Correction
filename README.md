# Underwater Image Restoration and Color Correction Research Paper

## Overview
This project presents a research paper on underwater image restoration and color correction using a dual-branch deep learning framework. The work focuses on improving underwater image quality by reducing scattering effects, restoring scene structure, and correcting the strong blue-green color cast that commonly appears in marine images.

The study is built around a practical research workflow that combines:
- underwater image enhancement problem formulation,
- literature review of relevant methods,
- a custom deep learning architecture,
- experiments on benchmark datasets,
- ablation analysis, and
- qualitative and quantitative evaluation.

## Research Title
A Dual-Branch Deep Learning Framework for Underwater Image Restoration and Color Correction

## Problem Statement
Underwater images suffer from several degradations, including:
- wavelength-dependent light attenuation,
- scattering from suspended particles,
- low contrast and poor visibility,
- dominant blue-green color casts,
- loss of fine structure and edge details.

These issues reduce the usefulness of underwater images for marine observation, robotics, environmental monitoring, and computer vision tasks. Traditional image enhancement methods often handle either visibility restoration or color correction separately, which limits their robustness in real underwater scenes.

## Research Gap
Existing underwater image enhancement methods show progress in restoration and color balancing, but there is still a gap in models that can jointly:
- restore scene radiance and structure,
- correct chromatic imbalance,
- preserve image realism,
- adapt to varying water conditions,
- perform reliably on challenging underwater scenes.

This motivates the proposed dual-branch approach, where restoration and color correction are treated as complementary tasks rather than a single combined objective.

## Core Idea
The proposed model uses a dual-branch architecture:

1. Restoration branch
   - focuses on dehazing and scene recovery,
   - reconstructs structural details,
   - reduces haze-like veiling effects,
   - recovers transmission-aware image information.

2. Color-correction branch
   - focuses on correcting channel imbalance,
   - suppresses blue-green dominance,
   - restores natural color distribution,
   - improves perceptual image quality.

The two branch outputs are then combined through a fusion mechanism, allowing the network to adaptively balance structural restoration and color correction.

## Methodology
The paper follows a deep learning pipeline built from the notebook experiments:

### Dataset
- UIEB dataset for paired underwater and reference images
- Challenging-60 underwater subset for robustness evaluation
- Image preprocessing with resizing and augmentation

### Model variants tested
- U-Net + L1
- Dual-Branch + L1
- Dual-Branch + Gated Fusion
- Dual-Branch + Attention
- Final Dual-Branch Model

### Loss function
The final model uses a hybrid objective:
- L1 loss for pixel-wise reconstruction fidelity
- SSIM loss for structural similarity and contrast preservation

The notebook uses the combined form:

L_total = 0.8 * L1 + 0.2 * SSIM

This balance helps the model keep fine details while improving global color realism.

### Training Settings
- Batch size: 8
- Optimizer: AdamW
- Learning rate: 1e-4
- Scheduler: Cosine Annealing LR
- Epochs: 20
- Input size: 256 x 256

## Experiments
The experimental section includes:

### 1. Quantitative evaluation
Metrics used:
- PSNR
- SSIM
- UIQM
- UCIQE

These metrics measure image reconstruction quality, structure preservation, and perceptual underwater image quality.

### 2. Ablation study
The experiments compare different model variations to identify the contribution of each component. The results show that:
- a single U-Net model is effective but less robust to color distortion,
- dual-branch networks improve decomposition of restoration and correction tasks,
- fusion and attention modules further improve performance,
- the final model gives the best overall balance.

### 3. Challenge-set evaluation
The final model is tested on the challenging underwater subset to assess robustness under severe haze, scattering, and color distortion.

### 4. Visual analysis
Side-by-side comparisons show the final model recovers clearer structure, better color balance, and visually natural outputs compared to baseline approaches.

## Key Findings
- Underwater restoration and color correction should be addressed jointly.
- A single restoration stream is not enough to handle strong underwater color cast.
- Dual-branch decomposition improves the model’s ability to process both structural and chromatic distortions.
- Fusion and attention mechanisms improve overall image quality.
- The final model is better suited for real underwater environments than simpler baselines.

## Importance of the Work
This research is important because underwater image enhancement is critical for:
- ocean monitoring,
- marine biology studies,
- underwater robotics,
- surveillance and inspection,
- computer vision in low-visibility environments.

Improving underwater visual quality can directly lead to better scene understanding, object detection, and autonomous underwater navigation.

## Kaggle Notebook
This project is based on the following Kaggle implementation and experimental workflow:
- https://www.kaggle.com/code/mdabdullah909/underwater-image-restoration-research

## Project Structure
The repository contains:
- `main.tex` — the main LaTeX paper file
- `sections/` — individual paper sections
- `references.bib` — bibliography file
- `README.md` — project overview and experiment summary

## Files of Interest
- `main.tex` — main manuscript
- `sections/introduction.tex` — introduction
- `sections/related_work.tex` — literature review
- `sections/methodology.tex` — methodology and architecture
- `sections/experiments.tex` — experimental setup and results
- `references.bib` — references

## Notes
This README is intended to provide a concise but complete description of the research contribution, methodology, and importance of the paper. It is suitable for a project overview, documentation, or repository description.
