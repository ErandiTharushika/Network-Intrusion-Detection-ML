# Network Intrusion Detection Using Machine Learning

## Overview

This project implements a machine learning-based network intrusion detection system using the UNSW-NB15 cybersecurity dataset.

The objective is to classify network traffic as either **normal traffic** or **malicious traffic** by analyzing network flow features and applying supervised machine learning algorithms.

The project follows a complete machine learning workflow:

* Data exploration
* Data preprocessing
* Model training
* Model evaluation
* Hyperparameter optimization
* Model saving for deployment

---

## Dataset

Dataset used:

**UNSW-NB15 Network Intrusion Dataset**

Download from: https://research.unsw.edu.au/projects/unsw-nb15-dataset

The dataset contains network traffic records with various features describing communication behavior, including:

* Protocol information
* Service type
* Packet statistics
* Byte transfer information
* Connection behavior
* Traffic timing characteristics

The task is formulated as a binary classification problem:

| Label | Meaning        |
| ----- | -------------- |
| 0     | Normal traffic |
| 1     | Attack traffic |

---

## Project Structure

```
Network-Intrusion-Detection-ML/

│
├── data/
│   ├── raw/
│   │   ├── UNSW_NB15_training-set.csv
│   │   └── UNSW_NB15_testing-set.csv
│   │
│   └── processed/
│       ├── X_train_processed.csv
│       ├── X_test_processed.csv
│       ├── y_train.csv
│       └── y_test.csv
│
├── models/
│   ├── preprocessor.pkl
│   └── final_random_forest.pkl
│
├── notebooks/
│   ├── 01_Data_Exploration.ipynb
│   ├── 02_Data_Preprocessing.ipynb
│   ├── 03_Model_Training.ipynb
│   ├── 04_Model_Evaluation.ipynb
│   └── 05_Hyperparameter_Tuning.ipynb
│
├── requirements.txt
└── README.md
```

---

## Machine Learning Pipeline

### 1. Data Exploration

Performed exploratory data analysis to understand:

* Dataset distribution
* Attack categories
* Feature types
* Class balance
* Missing values

---

### 2. Data Preprocessing

The following preprocessing steps were applied:

* Removed unnecessary `id` feature
* Removed `attack_cat` to prevent target leakage
* Separated features and labels
* Applied StandardScaler to numerical features
* Applied OneHotEncoder to categorical features
* Saved the preprocessing pipeline for future inference

---

## Models Implemented

The following classification algorithms were evaluated:

### Logistic Regression

Used as a baseline model.

Accuracy:

```
81%
```

---

### Decision Tree

Improved performance by learning nonlinear decision rules.

Accuracy:

```
86%
```

---

### Random Forest

An ensemble model combining multiple decision trees.

Accuracy:

```
87%
```

---

### Optimized Random Forest

Hyperparameter tuning was performed using RandomizedSearchCV.

Final parameters:

```text
n_estimators = 300
max_depth = 10
min_samples_split = 5
class_weight = balanced
```

---

## Final Model Performance

The optimized Random Forest achieved:

| Metric           | Score |
| ---------------- | ----: |
| Accuracy         | 90.5% |
| Attack Precision |   87% |
| Attack Recall    |   97% |
| Attack F1-score  |   92% |
| ROC-AUC          | 0.980 |

The high recall value indicates that the model can successfully identify most malicious network traffic samples.

---

## Model Evaluation

The model was evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix
* ROC Curve
* ROC-AUC Score
* Feature Importance Analysis

---

## Feature Importance

Random Forest feature importance analysis was performed to identify the network characteristics that contribute most to intrusion detection.

This helps improve interpretability and understand important traffic patterns associated with attacks.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn
* Joblib
* Jupyter Notebook

---

## Future Improvements

Possible future extensions:

* Multi-class attack classification

  * DoS
  * Exploits
  * Reconnaissance
  * Fuzzers
  * Worms
  * Other attack categories

* Real-time network traffic prediction dashboard using Streamlit

* Comparison with advanced models:

  * XGBoost
  * LightGBM
  * Neural Networks

* Deployment as an API service

---

## Author

Erandi Tharushika

Electronic and Telecommunication Engineering
University of Moratuwa
