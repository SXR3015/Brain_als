# Brain_als
# ALSAnchorNet: Biologically Informed Multimodal MRI Fusion for Amyotrophic Lateral Sclerosis Diagnosis

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![PyTorch](https://img.shields.io/badge/PyTorch-1.9+-ee4c2c?logo=pytorch)](https://pytorch.org/)

> **Official PyTorch implementation of the MICCAI paper:**  
> *"ALSAnchorNet: Biologically Informed Multimodal MRI Fusion for Amyotrophic Lateral Sclerosis Diagnosis"*

🔗 **[Paper Link]** (Coming Soon) | 📊 **[Dataset]** (Restricted Access) | 📧 **[Contact]**

---

## 🌟 Highlights

- **Neuroanatomically Grounded Design**: Bridges macroscale connectomics (FC/SC) and microscale glymphatic dysfunction (PVS, ALPS, etc.) via a biologically plausible architecture.
- **Frontal Anchor Attention (FAA)**: A novel attention mechanism that leverages frontal lobe vulnerability in ALS, using intra-prefrontal connectivity as queries to modulate whole-brain interactions.
- **Superior Performance**: Achieves **77% Accuracy** and **0.80 AUC** on our multi-center ALS cohort (159 ALS, 107 HC), significantly outperforming standard fusion baselines (+6% Acc, +12% AUC).
- **Interpretability**: Gradient-based attribution validates that the model focuses on clinically relevant regions (SFG, PCL, PrG) consistent with known ALS pathogenesis.

---

## 🏗️ Architecture Overview

BrainAnchorNet integrates multimodal biomarkers through three core stages:

1.  **Frontal Extractors**: Separately process internal (68×68) and external (68×178) prefrontal connections from FC/SC matrices (246-region atlas).
2.  **AttentionFusion Module**: Uses intra-prefrontal features as *Queries* to attend to whole-brain contexts (*Keys/Values*).
3.  **Multimodal Fusion**: Fuses attended connectomic features with linear-encoded glymphatic markers (ALPS, PVS, ChP, FWF, gBOLD-CSF) for final classification.

<p align="center">
  <img src="assets/architecture_diagram.png" alt="ALSAnchorNet Architecture" width="800"/>
  <br>
  <em>Figure 1: Overall framework of BrainAnchorNet. The frontal Anchor Attention (FAA) module explicitly models frontal vulnerability.</em>
</p>

---

## 📋 Requirements

Install dependencies via `conda` or `pip`:

```bash
# Create environment
conda create -n brainanchor python=3.8
conda activate brainanchor

# Install PyTorch (adjust CUDA version as needed)
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

# Install other dependencies
pip install -r requirements.txt
