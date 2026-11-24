# CIE 2 – Activity 1: Multiple Linear Regression

## Activity
This activity uses Multiple Linear Regression to estimate the selling price of a used car from its manufacturing year and kilometres driven. The work follows a data-science workflow: inspect and clean the data, explore feature relationships, calculate a small regression example manually, train models and evaluate their predictions.

## Dataset and Source
- **Dataset:** Car Details from Car Dekho
- **Source:** [Kaggle – Vehicle Dataset from CarDekho](https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho)
- **Original size:** 4,340 rows and 8 columns
- **Columns:** name, year, selling_price, km_driven, fuel, seller_type, transmission and owner
- **Input features used:** year and km_driven
- **Target:** selling_price (Indian rupees)

The dataset contains used-car details. Duplicate records were removed, leaving 3,577 rows. No missing values or invalid values were found in the selected modelling columns.

## Work Completed
1. Loaded the dataset and checked its structure, data types, summary statistics, missing values, duplicates and invalid values.
2. Removed duplicate records and checked the selected numerical columns.
3. Created scatter plots and a correlation heatmap for year, km_driven and selling_price.
4. Built a design matrix using five observations and calculated the transpose, XᵀX, Xᵀy and regression coefficients using the normal equation.
5. Verified the manual calculation with Scikit-learn.
6. Split the cleaned data into 80% training and 20% testing data.
7. Trained and compared a single-feature Linear Regression model and a Multiple Linear Regression model.
8. Interpreted the coefficients, calculated standardised coefficients and compared actual and predicted test values.
9. Evaluated MAE, MSE, RMSE, R² and adjusted R². Examined residual plots, the residual histogram and VIF.
10. Generated a selling-price estimate for a new car using the median training values.

## Key Results
The test-set comparison is shown below.

| Metric | Single-feature model (year) | Multiple-feature model (year + km_driven) |
|---|---:|---:|
| MAE | ₹236,626.94 | ₹236,606.53 |
| MSE | 267,737,137,875.10 | 267,709,663,356.21 |
| RMSE | ₹517,433.22 | ₹517,406.67 |
| R² | 0.1689 | 0.1689 |
| Adjusted R² | 0.1677 | 0.1666 |

The multiple-feature model gives only a very small improvement in test R² and RMSE. Its adjusted R² is slightly lower, so adding km_driven provides very limited improvement for this model.

**Multiple Linear Regression equation:**

```text
Selling Price = -100034847.64 + (49930.18 × Year) - (0.01208 × KM Driven)
```

The VIF values for year and km_driven are approximately 1.21 each, indicating low multicollinearity between these two features.

For a car with the median training values (year = 2014 and km_driven = 61,585), the model predicted a selling price of approximately **₹523,782.98**.

The residual distribution is strongly right-skewed (skewness is approximately 7.50), so the normality assumption is doubtful and large prediction errors/outliers may be present. The low R² also indicates that the selected features explain only a limited part of the variation in selling prices. Other factors such as car model, fuel, transmission, condition and ownership may also affect price.

## Files
- `RCA__1(1).ipynb` – Activity 1 Jupyter Notebook
- `CAR DETAILS FROM CAR DEKHO.csv` – Dataset used by the notebook


## Tools and Libraries
Python, Jupyter Notebook, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn and Statsmodels.

## Faculty GitHub
[https://github.com/complexiota](https://github.com/complexiota)

