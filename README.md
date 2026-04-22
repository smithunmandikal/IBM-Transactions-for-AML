# IBM-Transactions-for-AML
This repository contains a full-scale Anti-Money Laundering (AML) pipeline designed to ingest synthetic transaction data, engineer behavioral features, and classify high-risk activity using Gradient Boosting. The project culminates in a Tableau/Plotly Dashboard designed for compliance officers to investigate generated alerts.

Dataset Overview: IBM Transactions for AML
The core of this project utilizes the IBM Synthetic Transactions for Anti-Money Laundering dataset. Unlike standard credit card fraud datasets, this data is designed to simulate complex money laundering schemes.

Source: Kaggle / IBM Research

Structure: A directed graph of transactions between accounts.

Key Typologies: Includes simulated patterns for Structuring (Smurfing), Fan-In/Fan-Out transactions, and Circular Trades.

Data Scale: Multi-million row synthetic ledger featuring Timestamp, From_Account, To_Account, Amount, Currency, and Payment_Type.

🛠️ The Pipeline Architecture
1. Data Ingestion & SQL Processing
Schema: Transactions are stored in a relational format (PostgreSQL/DuckDB).

OFAC Simulation: A mock Sanctions List is joined with account data to simulate real-world KYC (Know Your Customer) checks.

2. Feature Engineering (The "Risk Signals")
We engineer three primary classes of features to detect suspicious behavior:

Velocity Features: Counts of transactions per account over rolling windows (e.g., 1h, 24h, 7d).

Geo-Anomalies: Tracking sudden changes in Payment_Currency or Bank_Location inconsistent with history.

Amount Z-Scores: Measuring the standard deviation of a transaction amount relative to the account's historical mean to identify outliers.

3. Machine Learning Model
Algorithm: Gradient Boosting Classifier (XGBoost/LightGBM).

Training: Imbalanced class handling using SMOTE or scale-pos-weights to account for the rarity of "Laundering" labels.

False-Positive Reduction: A secondary heuristic layer that suppresses alerts for verified low-risk entities (e.g., government accounts or high-volume regulated utilities).

4. Risk Scoring Dashboard
The final output is a Tableau Public or Plotly Dash interface featuring:

Alert Queue: Prioritized by ML "Risk Probability" scores.

Entity Profile: A deep dive into an individual account's transaction history and velocity spikes.

Network View: (Optional) Visualizing the flow of funds between accounts to spot layering.
