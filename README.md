# California_Housing_Price_Prediction_Regression
***An end-to-end regression project featuring thorough EDA, data preprocessing, outlier analysis, and model development using linear and non-linear techniques.***
<p align="center">
  <img src="https://github.com/Parichehr-Khanbani/California_Housing_Price_Prediction_Regression/blob/main/assets/CALIFORNIA%20HOUSING.png" alt="California Housing Banner" width="100%">
</p>


This project develops and evaluates regression models for predicting California housing prices using the California Housing dataset. The workflow includes extensive exploratory data analysis (EDA), outlier detection,preprocessing, and model experimentation with linear, SGD-based, and polynomial regression methods.

The objective is to understand the impact of nonlinearity, regularization, and outlier handling on model performance and to build a well-validated baseline model for the dataset.
## **1. Project Overview**
This project focuses on:
*    Performing detailed EDA on numerical and categorical variables
*    Detecting and handling outliers using distribution-based and model-based methods
*    Applying Yeo–Johnson transformations for improved feature normalization
*    Building and comparing multiple regression models
*    Evaluating the predictive power of polynomial feature expansion
*    Analyzing model behavior using evaluation plots

The final model demonstrates the performance benefits of introducing non-linear features and L1 regularization.
## **2. Dataset**
The dataset originates from the California Housing dataset and includes approximately 20,000 total samples and 10 columns:
| **Column Name**        | **Description**                                                                                                                                                                                                                          |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **longitude**          | The geographical coordinate that specifies how far west or east a house block group is located (in degrees). Negative values indicate locations west of the prime meridian — all values are negative because California lies west of it. |
| **latitude**           | The geographical coordinate specifying how far north a house block group is located (in degrees).                                                                                                                                        |
| **housing_median_age** | The median age of houses (in years) within a block group — older areas have higher values.                                                                                                                                               |
| **total_rooms**        | The total number of rooms (of all types: bedrooms, kitchens, etc.) in all houses within a block group.                                                                                                                                   |
| **total_bedrooms**     | The total number of bedrooms in all houses within a block group. Used along with `total_rooms` to estimate average house size.                                                                                                           |
| **population**         | The total population living within a block group. Useful for understanding density and neighborhood characteristics.                                                                                                                     |
| **households**         | The total number of households (i.e., groups of people living together) in a block group.                                                                                                                                                |
| **median_income**      | The median income (in tens of thousands of USD) for households in a block group. For example, `8.3252` represents $83,252.                                                                                                               |
| **median_house_value** | The median house value (in USD) for households in a block group. This is the target variable (label) often used for regression tasks.                                                                                                    |
| **ocean_proximity**    | A categorical feature indicating the location of the block group relative to the ocean. Possible categories include:<br>• `NEAR BAY`<br>• `NEAR OCEAN`<br>• `INLAND`<br>• `ISLAND`<br>• `<1H OCEAN` (less than one hour to the ocean).   |

## **3. Workflow Summary**
### **3.1 Exploratory Data Analysis (EDA)**
The EDA phase is divided into 3 sections:
*    Univariate analysis including examining the distribution of data
*    Bivariate analysis including examining the relation of each variable with the target variable
*    Multivariate analysis including the effect of multiple variables on the target variable
### **3.2 Preprocessing & Outlier Detection**
Key steps including but not limited to:
*    Yeo–Johnson transformation applied to all numeric features
*    IQR-based outlier flags with modified thresholds
  
## **4. Models Implemented**
### **4.1 Baseline: Linear Regression (SGDRegressor)**
*    Standardized features
*    ElasticNet penalty
*    Achieved R² ≈ 0.67

Showed underestimation of high-value houses

### **4.2 Polynomial Regression Models**
Multiple polynomial regression pipelines were tested using:
*    PolynomialFeatures(degree=2–5)
*    StandardScaler or MinMaxScaler
*    ElasticNetCV and LassoCV

Key Findings:
*    Best regularization strength: alpha = 0.01
*    Best penalty type: l1_ratio = 1.0 (pure Lasso)
*    Final Train R²: ~0.728
  
Inccreasing the polynomial degree beyond 2 did not yield meaningful improvement.

## **5. Performance Interpretation**
The final model demonstrates:
*    Better alignment with the diagonal in Predicted vs. Actual plots
*    Reduced underestimation in high-value ranges
*    Improved overall variance explanation (up from ~0.67 to ~0.72 R²)

However, a mild trend of overestimation for lower target values and underestimation for higher target values persists which indicates that while polynomial regression outperforms linear baselines, the dataset likely requires more flexible models (XGBoost, RandomForest, GradientBoosting) for further gains.
