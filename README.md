# Predicting Acceptance of Personal Loans Using Machine Learning Algorithms

## 1. Project Overview

This project focuses on predicting whether a customer will accept a personal loan offer using Machine Learning algorithms.

Banks often spend considerable resources promoting personal loans to customers who may not be interested. This project aims to identify potential loan acceptors based on customer demographic and financial attributes.

The project implements and compares multiple machine learning algorithms, handles class imbalance, performs hyperparameter tuning, and evaluates model performance using various classification metrics.

## 2. Objectives

- Predict personal loan acceptance using customer data.
- Perform data cleaning and preprocessing.
- Implement and compare multiple machine learning algorithms.
- Address class imbalance using class balancing techniques.
- Perform hyperparameter tuning using GridSearchCV.
- Evaluate models using Accuracy, Precision, Recall, F1-score and ROC-AUC.
- Identify the best-performing model based on ROC-AUC.

## 3. Dataset Description

**Dataset:** Bank Personal Loan Modelling

**Source:** Kaggle

- Original records: 5,000
- Cleaned records: 4,987
- Input features: 11
- Target variable: `Personal Loan`
- Class 0: Customers who did not accept the loan.
- Class 1: Customers who accepted the loan.

The dataset contains customer attributes such as age, experience, income, family size, education, mortgage, credit card spending and banking-related information.

### Class Distribution

- Class 0: 90.4%
- Class 1: 9.6%

The dataset is highly imbalanced, making minority-class detection an important consideration.

## 4. Technologies and Libraries Used

| Technology | Purpose |
|---|---|
| Python 3.11 | Programming language |
| Pandas | Dataset loading and manipulation |
| NumPy | Numerical operations |
| Scikit-learn | Machine learning and evaluation |
| Matplotlib | ROC curve visualization |
| Seaborn | Confusion matrix visualization |
| Joblib | Model persistence dependency |

## 5. Project Structure

```text
loan-prediction/
│
├── data/
│   └── Bank_Personal_Loan_Modelling.csv
│
├── results/
│   ├── metrics.csv
│   ├── roc_baseline.png
│   ├── roc_improved.png
│   └── confusion_matrices.png
│
├── src/
│   ├── train.py
│   ├── preprocess.py
│   ├── models.py
│   └── evaluate.py
│
├── .gitignore
├── README.md
└── requirements.txt
```

## 6. Data Preprocessing

The following preprocessing operations were performed:

1. Loaded the dataset using Pandas.
2. Removed unnecessary columns such as ID and ZIP Code.
3. Corrected 52 negative Experience values using the absolute value function.
4. Handled missing and duplicate records.
5. Separated independent features (X) and the target variable (y).
6. Applied stratified train-test splitting in an 80:20 ratio.
7. Applied Min-Max scaling to numerical features.

The final cleaned dataset contains 4,987 records.

- Training samples: 3,989
- Testing samples: 998
- Positive samples in test set: 96

The scaler was fitted only on the training data to prevent data leakage.

## 7. Machine Learning Models

### Part 1: Baseline Models

The following algorithms were implemented:

1. Perceptron
2. Logistic Regression
3. K-Means
4. Support Vector Machine (Linear SVM)
5. Multi-Layer Perceptron (MLP)

### Part 2: Improved Models

The following improvements were implemented:

1. Perceptron with class balancing
2. Logistic Regression with class balancing
3. Linear SVM with class balancing
4. Random Forest with class balancing
5. Hyperparameter-tuned SVM
6. Hyperparameter-tuned MLP

### Hyperparameter Tuning

GridSearchCV with 5-fold StratifiedKFold cross-validation was used to identify suitable hyperparameters for SVM and MLP.

Best SVM parameters:
- C = 10
- Kernel = RBF

Best MLP parameters:
- Hidden layer sizes = (50,)
- Alpha = 0.01

ROC-AUC was used as the hyperparameter tuning scoring metric.

## 8. Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- False Positives (FP)
- False Negatives (FN)

### Final Test Results

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Perceptron | 91.48% | 54.78% | 65.62% | 0.5972 | 0.9329 |
| Logistic Regression | 93.79% | 72.97% | 56.25% | 0.6353 | 0.9610 |
| K-Means | 42.08% | 9.29% | 57.29% | 0.1599 | 0.4584 |
| SVM (Linear) | 94.59% | 79.17% | 59.38% | 0.6786 | 0.9611 |
| MLP | 98.70% | 93.68% | 92.71% | 0.9319 | 0.9978 |
| Random Forest (Balanced) | 98.50% | 87.16% | 98.96% | 0.9268 | 0.9987 |
| SVM (Tuned) | 95.79% | 71.09% | 94.79% | 0.8125 | 0.9947 |
| MLP (Tuned) | 98.50% | 90.91% | 93.75% | 0.9231 | 0.9977 |

### Best Performing Model

Random Forest with class balancing achieved the highest ROC-AUC of **0.9987** and recall of **98.96%**.

Its confusion matrix results are:

- True Negatives: 888
- False Positives: 14
- False Negatives: 1
- True Positives: 95

MLP achieved the highest test accuracy of 98.70% and F1-score of 0.9319 among the evaluated models.

## 9. Generated Outputs

The execution generates the following files inside the `results/` directory:

| Output File | Description |
|---|---|
| `metrics.csv` | Performance metrics of all trained models |
| `roc_baseline.png` | ROC curves comparing baseline models |
| `roc_improved.png` | ROC curves comparing improved models |
| `confusion_matrices.png` | Confusion matrices for model evaluation |

These outputs are used to compare the models and analyse their classification performance.

## 10. How to Run the Project

### Prerequisites

- Python 3.11
- pip
- Visual Studio Code (recommended)

### Step 1: Clone the Repository

```bash
git clone https://github.com/ASHMITHA1045/Loan-prediction-ML
```

### Step 2: Navigate to the Project Directory

```bash
cd loan-prediction
```

### Step 3: Create a Virtual Environment

```bash
python -m venv .venv
```

### Step 4: Activate the Virtual Environment

For Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

### Step 5: Install Dependencies

```bash
python -m pip install -r requirements.txt
```

### Step 6: Execute the Project

```bash
python src/train.py
```

### Step 7: View the Generated Results

```bash
dir results
```

The evaluation metrics and visualization files will be generated in the `results/` directory.

## 11. Conclusion

The project successfully implements and compares multiple machine learning algorithms for predicting personal loan acceptance.

The experiments demonstrate the importance of handling class imbalance and evaluating models using multiple performance metrics rather than relying solely on accuracy.

Random Forest with class balancing achieved the highest ROC-AUC of 0.9987 and recall of 98.96%, making it the selected model based on the primary evaluation criterion.

The project demonstrates how machine learning can support data-driven customer targeting and help banks identify potential personal loan customers more effectively.

## 12. Reference

Rossman, A. J., and Casey, Conor. *Predicting Acceptance of Personal Loans Using Machine Learning Algorithms.*

Dataset: Bank Personal Loan Modelling – Kaggle.