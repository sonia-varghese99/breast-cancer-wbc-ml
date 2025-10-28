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
