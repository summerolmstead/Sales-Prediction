# Sales-Prediction

Overview of Sales Forecasting Code
Daily aggregation of sales data (sum of prices, quantities, and count of orders)
Time-based feature extraction from dates (day, month, weekday, weekend flags)

Statistical Methods & Feature Engineering
Lag Features: Creates features that look back in time (1, 7, and 14 days) to capture temporal patterns. This helps the model learn from previous sales values.
Rolling Statistics: Implements moving averages over 7 and 14-day windows, capturing medium-term trends and smoothing out daily fluctuations.
Cyclical Encoding: Transforms cyclical time variables (month, weekday) into sine and cosine components, helping the model understand seasonality patterns without treating them as linear variables.
Weekday Averages: Captures day-of-week sales patterns by including the average historical sales for each weekday.

Model
XGBoost Regressor: An advanced implementation of gradient boosted trees that excels at capturing complex, non-linear relationships in data.
Key parameters:
n_estimators=500: Uses 500 decision trees for ensemble learning
max_depth=5: Limits each tree to 5 levels to prevent overfitting
learning_rate=0.05: Controls how quickly the model adapts to the error
subsample=0.9: Uses 90% of data for each tree, improving generalization
colsample_bytree=0.8: Uses 80% of features for each tree, reducing overfitting

Evaluation Metrics
MAE (Mean Absolute Error): Average absolute difference between predictions and actual values
RMSE (Root Mean Squared Error): Square root of the average squared differences
R² (R-squared): Proportion of variance explained by the model
MAPE (Mean Absolute Percentage Error): Average percentage difference between predictions and actual values

Forecasting Approach
Walk-forward Validation: Generates predictions one day at a time, updating the model's inputs with each new prediction
Iterative Forecasting: Updates lag features and rolling statistics after each prediction to maintain forecast accuracy over longer horizons
Confidence Intervals: Creates 95% confidence bands around predictions based on the model's historical error (MAE)

Key Advantages
Feature-rich approach: Combines multiple statistical signals (time patterns, trends, seasonality)
Non-linear modeling: Captures complex relationships in sales data
Recursive multi-step forecasting: Maintains accuracy over the 30-day forecast window
Uncertainty quantification: Provides confidence intervals, not just point estimates

This approach balances sophistication with interpretability, making it suitable for business forecasting applications where understanding the model's behavior is as important as its accuracy.
