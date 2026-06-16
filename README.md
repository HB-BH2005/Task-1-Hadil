# Data Science Project 1 — Advanced EDA & Feature Engineering

Ce projet explore deux jeux de données de vente :
- `Online-Store-Orders.xlsx` pour les commandes client
- `Product-Sales-Region.xlsx` pour les ventes par produit et région

L’objectif est de nettoyer, enrichir et valider ces données avant de produire des jeux de données prêts pour l’analyse et le déploiement. Nous avons traité les dates Excel, géré les valeurs manquantes, détecté et limité les valeurs aberrantes, puis construit des variables explicatives supplémentaires.

---

## 📁 Project Structure

```
ds_project_1/
│
├── data/
│   ├── raw/                         ← Original unmodified datasets
│   │   ├── Online-Store-Orders.xlsx
│   │   └── Product-Sales-Region.xlsx
│   │
│   └── processed/                   ← Cleaned & feature-engineered outputs
│       ├── orders_processed.csv
│       └── sales_processed.csv
│
├── notebooks/
│   ├── project1_eda_feature_engineering.ipynb   ← Main notebook (run this)
│   └── executed_project1_eda_feature_engineering.ipynb   ← Executed copy with saved outputs
│
├── scripts/                         ← Reusable Python modules (extend here)
│
├── outputs/
│   ├── plots/                       ← Saved matplotlib/seaborn figures
│   │   ├── outlier_treatment_orders.png
│   │   ├── correlation_heatmaps.png
│   │   └── eda_distributions.png
│   │
│   └── reports/                     ← JSON/CSV reports
│       └── feature_store_report.json
│
└── README.md                        ← This file
```

---

## 🚀 How to Run

```bash
cd ds_project_1/notebooks
jupyter notebook project1_eda_feature_engineering.ipynb
```

## 📦 Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl pandera
```

---

## 🏗️ Pipeline (IPO Architecture)

### MODULE 1 — INPUT: Securing Fidelity
- Load and inspect both datasets
- Fix Excel serial-number date columns
- Apply the **Missing Data Decision Matrix**:
  - `< 5%` missing → Drop rows
  - `5–20%` missing → Median / Group-wise imputation
  - `> 20%` missing → KNN Imputation
- IQR Winsorization (non-parametric outlier capping)

### MODULE 2 — PROCESS: Vectorized Computation Engine
- **Feature Engineering** (≥ 7 new features per dataset, all vectorized)
- One-Hot Encoding for nominal categories (no label encoding)
- **Collinearity Eradication Algorithm** (threshold = 0.80)
- EDA visualizations

### MODULE 3 — OUTPUT: Structural Contracts & Serving
- Pandera runtime schema validation
- Export processed CSVs to `data/processed/`
- Feature Store JSON report

