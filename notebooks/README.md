# 📓 Notebooks Overview

This folder contains all the Jupyter notebooks used for generating distorted video data, extracting features, and training models to estimate video quality.

Each notebook serves a specific purpose in the end-to-end workflow:

---

### 🧪 `Distorted_Labels.ipynb`

- Applies synthetic distortions (blur, noise, blockiness, contrast, brightness changes) to original clean videos.
- Assigns a continuous **quality score (0–1)** to each distorted video.
- Saves distorted videos and labels for training.

---

### 🔍 `Test_Calculate_features.ipynb`

- Extracts **hand-crafted spatial features** (e.g., sharpness, brightness, contrast, noise level) from distorted videos.
- Features are saved in a CSV format for model input.

---

### 🔗 `Merge.ipynb`

- Maps the **extracted features** to the corresponding **video quality scores**.
- Produces the final **MLP training dataset** in CSV format.

---

### 🧠 `MLP.ipynb`

- Trains and evaluates a **Multi-Layer Perceptron (MLP)** on the extracted spatial features.
- Outputs performance metrics: MAE, RMSE, R².
- Includes predictions and visualizations.

---

### 🎯 `TSN_final.ipynb`

- Implements the **spatial-only version of the Temporal Segment Network (TSN)**.
- Samples frames from videos and uses a **ResNet backbone** to extract deep spatial features.
- Trains a regression model to predict quality scores without modeling temporal sequences.

---

### 🗂 Recommended Order of Execution

1. `Distorted_Labels.ipynb`
2. `Test_Calculate_features.ipynb`
3. `Merge.ipynb`
4. `MLP.ipynb`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;or  
5. `TSN_final.ipynb`

---

> 📌 All notebooks are designed to run independently but follow a logical sequence in the project workflow.
