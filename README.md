# Telco Customer Churn Prediction

This repository contains a Python Jupyter Notebook and report for end-to-end churn prediction using the `WA_Fn-UseC_-Telco-Customer-Churn.csv` dataset.

## Files

- `churn_prediction.ipynb`: Notebook with full workflow: data understanding, cleaning, feature engineering, EDA, modeling, evaluation, tuning, and model serialization.
- `churn_report.pdf`: Summary report generated from notebook findings and results.
- `churn_model.pkl`: Serialized trained Random Forest model (best estimator from tuning).
- `README.md`: Project summary and usage guide.

## Project Task Flow

1. **Data Understanding**
   - Loaded dataset
   - `.info()`, `.describe()`, missing values, and class balance
   - Discovered `TotalCharges` invalid entries (spaces) and converted to numeric

2. **Data Cleaning**
   - Cast `TotalCharges` to numeric with coercion
   - Dropped invalid/missing rows and `customerID`
   - Encoded `Churn` (Yes=1, No=0)

3. **Feature Engineering**
   - Added `TenureGroup` and `AvgMonthlySpend`
   - Binary mapping for partner/dependents/phoneservice/paperlessbilling/gender
   - One-hot encoding for categorical columns

4. **EDA & Visualization**
   - Churn countplot
   - Contract vs Churn barplot
   - Correlation heatmap
   - MonthlyCharges boxplot by churn
