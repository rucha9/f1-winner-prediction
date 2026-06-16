# F1 Race Outcome Prediction Using Pre-Race Features

A machine learning project that predicts Formula 1 race finishing positions using only information available before the race starts — no lap times, pit stop data, or in-race telemetry.

## Overview

This project builds and evaluates several regression models to predict driver finishing positions for F1 races spanning 1994–2024. The core constraint is strict temporal honesty: all features are derived from pre-race data so the model could realistically be used to make predictions before a race begins.

**Best model:** Linear Regression — MAE: 3.32, R²: 0.453  
**Key finding:** Grid position (35%) + constructor performance (28%) account for 63% of prediction weight.

## Project Structure

```
f1-winner-prediction/
├── data/
│   ├── raw/                  # 14 CSV files from Kaggle Ergast F1 dataset
│   └── processed/
│       ├── merged_data.csv       # 10,494 records (1994–2024)
│       └── features_complete.csv # Engineered feature set
├── scripts/
│   ├── 00_data_merging.ipynb
│   ├── 01_EDA.ipynb
│   ├── 02_feature_engineering.ipynb
│   └── 03_models.ipynb
└── requirements.txt
```

## Workflow

Run the notebooks in order for fully reproducible results.

### 00 — Data Merging
Loads 14 raw CSVs from the Ergast dataset, filters to 9 tables containing only pre-race information, removes records with missing grid positions, and outputs `merged_data.csv` (10,494 records).

### 01 — Exploratory Data Analysis
Explores the relationship between starting grid position and race outcome, including:
- Grid vs. finish position correlation (r = 0.58)
- Win rate by starting position
- Pole position win rate
- Position change distributions

### 02 — Feature Engineering
Creates 6 predictive features from pre-race data:

| Feature | Description |
|---|---|
| Grid position | Starting position on the grid |
| Rolling avg (3 races) | Driver's average finish over last 3 races |
| Rolling avg (5 races) | Driver's average finish over last 5 races |
| Circuit history | Driver's historical performance at this specific circuit |
| Team performance | Constructor's recent results |
| Championship points | Driver's current season standing |

**Temporal split:**
- Train: 1994–2015
- Validation: 2016–2018
- Test: 2019–2024

### 03 — Model Development
Trains and compares four models with GridSearchCV hyperparameter tuning:

| Model | MAE | R² |
|---|---|---|
| Linear Regression | **3.32** | **0.453** |
| Random Forest | — | — |
| XGBoost | — | — |
| Stacking Ensemble | — | — |

Also includes feature importance analysis and a 2024 season holdout validation.

## Data Source

**Ergast API** — a free, open-source web service providing historical F1 data from 1950 to 2024, accessed via its [Kaggle export](https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020). Covers races, drivers, constructors, qualifying results, lap times, pit stops, and standings.

## Setup

```bash
pip install -r requirements.txt
```

Then launch Jupyter and run notebooks `00` through `03` in sequence:

```bash
jupyter notebook scripts/
```

## Requirements

- Python 3.x
- pandas, numpy
- scikit-learn
- xgboost
- matplotlib, seaborn
- scipy
- jupyter / notebook / ipykernel
