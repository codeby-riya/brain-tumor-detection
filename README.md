# Brain Tumor Detection with Explainable AI

An AI-powered brain tumor detection system that uses MRI scans and Explainable AI (XAI) techniques to provide accurate and interpretable predictions. The model leverages EfficientNetB4 along with Grad-CAM, Grad-CAM++, and LIME to improve both performance and transparency.

## Overview

Traditional deep learning models often behave as "black boxes", making it difficult to understand why a prediction was made. This project addresses that challenge by integrating multiple Explainable AI techniques to generate interpretable visual explanations alongside predictions.

The model was trained on a balanced MRI dataset and enhanced using advanced training strategies to improve robustness and generalization.

---

## Features

- Brain tumor classification from MRI images
- EfficientNetB4-based deep learning architecture
- Explainable AI using:
  - Grad-CAM
  - Grad-CAM++
  - LIME
- Consensus heatmap combining multiple explanations
- Advanced data augmentation using Albumentations
- Two-phase fine-tuning strategy
- Test-Time Augmentation (TTA)
- Robust training with Mixup, CutMix, and Focal Loss

---

## Dataset

Dataset used:

**Br35H Brain Tumor Detection Dataset**

Dataset characteristics:

- Total Images: 3000
- Tumor Images: 1500
- No Tumor Images: 1500
- Train Split: 2100
- Validation Split: 450
- Test Split: 450

---

## Model Architecture

### Backbone

EfficientNetB4

### Classification Head

```text
GlobalAvgPool
↓
BatchNorm
↓
Dropout (0.4)
↓
Fully Connected (512)
↓
GELU
↓
BatchNorm
↓
Dropout (0.3)
↓
Fully Connected (2)
```

---

## Training Strategy

### Phase 1
- Freeze EfficientNet backbone
- Train custom head
- Epochs: 10
- Learning Rate: 3e−4

### Phase 2
- Unfreeze all layers
- Fine-tune complete model
- Epochs: 15
- Learning Rate: 5e−5

---

## Data Augmentation

Albumentations pipeline:

- Random Affine Transform
- Elastic Transform
- Gaussian Blur
- Random Brightness/Contrast
- Horizontal Flip
- Vertical Flip
- Gaussian Noise

Additional techniques:

- Mixup
- CutMix
- Test-Time Augmentation (TTA)

---

## Explainable AI Methods

### Grad-CAM
Generates class activation maps highlighting important image regions.

### Grad-CAM++
Improves localization performance for multiple regions and finer details.

### LIME
Creates local interpretable explanations by perturbing image segments.

### Consensus Map
Combines Grad-CAM and LIME outputs to provide more reliable and clinically interpretable explanations.

---

## Results

| Metric | Score |
|----------|--------|
| Accuracy | 97.33% |
| Precision | 98.63% |
| Recall | 96.00% |
| F1 Score | 97.29% |
| AUC-ROC | 0.9992 |
| Cohen Kappa | 0.9467 |
| MCC | 0.9467 |

---


## Tech Stack

- Python
- PyTorch
- EfficientNetB4
- Albumentations
- OpenCV
- NumPy
- Matplotlib
- Scikit-learn
- Grad-CAM
- LIME
- Kaggle GPU

---



---

## License

This project is licensed under the MIT License.
