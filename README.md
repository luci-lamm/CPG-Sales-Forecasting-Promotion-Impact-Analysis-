CPG Sales Forecasting & Promotion Impact Analysis

Overview
This project explores CPG retail sales data to help improve buying predictions at the store level — specifically to prevent stockouts, reduce shrink, and help category managers buy product in a way that actually reflects how consumers shop rather than relying on gut instinct or outdated ordering patterns. Using the M5 Forecasting Competition dataset from Walmart, six machine learning models were built and evaluated to forecast daily product-level demand across 3,049 item-store combinations spanning 10 stores in California, Texas, and Wisconsin.

BLUF
* Recent sales history is the dominant demand driver — lag features capturing the prior 1, 2, 7, and 28 days account for the majority of predictive power across all stores and product categories
* Linear Regression was the best performing model with an R² of 0.661 and a Mean Absolute Error of 1.27 units per day, explaining 66% of daily demand variance on a 28-day holdout window
* SNAP promotion days generate measurable sales lift and were identified as a meaningful secondary demand signal for inventory pre-positioning
* Tree-based models underperformed linear models due to zero-inflated demand distributions at the item-store-day level, a known challenge in retail forecasting at this scale
* Hardware constraints required strategic sampling — the dataset was filtered to the last 365 days per item-store combination with items selling on fewer than 20% of days removed as a principled data quality decision

Repository Contents
**[`Capstone_Project_2.ipynb`](https://github.com/luci-lamm/CPG-Sales-Forecasting-Promotion-Impact-Analysis-/blob/main/Capstone_Project_2.ipynb)** Full CRISP-DM workflow including data loading, quality checks, EDA, feature engineering, modeling, and evaluation
**[`best_model_pipeline.pkl`](https://github.com/luci-lamm/CPG-Sales-Forecasting-Promotion-Impact-Analysis-/blob/main/best_model_pipeline.pkl)**: Serialized best model pipeline for deployment
Interactive Tableau Dashboard: Live interactive analysis
M5 Data Files: Download from Kaggle — files are too large to host on GitHub

Visuals
**[`Project_Banner.jpg`](https://github.com/luci-lamm/CPG-Sales-Forecasting-Promotion-Impact-Analysis-/blob/main/Project_Banner.jpg)**: Project banner image

Data Usage Guide
This project uses the M5 Forecasting Competition dataset from Walmart, publicly available on Kaggle

Download the following three files from:
https://www.kaggle.com/competitions/m5-forecasting-accuracy/data

sales_train_validation.csv -Daily unit sales per product (120 MB)
calendar.csvDates, holidays, events, and SNAP flags (103 KB)
sell_prices.csvWeekly price history per item and store (203 MB)

Setup Instructions:
1. Download all three files from Kaggle
2. Create a folder called data inside your project folder and place all three files inside it
3. Install dependencies: pip install pandas numpy matplotlib seaborn scikit-learn xgboost statsmodels
4. Run Capstone_Project_2.ipynb from top to bottom

Note: A minimum of 16GB RAM is recommended due to the scale of the dataset.

Data Preprocessing

*Pre-launch filtering: Removed rows before each product's first recorded price to eliminate pre-launch noise

*Missing prices: Forward and backward filled within each item-store group

*Price inconsistencies: Week-over-week swings exceeding 50% capped to correct likely data entry errors

*Sparse items: Item-store combinations selling on fewer than 20% of available days removed before modeling

