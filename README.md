# 🚗 Automatic Vehicle Accident Detection from Images During Adverse Weather Conditions Using YOLOv10 and VGG19

> **Research Paper** | Computer Vision | Deep Learning | Road Safety

![Python](https://img.shields.io/badge/Python-3.9-blue?logo=python)
![YOLO](https://img.shields.io/badge/YOLOv10-Object%20Detection-red)
![VGG19](https://img.shields.io/badge/VGG19-Classification-orange)
![Deep Learning](https://img.shields.io/badge/Deep%20Learning-CNN-green)
![License](https://img.shields.io/badge/License-CC%20BY--4.0-lightgrey)

---

## 📌 Overview

This research addresses the critical challenge of detecting vehicle accidents in **adverse weather conditions** (rain, fog, snow, low light). Poor visibility, environmental noise, and complex scenes hinder accurate detection, yet reliable accident detection is essential for autonomous driving systems, traffic surveillance, and emergency response.

We propose a **hybrid deep learning framework** combining:
- **YOLOv10** – Real-time object detection (speed & efficiency).
- **VGG19** – Deep feature extraction and classification (accuracy & detail).
- **Adaptive Preprocessing** – Contrast enhancement and dehazing to improve image clarity.

---

## 🎯 Key Highlights

| **Aspect** | **Details** |
| :--- | :--- |
| **Dataset** | 3,480 annotated images under various weather conditions (rain, fog, snow, low light). |
| **YOLOv10 Precision** | Achieved **54.2%** (epoch 50), **63.2%** (epoch 100), and **81.8%** (epoch 200). |
| **VGG19 Performance** | Highest accuracy, precision, recall, and F1-score at epoch 200. |
| **Key Finding** | Hybrid model significantly reduces false positives and outperforms single-model approaches. |

---

## 📊 Dataset Distribution

### YOLOv10 Dataset (1,307 images)
| **Split** | **Images** |
| :--- | :--- |
| **Training** | 915 |
| **Validation** | 261 |
| **Testing** | 131 |

### VGG19 Dataset (1,679 images)
| **Split** | **Total** | **Accident** | **Non-Accident** |
| :--- | :--- | :--- | :--- |
| **Training** | 1,175 | 596 | 579 |
| **Validation** | 336 | 169 | 167 |
| **Testing** | 168 | 90 | 78 |

All images were sourced from YouTube and annotated using the **Roboflow** platform.

---

## 🧠 Models & Architecture

### 1. YOLOv10 (Real-Time Detection)
- **Purpose:** Fast, single-pass object detection.
- **Strengths:** Real-time processing, handles complex scenes, reduces redundant bounding boxes (Non-Maximum Suppression).
- **Performance:** Achieved **81.8% precision** at epoch 200.

| **Epoch** | **Precision (P)** | **Recall (R)** | **mAP 50%** | **mAP 50-95%** |
| :--- | :--- | :--- | :--- | :--- |
| 50 | 54.2% | 45.7% | 44.6% | 19.1% |
| 100 | 63.2% | 56.8% | 62.9% | 27.8% |
| 200 | **81.8%** | **61%** | **72.5%** | **22.9%** |

### 2. VGG19 (Feature Extraction & Classification)
- **Purpose:** Detailed feature extraction and classification.
- **Strengths:** 16 convolutional layers + 3 fully connected layers, excels at detecting **subtle indicators** (minor vehicle damage, unusual object interactions).
- **Best Performance:** Achieved highest accuracy, precision, recall, and F1-score at **epoch 200**.

### 3. CNN Models (Baseline Comparison)
- 7-layer CNN (with and without dropout)
- 10-layer CNN (without dropout)
- **Result:** VGG19 with fully connected layer consistently outperformed all CNN configurations.

---

## 📈 Results & Visualizations

### YOLOv10 Confusion Matrices
| **Epoch** | **Confusion Matrix** |
| :--- | :--- |
| 50 | ![Confusion Matrix Epoch 50](./results/charts/yolov10_confusion_matrix_epoch50.png) |
| 100 | ![Confusion Matrix Epoch 100](./results/charts/yolov10_confusion_matrix_epoch100.png) |
| 200 | ![Confusion Matrix Epoch 200](./results/charts/yolov10_confusion_matrix_epoch200.png) |

### Sample Detections
| **Epoch** | **Training Batch** | **Validation Batch** |
| :--- | :--- | :--- |
| 50 | ![Train Batch 50](./results/sample_outputs/train_batch_epoch50.jpg) | ![Valid Batch 50](./results/sample_outputs/valid_batch_epoch50.jpg) |
| 100 | ![Train Batch 100](./results/sample_outputs/train_batch_epoch100.jpg) | ![Valid Batch 100](./results/sample_outputs/valid_batch_epoch100.jpg) |
| 200 | ![Train Batch 200](./results/sample_outputs/train_batch_epoch200.jpg) | ![Valid Batch 200](./results/sample_outputs/valid_batch_epoch200.jpg) |

### Loss Curves
- **Epoch 50:** ![Loss Curves 50](./results/charts/yolov10_loss_curves_epoch50.png)
- **Epoch 100:** ![Loss Curves 100](./results/charts/yolov10_loss_curves_epoch100.png)
- **Epoch 200:** ![Loss Curves 200](./results/charts/yolov10_loss_curves_epoch200.png)

### CNN vs VGG19 Performance Comparison
| **Model** | **Epoch** | **Accuracy** | **Precision** | **Recall** | **F1-Score** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| CNN (7-layer, no dropout) | 200 | Moderate | Moderate | Moderate | Moderate |
| CNN (7-layer, with dropout) | 200 | Moderate | Moderate | Higher | Higher |
| CNN (10-layer, no dropout) | 200 | Slightly Higher | Slightly Higher | Slightly Higher | Slightly Higher |
| **VGG19 (with FC layer)** | **200** | **Highest** | **Highest** | **Highest** | **Highest** |
| VGG19 (without FC layer) | 200 | Lower | Lower | Lower | Lower |

---

## 🛠️ Technical Implementation

### Hardware & Environment
- **Platform:** Google Colab (GPU acceleration).
- **Frameworks:** TensorFlow, PyTorch.
- **Libraries:** OpenCV, NumPy, Matplotlib, scikit-learn.

### Hyperparameters
| **Parameter** | **Value** |
| :--- | :--- |
| **Epochs** | 50, 100, 200 |
| **Batch Size** | 32 |
| **Learning Rate** | 0.001 |

### Preprocessing Techniques
- **Dehazing:** Improved clarity in foggy images.
- **Contrast Adjustment:** Enhanced visibility in low-light conditions.
- **Augmentation:** Applied to validation set for better generalization.

---

## 📄 Full Paper
- [Research Paper (PDF)](./paper/Research_Paper.pdf)

---

## 🔑 Keywords

`Vehicle accident detection` `YOLOv10` `VGG19` `Adverse weather` `Deep learning` `Computer vision` `Object detection` `Real-time detection` `CNN` `Road safety` `Image processing` `Convolutional neural networks`

---

## 🧪 Evaluation Metrics

- **Precision (P):** TP / (TP + FP)
- **Recall (R):** TP / (TP + FN)
- **Accuracy:** (TP + TN) / (TP + TN + FP + FN)
- **Mean Average Precision (mAP):** Average of AP across all classes.
- **F1-Score:** Harmonic mean of precision and recall.

---

## 🔮 Future Work

- Integrate **additional sensors** (LiDAR, radar) for multi-modal detection.
- Expand **synthetic data** to simulate a wider range of weather conditions.
- Optimize models for **edge devices** (real-time deployment).
- Explore **YOLO variants** (YOLOv11, YOLO-NAS) for faster inference.
- Add **multi-language support** for global usability.

---

## 👩‍💻 My Role

As the lead researcher and developer, I was responsible for:

- Designing the **hybrid deep learning framework**.
- Collecting and annotating the **dataset** (3,480 images).
- Training and fine-tuning **YOLOv10** and **VGG19** models on Google Colab.
- Performing **data preprocessing** (dehazing, contrast adjustment).
- Analyzing **performance metrics** (precision, recall, accuracy, mAP, F1-score).
- Writing the **full research paper** and interpreting results.

---

## 🏆 Significance

This research contributes to **intelligent transportation systems** by providing a reliable tool for real-time accident identification under adverse weather conditions. It supports:

- **Faster emergency response.**
- **Enhanced road safety.**
- **Reduced false positives** compared to single-model approaches.
- **Alignment with Vision 2030** digital transformation goals.

---

## 📫 Connect with Me

- **LinkedIn:** [https://linkedin.com/in/[your-username]](https://linkedin.com/in/[your-username])
- **GitHub:** [https://github.com/YaraAlansari-CS](https://github.com/YaraAlansari-CS)
- **Email:** [your-email@example.com](mailto:your-email@example.com)

---

**⭐ If you find this research valuable, don't forget to give it a star!**
