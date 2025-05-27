# 🎥 Quantitative Estimation of Video Pixel Quality for Action Recognition

![Made with Python](https://img.shields.io/badge/Made%20with-Python-blue?logo=python)

This project develops deep learning models to **quantitatively estimate video pixel quality**, with a focus on understanding how **video degradation affects action recognition** performance. Using spatial features such as sharpness, brightness, contrast, and noise, the models (both classical and deep learning approaches) predict video quality scores to support improved video analysis in computer vision applications.

This work was submitted as part of the MSc in Data Science programme at the University of Bath (2023–24).

---

## 📌 Project Overview

This project implements and evaluates two models for **video quality assessment**:

- **Multi-Layer Perceptron (MLP)**: Uses hand-crafted spatial features (sharpness, brightness, contrast, noise) from individual frames to predict quality scores.
- **Modified Temporal Segment Network (TSN)** with ResNet backbone: Uses sampled frames and deep feature extraction to capture spatial characteristics of video degradation.

Both models were trained on a dataset of videos with various degradation types and levels, each annotated with a quality score between 0 (worst) and 1 (best). The models were evaluated using metrics such as Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and R-squared (R²).

---

## 📁 Dataset Details

### 🔸 Original Source Dataset

- **Dataset**: [EPIC-KITCHENS-100](https://epic-kitchens.github.io)
- **Type**: Egocentric (first-person) video dataset for action recognition
- **Scope**: 700+ hours of kitchen activity video from 45 participants
- **Annotations**: Action segments with labeled verbs and nouns

> ⚠️ EPIC-KITCHENS is accessed under academic license and is **not redistributed** in this repository. Users must register to obtain the dataset directly from the [official site](https://epic-kitchens.github.io).

---

## 🎯 Objectives

- Develop models to estimate video quality scores in a way that supports downstream action recognition tasks.
- Compare classical feature-based learning (MLP) with a spatial-only TSN approach.
- Evaluate robustness to various types of video degradation.
- Highlight how specific visual distortions affect perceived video quality and model performance.

---

## 🧰 Tools & Technologies

- **Languages**: Python
- **Frameworks**: PyTorch
- **Libraries**: OpenCV, NumPy, Matplotlib, Scikit-learn
- **Evaluation Metrics**: MAE, RMSE, R²

---

## 🧪 Methodology

### 🟠 Data Preparation

- A subset of EPIC-KITCHENS videos was selected and degraded to simulate real-world distortions.
- Videos were synthetically degraded using:
  - **Blur**, **Noise**, **Blockiness**, **Luminance distortion**, **Contrast changes**
  - Each video was processed to apply one degradation type at multiple severity levels.
- A **continuous score between 0 and 1** was assigned to each video programmatically based on severity of degradation applied, where:
  - **0** = extremely poor quality (severe degradation)
  - **1** = high visual quality (no degradation)

### 🟠 Model Development

- **MLP Model**:
  - Extracted frame-level spatial features: sharpness, brightness, contrast, and noise levels.
  - Aggregated features per video and trained a fully connected neural network to predict quality scores.

- **Modified TSN Model (Spatial-Only)**:
  - Adapted from the **spatial stream** component of the original Temporal Segment Network.
  - Sampled frames from each video segment, but **did not model temporal relationships** or aggregate features across time.
  - Employed a **ResNet-18 backbone** to extract deep spatial features from sampled frames.
  - Focused solely on **per-frame visual quality attributes**, excluding motion or sequence modeling.

> ⚠️ This spatial-only TSN adaptation simplifies the original TSN design to prioritize **pixel-level quality estimation** rather than spatio-temporal action classification.

### 🟠 Training & Evaluation

- Split data into training, validation, and test sets.
- Models were trained with appropriate loss functions and optimizers.
- Evaluated using:
  - **Mean Absolute Error (MAE)**
  - **Root Mean Squared Error (RMSE)**
  - **R-squared (R²)** for prediction accuracy

---

## 📊 Key Findings

- Both models were able to predict video quality scores with reasonable accuracy.
- The **TSN model outperformed the MLP**, particularly in generalization (higher R²) and robustness to complex distortions.
- The **MLP model** was more interpretable and stable, performing well with explicit feature engineering.
- Visual degradations such as **blur** and **noise** had the most significant impact on predicted quality, aligning with human perception.

---

## 🔗 Data Access

The dataset is **not included** in this repository due to size and licensing.

You can:
- Apply for access to EPIC-KITCHENS via [epic-kitchens.github.io](https://epic-kitchens.github.io)
