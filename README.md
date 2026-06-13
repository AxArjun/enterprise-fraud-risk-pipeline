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
Ingress & Robust Engineering: Raw numerical data and anonymized principal component vectors ($V1$ through $V28$) pass through a row-clearing guardrail to filter null values before being normalized using a RobustScaler to eliminate extreme transaction outlier bias.Balanced Machine Learning Layer: The balanced data pool uses a strictly stratified training split. Synthetic Minority Over-sampling Technique (SMOTE) is applied exclusively to the training vectors to prevent data leakage and baseline inflation.Downstream Business Intelligence Engine: Validated test probabilities are exported into a structured analytics table, converting system probabilities into an operational triage ledger inside Power BI Desktop.🏎️ Model Performance & Benchmarking LedgerIn an enterprise risk audit, sophisticated ensemble mechanisms must mathematically justify their computational costs over traditional statistical baselines. The pipeline cross-evaluates our optimized SentinEdge Random Forest Ensemble against a standard Logistic Regression baseline:Evaluation MetricLogistic Regression (Baseline)Random Forest (SentinEdge)Performance DeltaOperational ImpactSystem Accuracy97.43%99.95%+2.52%Drastic reduction in baseline query processing noise.Precision (Confidence)5.48%86.42%+80.94%Eliminates merchant false alarms and customer checkout checkout flags.Recall (Fraud Caught)88.78%85.71%-3.07%Maintains stable intercept metrics while protecting customer experience.F1-Score Index0.10320.8606+75.74%Proves model stability under asymmetric data distributions.📈 Advanced Discrimination Curve VerificationTo establish dynamic risk thresholds for corporate stakeholders, the model generates dual-axis discrimination vectors across all probability intervals:Receiver Operating Characteristic (ROC) Curve: Tracks true validation capture against false alarm propagation.Precision-Recall (PR) Curve: The primary validation metric for severe data imbalance, proving high model confidence is maintained even at strict recall cutoffs.🖥️ Operational Control Center (Power BI Dashboard)The front-end user experience transforms raw backend model probabilities into an active triage command panel for fraud analysts and executives.📊 Strategic Component Matrix Breakdown:Executive Metric Card Strips: Tracks global risk indexes including Volume Audited, Intercepted Exploits, and the Systemic Threat Index (computed via performance-stable explicit DAX formulations).Chronological Risk Distribution (Line Chart): Maps mean fraud probability over a 24-hour cycle, unmasking a massive threat multiplier spike concentrated between 2:00 AM and 5:00 AM.High-Risk Action Triage Ledger (Data Table): An interactive matrix sorted descending by Risk_Score, utilizing conditional color formatting gradients to draw analyst attention to active exploits immediately.Operational Control Filters (Slicers): Allows automated slicing by Prediction_Outcome (Cleared vs. Flagged / Blocked) to dynamically audit model-flagged transaction blocks.📦 Production Engineering & SerializationTo prepare the validated machine learning pipeline for real-time cloud API integration (e.g., AWS S3, Azure Blob, or a FastAPI wrapper), the system automatically serializes and packages core analytical objects:Pythonimport joblib

# Exporting serialized microservice assets
joblib.dump(rf_model, 'sentinedge_random_forest_model.pkl')
joblib.dump(scaler, 'sentinedge_data_scaler.pkl')
sentinedge_random_forest_model.pkl (6.34 MB): A fully compiled, compressed model footprint optimized for fast microservice container spin-ups.sentinedge_data_scaler.pkl: Preserves the exact scaling weights calculated during training, ensuring fresh production transaction streams undergo identical transformations.🛠️ Installation & Pipeline ExecutionPrerequisitesEnsure your local Python workspace contains the standard analytical dependency layers:Bashpip install pandas numpy scikit-learn matplotlib seaborn joblib
Reproducing the PipelineClone the repository and position yourself within the root project structure:Bashgit clone [https://github.com/AxArjun/enterprise-fraud-risk-pipeline.git](https://github.com/AxArjun/enterprise-fraud-risk-pipeline.git)
cd enterprise-fraud-risk-pipeline
Execute the self-contained pipeline script to process data, train models, plot metrics, and generate the Power BI data source file:Bashpython src/train_pipeline.py
Open SentinEdge_Risk_Operations.pbix inside Power BI Desktop, point the data source parameters to your newly generated SentinEdge_PowerBI_RiskData.csv, and execute a model refresh.📋 Governance & Financial Compliance MappingSOX Compliance: Explicit model tracking provides auditing paths for financial transaction controls.Operational Overhead Mitigation: Pre-filtering low-risk transactions through top latent parameters (V17, V14, V12) minimizes server lag and compute costs.Consumer Protection: Restricting false positive rates protects consumer trust and shields merchant networks from card-not-present (CNP) chargeback penalties.🗂️ Recommended Local Repository LayoutBefore pushing to your remote GitHub branch, arrange your files locally on your computer to match this structure. This structured layout instantly proves to a reviewer that you follow enterprise software engineering standards:Plaintextenterprise-fraud-risk-pipeline/
│
├── .gitignore                          # Excludes heavy raw datasets and cache files
├── README.md                           # The premium markdown profile document provided above
├── sentinedge_random_forest_model.pkl  # Serialized model artifact (6.34 MB)
├── sentinedge_data_scaler.pkl          # Serialized scaling asset
│
├── assets/
│   └── dashboard_mockup.png            # High-resolution screenshot of your Power BI canvas
│
├── dashboards/
│   └── FRAUD DETECTION PIPELINE POWER BI DASHBOARDS.pbix  # Your master Power BI dashboard
│
├── data/
│   └── SentinEdge_PowerBI_RiskData.csv # The generated export data file
│
└── notebooks/
    └── Fraud_Detection_Pipeline.ipynb  # Your complete, error-free Colab execution notebook
