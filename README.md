# Melbourne-Rainfall-Prediction
This project focuses on building and evaluating machine learning models to predict daily rainfall in the Melbourne area of Australia. Utilizing historical weather data, the aim is to develop a robust predictive system that can forecast whether it will rain on a given day, providing valuable insights for planning and preparedness.
Methodology

The project follows a standard machine learning workflow, including data preprocessing, feature engineering, model training, and evaluation.

Data Preprocessing and Feature Engineering

1.
Handling Missing Values: Initial analysis revealed a significant number of missing values in features like Sunshine and Cloud cover. To maintain data integrity and model performance, rows with any missing values were dropped. This resulted in a reduced but clean dataset of approximately 56,000 entries.

2.
Location Filtering: To create a more localized and potentially more accurate prediction model, the dataset was filtered to include only observations from 'Melbourne', 'MelbourneAirport', and 'Watsonia', which are geographically close. This reduced the dataset to about 7,500 entries.

3.
Target Variable Renaming: The original RainToday and RainTomorrow columns were renamed to RainYesterday and RainToday respectively, to align with the prediction task of forecasting rain for the current day based on yesterday's conditions.

4.
Seasonality Feature: A Season feature was engineered from the Date column to capture seasonal weather patterns, which are crucial for rainfall prediction. The Date column was subsequently dropped.

5.
Data Imbalance: The target variable (RainToday) was found to be imbalanced, with approximately 76.3% 'No' (no rain) and 23.7% 'Yes' (rain). This imbalance was addressed during model training using techniques like class_weight='balanced' in Random Forest.

Model Training and Evaluation

Two classification models were trained and evaluated:

1.
Random Forest Classifier: A pipeline was constructed, combining StandardScaler for numerical features and OneHotEncoder for categorical features, followed by a RandomForestClassifier. GridSearchCV with StratifiedKFold cross-validation was used to optimize hyperparameters, ensuring robust evaluation on the imbalanced dataset.

2.
Logistic Regression: The pipeline was updated to use LogisticRegression as the classifier, and GridSearchCV was again employed to find the best hyperparameters for this model.

Results

Both models were evaluated based on accuracy, precision, recall, and F1-score, with a particular focus on the 'Yes' class (rain) due to the imbalanced nature of the dataset.

Random Forest Classifier Performance

•
Best Cross-Validation Score: 0.85

•
Test Set Score: 0.85

Class
Precision
Recall
F1-Score
Support
No
0.88
0.93
0.90
1154
Yes
0.72
0.58
0.64
358




Logistic Regression Performance

•
Test Set Score: 0.83

Class
Precision
Recall
F1-Score
Support
No
0.85
0.93
0.89
1154
Yes
0.69
0.49
0.57
358




Model Comparison

Metric
Random Forest
Logistic Regression
Accuracy
85%
83%
Rain Recall (Yes)
58%
49%
Rain Precision (Yes)
72%
69%
F1-Score (Yes)
64%
57%




Conclusion: The Random Forest Classifier generally outperformed Logistic Regression, particularly in terms of recall and F1-score for predicting rain, making it the preferred model for this task.

