# 🚀 AI-Powered Predictive Maintenance & Failure Mode Classification

> Predict machine failures before breakdown and identify the most likely failure mode using Machine Learning and Explainable AI.

---

## 📌 Project Overview

Unexpected machine failures in manufacturing lead to production downtime, increased maintenance costs, and reduced operational efficiency.

This project builds an **end-to-end Predictive Maintenance system** using the **AI4I 2020 Predictive Maintenance Dataset** to:

- Predict whether a machine will fail.
- Identify the most likely failure mode.
- Explain model predictions using feature importance 

---

# 🎯 Problem Statement

Industrial machines continuously generate sensor readings such as:

- Air Temperature
- Process Temperature
- Rotational Speed
- Torque
- Tool Wear

The challenge is to predict failures **before they happen** so maintenance can be scheduled proactively instead of reactively.

---

# 🎯 Objectives

### Binary Classification

Predict whether a machine will:

- ✅ No Failure
- ❌ Machine Failure

### Multi-Class Classification

If a machine fails, predict the reason:

- Heat Dissipation Failure (HDF)
- Power Failure (PWF)
- Overstrain Failure (OSF)
- Tool Wear Failure (TWF)

---

# 📂 Dataset

**Dataset:** AI4I 2020 Predictive Maintenance Dataset

### Features

| Feature | Description |
|----------|-------------|
| Type | Product Quality (L/M/H) |
| Air Temperature | Ambient temperature |
| Process Temperature | Operating temperature |
| Rotational Speed | RPM of machine |
| Torque | Mechanical load |
| Tool Wear | Tool usage time |
| Machine Failure | Target Variable |

Failure Modes

- HDF
- PWF
- OSF
- TWF
- RNF

---

# 🛠 Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost


---

# 📊 Exploratory Data Analysis

Performed:

- Missing Value Analysis
- Data Type Validation
- Distribution Analysis
- Correlation Analysis
- Outlier Detection
- Failure Mode Analysis
- Cross-tab Analysis
- Class Imbalance Analysis

---

# 💡 Feature Engineering

Created domain-specific features to improve predictive performance.

### Temperature Difference

```python
Temp_diff_K = Process Temperature - Air Temperature
```

Reason:

Difference between process and air temperature better captures abnormal heating.

---

### Mechanical Power

```python
Power = Torque × Angular Velocity
```

where

```
Angular Velocity = RPM × 2π / 60
```

Reason:

Represents the actual mechanical load on the machine.

---

### Torque × Tool Wear

```python
Torque × Tool Wear
```

Reason:

High torque acting on worn tools increases failure probability.

---

### Label Encoding

Encoded machine Type:

```
L → 0
M → 1
H → 2
```

---

# ⚠ Class Imbalance

Only **3.4%** of machines experienced failure.

Compared multiple imbalance handling techniques:

- class_weight='balanced'
- SMOTE
- scale_pos_weight (XGBoost)

---

# 🤖 Models Implemented

- Logistic Regression
- Random Forest
- XGBoost

---

# 📈 Model Performance

| Model | Precision | Recall | F1 | PR-AUC |
|-------|----------:|-------:|----:|-------:|
| Logistic Regression | 0.178 | 0.882 | 0.296 | 0.434 |
| Random Forest | 0.659 | 0.824 | 0.732 | 0.840 |
| **XGBoost** | **0.846** | **0.809** | **0.827** | **0.892** |

🏆 **Best Model:** XGBoost


---

# 🔍 Why PR-AUC?

The dataset is highly imbalanced.

Instead of Accuracy or ROC-AUC, **PR-AUC** was used because it focuses on correctly identifying the rare failure class.

---

# 📉 Confusion Matrix (XGBoost)

| Metric | Count |
|---------|------:|
| True Negative | 1922 |
| False Positive | 10 |
| False Negative | 13 |
| True Positive | 55 |

Business Interpretation

- 55 failures detected before breakdown.
- Only 10 false maintenance alarms.
- 13 failures missed (area for future improvement).

---

# 🔥 Failure Mode Prediction

Built a multiclass model to identify the likely failure reason after detecting a machine failure.

### Performance

- Accuracy: **98%**

Failure Modes:

- Heat Dissipation Failure
- Overstrain Failure
- Power Failure
- Tool Wear Failure

---

# 📊 Feature Importance

Top predictive features:

- Rotational Speed
- Mechanical Power
- Tool Wear

These features were also confirmed using SHAP explainability.

---

# 💼 Business Impact

This system helps industries:

- Predict failures before breakdown.
- Reduce maintenance costs.
- Reduce production downtime.
- Schedule preventive maintenance.
- Improve machine reliability.

---

# 📁 Project Structure

```
Predictive-Maintenance/
│
├── data/
│   └── ai4i2020.csv
│
├── notebooks/
│   └── solution.ipynb
│
├── README.md
├── CaseStudy_DataScience_IronPulse_PredictiveMaintenance.docx
└── Maintenance_Recommendation_OnePage.docx
```

---

# 🚀 Future Improvements

- Hyperparameter Optimization
- Real-time Prediction Dashboard
- IoT Integration
- Deep Learning Models
- Live Monitoring System

---

# 👨‍💻 Author

**Rahi Chaudhary**

M.Sc. Information Technology | Machine Learning & Data Science Enthusiast

---

⭐ If you found this project useful, consider giving it a star!
