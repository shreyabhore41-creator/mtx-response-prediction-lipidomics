# mtx-response-prediction-lipidomics
Machine learning-based prediction of methotrexate response in rheumatoid arthritis using baseline serum lipidomics, with model evaluation, feature selection, SHAP analysis, and nested cross-validation.
# Machine Learning-Based Prediction of Methotrexate Response Using Baseline Serum Lipidomics in Rheumatoid Arthritis

## Project Overview

Rheumatoid arthritis (RA) is a chronic inflammatory autoimmune disease in which patients show variable responses to methotrexate (MTX), a commonly used first-line treatment.

This project investigates the potential of baseline serum lipidomic profiles to predict MTX treatment response using machine-learning approaches.

A high-dimensional dataset consisting of 100 RA patients and 3,366 lipidomic features was analysed to distinguish good responders from non-responders.

Six machine-learning classifiers were evaluated using five-fold nested cross-validation. Additional analyses included permutation testing, feature selection, SHAP-based model interpretation, and comparison of positive- and negative-ionization lipidomic features.

## Objectives

- Investigate the predictive potential of baseline serum lipidomics for MTX response.
- Develop and compare six machine-learning classification models.
- Evaluate model performance using five-fold nested cross-validation and ROC-AUC.
- Assess predictive significance using permutation testing.
- Investigate the effect of feature selection on model performance.
- Compare positive-ionization (LPOS) and negative-ionization (LNEG) feature sets.
- Interpret influential lipidomic features using SHAP analysis.

## Dataset Description

The dataset was obtained from the published study:

Maciejewski et al. (2021), *Prediction of response of methotrexate in patients with rheumatoid arthritis using serum lipidomics*.

**Dataset characteristics:**

| Parameter | Description |
|---|---|
| Disease | Rheumatoid Arthritis |
| Treatment | Methotrexate (MTX) |
| Total patients | 100 |
| Good responders | 50 |
| Non-responders | 50 |
| Total lipidomic features | 3,366 |
| Negative ionization (LNEG) | 1,060 features |
| Positive ionization (LPOS) | 2,306 features |
| Prediction task | Binary classification |

The response variable was encoded as:
- 1 – Good responder
- 0 – Non-responder

## Methodology

### 1. Data Preparation
Baseline serum lipidomic data were processed to obtain 3,366 features from positive- and negative-ionization modes.

### 2. Nested Cross-Validation
Stratified five-fold nested cross-validation was implemented:
- Inner cross-validation: Hyperparameter optimization.
- Outer cross-validation: Model performance evaluation.

### 3. Machine-Learning Models

Six classification algorithms were evaluated:

1. Logistic Regression
2. K-Nearest Neighbours (KNN)
3. Decision Tree
4. Random Forest
5. Support Vector Machine (SVM)
6. Elastic-Net Logistic Regression

StandardScaler and GridSearchCV were incorporated into the modelling pipelines where appropriate.

### 4. Model Evaluation
ROC-AUC was used as the primary evaluation metric. Mean ROC-AUC and standard deviation were calculated across the five outer folds.

### 5. Permutation Testing
A permutation test with 100 random label permutations was performed to evaluate whether the observed KNN performance exceeded that expected by chance.

### 6. Feature Selection
SelectKBest with the ANOVA F-test (f_classif) was used to investigate feature subsets containing 50, 100, 250 and 500 features.

### 7. Ionization-Mode Comparison
KNN performance was compared across three feature configurations:
- LNEG – Negative-ionization features.
- LPOS – Positive-ionization features.
- Combined – Both ionization modes.

### 8. SHAP Analysis
SHAP (SHapley Additive exPlanations) was used to interpret the contribution of individual lipidomic features to KNN predictions.

## Technologies Used

- Python
- Jupyter Notebook
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- SHAP

## Results and Findings

### 1. Comparison of Machine-Learning Models

| Model | Mean ROC-AUC |
|---|---:|
| Logistic Regression | 0.538 |
| KNN | **0.574** |
| Decision Tree | 0.507 |
| Random Forest | 0.527 |
| SVM | 0.490 |
| Elastic-Net Logistic Regression | 0.542 |

KNN achieved the highest mean ROC-AUC of 0.574 ± 0.112 using all 3,366 features.

### 2. Permutation Testing

- Observed KNN ROC-AUC: 0.574
- Number of permutations: 100
- Permutation p-value: 0.139

The result did not provide statistically significant evidence of predictive performance above randomly shuffled response labels.

### 3. Feature Selection

Feature selection did not consistently improve predictive performance.

For KNN, mean ROC-AUC decreased from 0.574 to 0.518 after feature selection.

### 4. Ionization-Mode Comparison

| Feature Set | Mean ROC-AUC |
|---|---:|
| LNEG | 0.540 |
| LPOS | 0.559 |
| Combined | **0.574** |

The combined feature set showed the highest observed predictive performance, although the differences were not statistically tested.

### 5. SHAP-Based Interpretation

SHAP analysis identified influential lipidomic features contributing to KNN predictions.

Some of the top feature identifiers included:
- LNEG_V259
- LPOS_V1786
- LPOS_V1881
- LPOS_V2059
- LPOS_V437
- LNEG_V929

These features represent model-influential variables and should not be considered validated biomarkers.

## Conclusion

The study investigated the application of machine learning to predict methotrexate response in rheumatoid arthritis using baseline serum lipidomic profiles.

Among the six evaluated classifiers, KNN achieved the highest mean ROC-AUC of 0.574. However, the overall predictive performance remained modest, and permutation testing did not establish statistically significant predictive performance above chance.

Feature selection did not consistently improve prediction, while combining positive- and negative-ionization features produced the highest observed ROC-AUC.

Overall, the findings indicate limited predictive performance of baseline serum lipidomics in this dataset and highlight the importance of robust validation and model interpretation in high-dimensional biomedical data analysis.

## Future Directions

- Evaluate larger and independent patient cohorts.
- Map lipidomic feature identifiers to chemically annotated lipid molecules.
- Investigate advanced multivariate feature-selection approaches.
- Integrate clinical and demographic information with lipidomic data.
- Perform external model validation.
- Extend SHAP analysis and biological interpretation.
- Conduct experimental and clinical validation of potentially informative features.

## Repository Contents

- Jupyter Notebook – Machine-learning implementation, model evaluation, feature selection, permutation testing, ionization-mode comparison and SHAP analysis.
- README.md – Project documentation.
- .gitignore – Files excluded from version control.

## References

1. Maciejewski, M. et al. (2021). Prediction of response of methotrexate in patients with rheumatoid arthritis using serum lipidomics. *Scientific Reports*, 11, 7266. https://doi.org/10.1038/s41598-021-86729-7

2. Lee, J. L. et al. (2022). Machine learning using genetic and clinical data identifies a signature that robustly predicts methotrexate response in rheumatoid arthritis. *Rheumatology*, 61, 4175–4186. https://doi.org/10.1093/rheumatology/keac032

---


**Project Guide:** Dr. Kushagra Kashyap

**Academic Year:** 2026–2027
