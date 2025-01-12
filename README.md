# Predictive Maintenance using Machine Learning

## Overview

This project focuses on predictive maintenance to forecast machinery failures in manufacturing operations. By leveraging machine learning techniques, the goal is to predict machinery failures, identify potential issues early, and enable proactive maintenance. This will help manufacturers minimize downtime, reduce maintenance costs, and optimize the overall efficiency of operations.

The project uses sensor data from machines to predict when maintenance is required. The Random Forest model implemented here serves as a key tool for forecasting machine failures and understanding the causes behind them.

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

The binary classification model performed excellently with high accuracy and ROC-AUC, making it very effective at distinguishing between failures and non-failures. However, the multi-class classification showed some false positives and missed a few failures, indicating areas for improvement.

2. Class Imbalance:

Using SMOTE for balancing the class distribution helped the model better learn the minority class and improved recall.

3. Feature Importance:

Features like rotational speed, torque, and tool wear were identified as critical indicators of machinery failure, helping prioritize monitoring these factors for early detection.

### Future Directions

1. Deep Learning Models: Explore neural networks for improved failure prediction accuracy, especially for more complex patterns in the sensor data.

2. Time Series Modeling: Incorporate temporal dependencies in the sensor data to capture trends and improve predictive maintenance accuracy.

3. Real-Time Monitoring: Develop a real-time monitoring system that uses the model's predictions to trigger maintenance alerts and optimize resource allocation.

4. Failure Severity Prediction: Extend the model to predict not only whether a failure will occur but also its severity, enabling more precise maintenance scheduling.        

### Source

https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-classification
