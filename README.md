# 📊 Project Enterprise Fraud Risk Pipeline: Enterprise Transaction Monitoring & Advanced Risk Mitigation Engine

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Latest-orange.svg)](https://scikit-learn.org/)
[![Imbalanced-Learn](https://img.shields.io/badge/Imbalanced--Learn-SMOTE-red.svg)](https://github.com/scikit-learn-contrib/imbalanced-learn)

An end-to-end data analytics and predictive pipeline engineered for high-volume financial services environments. This framework navigates severe class imbalances to identify fraudulent exploits, optimizes operational cost-benefit trade-offs, and delivers actionable, executive-ready visual insights.

---

## 🏢 Business Context & Problem Statement
In large-scale retail banking and financial data systems, malicious activity is highly asymmetric. This architecture models an enterprise environment containing **284,807 transactions**, where fraudulent vectors account for only **492 instances (0.173% of total volume)**. 

Standard evaluation criteria (such as raw predictive accuracy) are deceptive and operationally hazardous in this space. This project designs a robust risk platform that successfully targets anomalies while strategically managing the delicate friction point between security constraints and baseline consumer throughput.

---

## 🛠️ System Architecture & Data Pipeline

The project is structured around a rigorous four-tiered pipeline ensuring high data integrity and robust evaluation boundaries:

1. **Exploratory Data Analysis (EDA) & Normalization:** Identifying structural distribution shifts and isolating time-series anomalies.
2. **Imbalance Mitigation (Targeted SMOTE):** Synthetically oversampling minority instances strictly inside training partitions to protect against data leakage.
3. **Ensemble Predictive Modeling:** Deploying tuned Random Forest Classifiers engineered to handle non-linear structural variations.
4. **Advisory Translation Layer:** Mapping mathematical confusion matrices directly to business metrics and operational queues.

---

## 📈 Key Visual Insights & Discoveries

### 1. Normalized Temporal Risk Profiling
Traditional transaction counts hide systemic risk due to scale disparities. By normalizing the data to track the exact **Fraud Probability Percentage by Hour**, this framework uncovered a massive risk spike during off-peak windows (**2:00 AM – 5:00 AM**). Even though total volume is low during these hours, the likelihood of a transaction being a fraudulent exploit increases exponentially.

### 2. True Spread Identification (Outlier Suppression)
Financial transaction datasets are heavily skewed by extreme outliers (ranging up to $25,000+). By deploying an intentional visual suppression mechanism (`showfliers=False`), the exploratory layers reveal a clear structural variance: fraudulent activities maintain a significantly higher median transaction volume and a broader Interquartile Range (IQR) than genuine consumer activity.

---

## ⚙️ Core Implementation Highlights

### Resampling Strategy (Eliminating Bias)
A major structural strength of this architecture is its boundary control. Synthetic Minority Over-sampling Technique (SMOTE) is applied **strictly to the training features** after scaling, leaving the evaluation test data completely unaltered. This prevents synthetic noise from bleeding into validation layers and ensures the empirical verification reflects true production capabilities.

```python
# Strategic Isolation of SMOTE Resampling
from imblearn.over_sampling import SMOTE
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# Synthetic expansion strictly bound to training arrays
smote = SMOTE(random_state=42)
X_train_balanced, y_train_balanced = smote.fit_resample(X_train_scaled, y_train)
┌─────────────────────┐
│ Credit Card Dataset │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Python (Pandas)     │
│ Data Cleaning       │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Fraud Detection ML  │
│ Model Training      │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Risk Scoring Engine │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ SentinEdge CSV      │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Power BI Dashboard  │
│ Executive Analytics │
└─────────────────────┘
