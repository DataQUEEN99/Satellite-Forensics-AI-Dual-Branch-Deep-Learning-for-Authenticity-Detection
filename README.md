# 🛰️ Satellite Forensics AI

## Dual-Branch Deep Learning for Satellite Image Authenticity Analysis

Satellite Forensics AI is a deep learning and computer vision project designed to analyze satellite-style imagery using both **spatial visual features** and **frequency-domain characteristics**.

The system combines a pretrained **EfficientNet-B0 CNN branch** with a custom **Fourier-frequency CNN branch**. These two feature streams are fused to classify images into:

- **Authentic Satellite**
- **Synthetic / AI-Inpainted**

The project also performs spectral analysis, generates forensic metadata, and uses **Grad-CAM visualization** to provide insight into the spatial regions influencing the model's prediction.

> **Important:** The current implementation uses publicly accessible flower imagery as a computational image source and creates synthetic/inpainted samples programmatically using image filtering and a periodic frequency pattern. Therefore, the current version is a **satellite-forensics research prototype**, not a validated detector trained on a real-world satellite-vs-AI-generated benchmark dataset.

---

# 🎯 Project Objective

The goal of Satellite Forensics AI is to investigate whether combining:

1. **Spatial-domain visual features**
2. **Frequency-domain features**

can provide useful information for distinguishing authentic imagery from synthetically modified imagery.

The system follows this pipeline:

```text
Input Image
     │
     ├───────────────────────┐
     │                       │
     ▼                       ▼
Spatial Image          Fourier Transform
     │                       │
     ▼                       ▼
EfficientNet-B0         Frequency CNN
     │                       │
     └───────────┬───────────┘
                 ▼
          Feature Fusion
                 │
                 ▼
          Classification
                 │
        ┌────────┴────────┐
        ▼                 ▼
   AUTHENTIC          SYNTHETICvv
