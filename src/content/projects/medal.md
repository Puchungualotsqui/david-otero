---
title: MedAL - Skin Cancer Detection System
description: >-
  Classifier model to detect skin cancer based on mole images. The model was used in the app MedAL
image: '@assets/projects/medal/image.png'
startDate: 2024-07-05
endDate: 2024-11-04
skills:
  - Python
  - Keras
  - Transfer Learning
  - Image Classification
  - Matplotlib
sourceLink: https://github.com/Puchungualotsqui/mole-detection
featured: true
---
## 📊 Key Results
We achieved a **97% Recall rate** for Malignant cases, ensuring that the vast majority of cancerous moles are flagged for further review by a dermatologist.

| Class | Precision | Recall | F1-Score | Support |
| :--- | :--- | :--- | :--- | :--- |
| **Benign** | 0.96 | 0.64 | 0.77 | 360 |
| **Malignant** | 0.69 | **0.97** | 0.81 | 300 |
| **Overall Accuracy** | | | **79%** | 660 |

---

## 🧠 Model Architectures
We experimented with two distinct architectures to benchmark performance:

### 1. Transfer Learning (EfficientNetB0)
* **Base:** Pre-trained on ImageNet (frozen weights).
* **Head:** Global Average Pooling + Dropout (0.3) + Dense Output.
* **Why:** EfficientNet provides excellent feature extraction with lower computational cost than ResNet.

### 2. Custom CNN (Built from scratch)
* **Structure:** 3 Blocks of `Conv2D` + `MaxPooling`.
* **Activation:** Used **GELU** (Gaussian Error Linear Units) instead of ReLU for smoother gradient flow.
* **Regularization:** Heavy Dropout (0.5) to prevent overfitting on the medical dataset.



---

## ⚙️ Engineering Pipeline

### Data Preprocessing & Augmentation
Medical datasets are often imbalanced or limited. We implemented a robust `tf.data` pipeline:
* **Resizing:** Standardized to `(224, 224)`.
* **Augmentation Layer:** Random Flips, Rotations (10%), Zooms (10%), and Contrast adjustments.
* **Normalization:** Rescaling pixel values to `[0,1]`.

### Optimization Strategy
* **Loss Function:** `BinaryCrossentropy`.
* **Optimizer:** `Adam`.
* **Callback:** `EarlyStopping` (patience=3) to prevent overfitting and restore best weights.

### The "Recall-First" Approach
Standard classification uses a decision threshold of `0.5`. However, for cancer detection, this is often too conservative. 
We analyzed the **Precision-Recall Curve** and adjusted the decision threshold to **0.37**.

* **Result:** This shift sacrificed some Precision (more false alarms) to significantly boost Recall (catching more cancer), which is the medically correct trade-off.

---

## 🛠️ Tech Stack
* **Core:** Python, TensorFlow, Keras.
* **Data Viz:** Matplotlib, Seaborn (Confusion Matrices).
* **Metrics:** Scikit-Learn (`classification_report`, `precision_recall_curve`).

## 🚀 Usage

```python
# Load the model
model = tf.keras.models.load_model('medal_model.h5')

# Predict on an image
img = load_and_prep_image('mole.jpg')
prob = model.predict(img)

# Apply the medical threshold
is_malignant = prob > 0.37
```
