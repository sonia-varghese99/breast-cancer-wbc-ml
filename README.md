# BENCHMARKING MACHINE LEARNING (ML) MODELS WITH WISCONSIN BREAST CANCER (WBC) DATA 

This repository benchmarks classical ML models on the curated WBC dataset and checks whether model feature importances align with findings from medical literature. 

A brief description of the project workflow can be accessed here: [Project Workflow](../docs/workflow.md) 

## STRUCTURE 

![Structure](reports/figures/structure.png)

breast-cancer-wbc-ml/
│
├── data/                        # Dataset
│   └── breast-cancer.csv
│
├── docs/                        # Documentation
│   ├── about-dataset.md
│   ├── about-ml-algorithms.md
│   ├── about-performance-metrics.md
│   └── workflow.md
│
├── notebooks/                   # Jupyter notebooks
│   └── wbc-modelling.ipynb
│
├── reports/
│   ├── figures/                 # Plots (ROC curves, confusion matrices, etc.)
│   └── model_results.csv
│
├── src/                         # (optional future expansion)
├── tests/                       # (optional)
│
├── requirements.txt             # Python dependencies
├── pyproject.toml / pdm.lock    # PDM environment files
├── LICENSE
└── README.md

## REPRODUCIBILITY

You can clone the repository with: 
```bash
gh repo clone sonia-varghese99/breast-cancer-wbc-ml
cd breast-cancer-wbc-ml
``` 

For creating a virtual environment, you have two options: 

1. **Using PDM (recommended):** 
```bash 
# Install dependencies
pdm install

# Activate environment
pdm run jupyter lab
``` 

