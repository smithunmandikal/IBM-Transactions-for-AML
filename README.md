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
