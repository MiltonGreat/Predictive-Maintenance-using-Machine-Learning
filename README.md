# Predictive-Maintenance-using-Machine-Learning

### Project Overview

This project focuses on predictive maintenance using machine learning to forecast machinery failures based on historical sensor data. By predicting failures, manufacturers can implement proactive maintenance, reduce downtime, and optimize operational efficiency. 

The project involves two tasks:

- Binary Classification: Predict whether a machine will fail.
- Multi-Class Classification: Identify the specific type of failure when it occurs.

### Dataset Description

The dataset contains 10,000 records with the following features:

Features:
- Air temperature [K]: Air temperature in Kelvin.
- Process temperature [K]: Process temperature in Kelvin.
- Rotational speed [rpm]: Rotational speed of the machinery.
- Torque [Nm]: Torque applied in Newton-meters.
- Tool wear [min]: Tool wear time in minutes.
- Type: One-hot encoded categorical variable representing machine type (L, M, H).
- product_quality: Extracted product quality (1 = Low, 2 = Medium, 3 = High).
- product_serial: Unique serial number of the product.

Targets:
- Target: Binary variable indicating failure (1 = Failure, 0 = No Failure).
- Failure Type: Categorical variable indicating failure type (e.g., "Heat Dissipation Failure", "Tool Wear Failure").

### Project Workflow

Data Preparation and Exploration:
- Cleaned dataset by handling irrelevant columns (UDI, Product ID) and encoding categorical features.
- Normalized continuous features to ensure uniform scaling.
- Visualized feature distributions, class imbalance, and correlations.

Feature Engineering:
- One-hot encoded Type and extracted numerical features (product_quality, product_serial) from Product ID.
- Normalized all continuous features for consistent scaling.

Binary Classification:
- Handled class imbalance in the Target variable using SMOTE.
- Trained a Random Forest Classifier with hyperparameter tuning to predict binary failures.
- Evaluated the model using metrics such as accuracy, precision, recall, F1-score, and ROC-AUC.

Multi-Class Classification:
- Developed a separate model to classify failure types using a Random Forest Classifier.
- Addressed class imbalance in multi-class data with class_weight='balanced'.
- Evaluated using a classification report and a confusion matrix.

### Key Results

Binary Classification:
- Achieved high accuracy and ROC-AUC after hyperparameter tuning.
- SMOTE successfully balanced the training data, improving minority class predictions.

Multi-Class Classification:
- Model performed well on specific failure types, with precision and recall improving through class weighting.
- Confusion matrix highlighted areas for further improvement.

### Future Work

- Implement deep learning models (e.g., neural networks) for improved failure prediction.
- Explore time series modeling to incorporate temporal dependencies in sensor data.
- Extend the model to predict failure probabilities for real-time monitoring systems.

### Source

https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-classification
