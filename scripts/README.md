# Scripts Directory
This folder contains all Jupyter notebooks for Formula 1 Race Outcome Prediction Using Pre-Race Features.
Each notebook represents a stage in the project workflow. Run them sequentially for reproducible results.

## 📁 Notebook Structure
### 00 Data Merging
File: 00_data_merging.ipynb

 - Loads 14 CSV files from Kaggle Ergast F1 dataset
 - Keeps 9 files with pre-race data only
 - Excludes in-race information (lap times, pit stops)
 - Removes records with missing grid positions
 - Output: merged_data.csv (10,494 records, 1994-2024)


### 01 Exploratory Data Analysis
File: 01_EDA.ipynb

 - Grid position vs finish position correlation (0.58)
 - Win rate by starting position
 - Pole position win rate
 - Position change distributions


### 02 Feature Engineering
File: 02_feature_engineering.ipynb

 - Creates 6 features: grid position, rolling averages (3 & 5 races), circuit history, team performance, championship points
 - Temporal split: Train (1994-2015), Validation (2016-2018), Test (2019-2024)
 - Output: features_complete.csv


### 03 Model Development
File: 03_models.ipynb

 - Implements Linear Regression, Random Forest, XGBoost, Stacking Ensemble
 - Hyperparameter tuning with GridSearchCV
 - Feature importance analysis
 - 2024 season validation
 - Best Model: Linear Regression (MAE: 3.32, R²: 0.453)
 - Key Finding: Grid (35%) + Constructor (28%) = 63% of prediction weight


