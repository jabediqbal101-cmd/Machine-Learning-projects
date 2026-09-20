# Student Performance Prediction Using Machine Learning

## 📌 Project Overview

This project focuses on predicting students' final academic performance using Machine Learning techniques. The target variable is **G3 (Final Grade)**, and the model uses academic, demographic, family, social, and behavioral factors such as **G1, G2, absences, study time, failures, age, family relationship, and other student-related attributes**.

The main objective is to build and compare different regression models and analyze which factors have the strongest influence on predicted student performance.

## 🎯 Objectives

* Predict students' final grades using Machine Learning.
* Compare multiple regression algorithms.
* Evaluate model performance using **MAE, RMSE, and R²**.
* Use **5-Fold Cross-Validation** to measure model stability.
* Perform hyperparameter tuning using **GridSearchCV**.
* Analyze feature importance.
* Apply **Permutation Importance** and **SHAP** for model explainability.
* Identify the most influential features affecting model predictions.

## 🛠️ Machine Learning Workflow

The project follows this workflow:

**Data → Preprocessing → Train/Test Split → Model Training → Hyperparameter Tuning → Cross-Validation → Model Comparison → Final Evaluation → Explainability → Results Analysis**

### Data Preprocessing

The dataset contains both numerical and categorical features.

* Categorical features were encoded using **One-Hot Encoding**.
* Numerical features were standardized using **StandardScaler**.
* A **ColumnTransformer** was used to manage both types of features.
* A **Pipeline** was used to combine preprocessing and model training.
* An 80/20 train-test split was used with `random_state=42`.

## 🤖 Models Evaluated

The following regression models were implemented and compared:

1. Linear Regression
2. Decision Tree Regressor
3. Random Forest Regressor
4. Gradient Boosting Regressor
5. XGBoost Regressor

## 📊 Model Comparison

Performance was evaluated using 5-Fold Cross-Validation.

| Model             | Mean MAE | Mean RMSE | Mean R² | R² Std |
| ----------------- | -------: | --------: | ------: | -----: |
| Linear Regression |    1.393 |     1.987 |   0.804 |  0.032 |
| Decision Tree     |    1.070 |     2.012 |   0.792 |  0.084 |
| Random Forest     |    0.957 |     1.499 |   0.890 |  0.034 |
| Gradient Boosting |    0.994 |     1.543 |   0.882 |  0.037 |
| XGBoost           |    0.973 |     1.519 |   0.886 |  0.035 |

The cross-validation results show that the ensemble tree-based models achieved strong predictive performance compared with the linear regression and single decision tree models.

## 🔍 Feature Importance

Feature importance analysis was performed to understand which variables contributed most to the Gradient Boosting model's predictions.

The most prominent features included:

* **G2 (Second-period grade)**
* **Absences**
* **G1 (First-period grade)**
* Reason for choosing the school
* Family relationship
* Age

The model showed particularly strong importance for **G2**, followed by **absences** and **G1**.

Feature importance indicates how the trained model uses features for prediction and should not be interpreted as proof of causation.

## 🔄 Permutation Importance

Permutation Importance was used to measure how model performance changes when individual features are randomly shuffled.

The analysis showed a similar pattern:

**G2 → Absences → G1 → Other features**

This provides an additional model-agnostic perspective on feature importance.

## 🧠 SHAP Explainability

**SHAP (SHapley Additive exPlanations)** was used to further understand the model's predictions.

SHAP analysis was used for both:

* **Global explainability** — understanding important features across the dataset.
* **Local explainability** — understanding how individual features contribute to a specific student's prediction.

The global SHAP analysis again identified **G2, absences, and G1** as the most influential features.

SHAP values indicate how features contribute to a model prediction and describe model behavior rather than causal relationships.

## 📈 Key Findings

* Ensemble tree-based models performed strongly on the student performance prediction task.
* Random Forest achieved the highest mean cross-validation R² among the evaluated models.
* G2 was consistently identified as the most influential feature across different explainability methods.
* Absences and G1 were also important predictors.
* Feature Importance, Permutation Importance, and SHAP produced broadly consistent importance patterns.
* Cross-validation provided a more robust assessment of model performance than relying on a single train-test split.

## ⚠️ Important Consideration

The variables **G1 and G2** represent earlier academic grades and are highly related to the final grade G3. Therefore, the usefulness of this model depends on the intended prediction stage.

For example, a model intended to identify students at an early stage would need to define whether G1 and G2 are available at the time of prediction.



## 📁 Project Structure

```text
Student-Performance-ML/
│
├── student-performance.ipynb
├── README.md
├── dataset/
└── results/
```

