# Fraud Detection Project

## 📌 Objective
This project develops a machine learning pipeline to detect fraudulent financial transactions using the provided dataset (`Fraud.csv`).  
The goal is to identify high-risk transactions in real time and provide actionable business insights to help reduce fraud losses.

---

## 📂 Dataset Overview
- **Rows:** 6,362,620  
- **Columns:** 10  
- **Fraud Cases:** 8,213 (~0.13% of all transactions)  
- **Data Dictionary:**
    - `step` — Time step in hours (1 step = 1 hour; total 744 = 30 days)  
    - `type` — Transaction type (`CASH-IN`, `CASH-OUT`, `DEBIT`, `PAYMENT`, `TRANSFER`)  
    - `amount` — Transaction amount in local currency  
    - `nameOrig` — ID of customer initiating the transaction  
    - `oldbalanceOrg` — Balance before transaction  
    - `newbalanceOrig` — Balance after transaction  
    - `nameDest` — ID of recipient  
    - `oldbalanceDest` — Recipient's balance before transaction (NaN for merchants `M...`)  
    - `newbalanceDest` — Recipient's balance after transaction (NaN for merchants `M...`)  
    - `isFraud` — 1 if the transaction is fraudulent, else 0  
    - `isFlaggedFraud` — 1 if flagged by rule (transfer > 200,000), else 0  

⚠️ **Note:** The dataset is highly imbalanced. Class balancing techniques such as **SMOTE** are applied during model training.

---

## 🛠️ Project Workflow
1. **Data Loading & Exploration**  
   - Reviewed dataset structure, missing values, fraud distribution, and class imbalance.
2. **Feature Engineering**  
   - Created merchant flag, aggregated customer transaction stats, handled NaNs carefully.  
3. **Preprocessing**  
   - Scaled numeric features, encoded categorical variables via pipelines.
4. **Class Balancing**  
   - Applied **SMOTE** to training data only.
5. **Model Training**  
   - Implemented **XGBoost Classifier** with early stopping for efficiency.  
6. **Evaluation**  
   - ROC Curve, Precision–Recall Curve, Average Precision Score, Confusion Matrix, and Threshold Tuning.
7. **Business Insights & Recommendations**  
   - Identified patterns in fraud transactions and proposed prevention strategies.

---

## 📊 Key Findings
- `CASH-OUT` and `TRANSFER` transactions account for most fraud cases.
- Large transaction amounts executed in short time frames are common in fraud.
- Unusual transaction hours often correlate with fraudulent activity.
- The dataset's `isFlaggedFraud` rule misses many frauds that the model detects.

---

