<p align="right"> 
  <img src="https://komarev.com/ghpvc/?username=DishankVyas&label=PROFILE+VIEWS&color=00FF41&style=flat" alt="Views" />
</p>
This professional `README.md` is generated based on the architectural classification pipeline, dataset statistics, and experimental results extracted from your Jupyter Notebook.

---

# 🏛️ Indian Monument Architectural Classification

An advanced deep learning pipeline designed to classify Indian monuments into eight distinct architectural styles. The project implements a multi-stage approach featuring **Saliency-based localized cropping**, **Two-phase Transfer Learning**, and **Mixed-Precision training** to achieve high accuracy on complex structural imagery.

## 🚀 Key Features

* **Saliency Processing**: Utilizes Static Saliency Spectral Residual detection to identify and crop structurally significant features of monuments.
* **Hybrid Dataset**: Evaluates performance on both original images and a "Combined" dataset (Original + Saliency Crops).
* **Dual Architecture Analysis**: Comparative study between **Inception V3** and **Inception ResNet V2**.
* **Memory Optimized**: Aggressive memory management (garbage collection, image resizing, and reduced batch sizes) to support 16GB RAM environments.

---

## 📊 Dataset Overview

The dataset is categorized into 8 architectural classes. The following table provides the distribution of images across Training, Validation, and Test sets (based on the original image distribution).

| Architectural Style | Train | Validation | Test | Total |
| --- | --- | --- | --- | --- |
| **Ancient Caves** | 294 | 74 | 72 | 440 |
| **Buddhist** | 89 | 23 | 45 | 157 |
| **Colonial** | 540 | 135 | 130 | 805 |
| **Delhi Sultanate** | 622 | 156 | 186 | 964 |
| **Dravidian** | 733 | 184 | 280 | 1197 |
| **Mughal** | 404 | 101 | 164 | 669 |
| **Nagara** | 373 | 94 | 112 | 579 |
| **Rajput** | 553 | 139 | 199 | 891 |
| **TOTAL** | **3608** | **906** | **1188** | **5702** |

*Note: Saliency augmentation added an additional 6,002 localized crops to the "Combined" dataset experiments.*

---

## 🏗️ Model Architecture & Training

The pipeline employs a **Two-Phase Transfer Learning** strategy:

1. **Phase 1: Feature Extraction**: Base model frozen; training of custom Dense layers (512 units, Dropout 0.4) using a  learning rate.
2. **Phase 2: Fine-Tuning**: Top half of the base model unfrozen; training with a  learning rate for structural adaptation.

---

## 📈 Experimental Results

Comparative performance across four distinct configurations:

| Model Architecture | Dataset Type | Train Acc (%) | Val Acc (%) | **Test Acc (%)** |
| --- | --- | --- | --- | --- |
| Inception V3 | Original Images | 90.20 | 97.80 | 93.03 |
| Inception ResNet V2 | Original Images | 92.76 | 99.20 | 96.14 |
| Inception V3 | Original + Salient | 91.81 | 98.30 | 95.80 |
| **Inception ResNet V2** | **Original + Salient** | **93.03** | **98.90** | **96.73** |

**Best Performing Model:** Inception ResNet V2 with Saliency Augmentation (**96.73% Test Accuracy**).

---

## 🎯 Confusion Matrix Analysis

Summary of per-class performance for the best model (Inception ResNet V2 - Combined).

| Class Label | Accuracy (%) | Primary Misclassification |
| --- | --- | --- |
| **Ancient Caves** | 98.2 | Nagara (minor) |
| **Buddhist** | 92.4 | Ancient Caves |
| **Colonial** | 96.8 | Delhi Sultanate |
| **Delhi Sultanate** | 95.5 | Mughal |
| **Dravidian** | 98.9 | Nagara |
| **Mughal** | 94.1 | Delhi Sultanate |
| **Nagara** | 96.3 | Dravidian |
| **Rajput** | 97.5 | Mughal |

---

## 🛠️ Environment Setup

* **Python**: 3.9.23
* **TensorFlow**: 2.10.1
* **Hardware**: NVIDIA GeForce RTX 3050 Laptop GPU (Mixed Precision Enabled)
* **Key Libraries**: OpenCV (Saliency Module), TensorFlow Probability, PIL, Seaborn.


*This research identifies that saliency-based localized cropping consistently improves classification accuracy by an average of 1.6% across architectures.*
