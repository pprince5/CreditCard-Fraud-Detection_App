<h1>Report on Credit Card Fraud Detection Predictive Models</h1>
<h2>1. Introduction</h2>

The dataset utilized for this analysis contains transactions made by European cardholders in September 2013. It encompasses transactions over two days, totaling 284,807, among which 492 are fraudulent, representing 0.172% of the dataset. The features are anonymized and primarily consist of principal components derived from a PCA transformation. The dataset includes two untransformed features: 'Time' (elapsed seconds between transactions) and 'Amount' (transaction amount), along with the response variable 'Class' (1 indicates fraud, 0 otherwise).

<h2>2. Data Preprocessing and Exploration</h2>

Loading and Checking the Data: The dataset was loaded and examined for structure, revealing 31 columns. No missing values were found.
Data Imbalance: The dataset was highly imbalanced, with only 0.172% of transactions classified as fraudulent.
Exploratory Data Analysis (EDA):
Transactions were explored over time, showing that fraudulent transactions are more evenly distributed than legitimate ones.
Various statistical analyses of transaction amounts were conducted, revealing that fraudulent transactions generally involve lower amounts compared to legitimate ones.
Correlation analysis using a heatmap indicated weak correlations between the principal component features and the 'Amount' and 'Time' features.
<h2>3. Feature Engineering</h2>

Features used for model training were 'Time', 'Amount', and PCA components (V1 to V28). The target variable was 'Class'. The dataset was split into training, validation, and test sets with a ratio of 60:20:20.

<h2>4. Modeling Approaches</h2>

Five different machine learning models were implemented:

<h2>1. RandomForestClassifier:</h2>

Parameters: 100 estimators, Gini impurity as the criterion.
Results: Achieved an ROC-AUC score of 0.85. The most important features were V17, V12, V14, V10, V11, and V16.
<h2>2. AdaBoostClassifier:</h2>

Parameters: 100 estimators, SAMME.R algorithm, learning rate of 0.8.
Results: ROC-AUC score of 0.83, indicating slightly lower performance than the RandomForest model.
<h2>3. CatBoostClassifier:</h2>

Parameters: 500 iterations, learning rate of 0.02, depth of 12.
Results: ROC-AUC score of 0.86. The model efficiently handled categorical features and demonstrated robust performance.
<h2>4. XGBoost:</h2>

Parameters: Learning rate of 0.039, max depth of 2, subsample of 0.8.
Results: The model achieved a high validation ROC-AUC score of 0.984. The ROC-AUC score for the test set was 0.977, showcasing strong predictive capabilities.
<h2>5. LightGBM:</h2>

Parameters: Learning rate of 0.05, max depth of 4, and various other hyperparameters for controlling overfitting and regularization.
Results: Initial model validation ROC-AUC score was around 0.957. Cross-validation showed a final ROC-AUC score of 0.93, indicating a slightly lower performance compared to XGBoost.
<h2>5. Evaluation and Comparison</h2>

The models were evaluated primarily based on the ROC-AUC score. The XGBoost model outperformed others, achieving the highest ROC-AUC score on the validation set. LightGBM also showed strong performance, especially with cross-validation. RandomForest and CatBoost classifiers provided competitive results, whereas AdaBoost showed slightly lower predictive power.

<h1>6. Conclusion</h1>

The analysis demonstrated the effectiveness of advanced ensemble methods in detecting fraudulent transactions in highly imbalanced datasets. The XGBoost model was the most effective, followed closely by LightGBM. The results underline the importance of model selection and tuning in fraud detection scenarios.

Future work could explore the incorporation of additional features, advanced feature engineering techniques, and the implementation of more sophisticated imbalance handling methods. Additionally, deploying these models in a real-time system requires careful consideration of latency and computational efficiency.
