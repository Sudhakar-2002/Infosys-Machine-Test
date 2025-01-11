# Infosys-Machine-Test

# README: Online Retail Sales Analysis

This README file provides detailed instructions on how to replicate the sales analysis and forecasting process using the `Online Retail Dataset`. The analysis includes data cleaning, exploratory data analysis (EDA), visualizations, and forecasting.

---

## 1. Prerequisites

### a. Required Software
- Jupyter Notebook or JupyterLab

### b. Required Python Packages
Install the following Python packages using `pip`:

```bash
pip install pandas numpy matplotlib seaborn statsmodels scikit-learn
```

---

## 2. Dataset
The dataset used is `Online Retail Dataset`, which contains transactional data. Make sure the dataset is cleaned and saved as `Online_Retail_Cleaned.csv`. Key columns include:
- `InvoiceDate`
- `Description`
- `Quantity`
- `UnitPrice`
- `Revenue`
- `CustomerID`

---

## 3. Steps for Replicating the Analysis

### a. Data Cleaning
Follow these steps to clean the data:
1. **Remove Missing Values**: Eliminate rows with missing `Description` values. Replace missing `CustomerID` values with 'Unknown'.
2. **Remove Duplicates**: Identify and drop duplicate rows.
3. **Handle Inconsistent Data**:
   - Standardize `Description` by converting to lowercase and stripping whitespace.
   - Remove rows where `Quantity` or `UnitPrice` is less than or equal to zero.
4. **Add Derived Columns**:
   - Create a `Revenue` column: `Revenue = Quantity * UnitPrice`.
   - Extract `YearMonth` from `InvoiceDate` for time-series analysis.
   - Identify first purchase date for each customer.

### b. Exploratory Data Analysis (EDA)
Perform EDA to identify trends, top-performing products, and customer segments.
1. **Monthly Sales Trends**:
   - Group data by `YearMonth` and sum `Revenue`.
2. **Top Products by Revenue**:
   - Group data by `Description` and sum `Revenue`.
3. **Customer Segmentation**:
   - Analyze customer revenue distribution and retention rates.

### c. Data Visualization
Generate visualizations using Matplotlib and Seaborn:
- Monthly sales trends
- Top products by revenue
- Customer segmentation by revenue

### d. Forecasting with ARIMA
1. **Prepare Data**:
   - Resample monthly revenue data.
2. **Fit ARIMA Model**:
   ```python
   from statsmodels.tsa.arima.model import ARIMA

   model = ARIMA(train, order=(1, 1, 1))
   model_fit = model.fit()
   forecast = model_fit.forecast(steps=1)
   ```
3. **Evaluate Forecast**:
   - Compute Mean Squared Error (MSE) between forecast and actual values.

---

## 4. Files and Folders
- `Online_Retail_Cleaned.csv`: Cleaned dataset.
- `sales_analysis.ipynb`: Jupyter Notebook containing the analysis and visualizations.
- `monthly_sales_plot.png`: Monthly sales trends plot.
- `customer_segmentation_plot.png`: Customer segmentation plot.
- `top_products_plot.png`: Top products by revenue plot.

---



