# Student Life AI Analysis
### Project Overview

This project explores student session data to analyze behaviors, outcomes, and satisfaction levels. Machine learning techniques were applied to predict whether a student would use the system again (UsedAgain) and to evaluate different algorithms. The process followed a structured 40-step workflow that included data preprocessing, feature engineering, visualization, model training, hyperparameter tuning, and model comparison.

### Step-by-Step Workflow
#### 1–5: Dataset Exploration

The dataset was loaded and inspected to understand its structure.

Data types of each column were checked to distinguish categorical, numerical, and datetime features.

Missing values were identified; the dataset contained minimal missingness that did not significantly affect model training.

Summary statistics for numerical variables were explored, showing variations in session lengths and satisfaction ratings.

Categorical variables were examined to review unique values, with most categories being imbalanced (e.g., FinalOutcome).

#### 6–10: Feature Engineering

The SessionDate column was decomposed into Year, Month, and Day features, improving temporal analysis.

A new feature PromptsPerMinute was created by dividing total prompts by session length, revealing variability in engagement levels.

Session length was categorized into Short, Medium, and Long ranges, highlighting that most sessions fell into the short category.

Categorical columns such as StudentLevel, Discipline, TaskType, and FinalOutcome were encoded for modeling.

Unnecessary identifiers and raw datetime columns (e.g., SessionID, SessionDate) were dropped to avoid noise in models.

#### 11–15: Data Preparation

The target variable was defined as UsedAgain.

The dataset was split into training and testing sets (80/20).

Numerical features were scaled/normalized where necessary.

Categorical features were properly encoded to ensure compatibility across models.

The final feature set included both engineered and original features relevant for prediction.

#### 16–20: Initial Modeling

Logistic Regression was trained as a baseline model, providing moderate accuracy but limited handling of categorical complexity.

A Decision Tree Classifier was trained, which overfit slightly on training data and generalized poorly.

A Random Forest Classifier was trained, showing strong performance compared to simpler models.

A Naive Bayes classifier was applied but performed poorly due to independence assumptions.

K-Nearest Neighbors (KNN) was trained but showed low accuracy and sensitivity to feature scaling.

#### 21–25: Advanced Modeling

A Gradient Boosting Classifier was trained and performed competitively with Random Forest.

An XGBoost Classifier was trained, but it severely underperformed, particularly struggling with minority classes.

Baseline model accuracies were compared, showing Random Forest and Gradient Boosting as leaders.

Classification reports revealed class imbalance: minority classes (e.g., FinalOutcome = 2, 3) had near-zero recall and precision.

Confusion matrices confirmed that models consistently predicted majority classes more reliably than minority ones.

#### 26–30: Hyperparameter Tuning

Logistic Regression was tuned with class weights, improving balance slightly but not accuracy.

Decision Tree parameters (max_depth, criterion) were tuned, reducing overfitting but not boosting accuracy significantly.

Random Forest hyperparameters (n_estimators, max_depth) were tuned, yielding the best model performance overall.

Gradient Boosting hyperparameters were adjusted, producing strong but slower results compared to Random Forest.

XGBoost parameters were tuned, but accuracy remained poor, suggesting the dataset was not well-suited to this model.

#### 31–35: Model Evaluation

Accuracy was calculated for each tuned model, with Random Forest achieving the highest.

Classification reports showed that Logistic Regression remained interpretable but lacked predictive strength.

Precision, recall, and f1-scores highlighted poor recognition of minority classes across all models.

Confusion matrices indicated that most misclassifications occurred in less frequent categories.

Models such as Naive Bayes and KNN consistently performed poorly and were not suitable for deployment.

#### 36–40: Final Comparison & Insights

A comparison table was created summarizing model accuracies and classification metrics.

Random Forest and Gradient Boosting were identified as strong candidates.

Logistic Regression was found to be a useful baseline but not competitive in predictive power.

XGBoost significantly underperformed, with accuracy around 22%, and provided almost no predictions for minority classes.

The final conclusion was that Random Forest with tuned hyperparameters provided the best trade-off between accuracy, interpretability, and stability for predicting UsedAgain.