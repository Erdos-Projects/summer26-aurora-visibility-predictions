# KPIs for the Aurora Prediction Model

The combination of these metrics help us understand how well the model predicts aurora visibility.

1. F1-Score: The harmonic mean of precision and recall. It balances the trade-off between catching real auroras and avoiding false alarms. A high F1-score indicates good overall performance.
2. Recall: When there is an aurora, how often does the model correctly predict it? This shows how many real auroras we are missing.
3. Precision: When the model predicts an aurora, how often is it correct? This shows how many false alarms we have.
4. ROC-AUC: Measures the model's ability to distinguish between aurora and no aurora across all classification thresholds. A higher AUC indicates better overall discrimination.
