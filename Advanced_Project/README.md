# Early Disease Detection — Diabetes Risk Prediction 

## Description
An end-to-end advanced machine learning project that predicts early stage **diabetes risk** from patient biomarkers. The pipeline includes rigorous data cleaning (handling physiologically invalid zeros), feature engineering, multi-model training, hyperparameter-aware cross-validation, ROC-AUC evaluation, clinical decision threshold analysis, and Random Forest feature importance visualisation. This project demonstrates how ML can support (not replace) clinical screening decisions.



## Dataset
- **Source:** Simulated dataset structured after the [Pima Indians Diabetes Database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database) (NIDDK / UCI)
- **Description:** 768 patient records with 8 clinical biomarkers:

| Feature | Description |
|---|---|
| Pregnancies | Number of pregnancies |
| Glucose | Plasma glucose concentration (mg/dL) |
| BloodPressure | Diastolic blood pressure (mm Hg) |
| SkinThickness | Triceps skinfold thickness (mm) |
| Insulin | 2-hour serum insulin (µU/mL) |
| BMI | Body Mass Index (kg/m²) |
| DiabetesPedigreeFunction | Genetic risk score |
| Age | Age in years |
| Outcome | 0 = No Diabetes, 1 = Diabetes |

- **Class balance:** ~65% non-diabetic, ~35% diabetic

## Steps Performed
1. **Data Generation** — Realistic synthetic dataset with physiologically plausible distributions
2. **Exploratory Data Analysis** — Per-feature histograms split by class; descriptive statistics
3. **Correlation Heatmap** — Identifying multicollinearity and target-feature relationships
4. **Data Cleaning** — Replacing zero values (invalid for Glucose, BP, BMI, etc.) with NaN for proper imputation
5. **Feature Engineering** — Three composite features: `Glucose_BMI`, `Age_Preg`, `Insulin_Glucose`
6. **Train/Test Split** — 80/20 stratified split; median imputation and StandardScaler fitted only on training data (no data leakage)
7. **Model Training** — 5-fold stratified cross-validation on: Logistic Regression · Random Forest · Gradient Boosting · MLP
8. **Evaluation** — ROC curves, AUC scores, confusion matrix, and full classification report on test set
9. **Threshold Analysis** — Sensitivity, Specificity, Precision, and F1 plotted across thresholds 0.2–0.75 for clinical calibration
10. **Feature Importance** — Random Forest importances ranked and visualised

## Results
| Model | CV ROC-AUC | Test ROC-AUC | Test Accuracy |
|---|---|---|---|
| Logistic Regression | ~0.83 | ~0.84 | ~0.77 |
| Random Forest | ~0.86 | ~0.87 | ~0.80 |
| **Gradient Boosting** | **~0.87** | **~0.88** | **~0.81** |
| MLP Neural Net | ~0.85 | ~0.86 | ~0.79 |

**Key findings:**
- **Glucose** is the strongest single predictor of diabetes
- **BMI** and **Age** are the next most informative features
- At threshold 0.35 (clinical screening mode): Sensitivity ≈ 0.88, Specificity ≈ 0.74
- At threshold 0.50 (default): Sensitivity ≈ 0.78, Specificity ≈ 0.85

## Tools Used
- Python 3.10+
- NumPy, Pandas
- Scikit-learn (LogisticRegression, RandomForestClassifier, GradientBoostingClassifier, MLPClassifier, StandardScaler, SimpleImputer, StratifiedKFold)
- Matplotlib, Seaborn

## Conclusion
Gradient Boosting delivered the best ROC-AUC among all models evaluated. Feature engineering (composite biomarker interactions) improved model performance. The clinical threshold analysis reveals a fundamental trade-off: lowering the decision threshold catches more diabetic patients (higher Sensitivity) but increases false positives — a decision that must be driven by clinical cost considerations, not accuracy alone. Future enhancements include SHAP explainability, Bayesian hyperparameter tuning with Optuna, SMOTE for class imbalance, and deployment as a REST API.

## Author
ATHARVA H SAWANT

