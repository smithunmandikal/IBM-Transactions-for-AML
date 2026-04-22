# 🛡️ RiskGuard AML — End-to-End Transaction Risk & Compliance Pipeline

📌 **Project Overview**

**RiskGuard AML** is a professional-grade Anti-Money Laundering (AML) pipeline and risk-scoring engine. Built on the **IBM Transactions for AML** dataset, it simulates how global financial institutions ingest millions of records to detect "smurfing," layering, and OFAC-sanctioned activity.

The project moves beyond simple fraud detection by implementing **behavioral velocity logic**, **geographic anomaly detection**, and a **false-positive reduction engine**—bridging the gap between data science and regulatory compliance.

> *"In AML, a 99% accuracy rate is useless if the 1% of missed cases represents a $50M laundering scheme. RiskGuard focuses on high-recall detection with human-in-the-loop alert prioritization."*

🚀 **What It Does**

* **Ingest & Clean:** Processes raw transaction ledgers into a relational SQL-ready format.
* **Engineer Behavioral DNA:** Automatically calculates rolling velocity (txn counts), amount Z-scores (spending spikes), and geographic "hops."
* **Predict Risk:** Classifies transactions into "Low," "Medium," and "High" risk using Gradient Boosting (XGBoost).
* **Sanctions Screening:** Cross-references entities against a simulated **OFAC SDN list**.
* **Interactive Triage:** Surfaces high-probability alerts in a **Tableau Dashboard** for compliance review.

📊 **Dataset**

**[IBM Synthetic Transactions for AML](https://www.kaggle.com/datasets/ealtman2019/ibm-transactions-for-anti-money-laundering-aml)**
* **Scope:** Multi-million synthetic transactions between accounts.
* **Complexity:** Designed by IBM Research to simulate realistic laundering typologies (Circular trades, Fan-in/Fan-out).
* **Key Challenge:** Extreme class imbalance (Laundering events are < 0.1% of data).

🤖 **ML Models**

| Task | Models Used | Key Metric |
| :--- | :--- | :--- |
| **Laundering Classification** | XGBoost, LightGBM, Random Forest | **Recall (Minimizing Misses)** |
| **Anomaly Detection** | Isolation Forest, Z-Score Scaling | **Outlier Identification** |
| **Feature Engineering** | SQL Window Functions, Pandas | **Velocity & Geo-hops** |

🛠️ **Tech Stack**

| Layer | Technology |
| :--- | :--- |
| **Language** | Python 3.9+ |
| **Data Engine** | SQL (DuckDB/PostgreSQL), Pandas, NumPy |
| **Machine Learning** | scikit-learn, XGBoost, Imbalanced-Learn |
| **Visualization** | Tableau Public / Plotly |
| **Workflow** | Jupyter Notebooks, GitHub Actions |

📁 **Repository Structure**

```text
riskguard-aml/
├── data/
│   ├── raw/                # IBM Dataset (CSV)
│   └── processed/          # Engineered features & SQL exports
├── notebooks/
│   ├── 01_eda_and_sql.ipynb      # Initial analysis & cleaning
│   ├── 02_feature_engineering.ipynb # Velocity & Z-score logic
│   └── 03_model_training.ipynb   # XGBoost & Evaluation
├── src/
│   ├── ofac_simulator.py   # Sanctions lookup logic
│   └── pipeline_utils.py   # Modular helper functions
├── dashboard/
│   └── aml_triage.twbx     # Tableau Packaged Workbook
└── README.md
