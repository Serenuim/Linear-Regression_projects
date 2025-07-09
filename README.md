# Linear-Regression_projects
# 🏡 California Housing Price Prediction

## 📌 Overview

This project applies multiple machine learning models to predict median house values across California using the **California Housing Dataset**. It includes complete preprocessing, feature engineering, evaluation, and model comparison.

---

## 📁 Dataset

- **Source**: California Housing dataset (from Scikit-learn / Kaggle)
- **Features**:
  - Location: `longitude`, `latitude`
  - Demographics: `population`, `households`, `median_income`
  - Housing: `total_rooms`, `total_bedrooms`, `housing_median_age`
  - Categorical: `ocean_proximity`
  - Target: `median_house_value`

---

## ⚙️ Workflow Summary

### ✅ Data Cleaning
- Imputed missing values in `total_bedrooms` using **group-wise median by `ocean_proximity`**
- Converted boolean features to integers
- Removed outliers using **IQR-based filtering**

### ✅ Feature Engineering
- Added new features:
  - `bedrooms_per_room`
  - `population_per_household`
- Encoded categorical column `ocean_proximity` using **One-Hot Encoding**

### ✅ Exploratory Data Analysis
- Heatmap used to visualize feature correlation
- Top correlation: `median_income`, `ocean_proximity_<1H OCEAN`, `total_rooms`
- Strong negative correlation: `ocean_proximity_INLAND`

---

## 🤖 Models Used & Results

| Model                | R² (Train) | R² (Test) | MSE (Test)         |
|----------------------|------------|-----------|--------------------|
| Linear Regression     | 0.5561     | 0.5473    | 4.14 Billion        |
| Polynomial Regression | **0.5868** | **0.5828**| **3.81 Billion** ✅ |
| SGD Regressor         | 0.5541     | 0.5468    | 4.14 Billion        |
| Ridge Regression      | 0.5560     | 0.5473    | 4.14 Billion        |
| Lasso Regression      | 0.5558     | 0.5473    | 4.14 Billion        |

📌 **Polynomial Regression** performed best, revealing non-linear relationships between income, location, and house prices.

---

## 🔁 Cross-Validation

- Used `cross_val_score()` with 5-fold CV
- Averaged R² scores across folds for stability
- Prevented overfitting to a single train-test split

---

## 📈 Insights

- 💵 **Income is the strongest predictor** of house value (`R² = 0.63`)
- 🗺️ Inland homes are cheaper; homes near water are more expensive
- 📊 Ratios like `bedrooms_per_room` and `income_per_household` improved performance

---

## 🧪 Evaluation Metrics

- **R² Score** — measures how well variance is explained
- **MSE** — average squared error (lower is better)
- **Cross-validation** — generalization estimate using 5 folds

---

## 📚 Tech Stack

- Python 3
- Pandas, NumPy
- Scikit-learn
- Seaborn, Matplotlib

---

## 🚀 Future Work

- Add **Random Forest**, **XGBoost**, and **Gradient Boosting**
- Perform **hyperparameter tuning** with GridSearchCV
- Deploy model using **Streamlit or Flask**
- Use **log-transformed features** to reduce skew
---
## 🙏 Acknowledgments

- [Scikit-learn Datasets](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.fetch_california_housing.html)
- Thanks to the open-source community for the tools and libraries used in this project.
