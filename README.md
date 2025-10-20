# JEPA Image Segmentation for Cattle Images

This repository contains code and resources for applying **Joint Embedding Predictive Architecture (JEPA)** to cattle image segmentation. The project explores self-supervised learning to segment individual cattle from images, aiming to improve animal monitoring and research.

## Project Overview
- Uses **JEPA** for self-supervised feature learning from unlabeled cattle images.
- Segments cattle silhouettes and regions for downstream health and behavior analysis.
- Implements a three-stage pipeline: pretraining, segmentation, and evaluation.

## Model Architecture & Methods
- **Encoder:**
  - ResNet18 and Vision Transformer (ViT) backbones are used for JEPA pretraining.
  - The encoder learns to predict masked image representations from unmasked context, using thousands of colormap-converted depth images.
- **Decoder:**
  - A lightweight U-Net-style decoder is trained on a small labeled subset, mapping encoder features to segmentation masks.
- **Ablation Study:**
  - ResNet18-JEPA achieved high in-distribution accuracy (Dice up to 0.98, IoU 0.975), but overfit to training conditions and dropped sharply on out-of-distribution (OOD) data.
  - ViT-JEPA required more data, but showed better OOD stability (IoU ~0.89).
  - CBAM attention and skip connections improved generalization and fine structure recovery, but data diversity was most critical.

## Training & Evaluation
- **Objectives:** Dice, IoU, and Cross-Entropy loss for segmentation.
- **Validation:** Results are preliminary; current models perform well on same-day test sets but generalize poorly to new environments, breeds, or lighting.
- **Preprocessing:** Ongoing improvements in image augmentation and normalization are being tested to boost robustness.

## Features
- JEPA-based self-supervised learning for cattle segmentation
- Support for ResNet and ViT backbones
- Scripts for training, evaluation, and mask visualization
- Sample annotated data and model checkpoints (if available)

## Technologies Used
- Python, PyTorch
- JEPA, U-Net, ResNet18, Vision Transformer (ViT)
- OpenCV, torchvision

## Future Work
- Expand dataset with more farms, breeds, and time points to improve generalization
- Enhance preprocessing and augmentation pipelines
- Integrate instance segmentation and fine-grained mask output
- Link segmentation to behavioral and health analytics

***

**Note:** Results are preliminary and subject to change as preprocessing and data diversity are improved. For questions or contributions, please open an issue or pull request.
