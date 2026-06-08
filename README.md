# Early Sepsis Prediction Using Machine Learning on ICU Patients

> End-to-end healthcare machine learning project leveraging ICU patient data to predict sepsis risk, evaluate model performance, detect information leakage, and generate clinically interpretable insights.

---

## Project Overview

Sepsis remains one of the leading causes of mortality among critically ill patients. Early identification is essential for improving patient outcomes and reducing healthcare burden.

This project develops and evaluates machine learning models for sepsis prediction using ICU patient data inspired by the MIMIC-IV clinical database. The analysis covers the entire machine learning lifecycle, from data preprocessing and exploratory analysis to model evaluation, explainability, and clinical utility assessment.

### Key Highlights

- Exploratory Data Analysis (EDA)

- Missing Value Handling & Feature Engineering

- Class Imbalance Treatment using SMOTE

- Logistic Regression, Random Forest, and XGBoost Modeling

- Information Leakage Validation

- SHAP Explainability Analysis

- Calibration Curve Evaluation

- Decision Curve Analysis (DCA)

- Clinical Insight Generation

---

## Business & Clinical Problem

Sepsis is a life-threatening condition resulting from the body's dysregulated response to infection.

Healthcare providers often face challenges in:

- Identifying sepsis early enough for intervention
- Prioritizing high-risk ICU patients
- Interpreting large volumes of clinical data
- Developing reliable predictive models without data leakage

This project investigates whether machine learning can support earlier risk identification using routinely collected ICU data.

---

## Dataset

### Source

Synthetic ICU dataset designed to resemble the structure of the MIMIC-IV database.

### Dataset Characteristics

| Attribute | Value |
|------------|--------|
| Total Records | 5,000 Patients |
| Features | 77 Variables |
| Target | Sepsis Status |
| Target Type | Binary Classification |

### Target Variable

| Value | Description |
|---------|-------------|
| 0 | Non-Sepsis |
| 1 | Sepsis |

---

## Features Included

### Demographic Features

- Age
- Gender
- Ethnicity

### Vital Signs

- Heart Rate
- Respiratory Rate
- Temperature
- Mean Arterial Pressure (MAP)
- Oxygen Saturation (SpO₂)

### Laboratory Results

- White Blood Cell Count (WBC)
- Lactate
- Creatinine
- Hemoglobin
- Platelet Count
- Bilirubin
- INR
- Glucose

### Clinical Severity Indicators

- SOFA Score
- qSOFA Score
- APACHE IV
- SIRS Criteria

### ICU Interventions

- Mechanical Ventilation
- Vasopressor Usage
- Renal Replacement Therapy

---

## Exploratory Data Analysis

The EDA phase focused on understanding data quality, feature distributions, and relationships with sepsis outcomes.

### Analysis Performed

- Missing Value Assessment
- Distribution Analysis
- Correlation Analysis
- Outlier Detection
- Target Distribution Inspection

### Key Findings

- Several laboratory variables contained approximately 10–11% missing values.
- Lactate demonstrated a strong association with sepsis.
- Organ dysfunction markers were highly predictive.
- Clinical severity scores showed near-perfect predictive power, indicating possible information leakage.

---

## Data Preprocessing

### Missing Values

Median imputation was applied to numerical variables.

### Feature Encoding

One-Hot Encoding was used for categorical variables.

### Data Splitting

| Dataset | Percentage |
|----------|------------|
| Training | 80% |
| Testing | 20% |

### Class Imbalance Treatment

SMOTE (Synthetic Minority Oversampling Technique) was applied to improve class balance.

### Feature Scaling

StandardScaler was used where appropriate.

---

## Machine Learning Models

Three classification models were developed and compared.

### 1. Logistic Regression

Baseline interpretable model for binary classification.

### 2. Random Forest

Ensemble tree-based model using bootstrap aggregation.

### 3. XGBoost

Gradient boosting model optimized for predictive performance.

---

## Information Leakage Investigation

One of the most important components of this project was validating model reliability by investigating information leakage.

### Initial Model

Included:

- SOFA Score
- qSOFA Score
- APACHE IV
- SIRS Criteria

Result:

- Extremely high ROC-AUC
- Near-perfect predictive performance

### Leakage Concern

These variables may already incorporate information reflecting sepsis severity and diagnosis, making them unsuitable for real-world early prediction.

### Reduced Model

Severity-score variables were removed and models were retrained.

### Outcome

Performance decreased but became more realistic and clinically deployable.

---

## Model Evaluation

### Performance Metrics

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC

### Additional Validation

#### ROC Curve Analysis

Evaluates discrimination capability.

#### Confusion Matrix

Examines prediction errors.

#### Calibration Curve

Measures probability reliability.

#### Brier Score

Assesses probabilistic prediction quality.

#### Decision Curve Analysis (DCA)

Evaluates potential clinical usefulness.

---

## Model Explainability

SHAP (SHapley Additive exPlanations) was used to explain model predictions.

### Most Influential Features

- Lactate
- Creatinine
- Oxygen Saturation (SpO₂)
- Respiratory Variables
- Organ Dysfunction Indicators
- Severity Scores

SHAP analysis provides transparent and clinically interpretable insights into model behavior.

---

## Key Insights

### Clinical Findings

- Elevated lactate was among the strongest predictors of sepsis.
- Renal dysfunction markers significantly contributed to risk prediction.
- Respiratory deterioration was associated with increased sepsis likelihood.
- Physiological measurements remained informative even after removing severity scores.
- Information leakage can substantially overestimate model performance.

### Data Science Findings

- Feature selection is critical in healthcare machine learning.
- Model calibration is as important as discrimination performance.
- Explainability techniques improve trust and interpretability.
- Leakage validation is essential before deployment.

---

## Tech Stack

### Programming Language

- Python

### Data Processing

- Pandas
- NumPy

### Visualization

- Matplotlib
- Seaborn

### Machine Learning

- Scikit-Learn
- XGBoost
- Imbalanced-Learn (SMOTE)

### Explainability

- SHAP

### Statistical Analysis

- SciPy

---

## Repository Structure

```bash
MIMIC-IV-Sepsis-Prediction/
│
├── data/
│   └── sepsis_icu_synthetic.csv
│
├── notebooks/
│   └── MIMIC_IV_for_Sepsis_Prediction.ipynb
│
├── images/
│   ├── roc_curve.png
│   ├── calibration_curve.png
│   ├── shap_summary.png
│   └── feature_importance.png
│
├── requirements.txt
│
└── README.md
```

---

## Future Improvements

Potential future work includes:

- External validation using real-world ICU cohorts
- Time-series prediction using patient trajectories
- Survival analysis for mortality prediction
- Hyperparameter optimization
- Streamlit dashboard deployment
- MLOps pipeline development
- Real-time clinical decision support integration

---

## Project Outcomes

This project demonstrates a complete healthcare analytics workflow, combining:

- Clinical domain understanding
- Data preprocessing
- Machine learning modeling
- Explainable AI
- Model validation
- Clinical utility assessment

The findings highlight the importance of rigorous validation and explainability when developing machine learning solutions for healthcare applications.

---
