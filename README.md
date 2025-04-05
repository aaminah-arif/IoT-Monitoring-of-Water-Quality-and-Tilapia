# IoT Monitoring Dataset of Water Quality and Tilapia Health in Aquaculture Ponds (Montería, Colombia - 2024)

This project explores the application of logistic regression to analyze a real-world aquaculture dataset collected using IoT sensors. The dataset includes water quality parameters and tilapia health indicators gathered over six months in Montería, Colombia.

The goal is to build a predictive model for fish health status ("Stable" vs. "At Risk") using environmental and operational variables.

## Dataset Description

**File:** `Data Model IoTMLCQ 2024.xlsx` – Contains hourly sensor and health data from January to June 2024.

### Features (Inputs)
- `Temperature (°C)`
- `Dissolved Oxygen (mg/L)`
- `pH`
- `Turbidity (NTU)`
- `Oxygenation Automatic` (Yes/No → Encoded as 1/0)
- `Oxygenation Interventions` (Yes/No → Encoded as 1/0)
- `Corrective Interventions`
- `Thermal Risk Index` (High/Normal → Encoded)
- `Low Oxygen Alert` (Critical/Safe → Encoded)

### Target (Output)
- `Health Status`: Categorical feature representing fish health condition:
  - `Stable` → 0
  - `At Risk` → 1

## Objective

We aim to:

1. **Predict the fish health status** based on water quality and operational variables.
2. Train a logistic regression classifier using:
   - Python libraries (`scikit-learn`)
   - Gradient Descent from scratch
   - Newton-Raphson Algorithm
3. Compare performance and optimal parameters from each method.

## 📐 Logistic Regression Model

The logistic regression hypothesis is defined as:

$$
h_{\theta}(X) = \sigma(X\theta) = \frac{1}{1 + e^{-X\theta}}
$$

Where:
- \( X \) is the feature matrix (including a bias term).
- \( \theta \) is the parameter vector.
- \( h_{\theta}(X) \) is the probability that the fish is "At Risk".

## Data Preparation

### 1. Cleaning:
- Missing data interpolated using linear methods
- Categorical features encoded (One-Hot Encoding)

### 2. Feature Scaling:
- Features normalized using `StandardScaler` (mean = 0, std = 1)

### 3. Train-Test Split:
- 80% for training, 20% for testing

## Model Training

### 1. Using Python Libraries

- **Library:** `scikit-learn`
- **Model:** `LogisticRegression(solver='liblinear')`
- **Optimal Parameters:** Displayed after fitting
- **Evaluation Metrics:** Accuracy, Precision, Recall, F1-score Confusion Matrix

### 2. Using Gradient Descent

- Implemented from scratch
- Learning Rate (α) tuned via grid search
- Parameters updated using:

\[
\theta := \theta - \alpha \nabla J(\theta)
\]

- **Comparison:** Training accuracy vs. library implementation

### 3. Using Newton-Raphson Algorithm

- Implements:

\[
\theta := \theta - H^{-1} \nabla J(\theta)
\]

Where \( H \) is the Hessian matrix of the cost function.

- Usually converges faster than GD for convex problems like logistic regression
- **Comparison:** Iteration count and final accuracy vs. GD and library-based method

## Usage Notes

- This dataset is ideal for research in **aquaculture monitoring**, **fish health modeling**, and **IoT-driven environmental analytics**.
- Sensor accuracy is ensured via routine calibration.
- Health risks were defined based on domain-specific thresholds (e.g., DO < 5 mg/L → "Critical").
