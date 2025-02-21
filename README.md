# Predictive Maintenance using Machine Learning

## Overview

This project focuses on predictive maintenance to forecast machinery failures in manufacturing operations. The goal is to use machine learning techniques to predict potential failures, identify issues early, and enable proactive maintenance. By minimizing downtime, reducing maintenance costs, and optimizing operational efficiency, manufacturers can improve overall performance.

The project leverages sensor data from machines and employs a Random Forest model to predict machinery failures. It also explores imbalanced class handling and feature importance to better understand failure causes and enhance predictive accuracy.

### Problem Statement

Unplanned machinery failures often result in significant downtime, financial losses, and inefficiencies in manufacturing processes. Predictive maintenance aims to address this problem by forecasting potential machinery failures, allowing operators to perform timely maintenance and avoid unexpected breakdowns.

The project has two main tasks:

1. Binary Classification: Predict whether a machine will fail or not.
2. Multi-Class Classification: Identify the specific type of failure when it occurs.

### Data

The dataset used in this project includes historical sensor data for machinery, with features that capture key machine parameters over time. The data contains 10,000 records, and the key features are:

- Air Temperature [K]: Air temperature in Kelvin.
- Process Temperature [K]: Process temperature in Kelvin.
- Rotational Speed [rpm]: Rotational speed of the machinery.
- Torque [Nm]: Torque applied in Newton-meters.
- Tool Wear [min]: Tool wear time in minutes.
- Machine Type: Categorical variable (L, M, H).
- Product Quality: Quality rating (1 = Low, 2 = Medium, 3 = High).
- Product Serial: Unique identifier for the product.

#### Targets:

- Target: Binary variable indicating failure (1 = Failure, 0 = No Failure).
- Failure Type: Categorical variable indicating failure type (e.g., "Heat Dissipation Failure", "Tool Wear Failure").

### Solution Approach:

1. Data Preprocessing
- Data Cleaning: Removed irrelevant columns (e.g., Product ID), and encoded categorical features.
- Feature Scaling: Normalized continuous features to ensure uniform scaling across the dataset.
- Feature Selection: Selected relevant features that impact the prediction of failures, focusing on sensor readings and operational conditions.

2. Model Building

Binary Classification:
- SMOTE was used to handle class imbalance in the target variable.
- A Random Forest Classifier was trained to predict whether a machine will fail.
- The model was evaluated using metrics such as accuracy, precision, recall, F1-score, and ROC-AUC.

Multi-Class Classification:
- A separate Random Forest Classifier was used to classify the type of failure when it occurs.
- Class imbalance was addressed using class_weight='balanced'.
- Evaluation metrics include a classification report and confusion matrix.

### Evaluation Metrics

- Accuracy: Measures the percentage of correct predictions.
- Precision: Measures the accuracy of positive predictions.
- Recall: Measures the ability to identify all positive instances.
- F1-score: The harmonic mean of precision and recall for balanced evaluation.
- ROC-AUC: Measures the ability of the model to distinguish between failure and non-failure instances.

### Results

Binary Classification Model Evaluation:

- Accuracy: 97.9% ± 0.28%
- ROC-AUC: 0.9984 ± 0.0002
- Precision: 99%
- Recall: 97%
- F1-Score: High precision and recall indicate that the model correctly identifies non-failures with minimal false positives and false negatives.

Multi-Class Classification Model Evaluation:
- Classification Report: Provided detailed metrics for each class (failure type).
- Confusion Matrix: Visualized misclassifications and helped identify areas for model improvement.

### Key Findings

1. Model Performance:

The binary classification model performed excellently with high accuracy and ROC-AUC, effectively distinguishing between failures and non-failures. However, the multi-class model showed challenges with certain classes, especially those representing less frequent failure types (classes 4 and 5), where precision, recall, and F1-scores were very low.

2. Class Imbalance:

SMOTE successfully balanced the class distribution, improving the model's ability to learn from the minority class and improving recall, particularly for predicting machinery failures.

3. Feature Importance:

Features such as rotational speed, torque, and tool wear were identified as critical indicators of machinery failure. These features should be prioritized for monitoring to enable early detection of failures. However, temperature and tool wear exhibited minimal impact in the model, suggesting that further feature engineering or additional data may be needed for better predictive power.

### Future Work

1. Class Imbalance Handling: Consider additional techniques such as SMOTE or class weighting to improve model performance for underrepresented failure classes.

2. Model Optimization: Investigate ensemble learning techniques or other machine learning models to improve performance, especially in multi-class classification.

3. Feature Engineering: Additional domain-specific features or more granular data could enhance prediction accuracy for specific failure types.       

### Source

https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-classification
