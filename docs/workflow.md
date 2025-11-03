# WORKFLOW OF THE PROJECT 

This project follows a systematic machine learning workflow designed to identify the most suitable algorithm for classifying breast cancer cases using the **Wisconsin Breast Cancer Dataset**.
The workflow ensures scientific rigor, reproducibility, and interpretability. It aligns both computational performance and biological relevance.

## Overview

The analysis is divided into six main stages:

1. Reproducibility and Environment Setup
2. Data Loading and Initial Inspection
3. Data Pre-processing
4. Modelling, Hyperparameter Tuning, and Model Evaluation
5. Model Interpretation and Visualisation
6. Model Selection and Scientific Justification 

Each stage builds on the previous one, moving from data understanding to evidence-based model selection.

1. **Reproducibility and Environment Setup:**

Before beginning the analysis, a controlled environment is created to ensure that results are fully reproducible. This includes:

- Setting a fixed `RANDOM_STATE` across libraries (`numpy`, `random`, `os`, and scikit-learn).
- Installing and importing the required packages (e.g., `pandas`, `numpy`, `matplotlib`, `scikit-learn`, `seaborn`).
- Documenting the Python environment and library versions used.

This step guarantees consistent results each time the notebook is run.

2. **Data Loading and Initial Inspection**

**2A. Loading the Dataset:**

The curated version of the Wisconsin Breast Cancer dataset is loaded using `pandas`. Basic information such as the number of rows, columns, and feature data types is examined.

**2B. Initial Inspection:**

An overview of the dataset’s structure is generated with `data.info()` and `data.describe()` to check for anomalies, data ranges, and value distributions. The target variable (`Class`) is identified, with 2 representing benign and 4 representing malignant samples.

**2C. Visualising Class Distribution:**

A bar chart is used to visualise class balance. Since the dataset shows a moderate imbalance (≈65% benign, 35% malignant), stratified sampling is used in later evaluation to maintain proportional class representation.

3. **Data Pre-processing**

**3A. Checking for Missing Values:**

The dataset is inspected for missing entries. If present, an appropriate imputation strategy would be applied; otherwise, no imputation is needed.

**3B. Checking for Correlation:**

A correlation matrix and heatmap are created to identify highly correlated features (|r| ≥ 0.9).
High correlation can lead to redundant information and model instability.

**3C. Mitigating Correlation:**

Highly correlated features are handled by **dropping one of the correlated pairs**, guided by domain knowledge from literature. For instance, Uniformity of Cell Size was removed in favour of *Uniformity of Cell Shape*, which has stronger biological justification. After correlation mitigation, the cleaned feature matrix (`X_reduced`) is used for modeling.

4. **Modelling, Hyperparameter Tuning, and Model Evaluation:**

Multiple machine learning algorithms are trained and compared:

- k-Nearest Neighbours (kNN)
- Logistic Regression
- Support Vector Machine (SVM)
- Decision Tree (DT)
- Random Forest (RF)
- AdaBoost
- Gradient Boosting (GB)

Each model is wrapped in a pipeline with standard scaling and evaluated using 5-fold Stratified Cross-Validation to maintain balanced class representation.

**Model Tuning:**

- GridSearchCV is used for hyperparameter tuning. 
- Models are optimised using two metrics: F1-score (for malignant class) and AUCROC (for discrimination ability). 
- The best hyperparameter configuration is selected based on AUCROC.

**Model Evaluation:**

A consolidated results table is created summarising:

- Best hyperparameters 
- Mean and standard deviation of F1 and AUROC scores across folds (this allows objective ranking of model performance) 

5. **ROC Curves and Confusion Matrices:**

Top-performing models are further evaluated visually:

- ROC curves are plotted on a held-out test set to visualise the trade-off between sensitivity and specificity. 
- Confusion matrices show actual versus predicted classifications, providing insight into false positives and false negatives, which is especially critical in medical diagnostics.

These plots validate the models’ generalisation capability and help interpret performance beyond numerical metrics.

6. **Feature Importance Analysis:**

For each model, feature importances are computed and plotted using:

- `.feature_importances_` (for tree-based models),
- `.coef_` (for linear models), or
- permutation importance (for non-interpretable models).

The results are compared against medical literature, confirming whether the model’s decision process is biologically plausible. Consistent top features, such as Bare Nuclei, Clump Thickness, and Uniformity of Cell Shape, align strongly with known cytological indicators of malignancy.

7. **Selecting the Best Model:**

The final model is chosen using both:

- Performance metrics (F1 and AUROC)
- Feature interpretability and scientific validity

While both Random Forest and Logistic Regression performed exceptionally, Logistic Regression was selected as the best model because it offers:

- High accuracy and AUCROC
- Stable cross-validation performance
- Clear interpretability aligned with medical evidence

## Summary of Workflow

| Stage            | Goal                                 | Outcome                                      |
| ---------------- | ------------------------------------ | -------------------------------------------- |
| Data Loading     | Import and inspect data              | Understand dataset structure                 |
| Pre-processing   | Clean and decorrelate data           | Ready dataset for modeling                   |
| Modeling         | Train and tune multiple algorithms   | Obtain best-performing models                |
| Evaluation       | Measure and visualize performance    | Compare metrics and validate generalization  |
| Feature Analysis | Interpret feature influence          | Ensure biological alignment                  |
| Model Selection  | Combine metrics and interpretability | Select final scientifically consistent model |
