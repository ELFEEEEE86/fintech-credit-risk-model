# Credit Default Prediction and Risk Segmentation for Consumer Lending

## Project Overview

This project developed an end-to-end probability-of-default (PD) modeling workflow using LendingClub consumer loan data. The objective was to estimate borrower-level default risk using only information available at loan origination, simulating a realistic fintech underwriting and portfolio risk assessment workflow.

The project combined traditional credit-risk modeling approaches with modern machine-learning techniques, emphasizing:
- underwriting realism
- leakage control
- model validation
- explainability
- business interpretation
- portfolio risk segmentation

---

## Business Problem

Fintech lenders must balance:
- portfolio growth
- borrower approval rates
- default risk
- portfolio quality

This project framed the problem as a real underwriting decision:

> Given borrower and loan information available at origination, can we estimate the probability that a borrower will default?

The goal was not only to build predictive models, but also to evaluate whether the resulting risk estimates were operationally useful for underwriting and portfolio monitoring.

---

## Dataset

Dataset:
- LendingClub accepted consumer loans dataset

Features included:
- borrower financial characteristics
- loan structure information
- credit history variables
- repayment outcomes

### Target Definition

Bad loans (`1`)
- Charged Off
- Default
- Severe Delinquency

Good loans (`0`)
- Fully Paid

Unresolved loan statuses were removed to avoid target contamination.

Post-origination variables (such as payment recoveries and collection activity) were excluded to preserve underwriting realism and prevent temporal leakage.

---

## Project Workflow

### 1. Data Cleaning and Target Definition
- Removed unresolved loan outcomes
- Excluded leakage variables unavailable at underwriting time
- Cleaned and transformed borrower/loan variables
- Constructed underwriting-ready modeling dataset

Notebook:
```text
01_data_cleaning_and_target_definition.ipynb
```

---

### 2. Exploratory Risk Analysis
Analyzed default-risk concentration across:
- loan grades
- interest rates
- loan terms
- debt-to-income ratios
- borrower risk segments

Used portfolio-average benchmarking to evaluate relative risk concentration.

Notebook:
```text
02_exploratory_risk_analysis.ipynb
```

---

### 3. Probability-of-Default Modeling

Built and compared:
- Logistic Regression (baseline)
- LightGBM (challenger model)

Used a temporal train/test split based on loan origination date to better simulate real underwriting deployment.

Validation metrics:
- ROC-AUC
- Precision / Recall
- Confusion Matrix
- Threshold Analysis

Notebook:
```text
03_pd_modeling.ipynb
```

---

### 4. Model Validation and Business Interpretation

Performed:
- calibration analysis
- SHAP explainability
- feature importance analysis
- threshold tradeoff analysis
- portfolio risk segmentation

The project emphasized translating model outputs into underwriting and portfolio-management insights rather than optimizing prediction metrics alone.

Notebook:
```text
04_model_validation_and_business_interpretation.ipynb
```

---

### 5. Final Project Summary

Prepared:
- executive summary
- final visualizations
- resume-ready project descriptions

Notebook:
```text
05_project_summary.ipynb
```

---

## Modeling Approach

### Logistic Regression
Used as an interpretable benchmark commonly applied in traditional credit-risk modeling.

Advantages:
- coefficient transparency
- regulatory interpretability
- stable probability outputs

### LightGBM
Used as a nonlinear machine-learning challenger model.

Advantages:
- improved predictive flexibility
- stronger nonlinear pattern detection
- enhanced borrower risk ranking

---

## Key Findings

- Borrowers with weaker credit grades, elevated debt burdens, longer loan terms, and higher interest rates exhibited materially higher default risk.

- LightGBM demonstrated modestly stronger discriminatory performance than Logistic Regression, though the performance gap was incremental rather than transformative.

- Calibration analysis showed that predicted default probabilities aligned reasonably with observed portfolio outcomes.

- SHAP analysis confirmed that affordability and credit-quality variables were among the strongest drivers of predicted default risk.

- Risk-band segmentation successfully differentiated low-risk and high-risk borrower populations, supporting potential underwriting and portfolio-monitoring use cases.

---

## Example Visualizations

### ROC Curve Comparison

![ROC Curve](visuals/roc_curve_comparison.png)

---

### Calibration Curve

![Calibration Curve](visuals/calibration_curve.png)

---

### SHAP Feature Importance

![SHAP Summary](visuals/shap_summary.png)

---

### Risk Band Default Rates

![Risk Bands](visuals/risk_band_default_rates.png)

---

## Repository Structure

```text
fintech-credit-risk-model/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── models/
│
├── notebooks/
│   ├── 01_data_cleaning_and_target_definition.ipynb
│   ├── 02_exploratory_risk_analysis.ipynb
│   ├── 03_pd_modeling.ipynb
│   ├── 04_model_validation_and_business_interpretation.ipynb
│   └── 05_project_summary.ipynb
│
├── reports/
├── visuals/
├── README.md
└── requirements.txt
```

---

## Technologies Used

### Programming
- Python

### Libraries
- pandas
- NumPy
- scikit-learn
- LightGBM
- SHAP
- matplotlib
- seaborn

---

## Skills Demonstrated

- Credit Risk Modeling
- Probability of Default (PD) Modeling
- Logistic Regression
- Gradient Boosting
- Feature Engineering
- Model Validation
- Calibration Analysis
- SHAP Explainability
- Portfolio Risk Segmentation
- Underwriting Analytics
- Fintech Risk Analytics
- Python for Data Science

---

## Limitations

- The dataset only includes approved borrowers, creating potential selection bias.
- LendingClub borrowers may not represent the broader consumer lending market.
- Historical borrower behavior may shift under different macroeconomic conditions.
- Additional behavioral and transaction-level data could improve predictive performance.

---

## Future Improvements

Potential extensions include:
- reject inference
- macroeconomic stress testing
- expected loss (ECL) modeling
- probability calibration refinement
- risk-based pricing simulation
- portfolio vintage analysis

---

## Author

Huruizhen Qin  
MS in Business Analytics — Duke University  
Interested in fintech credit risk, underwriting analytics, and risk data science roles.