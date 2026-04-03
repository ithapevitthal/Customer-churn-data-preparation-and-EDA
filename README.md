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

5. **Modeling**
   - Trained Logistic Regression and Random Forest
   - Evaluated using accuracy, precision, recall, F1, ROC AUC, confusion matrix

6. **Hyperparameter Tuning**
   - `GridSearchCV` on Random Forest
   - Best model: `n_estimators=200`, `max_depth=10`

7. **Model Persistence**
   - Model saved as `churn_model.pkl` and reloaded to verify predictions.

## Run Notebook

1. Install dependencies:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn joblib reportlab
```

2. Launch notebook:
```bash
jupyter notebook churn_prediction.ipynb
```

## Generate / Regenerate PDF Report

If `pandoc` is installed, run:
```bash
jupyter nbconvert --to pdf churn_prediction.ipynb
```

Otherwise script generates `churn_report.pdf` with key results and summary.

## Notes

- Data pre-processing and modeling results are deterministic via `random_state=42`.
- Current best test ROC AUC is ~0.835 with tuned Random Forest.
