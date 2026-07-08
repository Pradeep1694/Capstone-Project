# Load Data and Define Labels
Loaded the cleaned_data.csv dataset.
Created the feature matrix X.
Created two target variables:
y_reg for Regression (discounted_price)
y_clf for Classification (High/Low price)
Regression predicts the exact discounted price.
Classification predicts whether a product belongs to the Low Price (0) or High Price (1) category.

# Encode Categorical Columns
Removed unnecessary columns like IDs, links, and review text.
Applied One-Hot Encoding to the category column.
Machine learning models only work with numerical values. One-Hot Encoding converts categories into numbers without introducing an artificial order.

# Train-Test Split and Feature Scaling
Split the dataset into:
80% Training data
20% Testing data
Applied StandardScaler.
Training data is used to build the model, while testing data is used to evaluate it.
Scaling ensures all features are on the same scale, helping the model learn effectively.
The scaler was fitted only on the training data to prevent data leakage.

# Linear Regression
Trained a Linear Regression model.
Predicted discounted_price.
Evaluation Metrics
Mean Squared Error (MSE)
R² Score
Regression is used because discounted_price is a continuous numerical value.
Lower MSE and higher R² indicate better model performance.

# Ridge Regression
Trained a Ridge Regression model (alpha = 1.0).
Compared it with Linear Regression.
Ridge Regression uses L2 Regularization to reduce overfitting by shrinking large coefficients.
The model with the lower MSE and higher R² performs better.

# Logistic Regression
Converted discounted_price into two classes:
0 → Low Price
1 → High Price
Trained a Logistic Regression model.
Evaluation Metrics
Accuracy
Precision
Recall
F1-score
Confusion Matrix
ROC Curve
AUC
Classification is used because the target now consists of two categories instead of continuous values.

# Decision Threshold
Tested different thresholds:
0.3
0.4
0.5
0.6
0.7
Compared:
Precision
Recall
F1-score
Changing the threshold changes how strict the classifier is. The threshold with the highest F1-score provides the best balance between precision and recall.

# Regularization Experiment
Trained another Logistic Regression model with:
C = 0.01
Compared it with the default model (C = 1.0).
C controls the amount of regularization:
Smaller C → Stronger regularization
Larger C → Weaker regularization
Regularization helps reduce overfitting.

# Bootstrap Confidence Interval
Generated 500 bootstrap samples.
Calculated the AUC for each sample.
Computed the mean AUC and the 95% confidence interval.
Bootstrapping estimates how stable the model's performance is across different samples. A narrow confidence interval indicates more consistent performance.
