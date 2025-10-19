# HouseValAI
An end-to-end regression model predicting California housing prices using Linear, Ridge, Lasso, and Random Forest

# Predicting California Housing Prices (Machine Learning Project)

## Project Overview
This project aims to **predict median housing prices** using demographic and geographic data.  
The dataset includes variables such as income, population, total rooms, and proximity to the ocean.  
It demonstrates the **complete machine learning pipeline** — from data loading to model evaluation.

---

## Problem Definition
> Given housing data with multiple features (location, income, and demographics),  
> build a regression model to predict **`median_house_value`**.

- **Type:** Supervised Regression  
- **Goal:** Estimate continuous housing price values  
- **Dataset Source:** California housing data (Excel format)

---

## Dataset Summary

| Feature | Description |
|----------|-------------|
| longitude | Geographic coordinate (west-east) |
| latitude | Geographic coordinate (north-south) |
| housing_median_age | Median age of houses in the block |
| total_rooms | Total number of rooms |
| total_bedrooms | Total number of bedrooms |
| population | Population in the block |
| households | Number of households |
| median_income | Median income of residents |
| ocean_proximity | Categorical feature (distance to ocean) |
| median_house_value | **Target variable** – housing price |

- **Rows:** ~18,500  
- **Columns:** 10  
- **Missing Values:** In `total_bedrooms`  
- **Categorical Column:** `ocean_proximity`

---

## Workflow Summary

### Data Loading and Inspection
- Loaded dataset using `pandas.read_excel`
- Checked structure via `.info()` and `.describe()`
- Previewed initial rows with `.head()`
- Identified missing values and one categorical variable

### Exploratory Data Analysis (EDA)
- Used **matplotlib** and **seaborn** for visual analysis
- Observed correlations between `median_income` and `median_house_value`
- Confirmed regression nature of the problem (continuous target)

### Data Preprocessing
- Handled categorical column using **`pd.get_dummies`**
- No scaling applied (original value ranges retained)
- Missing values imputed
- Prepared `X` (features) and `y` (target)

### Model Building
Implemented multiple models for performance comparison:

| Model | Technique | Notes |
|--------|------------|-------|
| **Linear Regression** | Baseline model | Simple and interpretable |
| **Ridge Regression** | L2 Regularization | Reduces overfitting |
| **Lasso Regression** | L1 Regularization | Performs feature selection |
| **Random Forest Regressor** | Ensemble Method | Captures non-linear relationships |

### Model Tuning
- Used **`GridSearchCV`** for Ridge and Lasso models  
- Used both **`GridSearchCV`** and **`RandomizedSearchCV`** for Random Forest  
- Compared hyperparameter configurations and cross-validation scores

### Model Evaluation
- Evaluated using:
  - **Mean Absolute Error (MAE)**
  - **Mean Squared Error (MSE)**
  - **R² Score**
- Visualized results and residuals using `matplotlib`/`seaborn`
- Compared model performances on the test set

---

## Results Summary

| Model | MAE | RMSE | R² |
|--------|-----|------|----|
| Linear Regression | Moderate | Moderate | Baseline |
| Ridge Regression | Lower | Lower | Improved generalization |
| Lasso Regression | Similar to Ridge | Similar | Feature selection |
| Random Forest | Lowest | Lowest | Best performer overall |

**Best Model:** RandomForestRegressor (after tuning)

---

## Key Learnings
- End-to-end exposure to the **machine learning workflow**
- Importance of **feature encoding** and **regularization**
- How ensemble methods outperform linear models for non-linear data
- Practical experience with **GridSearchCV** and **RandomizedSearchCV**
- Interpreting **feature importances** to explain predictions

---

## Next Steps / Improvements
- Implement **`ColumnTransformer` + `Pipeline`** for better reproducibility  
- Add **feature engineering** (e.g., `rooms_per_household`, `bedrooms_per_room`)  
- Introduce **feature scaling** and cross-validation on all models  
- Save final model using `joblib.dump()`  
- Extend to **XGBoost** or **LightGBM** for further accuracy

---

## Technologies Used
- **Python 3.x**
- **Pandas**, **NumPy**
- **Scikit-learn**
- **Matplotlib**, **Seaborn**
- **Jupyter Notebook**

---
