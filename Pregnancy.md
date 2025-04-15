# Pregnancy Data Analysis: Birth Weight Prediction

## 📌 Introduction
This project analyzes pregnancy data to identify factors influencing birth weight (BWT), gestation periods, and maternal health. The dataset includes variables such as mother’s age, weight, height, smoking status, parity, and gestation duration. The goal is to explore relationships between these variables and predict birth weight using regression models.

---

## 🎯 Objective
1. Identify factors affecting birth weight  
2. Determine the range of gestation periods  
3. Calculate average birth weight and its relationship with gestation  
4. Assess the impact of maternal age on birth weight  

---

## ❓ Analytical Questions

### 🔍 Descriptive
- What are the mean and median values for weight, height, and birth weight?
- What is the range of gestation periods?
- Are there any outliers affecting the analysis?
- What is the average gestation period?

### 🔎 Exploratory
- Which variable most strongly influences birth weight?
- Is there a correlation between maternal age and birth weight?
- How does smoking status affect birth weight?
- Are birth weight and maternal weight/height correlated?
- Does parity influence birth weight?

### 🔮 Predictive
- Can birth weight be predicted using relevant features?
- Which variable has the greatest predictive power?

---

## 🧹 Data Cleaning

### Key Steps
- **Missing Values**: Imputed using `IterativeImputer`, ensuring all rows are usable for regression.
- **Outlier Removal**: Trimmed data using 10th–90th percentiles.
- **Transformations**: Applied log transformation to normalize distributions (`bwt`, `gestation`, `age`, `height`, `weight`).

---

## 📊 Analysis (Log-Transformed Data)

### Correlation Analysis
- `gestation` (r = 0.71) and `weight` (r = 0.45) strongly correlated with `bwt`.
- `age` showed weak correlation (r = 0.12).

### Regression Results
- **Model**: `bwt ~ age + gestation + weight + height`
- **Significant Predictors**: `gestation` and `weight` (p < 0.05)
- **R-squared**: 0.45
- **Heteroscedasticity**: Breusch-Pagan test rejected homoscedasticity
- **Fix**: Weighted Least Squares (WLS) improved model with weights = `1 / residuals²`
- **Post-outlier removal**: `R-squared` increased to 0.47

### Assumption Checks
- **Normality**: Residuals were nearly normal
- **Homoscedasticity**: Improved with WLS

---

## 📉 Raw Data Analysis (Without Log Transformation)

- Lower R² value (≈0.38)
- Higher heteroscedasticity
- More skewness in gestation and BWT distributions

---

## 📌 Key Insights

- **Top Predictors**: Gestation length and maternal weight
- **Non-significant**: Maternal age, smoking, and parity (in this dataset)
- **Outlier Removal**: Boosted model accuracy but reduced sample size
- **Transformations**: Improved model assumptions and fit

---

## ✅ Conclusion

- **Best Model**: WLS regression on log-transformed data
- **Recommendations**:
  - Explore variable interactions (e.g., `smoke × weight`)
  - Use cross-validation or external datasets for more robust evaluation

---


