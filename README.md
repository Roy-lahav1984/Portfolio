Stroke Prediction: Machine Learning Project

Overview

This project uses the Stroke Prediction Dataset to identify key health and demographic factors that influence stroke risk.  
It demonstrates a complete data science workflow — from cleaning and EDA to modeling and interpretation — suitable for healthcare analytics, predictive modeling, and risk assessment case studies.

---

Dataset

| Feature | Description |
|----------|-------------|
| `gender` | Male / Female |
| `age` | Age of the patient |
| `hypertension` | 0 = No, 1 = Yes |
| `heart_disease` | 0 = No, 1 = Yes |
| `ever_married` | Yes / No |
| `work_type` | Type of employment |
| `Residence_type` | Urban / Rural |
| `avg_glucose_level` | Average blood glucose |
| `bmi` | Body-Mass Index |
| `smoking_status` | smoking / formerly smoked / never smoked / Unknown |
| `stroke` | Target variable (1 = stroke occurred) |

---

Project Structure

```
stroke_prediction_project/
│
├── 01_data_cleaning.ipynb        → Handles missing values, encodes categories, scales numerics
├── 02_eda.ipynb                  → Explores data distributions & feature relationships
├── 03_modeling.ipynb             → Trains and evaluates predictive models
├── data/
│   └── stroke.csv
├── data_cleaned/
│   └── stroke_cleaned.csv
└── models/
    └── <saved_model>.joblib
```

---

Workflow Summary

1) Data Cleaning
- Filled missing BMI values with the median  
- Normalized categorical columns  
- Encoded binary and multi-class features  
- Scaled numerical variables (`age`, `avg_glucose_level`, `bmi`)  

---

2) Exploratory Data Analysis (EDA)
- Age, glucose, and BMI distributions  
- Stroke rates by gender, hypertension, and heart disease  
- Lifestyle indicators: smoking & work type  
- Correlation matrix and scatterplots  

Findings:
- Stroke patients tend to be older with higher glucose.  
- Hypertension and heart disease are major risk factors.  
- Dataset is highly imbalanced (~5% stroke cases).

---

3) Modeling & Prediction
Trained and compared three models:
- Logistic Regression (balanced) 
- Random Forest Classifier  
- Gradient Boosting Classifier

Evaluation Metrics:

| Model | ROC-AUC | PR-AUC | F1 | Recall |
|--------|----------|--------|----|--------|
| Logistic Regression | ~0.83 | ~0.28 | ~0.22 | ~0.68 |
| Random Forest | ~0.85 | ~0.31 | ~0.24 | ~0.73 |
| Gradient Boosting | ~0.84 | ~0.30 | ~0.25 | ~0.70 |

Best Model: Random Forest  
Key Predictors: Age, Avg Glucose Level, Hypertension, BMI  

---

Business & Clinical Insights

1.Early detection:  
   High glucose and older patients show elevated stroke risk; screening can be prioritized.

2.Chronic management:  
   Hypertension and heart disease significantly increase risk — control programs can reduce probability.

3.Threshold tuning:  
   Adjusting decision thresholds improved recall on the minority class, better for preventive use.

---

Tech Stack

- Python 3.x  
- Pandas / NumPy / Matplotlib  
- Scikit-learn  
- Joblib  

---

Run notebooks in order:  
   - `stroke_data_cleaning.ipynb`  
   - `stroke_eda.ipynb`  
   - `stroke_modeling.ipynb`  



