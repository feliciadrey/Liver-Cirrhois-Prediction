# Liver Cirrhosis Stage Prediction
Machine learning classification project to predict the stage of liver cirrhosis based on patient demographics, lab results, and clinical indicators. This project focuses on a complete end-to-end pipeline from data preprocessing and exploratory data analysis to model training, hyperparameter tuning, and evaluation, prioritizing balanced performance across imbalanced medical classes.

---

## Overview
This project was developed for the **Machine Learning** course as part of the individual final exam. The objective is to predict the stage of liver cirrhosis using structured medical records.  

The workflow includes:
- Exploratory Data Analysis (EDA) to identify anomalies, trends, and relationships between features and cirrhosis stages
- Data cleaning and preprocessing (handling missing values, fixing anomalies, encoding categorical variables, scaling numerical features)
- Class imbalance handling with RandomOverSampler
- Model experimentation and evaluation
- Hyperparameter tuning for optimal F1-score performance
- Feature importance analysis to interpret clinical relevance

**Deliverables include:**
- **Python notebook** – complete pipeline for preprocessing, model training, and evaluation
- **Presentation slides (PPT)** – summarizing key findings, methodology, and results
---

## Data

The dataset contains anonymized liver cirrhosis patient records, including demographics, lab results, and medical history.

**Key Information**
- **Entries:** 418 rows  
- **Features:** 18 columns after preprocessing (mix of numerical and categorical)  
- **Target Variable:** `Stage` (Stage 1, Stage 2, Stage 3, Stage 4)  

### Data Dictionary (selected variables)

| Variable        | Description |
|-----------------|-------------|
| **Gender**      | Patient gender |
| **Age**         | Patient age (derived from registration and birth dates) |
| **Bilirubin**   | Bilirubin level in blood |
| **Albumin**     | Albumin level in blood |
| **Platelets**   | Platelet count |
| **Ascites**     | Presence of fluid in the abdomen (Y/N) |
| **Hepatomegaly**| Presence of enlarged liver (Y/N) |
| **Drug**        | Medication given (Placebo / D-penicillamine) |
| **Prothrombin** | Blood clotting time |
| **Stage**       | Cirrhosis stage (target variable) |

---

## Features
- **Data Cleaning**
  - Anomaly correction (e.g., negative triglycerides replaced with absolute values)
  - Removal of unreliable features with excessive missing values (e.g., Cholesterol)
  - Median/mode imputation for remaining missing data
  - Standardization of categorical labels
- **Feature Engineering**
  - Age calculation from date columns
  - Dropping identifier columns to prevent data leakage
- **EDA Insights**
  - Higher bilirubin and lower albumin associated with later cirrhosis stages
  - Older patients more likely in Stage 4
  - Declining platelet counts correlated with disease progression
- **Modeling**
  - Class balancing with **RandomOverSampler**
  - Model comparison:
    - **Random Forest** (best overall)
    - **XGBoost**
  - Hyperparameter tuning via **GridSearchCV** (scoring: `f1_macro`)
- **Evaluation**
  - Main metric: **F1-score** (important in medical predictions to balance false positives and false negatives)
  - Confusion matrix analysis to identify class-specific misclassifications
- **Feature Importance**
  - Albumin, Platelets, Prothrombin, Age, and Bilirubin ranked as most important predictors in Random Forest

---

## Tools & Technologies
- **Python** – data preprocessing, analysis, and modeling
- **Pandas / NumPy** – data manipulation
- **Matplotlib / Seaborn** – data visualization
- **Scikit-learn** – preprocessing, model training, evaluation
- **XGBoost** – gradient boosting classifier
- **Random Forest** – ensemble classifier for final selection
- **Imbalanced-learn** – RandomOverSampler for class balancing
- **Statistics** – median/mode imputation
