#  Sales Forecasting

This project focuses on forecasting retail sales using historical data, incorporating factors like seasonality, promotions, and economic trends. The goal is to build a predictive model to optimize inventory management and sales strategies.

## Table of Contents
- [Project Overview](#project-overview)
- [Setup Instructions](#setup-instructions)
- [Dataset](#dataset)
- [How to Run](#how-to-run)
- [Methodology](#methodology)
- [Key Findings](#key-findings)
- [Business Insights](#business-insights)
- [Model Performance](#model-performance)

## Project Overview
Retail sales are influenced by multiple factors including seasonality, economic trends, and special events. Incorrect sales predictions can lead to stock shortages or overstocking, resulting in revenue loss. This project:
- Analyzes historical sales data
- Engineers meaningful features
- Trains multiple forecasting models
- Evaluates performance using error metrics
- Extracts business insights for decision-making

## Setup Instructions

### Extracting the Data
1. Download the `store_forecasting_data.zip` file from the repository
2. Extract the contents to a folder named `store_forecasting_data` in your project directory
3. Ensure the folder structure looks like:
   ```
   your_project/
   ├── Sales Forecasting.ipynb
   └── store_forecasting_data/
       ├── train.csv
       ├── test.csv
       ├── transactions.csv
       ├── stores.csv
       ├── oil.csv
       └── holidays_events.csv
   ```

### Prerequisites
- Python 3.7+
- Jupyter Notebook
- Required packages (install via pip):
  ```
  pip install numpy pandas matplotlib seaborn scikit-learn xgboost statsmodels tensorflow
  ```

## How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/MNitin-Reddy/Sales-Forecasting.git
   cd Sales-Forecasting
   ```

2. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```

3. Open `Sales Forecasting.ipynb` and run all cells sequentially


## Dataset
The dataset consists of multiple files:
1. `train.csv`: Historical sales data (3M+ records)
2. `test.csv`: Forecasting dates (28,512 records)
3. `transactions.csv`: Daily transactions per store
4. `stores.csv`: Store metadata (location, type, cluster)
5. `oil.csv`: Daily oil prices
6. `holidays_events.csv`: Holidays and special events

Key features:
- Date, store number, product family
- Sales figures, promotion status
- Store characteristics, economic indicators

## Methodology
1. **Data Preparation**:
   - Merged multiple datasets
   - Handled missing values (interpolation for oil prices, median imputation for transactions)
   - Feature engineering (time-based, event-based, rolling statistics)

2. **Exploratory Analysis**:
   - Seasonal trends analysis
   - Store and product performance evaluation
   - Impact analysis of holidays and promotions

3. **Modeling**:
   - Implemented multiple models:
     - Naive Forecast (baseline)
     - ARIMA
     - Random Forest
     - XGBoost (best performer)
     - LSTM
   - Evaluated using RMSE, MAPE, and R² metrics

## Key Findings
- **Seasonal Patterns**: Strong December sales peak across all years
- **Store Performance**: 
  - Cluster 5 has highest average sales per store
  - Cluster 14 leads in total sales volume
- **Product Trends**: 
  - GROCERY I dominates sales across all clusters
  - Beverages and Produce are top-performing categories
- **External Factors**:
  - Holidays increase sales by 15-20%
  - Promotions have even stronger impact (25-30% boost)
  - Oil prices show weak correlation (-0.0755) with sales

## Business Insights
1. **Inventory Planning**:
   - Increase stock for December and promotion periods
   - Focus on high-demand product families (GROCERY I, Beverages)

2. **Store Optimization**:
   - Replicate Cluster 5's successful strategies in other clusters
   - Investigate underperforming stores in Cluster 3

3. **Promotion Strategy**:
   - Time promotions with paydays (15th and month-end)
   - Focus discounts on top-performing product families

## Model Performance
| Model        | RMSE    | R² Score |
|--------------|---------|----------|
| Naive        | 1958.54 | -1.06    |
| ARIMA        | 1419.49 | -0.08    |
| Random Forest| 320.21  | 0.92     |
| **XGBoost**  | **257.98** | **0.96** |
| LSTM         | 410.75  | 0.89     |

XGBoost emerged as the best model with:
- 96% variance explained (R² = 0.96)
- Lowest RMSE (257.98)
- Effective handling of complex feature interactions
