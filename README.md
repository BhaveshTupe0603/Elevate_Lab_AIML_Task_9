# 💳 Task 9: Credit Card Fraud Detection

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit_Learn-orange?logo=scikit-learn)
![Pandas](https://img.shields.io/badge/Library-Pandas-150458?logo=pandas)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📖 Overview
**Task 9** focuses on building a machine learning model to detect fraudulent transactions. This project demonstrates how to handle **highly imbalanced datasets** and **messy real-world data**, where fraud cases are extremely rare compared to legitimate transactions.

We utilized a **Random Forest Classifier** to identify patterns in transaction amounts, merchant codes, and device information.

---

## 📂 Dataset
* **Source:** [Kaggle Credit Card Fraud Dataset (Custom Version)](https://kaggle.com/datasets/teamincribo/credit-card-fraud)
* **Shape:** ~8,000 transactions.
* **Key Challenge:**
    * **Data Imbalance:** Fraud cases represent a tiny fraction of the data.
    * **Dirty Data:** The dataset contained text values (e.g., "3 or more" in numerical columns) and categorical strings (e.g., "Mobile", "Tablet") that required extensive cleaning.

---

## ⚙️ Project Workflow

### 1. Data Cleaning & Preprocessing
* **Text-to-Numeric Conversion:** Handled inconsistent values (e.g., converted "3 or more" to `3` in the `Previous Transactions` column).
* **Feature Selection:** Removed PII (Personally Identifiable Information) like Names and Card Numbers. Focused on behavioral features: `Transaction Amount`, `MCC`, `Device Info`, and `Transaction Source`.
* **Encoding:** Applied **One-Hot Encoding** to categorical features like `Device Information` and `Card Type`.

### 2. Handling Imbalance
* Used **Stratified Splitting** (`stratify=y`) to ensure the training and testing sets maintained the same ratio of fraud cases as the original dataset.

### 3. Model Training
* **Algorithm:** Random Forest Classifier (`n_estimators=100`).
* **Why Random Forest?** It handles complex, non-linear relationships well and is generally more robust to imbalanced data than simple linear models.

### 4. Evaluation
We avoided using simple "Accuracy" as a metric because it can be misleading in fraud detection. Instead, we focused on:
* **Precision:** When the model flags a transaction, is it actually fraud?
* **Recall:** Did the model catch all the actual fraud cases?
* **F1-Score:** The harmonic mean of Precision and Recall.

---

## 📊 Key Results

| Metric | Performance |
| :--- | :--- |
| **Accuracy** | ~95%+ |
| **Precision (Fraud)** | High (Low False Positives) |
| **Recall (Fraud)** | High (Few Missed Frauds) |

*Note: The Random Forest model successfully identified the majority of fraud cases while keeping false alarms low.*

### 🔍 Top Fraud Indicators
According to the Feature Importance analysis, the most critical factors for detecting fraud were:
1.  **Transaction Amount:** Unusually high or low amounts.
2.  **Merchant Category Code (MCC):** Certain types of merchants are riskier.
3.  **Previous Transactions:** Account history plays a major role.

---

## 🖼️ Visualizations

### Confusion Matrix
<img width="510" height="393" alt="image" src="https://github.com/user-attachments/assets/d2e3d270-0d5a-4360-aa25-d45a84d13e6a" />


### Feature Importance
<img width="1044" height="528" alt="image" src="https://github.com/user-attachments/assets/d9e29c39-520c-49c8-8ff8-5602b2950c03" />


---

## 💻 How to Run
1.  Clone the repository.
2.  Install dependencies:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn joblib kagglehub
    ```
3.  Run the notebook `Task_9.ipynb`.

## 📂 Deliverables
* [📓 Jupyter Notebook](./Task_9.ipynb)


---
