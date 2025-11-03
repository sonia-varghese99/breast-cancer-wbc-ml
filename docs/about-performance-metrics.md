# MODEL EVALUATION AND EVALUATION METRICS 

## What is Model Evaluation? 

- Model evaluation refers to the process of analysing how well a machine learning model performs using various quantitative metrics. 
- It helps identify the model’s strengths, weaknesses, and overall ability to make correct predictions. 
- In essence, model evaluation ensures that the algorithm not only performs well on the training data but can also generalise effectively to unseen data. 

## Why is Model Evaluation Important? 

Evaluating a model is essential for confirming that it is reliable, generalisable, and accurate in real-world applications. Without proper evaluation, a model may appear successful during training but fail when exposed to new data.

Two common problems that evaluation helps detect are:

1. **Overfitting:** 
   - The model learns patterns and noise specific to the training data, losing the ability to generalise to new inputs. 
   - High training accuracy, poor test performance.

2. **Underfitting:** 
   - The model is too simple to capture the underlying patterns in the data. 
   - Poor performance on both training and test sets.

**Right Fit:** Achieved when the model balances bias and variance and both training and testing errors are minimal and stable. 

## Evaluation Metrics 

- Evaluation metrics are numerical measures used to quantify how well a model performs on a specific task. 
- They guide the selection, comparison, and tuning of algorithms. 
- The choice of metric depends on the type of problem - classification, regression, clustering, ranking, etc. 

### Classification Metrics: 

For classification problems (where the target variable is categorical), different metrics provide complementary insights into model behavior. This project utilises two such classification metrics - the F1 score and the AUCROC curve. However, other metrics are also available. They are explained in detail below. 

1. **Confusion Matrix:** 

A confusion matrix is a table that summarises the model’s predictions by comparing them to the true labels. It consists of four key values:

|                     | Predicted Positive  | Predicted Negative  |
| ------------------- | ------------------- | ------------------- |
| **Actual Positive** | True Positive (TP)  | False Negative (FN) |
| **Actual Negative** | False Positive (FP) | True Negative (TN)  |

It provides the foundation for most other classification metrics.

2. **Accuracy:** 

Accuracy is defined as the proportion of total correct predictions (both true positives and true negatives) out of all predictions.

Accuracy = (TP + TN) / (TP + TN + FP + FN) 

While intuitive, accuracy can be misleading for imbalanced datasets, as it may favour the majority class.

3. **Precision:** 

This metric measures how many of the samples predicted as positive are actually positive.

Precision = TP / (TP + FP)	​

High precision means the model makes few false-positive errors. In medical diagnosis, high precision ensures that when the model predicts cancer, it’s very likely correct.

4. **Recall (Sensitivity or True Positive Rate):** 

Recall measures how many of the actual positive cases are correctly identified.

Recall = TP / (TP + FN) 

High recall means the model catches most of the positive (malignant) cases, which is crucial in healthcare settings where false negatives are costly.

5. **F1 Score:** 

The F1 score is the harmonic mean of precision and recall, providing a single balanced measure of performance.

F1 = (2 x (Precision x Recall)) / (Precision + Recall) 

It is useful when there is an imbalance between classes, as it penalises extreme values in precision or recall.

6. **AUC-ROC Curve (Area Under the Receiver Operating Characteristic Curve):**

The ROC curve plots the True Positive Rate (Recall) against the False Positive Rate (1 − Specificity) across different probability thresholds. The AUC (Area Under Curve) quantifies the model’s ability to distinguish between classes:
- AUC = 1.0 -> Perfect classifier
- AUC = 0.5 -> Random guessing

A higher AUC indicates stronger separability between malignant and benign samples.

### Regression Metrics:  

1. Mean Squared Error (MSE)
2. Root Mean Squared Error (RMSE)
3. Mean Absolute Error (MAE)
4. R2 (Adjusted-R)