# Bank Term Deposit Subscription Prediction

## Project Overview
The goal of this project is to build a model that predicts whether a bank client will subscribe to a term deposit. The dataset comes from a Portuguese bank and includes client background, loan status, previous marketing interactions, and call details.  

This project demonstrates:
- Data exploration and preprocessing  
- Supervised machine learning modeling  
- Model evaluation using multiple metrics  
- Insights to support more effective marketing decisions  

---

## Dataset
- **Source:** Portuguese bank  
- **Records:** 29,271  
- **Attributes:** 15 features including both categorical and numerical variables  
- **Target variable:** `y` (subscription to a term deposit) — imbalanced  

### Key Features
- **Categorical:** job, marital status, education, contact method, previous campaign outcome  
- **Numerical:** age, call duration, number of past campaign contacts, days since previous contact  

### Notes on Data
- `pdays` = 999 indicates clients were not contacted previously  
- Missing/unknown values in job, education, housing loan, and personal loan were replaced with the most common value  
- One-hot encoding applied for categorical features  
- Call duration and previous campaign outcome were strongly related to subscription  

---

## Methods

Two supervised machine learning methods were applied:

### 1. Decision Tree Classifier
- Creates rules by splitting data based on important features  
- Limited depth and minimum samples per leaf to prevent overfitting  
- Class weight balancing applied to handle imbalanced target variable  

### 2. Logistic Regression
- Linear model suitable for large datasets  
- Scaled numerical features for proper convergence  
- One-hot encoding for categorical features  
- Class weight balancing to reduce impact of class imbalance  

---

## Evaluation Metrics
Models were evaluated using:
- **Accuracy:** Correct predictions percentage  
- **Precision:** Correct `yes` predictions out of total `yes` predicted  
- **Recall:** Correct `yes` predictions out of actual `yes`  
- **F1 Score:** Harmonic mean of precision and recall  
- **Confusion Matrix:** Visual summary of predictions  
- **ROC Curve & AUC:** Measure of class separation  

> Metrics like recall and ROC curve were particularly important due to class imbalance.

---

## Results

| Model                 | Accuracy | AUC    | Notes                                                                 |
|-----------------------|---------|--------|-----------------------------------------------------------------------|
| Decision Tree         | 93.03%  | 0.9838 | High recall for `yes` but lower precision; catches most subscribers |
| Logistic Regression   | 94.50%  | 0.9859 | Higher precision and F1 score; more balanced predictions             |

**Conclusion:** Logistic Regression provided the best overall performance, handling class imbalance effectively and producing stable predictions.

---

## Discussion
- Dataset contains strong patterns for predicting subscription behavior  
- **Decision Tree**:  
  - Strong recall — captures most potential subscribers  
  - Lower precision — misclassifies some `no` as `yes`  
  - Useful when maximizing subscriber identification  
- **Logistic Regression**:  
  - Balanced accuracy, precision, recall, and F1 score  
  - Higher AUC — better overall class separation  
  - More reliable for marketing decisions, minimizing false positives  

> Both models provide insights into which features influence subscription, but Logistic Regression is the preferred choice for deployment.

---

## Key Takeaways
- Call duration and previous campaign outcome are the most important predictors  
- Class balancing is essential when handling imbalanced datasets  
- Logistic Regression is a strong baseline for structured, binary classification problems  

---

## Project Files
- `bank_data.csv` – Original dataset  
- `data_preprocessing.ipynb` – Data cleaning and feature encoding  
- `model_training.ipynb` – Decision Tree and Logistic Regression implementation  
- `evaluation.ipynb` – Model evaluation and metrics visualization  

---

## References
- [PlaytestCloud / QA example](https://www.playtestcloud.com/)  
- [UCI Machine Learning Repository – Bank Marketing Dataset](https://archive.ics.uci.edu/ml/datasets/bank+marketing)  
