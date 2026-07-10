# Decision Tree Baseline
Train a Decision Tree classifier using the default parameters and evaluate its performance.
A Decision Tree is a supervised learning algorithm used for classification. It splits the data into smaller groups based on feature values until it reaches a prediction. The model was trained with default settings and evaluated using training and test accuracy.
Observation
If the training accuracy is much higher than the test accuracy, the model is overfitting because it has learned the training data too closely and performs worse on unseen data.

# Controlled Decision Tree
Reduce overfitting by limiting the tree size.
The Decision Tree was trained with:
max_depth = 5 to limit the depth of the tree.
min_samples_split = 20 to require at least 20 samples before splitting a node.
These parameters help improve the model's ability to generalize to new data.
The controlled tree usually has lower training accuracy but better generalization compared to the baseline model.

# Gini vs Entropy
Compare two splitting criteria used in Decision Trees.
Gini Impurity measures how mixed the classes are in a node. A Gini value of 0 means the node is completely pure.
Entropy measures the uncertainty in a node. An Entropy value of 0 also means the node is completely pure.
Both criteria produced very similar results. In this dataset, Entropy achieved slightly higher accuracy than Gini, but the difference was very small.

# Random Forest and Gradient Boosting
Train ensemble learning models and compare their performance.
Random Forest builds many Decision Trees independently and combines their predictions.
Gradient Boosting builds Decision Trees one after another, where each new tree corrects the mistakes made by the previous trees.
The models were evaluated using Accuracy and ROC-AUC.
Both ensemble models generally perform better than a single Decision Tree because they reduce prediction errors and improve overall accuracy.

# Feature Ablation
Study the importance of features.
Feature importance from the Random Forest model was used to identify the least important features. These features were removed, and the model was trained again.
The ROC-AUC scores of the full and reduced models were compared to determine whether removing less important features affected model performance.

# Cross Validation
Evaluate model performance using multiple train-test splits.
Five-fold Stratified Cross Validation was used to evaluate each model. The dataset was divided into five parts, and each part was used once as the validation set.
Cross Validation provides a more reliable estimate of model performance than a single train-test split because every sample is used for both training and testing.

# GridSearchCV
Find the best Random Forest hyperparameters.
# GridSearchCV tested different combinations
Number of trees (n_estimators)
Maximum tree depth (max_depth)
Minimum samples per leaf (min_samples_leaf)
The combination with the highest average ROC-AUC score was selected.
GridSearchCV automatically identified the best-performing hyperparameters, resulting in an optimized Random Forest model.

# Learning Curve
Analyze model performance with different training data sizes.
The model was trained using 20%, 40%, 60%, 80%, and 100% of the training data. Training AUC and Test AUC were recorded for each case.
As the amount of training data increased, the model generally became more stable and the test performance improved, showing that additional training data helps the model generalize better.

# Save and Load Model
Save the trained model for future use.
The best trained model was saved using the joblib library as best_model.pkl. The saved model was then loaded and used to predict new samples.
The model was successfully saved and reloaded, allowing it to be reused without retraining.

# Final Comparison Table

Model                  Test AUC     CV Mean AUC       CV Std
Logistic Regression    0.9398         0.9398          0.0096
Decision Tree          0.9898         0.9691          0.0165
Random Forest          0.9952         0.9905          0.0037
Gradient Boosting      0.9997         0.9988          0.0007

Compare the performance of all classification models and identify the best-performing model.
The models were evaluated using Test ROC-AUC, Cross-Validation Mean ROC-AUC, and Cross-Validation Standard Deviation. Test ROC-AUC measures how well a model distinguishes between the two classes. Cross-Validation Mean ROC-AUC provides the average performance across five folds, while the Standard Deviation indicates the consistency of the model across different data splits.
Final Recommendation
Among all the models, Gradient Boosting achieved the best overall performance. It obtained the highest Test ROC-AUC (0.9997) and the highest Cross-Validation Mean ROC-AUC (0.9988) with the lowest Standard Deviation (0.0007). This indicates that the model is both highly accurate and consistent. Therefore, Gradient Boosting is selected as the final model for this classification task because it provides the best balance of accuracy, robustness, and generalization to unseen data.
