[![Python Version](https://img.shields.io/badge/Python-3.12-blue.svg?style=flat-square&logo=python)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.4%2B-orange.svg?style=flat-square&logo=scikit-learn)](https://scikit-learn.org/)
[![Power BI](https://img.shields.io/badge/Power_BI-Enterprise_Reporting-yellow.svg?style=flat-square&logo=power-bi)](https://powerbi.microsoft.com/)
[![Deployment Ready](https://img.shields.io/badge/Pipeline-Production_Serialized-green.svg?style=flat-square)](https://github.com/)

An end-to-end Machine Learning pipeline and interactive Business Intelligence control center engineered to identify, isolate, and audit fraudulent credit card transactions under extreme class imbalance (0.173% base rate). 

This platform transitions financial risk frameworks from reactive crisis management to proactive, automated machine-learning-driven intercept controls—balancing systemic asset insulation against point-of-sale customer checkout friction.

---

## 🔗 Live Interactive Artifacts
* [🚀 Launch Live Interactive Power BI Risk Operations Control Dashboard](YOUR_PUBLISHED_POWER_BI_WEB_URL_HERE)
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

