# 🧠 Image Matching Challenge 2025 (Kaggle CVPR Workshop)

This repository contains my submission to the [Image Matching Challenge 2025](https://www.kaggle.com/competitions/image-matching-challenge-2025), hosted as part of the CVPR 2025 workshop. The goal is to reconstruct accurate 3D scenes from diverse and unstructured image collections — without GPS or metadata.

---

## 📌 Problem Summary

Participants are required to:
- Group related images into clusters (scenes)
- Estimate relative camera poses (rotation and translation matrices)
- Discard unrelated images (outliers)

Each submission is evaluated on clustering accuracy and pose reconstruction quality using a harmonic mean of scene recall and precision.

---

## 🚀 Submission Highlights

- ✅ Fully custom pipeline — no pretrained models or OpenCV extractors
- ✅ Patch-based descriptors with Harris keypoints
- ✅ Cosine similarity matching + RANSAC pose validation
- ✅ Graph construction with geometric pruning
- ✅ Scene clustering via connected components
- ✅ Pose estimation using Essential Matrix recovery
- ✅ Output compliant with Kaggle submission format (`submission.csv`)

---

## 🛠️ Pipeline Overview

### 1. Keypoint Detection
- Harris corner detection via convolution
- Keypoints sorted by response strength

### 2. Descriptor Extraction
- Local grayscale patches (normalized)
- Flattened to vector descriptors

### 3. Image Matching
- Cosine similarity between patch descriptors
- Ratio filtering and mutual match pruning

### 4. Match Graph
- Weighted match graph
- Pose-consistency pruning via RANSAC-based Essential Matrix

### 5. Scene Clustering
- Connected components = scene clusters
- No external GPS, timestamps, or metadata used

### 6. Camera Pose Estimation
- Relative poses computed per cluster
- Chained using recovered R and t

### 7. Final Submission
- Outputs camera poses for clustered images
- `nan` matrices for detected outliers

---

## 📦 Requirements

- Python ≥ 3.8  
- NumPy, PyTorch  
- OpenCV (minimal)  
- NetworkX, Matplotlib, tqdm  

Install with:

```bash
pip install -r requirements.txt


## 📁 Folder Structure
├── notebook/
│ └── Image Matching Challenge 2025.ipynb # Full pipeline with output
├── submission.csv # Final output file
├── README.md # You’re here


