# Predicting User Churn in Waze Data using Regression and Machine Learning Models
This project was completed as part of the [Google Advance Data Analytics Professional Certificate](https://www.coursera.org/professional-certificates/google-advanced-data-analytics).
This repository is a work-in-progress, as I am cleaning up notebooks and images.

## Overview
The goal of this project was to increase the overall growth of the company by preventing monthly user churn on the Waze app. Churn quantifies the number of users who have uninstalled the Waze app or stopped using the app. Ultimately, the final goal was to develop a machine-learning (ML) model that predicts user churn. To obtain a model with the highest predictive power, two different models were developed to cross-compare results: random forest and XGBoost. This project utilized synthetic data created in partnership with Waze, consisting of engagement metrics and driving behaviours of individual users in the previous month. The final random forest model performed with a recall of 12%, while the XGboost model boasted a recall of 17%, nearly double the performance of a previous logistic regression model and 50% better than the random forest model. This modeling effort shows that the data is insufficient in predicting user churn consistently. However, the effort was not in vain, as we have identified a critical need for additional metrics and information that Waze can collect, such as drive-level information, granular data on app-user interactions, and monthly counts of unique start/end locations for each user. 

## Data Understanding
The dataset captures various user engagement metrics and driving behaviors for an app, including the binary classification of whether a user churned or retained, the number of sessions and drives during the month, device type, days since onboarding, navigations to favorite locations, kilometers driven, and activity or driving days. The bar chart below shows the breakdown of how many users were churned or retained.

[churned vs retained chart]

## Modeling and Evaluation
The data was split into training, validation, and test sets. A grid search was performed to determine the optimal model hyperparameters. The final model was an XGBoost model consisting of 300 decision trees. The plots below show the model's confusion matrix and feature importance. The confusion matrix shows that the model predicted three times as many false negatives (users who churned who were not identified as churned) as it did false positives (users who were retained but were identified as churning), and it only correctly identified 16.6% of the users who churned. The XGBoost model made more use of many of the features than a previous logistic regression model did. Three of the top five features were engineered (`km_per_hour`, `percent_sessions_in_last_month`, `total_sessions_per_day`), demonstrating that feature engineering is effective in boosting model performance. The model performed with an accuracy score of 0.81 and a recall score of 0.17. 

[confusion matrix]

[feature importance]

## Conclusion
The final XGBoost model is not a strong predictor of user churn, as evidenced by its poor recall score (0.17). However, this model can still be used to guide further exploratory efforts. New features can be engineered in an attempt to generate better predictive signals. More importantly, there is a critical need for additional data to more accurately predict user churn. Such data could include drive-level information (such as drive times, geographic locations, etc.), along with more granular data to know how users interact with the app (e.g. how often do they report or confirm road hazard alerts?), the monthly count of unique start/end locations. While this effort did not result in a strong user churn predictor, valuable insights regarding data collection were obtained, which can be used in further iterations of this project. 
