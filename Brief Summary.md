## Data Issues & Fixes

- Checked for class imbalance; used stratified train-test split to preserve class proportions.
- Removed the target column (high_risk) from features before training to prevent data leakage.
- Encoded categorical columns (if any) using label encoding for compatibility with RandomForestClassifier.

## Model + Metric Choice

- Chose Random Forest Classifier for its robustness, interpretability, and ability to capture nonlinear relationships.
- Used ROC-AUC (for ranking/class separation) and F1-score (for imbalanced classification) as key metrics.
- Applied 5-fold cross-validation to ensure stable and unbiased performance estimation.

## Key Drivers of Risk

- Top features identified through feature importance plots (from the trained model).
- These variables represent the most influential predictors of high_risk individuals — likely reflecting financial behavior, repayment history, or demographic variables.
- Helps stakeholders understand actionable risk factors and prioritize interventions.

## Scaling to Production

- Wrap training and inference logic in reusable Python scripts or a pipeline (e.g., train.py and predict.py).
- Persist trained model using joblib or pickle for deployment.
- Integrate model serving with APIs (e.g., FastAPI, Flask) and automate retraining using scheduled pipelines (Airflow or MLflow).
- Monitor drift and performance metrics continuously on new data to retrain when degradation occurs.
