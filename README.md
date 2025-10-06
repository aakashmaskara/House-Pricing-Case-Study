# Housing Price Prediction (Regression)

Exploratory Data Analysis (EDA) and regression modeling to predict residential **sale prices** and explain the main drivers that influence valuation.

## Introduction

This case study applies **EDA + regression** to a real-estate pricing problem.  
We analyze historical housing data to uncover patterns (location, size, condition, age, amenities) and build transparent models that estimate prices with explainable drivers.

When pricing properties, two risks exist:
1. **Underpricing** → lost revenue
2. **Overpricing** → long time-on-market / failed sales

Data-driven valuation helps strike the right balance.

## Business Understanding

Stakeholders (brokers, lenders, developers) need accurate and explainable price estimates.  
Using EDA, we assess how features like **area, rooms, age, neighborhood, lot size, and amenities** influence price, and quantify their impact for both quoting and negotiations.

## Business Objectives

- Predict **sale price** for individual properties
- Identify **key drivers** of price (and their directionality)
- Provide a **robust, auditable pipeline** with stable generalization performance

## Analytical Approach

1. **Data Understanding**
   - Inspect schema, missingness, outliers; align feature semantics (units, categories).

2. **Data Cleaning**
   - Handle missing values; de-duplicate; unify units (e.g., sqft vs m²); winsorize extreme outliers when appropriate.

3. **Feature Engineering**
   - Create **age of property**, room/area **ratios**, total finished area, quality/condition composites.
   - Encode categorical features (e.g., **neighborhood**) and derive **interaction** terms where sensible.
   - Consider **log-transform** of `Price` and skewed numerics.

4. **Modeling**
   - Baseline: **Ordinary Least Squares** (with/without log target).
   - Regularized: **Ridge**, **Lasso**, **ElasticNet** for stable coefficients and variable selection.
   - Tree baselines: **RandomForest/GradientBoosting** for non-linearities (optional comparison).
   - Use **pipelines** with `ColumnTransformer` and **cross-validation**/**GridSearchCV**.

5. **Evaluation**
   - Report **MAE**, **RMSE**, **R²** (cross-validated and on holdout test).
   - Residual diagnostics; error by segment (e.g., neighborhoods, size buckets).
   - Global and local interpretability (coefficients, permutation importance; optional SHAP).

## Tools & Libraries

- **Python** (Jupyter Notebook)
- **pandas**, **numpy**, **scikit-learn**, **matplotlib**, **seaborn**

## Key Insights

This workflow surfaces patterns such as:
- **Positive** association with total living area, number of bathrooms/rooms, garage capacity, and **premium neighborhoods**
- **Negative** association with **age** (or condition issues) and certain distance/lot characteristics
- Interaction effects (e.g., area gains differ by neighborhood/quality)

*(Exact coefficients/feature importances and metrics are reported in the notebook.)*

## Conclusion & Business Impact

A regularized, explainable regression stack provides:
- **Accurate, auditable valuations** for quoting and underwriting
- Visibility into **price drivers** to guide renovations and listing strategies
- Stable performance across neighborhoods and sizes

## Files in this Repository

| File Name | Description |
|-----------|-------------|
| `Housing_Case_Study.ipynb` | Full workflow (EDA → feature engineering → modeling → evaluation) |
| `Housing.csv` | Raw housing dataset used by the notebook |

---

## Author

**Aakash Maskara**  
*M.S. Robotics & Autonomy, Drexel University*  
Data Science | Machine Learning | Quantitative Finance  

[LinkedIn](https://linkedin.com/in/aakashmaskara) • [GitHub](https://github.com/AakashMaskara)
