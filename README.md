# Predictive Maintenance: Engineering Operational Resilience with AI Governance

## Overview

In manufacturing, unplanned downtime is a silent profit killer. We wouldn't ship a product without stress-testing its components, yet many organizations deploy predictive maintenance models with minimal oversight. This project demonstrates a governed approach to predictive maintenance, treating the ML model as a mission-critical component on the factory floor. By integrating rigorous **pre-production auditing, bias checks, and continuous monitoring principles**, we move beyond simple predictions to build a system that plant managers can trust with their operational tempo.

The project leverages sensor data from machines and employs a Random Forest model to predict machinery failures. It also explores imbalanced class handling and feature importance to better understand failure causes and enhance predictive accuracy.

### Problem Statement: The High Cost of Unmanaged Risk

Unplanned machinery failures lead to catastrophic downtime, quality defects, and safety incidents. While predictive maintenance offers a solution, a poorly governed model introduces new risks:

- **False Alarms (False Positives):** Wasting maintenance team time and resources on unnecessary checks, leading to "alert fatigue."
- **Missed Failures (False Negatives):** Creating a false sense of security while a machine is on the verge of breakdown, resulting in catastrophic downtime.
- **Unfair Performance:** A model that works well on one machine type (e.g., 'H') but fails on another (e.g., 'L'),

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

### Our Approach: The Digital QMS for Predictive Maintenance

We applied a governance-first framework to ensure the predictive model is robust, fair, and actionable.

1. The Pre-Production Audit: Stress-Testing the Model

Before any model could be considered for deployment, it underwent a rigorous audit simulating factory floor conditions.
- Robustness Testing: We validated that the model's performance holds across different operational regimes. How does it perform under extreme process temperatures? Does it maintain accuracy at the upper limits of rotational speed?
- Fairness & Representativeness Audit: We critically evaluated performance across all Machine Types (L, M, H). A model that only predicts failures accurately for 'High'-type machines is an operational liability for lines using 'Low' or 'Medium' types. This was a core focus of our multi-class analysis.
- Drift Monitoring Baseline: We established a baseline for key feature distributions (e.g., normal ranges for Torque, Tool Wear) to enable future monitoring for data drift caused by new materials, seasonal changes, or wear-and-tear.

2. The Multi-Disciplinary Maintenance Team

Building a trustworthy system requires more than a data scientist.

- Plant Manager: Defines the cost of a false negative (downtime) vs. a false positive (labor cost).
- Maintenance Engineer: Provides the "why" behind the data, helping interpret why Torque and Rotational Speed are top features and validating that the model's failure predictions make physical sense.
- Data Scientist: Translates these operational requirements into algorithmic constraints and fairness checks.

### Governance-Driven Methodology
1. **Data Preprocessing & De-risking:**
- Removed non-predictive columns (Product ID).
- Strategic Oversampling: Applied SMOTE to correct for the high cost of missing a failure (False Negative), a critical risk-mitigation step.
- Encoded categorical features and scaled continuous ones.

2. **Model Training & Validation:**
- Binary Classification (Failure/No-Failure): Random Forest, tuned for high recall to minimize missed failures.
- Multi-Class Classification (Failure Type): Random Forest, to diagnose the root cause and enable targeted maintenance.

3. **Rigorous Model Auditing:**
- Used cross-validation to ensure generalizability.
- Evaluated with a full suite of metrics beyond accuracy, with a focus on Recall for the failure class.

### Audit Results & Operational Interpretation

#### Binary Classification Audit: The Failure Triage System
- Accuracy: 97.9% - High overall reliability.
- ROC-AUC: 0.998 - Exceptional ability to distinguish between failing and healthy machines.
- Recall (Failure Class): ~97% - This is the key metric. It means the model catches 97% of all actual failures, critically minimizing unplanned downtime.
- Governance Verdict: PASS. This model demonstrates the robustness and reliability required for a production environment as a first-line alert system.

#### Multi-Class Classification Audit: The Diagnostic Challenge
- Finding: The model performs well on common failure types but struggles with rare classes (e.g., Failure Types 4 & 5).
- Governance Verdict: CONDITIONAL PASS. This model is useful but requires a governance control: Human-in-the-Loop. For rare failure types, the system should flag the prediction as low-confidence and escalate to a maintenance engineer for diagnosis. Deploying it autonomously for all failure types is a risk.

#### Feature Importance Audit: The Sensor Strategy
- **Critical Signals:** Rotational Speed, Torque, and Tool Wear were identified as the leading indicators of failure. These sensors should be prioritized for calibration and real-time monitoring.
- **Unexpected Finding:** Temperature features had minimal impact. This is a vital insight—it suggests that investing in more temperature sensors may not yield a predictive ROI and that the root causes of failure are primarily mechanical.

### Conclusion: Building the Resilient Factory

This project proves that the value of a predictive maintenance system lies as much in its governance as in its algorithms. By auditing for robustness, fairness, and actionability, we transform a black-box model into a trustworthy partner for the maintenance team.

**The prognosis for this system is strong, provided that the following governance steps are implemented:**

- Deploy the binary model as the primary high-recall alert system.
- Use the multi-class model with a human-in-the-loop for common failures only.
- Establish a continuous monitoring dashboard (e.g., in Power BI) to track model performance and feature drift over time.

Manufacturing leaders: the choice is clear. Treat your predictive models with the same rigor as your most critical production equipment. By doing so, you don't just predict failures—you build a foundation for a truly resilient, efficient, and intelligent operation.     

### Source

https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-classification
