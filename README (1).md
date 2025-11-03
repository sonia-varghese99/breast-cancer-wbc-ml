# Wisconsin Breast Cancer (WDBC) — ML Benchmark

This repository benchmarks classical ML models on the curated **WDBC** dataset and checks whether model **feature importances** align with findings from the medical literature.

## 📌 Results (TL;DR)
- **Best model:** _TBD after running notebook_  
- **Metrics (5-fold stratified CV):** F1 = `X.XX ± X.XX`, AUROC = `X.XX ± X.XX`  
- **Top features (expected):** Clump Thickness, Bare Nuclei, Uniformity

> See `notebooks/01_wdbc_modeling.ipynb` for full workflow.

## 📂 Structure
```
breast-cancer-wdbc-ml/
├─ notebooks/01_wdbc_modeling.ipynb
├─ data/                # place curated CSV here (not committed)
├─ reports/figures/     # exported plots & tables
├─ requirements.txt
├─ LICENSE
└─ README.md
```
## Workflow

flowchart TD

A[🏁 Reproducibility & Environment Setup] --> B[📂 Data Loading & Initial Inspection]
B --> B1[Load dataset using pandas]
B --> B2[Inspect structure, data types, summary stats]
B --> B3[Visualize class distribution (benign vs malignant)]

B --> C[🧹 Data Pre-processing]
C --> C1[Check for missing values]
C --> C2[Generate correlation matrix]
C --> C3[Drop highly correlated features based on domain knowledge]
C --> C4[Standardize features and split into train/test sets]

C --> D[⚙️ Model Training & Evaluation]
D --> D1[Initialize models: kNN, LogReg, SVM, DT, RF, AdaBoost, GB]
D --> D2[Use StratifiedKFold (CV=5)]
D --> D3[Hyperparameter tuning via GridSearchCV]
D --> D4[Evaluate metrics: F1-score (malignant) & AUROC]
D --> D5[Rank models by mean AUROC & F1]

D --> E[📈 ROC Curves & Confusion Matrices]
E --> E1[Plot ROC curves for top models]
E --> E2[Visualize confusion matrices]
E --> E3[Interpret false positives & false negatives]

E --> F[🔍 Feature Importance Analysis]
F --> F1[Extract importances: .coef_ / .feature_importances_ / permutation]
F --> F2[Plot ranked feature importances]
F --> F3[Compare to medical literature (Bare Nuclei, Clump Thickness, etc.)]

F --> G[🏆 Selecting the Best Model]
G --> G1[Combine quantitative (F1, AUROC) and qualitative (interpretability) results]
G --> G2[Select Logistic Regression as final model]
G --> G3[Document justification & scientific consistency]

G --> H[✅ Final Results & Discussion]
H --> H1[Summarize workflow outcomes]
H --> H2[Highlight key insights & reproducibility]


## ▶️ Reproduce
```bash
python -m venv .venv && source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/01_wdbc_modeling.ipynb
```
- Put the curated CSV (e.g., `breast_cancer.csv`) into `data/` and set `DATA_PATH` in the notebook accordingly (default `../data/breast_cancer.csv`).

## 🧪 Methods
- Preprocessing: Missingness check; **drop one feature from any pair with |corr| ≥ 0.9**; scaling inside Pipelines.
- Models compared: kNN, Logistic Regression, SVM (RBF), Decision Tree, Random Forest, AdaBoost, Gradient Boosting.
- Model selection: **StratifiedKFold** CV with **GridSearchCV**; metrics: **F1** (malignant as positive), **AUROC**.
- Interpretability: Tree importances, Logistic coefficients (|coef|), and permutation importance for non-linear SVM.
- Literature alignment: Side-by-side table comparing top features with published findings.

## ⚖️ Ethics & Limitations
- Small dataset; no external validation set → risk of optimistic estimates.
- Feature importances can be unstable; prefer permutation-based checks and sensitivity analysis.
- This analysis is educational; not for clinical use.

## 📚 References
- Original dataset page: http://pages.cs.wisc.edu/~olvi/uwmp/cancer.html
- (Add your chosen clinical papers here.)

---
**Author:** Sonia Varghese
