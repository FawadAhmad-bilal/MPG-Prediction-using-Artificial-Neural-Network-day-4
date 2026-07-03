# 🚗 MPG Prediction using Artificial Neural Network

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-Keras-orange?logo=tensorflow)
![Scikit--learn](https://img.shields.io/badge/scikit--learn-ML-yellow?logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

Predicting a car's fuel efficiency (Miles Per Gallon) using a fully connected Artificial Neural Network, built on the classic **MPG dataset** (Seaborn).

---

## 📊 Dataset

| Detail | Value |
|---|---|
| Source | Seaborn built-in `mpg` dataset |
| Samples | 398 |
| Features (after preprocessing) | 44 |
| Target | `mpg` (continuous) |
| Missing values | `horsepower` (6 rows) → filled with median |

---

## 🛠️ Preprocessing

- Extracted **brand** from the `name` column (e.g., `toyota corolla` → `toyota`), then dropped `name`
- Filled missing `horsepower` values with the median
- One-hot encoded `brand` and `origin` (`drop_first=True`)
- Cast all features to `float32`
- Train/test split: 80/20
- Scaled features with `StandardScaler`

---

## 🧠 Model Architecture

| Layer | Units | Activation | Regularization |
|---|---|---|---|
| Dense | 64 | ReLU | Dropout 0.08 |
| Dense | 34 | ReLU | Dropout 0.08 |
| Dense | 28 | ReLU | — |
| Dense (output) | 1 | Linear | — |

- **Loss:** Mean Squared Error
- **Optimizer:** Adam
- **Metric:** R² Score
- **Callback:** EarlyStopping (`patience=16`, restores best weights)
- **Batch size:** 16 | **Max epochs:** 100 (stopped early via callback)

---

## 📈 Results (Test Set)

| Metric | Score |
|---|---|
| R² Score | **~0.82** |
| MSE | **~10.97** |
| MAE | **~2.41** |

> Note: Results vary slightly across runs since the train/test split isn't seeded before scaling/training.

---

---

## ✍️ Author

**Fawad Ahmad Bilal**
BS Artificial Intelligence, University of Haripur
[GitHub](https://github.com/FawadAhmad-bilal)