2. **Using pip and venv:** 
```bash
# Create a virtual environment
python -m venv .venv

# Activate it:
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

Please note: 
- All random states are fixed (RANDOM_STATE = 42) to ensure consistent results. 
- The environment is fully specified in requirements.txt and pyproject.toml. 
- The curated dataset (breast-cancer.csv) is included under /data.
  
## PROJECT OBJECTIVE

To evaluate multiple machine learning algorithms and select the best model based on:

1. Predictive performance 
   - F1-score (malignant class focus)
   - AUCROC 
2. Feature interpretability aligned with medical literature

## METHODS 

1. Data preprocessing: 
   - Missingness check
   - Checking for correlation 
   - Mitigating correlation by dropping one feature from any pair with |corr| ≥ 0.9
   - Scaling inside Pipelines
2. ML models compared: 
   - k-Nearest Neighbours (kNN)
   - Logistic Regression
   - Support Vector Machine (SVM)
   - Decision Tree
   - Random Forest
   - AdaBoost
   - Gradient Boosting
3. Model selection: StratifiedKFold Cross Validation with GridSearchCV 
4. Model evaluation with metrics: F1 score (malignant as positive) and AUCROC
5. Interpretability: Tree importances, Logistic coefficients (|coef|), and permutation importance for non-linear SVM 
6. Literature alignment  

## RESULTS 

- **Best model:** Logistic Regression was chosen as final model due to interpretability and alignment with medical literature. 
- **Metrics (5-fold stratified CV) (approximate values):** F1 (mean) = 0.957, AUCROC (mean) = 0.996 (best AUCROC)   
- **Top features:** Bare Nuclei, Clump Thickness, and Uniformity of Cell Shape 

## SUMMARY 

This project focuses on building and evaluating ML models for breast cancer diagnosis using the Wisconsin Breast Cancer Dataset. The primary goal is to identify the most accurate and scientifically interpretable algorithm for classifying tumours as benign or malignant based on Fine Needle Aspiration (FNA) cytological features.

The workflow follows a complete data science pipeline, from data preprocessing and feature correlation mitigation to model comparison, evaluation, and interpretability analysis.

Seven supervised learning algorithms were implemented and tuned using GridSearchCV and Stratified 5-Fold Cross-Validation:
1. k-Nearest Neighbours (kNN)
2. Logistic Regression
3. Support Vector Machine (SVM)
4. Decision Tree
5. Random Forest
6. AdaBoost
7. Gradient Boosting

Performance was evaluated using the F1-score (focused on malignant detection) and the Area Under the ROC Curve (AUCROC). 

Among all models, Logistic Regression and Random Forest achieved the best balance of accuracy and stability.

Feature importance analysis confirmed that the models relied on biologically relevant features such as Bare Nuclei, Clump Thickness, and Uniformity of Cell Shape, consistent with findings from medical literature.

The final selection of Logistic Regression was based on its:
- Strong generalisation (F1 ≈ 0.96, AUROC ≈ 0.996) 
- Simplicity and interpretability 
- Alignment with medical evidence

Overall, this project demonstrates a scientifically grounded, interpretable, and reproducible machine learning workflow for biomedical classification tasks.

## ETHICS 

1. **AI Assistance Disclosure:** Parts of this project’s code structure, documentation, and explanatory text were generated with the assistance of ChatGPT (GPT-5, OpenAI). The tool was used to support clarity, structure, and consistency in documentation and code commentary. 
2. **Bias and Fairness:** The dataset represents a limited demographic and sample source (University of Wisconsin Hospital). Models trained on such data may not generalise across populations with different genetic, demographic, or environmental characteristics. 
3. **Reproducibility:** All code, preprocessing steps, and hyperparameters are documented to support reproducibility and transparency. 

## LIMITATIONS

1. **Dataset Scope:** The dataset is relatively small (683 samples), which limits its representativeness and real-world applicability. 
2. **Lack of External Validation:** The models were evaluated only on internal cross-validation and a single hold-out test split; no external dataset was used to verify generalisability. 
3. **Class Imbalance:** Although moderate, the imbalance between benign and malignant cases can still bias some metrics like accuracy; hence, F1 and AUCROC were prioritised.
4. **Limited Model Scope:** Deep learning or hybrid models were not explored; future work could include image-based CNN approaches using the full digital cytology images. 
5. **Clinical Integration Challenges:** Translating these models into practice requires clinical validation, calibration, and regulatory approval before deployment in diagnostic workflows.

## FUTURE IMPROVEMENTS 

1. SHAP value interpretability
2. Include WDBC (Diagnostic) dataset comparison 

## REFERENCES 

- Machine Learning for cancer diagnosis and Prognosis. (n.d.). https://pages.cs.wisc.edu/%7Eolvi/uwmp/cancer.html
- Wolberg, W. (1990). Breast Cancer Wisconsin (Original) [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5HP4Z. 
- Brownlee, J. (2020, January 14). A gentle introduction to imbalanced classification. MachineLearningMastery.com. https://machinelearningmastery.com/what-is-imbalanced-classification/ 
- Agarap, A. F. M. (2018). On Breast Cancer Detection: An application of machine learning algorithms on the Wisconsin Diagnostic Dataset. ICMLSC ’18: Proceedings of the 2nd International Conference on Machine Learning and Soft Computing, 5–9. https://doi.org/10.1145/3184066.3184080 
- Brownlee, J. (2020b, July 30). How to fix K-Fold Cross-Validation for imbalanced classification. MachineLearningMastery.com. https://machinelearningmastery.com/cross-validation-for-imbalanced-classification/ 
- Brownlee, J. (2020c, September 18). Hyperparameter optimization with random search and grid search. MachineLearningMastery.com. https://machinelearningmastery.com/hyperparameter-optimization-with-random-search-and-grid-search/ 
- Kavyasrirelangi. (2024, June 29). Understanding Model Evaluation Metrics for Machine Learning. Medium. https://medium.com/@kavyasrirelangi100/understanding-model-evaluation-metrics-for-machine-learning-160d385b72c5 
- Han, R. (2023). Breast cancer prediction and feature importance estimation leveraging logistic regression model. Applied and Computational Engineering, 17(1), 163–168. https://doi.org/10.54254/2755-2721/17/20230929 
- Khater, T., Hussain, A., Bendardaf, R., Talaat, I. M., Tawfik, H., Ansari, S., & Mahmoud, S. (2023). An explainable artificial intelligence model for the classification of breast cancer. IEEE Access, 13, 5618–5633. https://doi.org/10.1109/access.2023.3308446 

## LICENCE

MIT Licence 

## CONTACT 

Sonia Varghese: sonia.r.varg@gmail.com (Constructive criticism is always appreciated!)

## ACKNOWLEDGEMENTS 

This project was completed as part of the 'Introduction to Machine Learning Tutorial 2024' course (an elective course part of the MSc Life Science Informatics program at the University of Bonn). 

I would like to thank Dr. Alexandra Reitelmann (course instructor) for her constant guidance and technical support. 

I would also like to express my appreciation and gratefulness towards the University of Wisconsin research team (and other such institutes) for making the UCI Machine Learning Repository publicly accessible, which supports gaining hands-on experience with biomedical data. 

Please note that creation of certain sections of the code and their explanations, as well as the documentation was assisted by ChatGPT (GPT-5, OpenAI, 2025). I have reviewed and verified the outputs to the best of my abilities. 