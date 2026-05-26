# 🏭 Industry Annual Revenue Prediction
### A Machine Learning Project by **Next Hikes IT Solution (NHIS)**

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-orange?logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-Champion-green?logo=xgboost)
![License](https://img.shields.io/badge/License-MIT-lightgrey)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Project Overview

This project, focuses on predicting the **Annual Revenue (in Millions)** of companies across multiple industries using supervised machine learning regression techniques.

The pipeline covers the full data science lifecycle — from raw data ingestion and exploratory analysis to feature engineering, model training, hyperparameter tuning, and final model deployment via a serialized `.pkl` file.

---

## 📂 Repository Structure

```
Project_4B_NHIS---Industry-Annual-Revenue-Prediction/
│
├── INDUSTRY.csv                          # Raw dataset (15,000 records)
├── Industry.ipynb                        # Main Jupyter Notebook (EDA + ML pipeline)
├── annual_revenue_prediction.pkl         # Serialized champion model (XGBoost)
├── Industry Annual revenue prediction.pptx  # Project presentation
├── LICENSE
└── README.md
```

---

## 📊 Dataset Summary

| Property         | Details                                      |
|------------------|----------------------------------------------|
| **File**         | `INDUSTRY.csv`                               |
| **Records**      | 15,000                                       |
| **Features**     | 12 (raw) → engineered to more                |
| **Target**       | `annual_revenue_million`                     |
| **Industries**   | Finance, Technology, Retail, Manufacturing, Healthcare |
| **Regions**      | Asia, Europe, North America                  |
| **Countries**    | 4 (USA, India, Germany, Canada)              |

### Feature Description

| Column | Type | Description |
|---|---|---|
| `id` | int | Unique company identifier (dropped in ML) |
| `company_name` | str | Name of the company |
| `industry` | categorical | Industry sector |
| `country` | categorical | Country of operation |
| `region` | categorical | Geographic region |
| `employee_count` | int | Total number of employees |
| `annual_revenue_million` | float | **Target** — Annual revenue in millions ($) |
| `profit_margin_percent` | float | Profit margin percentage |
| `founded_year` | int | Year the company was founded |
| `customer_count` | int | Number of customers |
| `market_rating` | float | Market rating (1–5 scale) |
| `created_date` | datetime | Record creation date |

---

## ⚙️ Feature Engineering

Five new features were derived to improve model performance:

| Feature | Formula |
|---|---|
| `company_age` | `max(year) - founded_year` |
| `rev_per_employee` | `annual_revenue_million / (employee_count + 1)` |
| `rev_per_customer` | `annual_revenue_million / (customer_count + 1)` |
| `emp_x_rating` | `employee_count × market_rating` |
| `profit_x_rating` | `profit_margin_percent × market_rating` |

Categorical features (`industry`, `country`, `region`) were encoded using **Label Encoding**.

---

## 🤖 Machine Learning Pipeline

### Train / Test Split
- **80% Training / 20% Testing** (`random_state=42`)
- Features were scaled using **StandardScaler**

### Baseline Models Evaluated

| Model | Description |
|---|---|
| Linear Regression | Simple linear baseline |
| Decision Tree | Non-linear tree-based model |
| Random Forest | Ensemble of decision trees |
| Gradient Boosting | Sequential boosting ensemble |
| XGBoost | Optimized gradient boosting |

### Hyperparameter Tuning

GridSearchCV (5-fold CV) was applied to the top 3 models:

| Model | CV R² | Test R² | RMSE | MAE | MAPE |
|---|---|---|---|---|---|
| **XGBoost** ⭐ | **0.9975** | **0.9980** | **12.75 M** | **7.69 M** | **1.77%** |
| Gradient Boosting | 0.9965 | 0.9967 | 16.43 M | 11.87 M | 2.89% |
| Random Forest | 0.9673 | 0.9708 | 49.08 M | 32.57 M | 8.40% |

---

## 🏆 Champion Model — XGBoost

```
=======================================================
  CHAMPION: XGBoost
=======================================================
  R²   : 0.998030
  RMSE : 12.7463 M
  MSE  : 162.4679 M²
  MAE  : 7.6878 M
  MAPE : 1.7691 %
=======================================================
```

The champion model was serialized and saved as:
```
annual_revenue_prediction.pkl
```

---

## 🧪 Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3.x |
| Data Processing | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Statistics | SciPy |
| Machine Learning | Scikit-Learn, XGBoost |
| Model Persistence | Pickle |
| Notebook | Jupyter Notebook |

---

## 📋 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.
