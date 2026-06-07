# Predicting Rehospitalization of Diabetes Patients

## Contents

- Overview
- Repository Structure

# Overview 

The purpose of this analysis is to predict diabetic patients' risk of rehospitalization within 30 days of discharge. The dataset - [Diabetes 130-US Hospitals for Years 1999-2008](https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008) - was derived from the UCI Machine Learning Repository and contains features describing patients and their hospital visits. This repository contains notebooks for data preprocessing, eda, feature engineering, and training/tuning classifiers with the goal of predicting whether diabetes patients are readmitted.

# Repository Structure
```
└── 📁diabetes-analysis
    └── 📁data
        └── 📁tuning
            ├── cv_scores.csv
            ├── cv_scores_undersample.csv
            ├── sampler_scores.csv
            └── selection_scores.csv
        ├── df_diabetic.csv
        ├── diabetic_data.csv
        ├── IDS_mapping.csv
    └── 📁notebooks
        └── 📁pdfs
            ├── eda.pdf
            ├── feature_engineering_selection.pdf
            ├── preprocessing.pdf
            └── tuning.pdf
        ├── eda.ipynb
        ├── feature_engineering_selection.ipynb
        ├── preprocessing.ipynb
        ├── tuning.ipynb
    ├── .gitignore
    └──  README.md
```

# Notebooks
* eda.ipynb - exploratory data analysis on patient characteristics and medication features
* feature_engineering_selection.ipynb - experiments to create new features and select features based on model importance
* preprocessing.ipynb - correct NA values in string feature columns and measure missing values
* tuning.ipynb - pipeline configuration, model training and hyperparameter tuning experiments. This file serves as our project report

# Artifacts

* Experiment results saved as CSV files within data/tuning
* PDF exports of all notebooks available in notebooks/pdfs

# Challenges/Limitations

* Model performance was severely limited by target class imbalance
* Undersampling techniques used in model tuning contributed to higher recall and lower precision
* Important features for predicting hospital readmission (blood tests, patient weight) had high rates of missing values that required their exclusion from the training data

# [Data Dictionary](https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008)

| Variable Name | Role | Type | Description |
| --- | --- | --- | --- |
| encounter_id | ID | Numeric | Unique identifier of a hospital encounter |
| patient_nbr | ID | Numeric | Unique identifier of a patient |
| race | Feature | Categorical | Values: Caucasian, Asian, African American, Hispanic, and other |
| gender| Feature | Categorical | Values: male, female, and unknown |
| age | Feature | Categorical | Grouped into 10-year intervals |
| weight | Feature | Numeric | Omitted from our analysis due to missing values |
| admission_type_id | Feature | Categorical | Identifies the context in which the patient was admitted to the hospital (emergency, elective, etc) |
| discharge_disposition_id | Feature | Categorical | Identifies where the patient was sent following hospital discharge |
| admission_source_id | Feature | Categorical | Identifies who admitted the patient (physician, emergency room, transfer from hospital, etc) |
| time_in_hospital | Feature | Numeric | Number of days between admission and discharge |
| payer_code | Feature | Categorical | Integer identifier for patient's insurance |
| medical_specialty | Feature | Categorical | Integer identifier of the admitting physician's medical specialty |
| num_lab_procedures | Feature | Numeric | Number of lab tests performed |
| num_procedures | Feature | Numeric | Number of procedures (other than lab tests) |
| num_medications | Feature | Numeric | Number of distinct medications administered |
| number_outpatient | Feature | Numeric | Number of outpatient visits in the year preceding the encounter |
| number_emergency | Feature | Numeric | Number of emergency visits in the year preceding the encounter |
| number_inpatient | Feature | Numeric | Number of inpatient visits in the year preceding the encounter |
| diag_1 | Feature | Categorical | Primary diagnosis ICD9 |
| diag_2 | Feature | Categorical | Secondary diagnosis ICD9 |
| diag_3 | Feature | Categorical | Additional diagnosis ICD9 |
| number_diagnoses | Feature | Numeric | Total number of diagnoses entered to the system |
| max_glu_serum | Feature | Categorical | Range of serum glucose test, if administered |
| A1Cresult | Feature | Categorical | Range of A1C test, if administered |
| 23 Diabetes Medications | Feature | Categorical | Steady if dosage not changed, up if dosage increased, down if dosage decreased, no if not prescribed |
| change | Feature | Categorical | Indicates whether or not there was a change in diabetic medications |
| diabetesMed | Feature | Categorical | Indicates if a diabetic medication was prescribed |
| readmitted | Target | Categorical | Indicates whether or not patient was readmitted within 30 days |

# Acknowledgements

Beata Strack, Jonathan P. DeShazo, Chris Gennings, Juan L. Olmo, Sebastian Ventura, Krzysztof J. Cios, and John N. Clore, “Impact of HbA1c Measurement on Hospital Readmission Rates: Analysis of 70,000 Clinical Database Patient Records,” BioMed Research International, vol. 2014, Article ID 781670, 11 pages, 2014.
