**Predicting Post-Operative Delirium Using Machine Learning**

Overview:
Post-operative delirium (POD) is a serious, fluctuating disturbance of attention and cognition that commonly occurs in elderly surgical patients. It increases hospital stay, complication risk, mortality, and long-term cognitive decline.
This project explores how classical machine learning algorithms can predict the risk of post-operative delirium using routine clinical data from elderly surgical or hip-fracture patients. The goal is to build an interpretable, data-driven workflow to help clinicians identify high-risk patients early.

Objectives:
*Preprocess and analyze an anonymized delirium dataset.
*Train and compare multiple machine learning classifiers.
*Identify key clinical predictors of delirium.
*Explore patient subgroups using PCA and K-Means clustering.
*Build a simple patient-level risk interface that outputs Low or High risk labels.

Dataset:
Source: An anonymized clinical dataset of elderly surgical patients (delirium_ml.xlsx).
Each row represents a patient; each column is a clinical variable.

Example Features:
*Demographics: Age, BMI, Height
*Frailty Index
*Lab values: Hematocrit (Hct), Albumin (Alb), Creatinine (Cre)
*Peri-operative variables: Duration of surgery/anesthesia, ICU admission, Infusions, Vasopressors
*Target: Postop_Delirium (0 = No, 1 = Yes)

Notes:
Numeric columns were cleaned and converted properly.
Missing numeric values were imputed using the median.
Data was split 80/20 using stratified sampling to preserve delirium ratio.

Methods:-
Step	Description:
1. Preprocessing	Data cleaning, type conversion, median imputation, scaling (StandardScaler).
2. Models Trained	Logistic Regression, Random Forest, Support Vector Machine (RBF kernel), Multi-Layer Perceptron (MLP).
3. Evaluation	Metrics include ROC AUC, confusion matrices, and classification reports.
4. Unsupervised Analysis	PCA for visualization; K-Means (k=3) to find patient clusters/phenotypes.
5. Interface	Random Forest-based function predicts delirium risk and outputs Low/High label.

Results:
Model	ROC AUC (Test)	Key Notes
Logistic Regression	0.779	Strong interpretable baseline
Random Forest	0.597	Provided valuable feature importances
SVM (RBF)	0.694	Moderate non-linear performance
MLP Neural Network	0.802	Best predictive performance

Key Predictors Identified:
Age
Frailty Index
ICU Admission
Hematocrit, Albumin, Creatinine
Duration of anesthesia/surgery

Cluster Analysis:
Three patient clusters identified
One high-risk cluster (~33% delirium rate)

Clinical Insight:
The Random Forest interface allows clinicians to input patient details (Age, Frailty, ICU admission, lab results) and instantly receive:
A delirium probability score, and
A Low or High risk label
This simplifies risk estimation using routine hospital data and demonstrates how ML models can assist in early delirium prevention strategies.

Limitations & Ethical Use:
Small, single-cohort dataset — limited generalization.
Not validated or calibrated for clinical use.
Missing variables such as medications or baseline cognition.
Strictly for educational and research purposes — not a medical tool.

Future Work:
Collect larger, multi-center datasets.
Explore advanced models (XGBoost, LightGBM).
Apply cross-validation and hyperparameter tuning.
Perform bias analysis and probability calibration.
Integrate an interpretable model into a web or EHR interface after regulatory validation.

Reference:-
Zhao, Hong (2022). Machine Learning Delirium. Mendeley Data, V1. DOI: 10.17632/5sbrfcg5r7.1
