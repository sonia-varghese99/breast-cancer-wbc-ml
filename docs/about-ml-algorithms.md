# A BRIEF EXPLANATION OF THE MACHINE LEARNING ALGORITHMS 

This project compares seven supervised machine learning algorithms for classifying breast cancer samples as benign or malignant. Each algorithm follows a different principle for learning decision boundaries and interpreting the data. 

1. **k-Nearest Neighbours (kNN):** 

- A simple, non-parametric algorithm that classifies a sample based on the majority class of its k closest neighbours in the feature space. 
- It relies on distance metrics (e.g., Euclidean distance) to determine similarity. 
- Advantages: Easy to implement, no training phase. 
- Limitations: Sensitive to feature scaling and the choice of k; computationally expensive for large datasets.

2. **Logistic Regression (LogReg):** 

- A linear model that estimates the probability of a sample belonging to a particular class using the logistic (sigmoid) function. 
- It models a linear relationship between input features and the log-odds of the target class. 
- Advantages: Highly interpretable, efficient, provides feature importance via coefficients. 
- Limitations: Assumes linear separability and is sensitive to multicollinearity.

3. **Support Vector Machine (SVM):** 
  
- Finds the optimal hyperplane that maximises the margin between different classes in the feature space. 
- It can use kernel functions (e.g., RBF, polynomial) to handle non-linear decision boundaries. 
- Advantages: Effective in high-dimensional spaces, robust to overfitting. 
- Limitations: Choice of kernel and parameters (C, gamma) greatly affect performance; slower on large datasets.

4. **Decision Tree (DT):** 

- A tree-structured model that splits the data recursively based on the most informative features, forming a hierarchy of decisions. 
- Each internal node represents a condition on a feature, and each leaf node represents a class label. 
- Advantages: Easy to interpret, handles non-linear relationships, requires little data preprocessing. 
- Limitations: Prone to overfitting; small changes in data can alter the tree structure.

5. **Random Forest (RF):** 

- An ensemble method that combines multiple decision trees trained on random subsets of the data and features. 
- Predictions are made by aggregating (voting or averaging) the outputs of all trees. 
- Advantages: Reduces overfitting, handles high-dimensional data well, provides reliable feature importances. 
- Limitations: Less interpretable than a single tree; can be slower with many trees.

6. **AdaBoost:** 

- Short for Adaptive Boosting. 
- It builds a sequence of weak learners (typically shallow trees), each focusing on correcting the errors of the previous one. 
- Weights are updated after each iteration so that misclassified samples get more emphasis. 
- Advantages: Often improves the performance of weak classifiers, effective on simple datasets. 
- Limitations: Sensitive to noisy data and outliers; performance depends on learning rate and number of estimators.

7. **Gradient Boosting (GB):** 

- Another boosting ensemble, but unlike AdaBoost, it minimises prediction error by fitting each new model to the residual errors of the previous ensemble using gradient descent. 
- Advantages: High predictive power, handles complex non-linear relationships, supports fine-tuning. 
- Limitations: More computationally expensive; prone to overfitting if not properly regularised.

## Summary: 

| Algorithm           | Type                | Key Strength               | Key Limitation                            |
| ------------------- | ------------------- | -------------------------- | ----------------------------------------- |
| kNN                 | Instance-based      | Simple and intuitive       | Sensitive to scaling, slow for large data |
| Logistic Regression | Linear              | Interpretable coefficients | Limited to linear relationships           |
| SVM                 | Margin-based        | Strong in high dimensions  | Sensitive to kernel parameters            |
| Decision Tree       | Tree-based          | Easy to interpret          | Overfits easily                           |
| Random Forest       | Ensemble (Bagging)  | Robust and accurate        | Less interpretable                        |
| AdaBoost            | Ensemble (Boosting) | Focuses on hard examples   | Sensitive to noise                        |
| Gradient Boosting   | Ensemble (Boosting) | High accuracy, flexible    | Slower and tunable                        |