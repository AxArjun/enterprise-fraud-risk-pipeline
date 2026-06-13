[![Python Version](https://img.shields.io/badge/Python-3.12-blue.svg?style=flat-square&logo=python)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.4%2B-orange.svg?style=flat-square&logo=scikit-learn)](https://scikit-learn.org/)
[![Power BI](https://img.shields.io/badge/Power_BI-Enterprise_Reporting-yellow.svg?style=flat-square&logo=power-bi)](https://powerbi.microsoft.com/)
[![Deployment Ready](https://img.shields.io/badge/Pipeline-Production_Serialized-green.svg?style=flat-square)](https://github.com/)

An end-to-end Machine Learning pipeline and interactive Business Intelligence control center engineered to identify, isolate, and audit fraudulent credit card transactions under extreme class imbalance (0.173% base rate). 

This platform transitions financial risk frameworks from reactive crisis management to proactive, automated machine-learning-driven intercept controls—balancing systemic asset insulation against point-of-sale customer checkout friction.

---

## 🔗 Live Interactive Artifacts
* [📓 View Production Machine Learning Pipeline Notebook](./notebooks/Fraud_Detection_Pipeline.ipynb)

---

## 🏛️ System Architecture & Data Topology

The SentinEdge framework segregates the analytical lifecycle into three isolated tiers to preserve mathematical validity and ensure sub-second API inference capabilities:

```text
[ Raw Transaction Feed ] ──> [ Data Cleansing & Robust Scaling ]
                                           │
                                           ▼
                            [ Stratified Train/Test Split ]
                                           │
                    ┌──────────────────────┴──────────────────────┐
                    ▼ (Train Partition Only)                      ▼ (Test Partition)
            [ SMOTE Resampling ]                              [ Held-Out Isolation ]
                    │                                             │
                    ▼                                             ▼
       [ Random Forest Training ]                          [ Model Benchmarking ]
                    │                                             │
                    ▼                                             ▼
       [ Serialization Layer (.pkl) ] ──> [ Microservice Ready ] <───┘
                                           │
                                           ▼
                             [ Summary Analytics Export ] ──> [ Power BI Control Center ]
```
1. Ingress & Robust Engineering: Raw numerical data and anonymized principal component vectors ($V1$ through $V28$) pass through a row-clearing guardrail to filter null values before being normalized using a RobustScaler to eliminate extreme transaction outlier bias.
2. Balanced Machine Learning Layer: The balanced data pool uses a strictly stratified training split. Synthetic Minority Over-sampling Technique (SMOTE) is applied exclusively to the training vectors to prevent data leakage and baseline inflation.
3. Downstream Business Intelligence Engine: Validated test probabilities are exported into a structured analytics table, converting system probabilities into an operational triage ledger inside Power BI Desktop.

---

## 🏎️ Model Performance & Validation

Fraud detection presents a highly imbalanced classification problem where fraudulent transactions represent only **0.17%** of the total transaction population. To evaluate model robustness, multiple performance metrics were used rather than relying solely on accuracy.

### Performance Summary

| Metric    | Value  |
| --------- | ------ |
| Accuracy  | 99.85% |
| Precision | 53.25% |
| Recall    | 83.67% |
| F1 Score  | 65.08% |

### Confusion Matrix

| Actual / Predicted | Genuine | Fraud |
| ------------------ | ------- | ----- |
| Genuine            | 56,792  | 72    |
| Fraud              | 16      | 82    |

### Key Validation Findings

* Successfully identified **82 fraudulent transactions**.
* Limited missed fraud cases to only **16 transactions**.
* Maintained fraud recall above **83%**, ensuring strong fraud capture capability.
* Achieved high overall accuracy despite severe class imbalance.
* Demonstrated operational viability for transaction monitoring environments.

---

## 📈 Risk Intelligence Dashboard Suite

The machine learning outputs are transformed into a multi-layer Power BI intelligence platform designed for executive stakeholders, fraud analysts, and operational investigators.

### 1️⃣ Executive Fraud Risk Intelligence Dashboard

Executive-level monitoring and portfolio risk visibility.

#### Key Metrics

* Volume Audited
* Mean Risk Score
* Confirmed Fraud Cases
* Monitored Transaction Value
* Fraud Rate
* High-Risk Transactions
* Fraud Loss Value

#### Visual Analytics

* Risk Score Trend by Hour
* Prediction Outcome Distribution
* Fraud Cases by Hour
* Risk Score Distribution Analysis
* Executive Insights Panel

#### Business Purpose

Provides a real-time overview of fraud exposure and operational fraud risk.

---

### 2️⃣ High Risk Transaction Investigation Center

Interactive fraud investigation workspace.

#### Investigation Metrics

* Transactions Investigated
* Investigation Exposure
* Average Investigation Risk

#### Investigation Features

* Transaction-level audit table
* Actual vs Predicted classifications
* Risk Score prioritization
* Fraud review workflow support
* Drill-down transaction analysis

#### Business Purpose

Enables fraud analysts to rapidly identify and investigate suspicious transactions.

---

### 3️⃣ Model Performance & Validation Dashboard

Dedicated model monitoring and validation workspace.

#### Model KPIs

* Accuracy
* Precision
* Recall
* F1 Score

#### Validation Components

* Confusion Matrix
* True Positives
* False Positives
* True Negatives
* False Negatives

#### Business Purpose

Provides transparency into model effectiveness and supports governance requirements.

---

### 4️⃣ Executive Recommendations & Business Impact Dashboard

Transforms model outputs into strategic business actions.

#### Executive Metrics

* Potential Fraud Savings
* Fraud Detection Recall
* High-Risk Transactions
* Fraud Exposure Rate
* Savings Opportunity

#### Business Impact Assessment

* Fraud exposure estimation
* Potential financial savings
* Operational efficiency improvements
* Fraud investigation prioritization
* Strategic risk mitigation recommendations

#### Business Purpose

Bridges the gap between predictive analytics and executive decision-making.

---

## 📦 Production Deployment Assets

To support deployment and future integration into cloud environments, serialized model artifacts are exported using Joblib.

```python
import joblib

joblib.dump(rf_model, "sentinedge_random_forest_model.pkl")
joblib.dump(scaler, "sentinedge_data_scaler.pkl")
```

### Exported Assets

* sentinedge_random_forest_model.pkl
* sentinedge_data_scaler.pkl
* SentinEdge_PowerBI_RiskData.csv

These assets can be integrated into:

* FastAPI
* Flask
* Azure Machine Learning
* AWS SageMaker
* Docker Containers
* Real-Time Fraud Scoring APIs

---

## 🛠️ Technology Stack

### Data Science & Machine Learning

* Python
* Pandas
* NumPy
* Scikit-Learn
* Imbalanced-Learn (SMOTE)
* Joblib

### Business Intelligence

* Power BI Desktop
* DAX
* Power Query

### Modeling Techniques

* Random Forest Classifier
* RobustScaler
* Stratified Sampling
* SMOTE Oversampling

---

## 📂 Repository Structure

```text
enterprise-fraud-risk-pipeline/
│
├── README.md
├── sentinedge_random_forest_model.pkl
├── sentinedge_data_scaler.pkl
│
├── assets/
│   ├── executive_dashboard.png
│   ├── investigation_dashboard.png
│   ├── model_validation_dashboard.png
│   └── business_impact_dashboard.png
│
├── dashboards/
│   └── FRAUD_DETECTION_PIPELINE_POWER_BI_DASHBOARDS.pbix
│
├── data/
│   └── SentinEdge_PowerBI_RiskData.csv
│
└── notebooks/
    └── Fraud_Detection_Pipeline.ipynb
```

---

## 🚀 Future Enhancements

* Explainable AI using SHAP
* Real-Time Fraud Scoring API
* Automated Model Retraining
* Kafka Event Streaming
* Azure Deployment Pipeline
* Alerting & Notification Framework
* Fraud Risk Forecasting
* Graph-Based Fraud Network Detection

---

## 👨‍💻 Author

**Arjun Ramprasad**

---


