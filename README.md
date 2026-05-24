# Road Damage Detection using YOLOv8

A deep learning-based object detection system for detecting and classifying road surface damage using the YOLOv8 architecture, trained on the RDD2022 dataset.

## Project Overview

This project applies computer vision techniques to automatically detect and localize road damage across four categories:

- **D00** – Longitudinal Crack
- **D10** – Transverse Crack
- **D20** – Alligator Crack
- **D40** – Pothole

The goal is to support automated road defect verification, reducing the need for manual inspection in systems like Malaysia's MyJPJ road reporting platform.

## Models Used

Two YOLOv8 variants were trained and compared:

| Model | Layers | Parameters | Precision | Recall | mAP50 | mAP50-95 |
|-------|--------|------------|-----------|--------|-------|----------|
| YOLOv8s | 129 | ~11.17M | 0.618 | 0.637 | 0.657 | 0.369 |
| YOLOv8m | 169 | ~25.9M | 0.669 | 0.622 | 0.666 | 0.377 |

**YOLOv8m** achieved better overall performance with higher precision and mAP scores.

## Dataset

- **Dataset:** Road Damage Dataset 2022 (RDD2022)
- **Total images:** 47,420 labeled road images from China, Czech Republic, Japan, India, United States
- **Annotated training images used:** 20,853

### Dataset Split

| Subset | Images |
|--------|--------|
| Training | 16,682 |
| Validation | 2,085 |
| Testing | 2,086 |

## Training Configuration

- Input image size: 640 × 640
- Batch size: 16
- YOLOv8s: 100 epochs (MPS device)
- YOLOv8m: 60 epochs (CUDA/GPU)
- Augmentations: horizontal flip, random scaling, rotation, HSV color adjustment, mosaic, mixup

## Results

Both models achieved stable convergence with no signs of overfitting. The main challenge was background confusion — distinguishing thin road cracks from complex road textures. YOLOv8m showed stronger precision while YOLOv8s had higher recall due to its more aggressive detection approach.

## Files

| File | Description |
|------|-------------|
| `Road-Damage-Classification.ipynb` | Main training and evaluation notebook |
| `Road-Damage-Augmentation.ipynb` | Data augmentation notebook |


