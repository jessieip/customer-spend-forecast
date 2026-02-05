# 🛍️ Customer Spend Forecast

## 🎯 Project Objective
The goal of this project is to build a predictive regression model to estimate future customer spend using e-commerce data. By segmenting customers based on predicted value, we can optimize marketing spend through targeted strategies:

* **High-Value Tier (Upselling):** Increase Average Order Value (AOV) by promoting premium products and loyalty rewards.
* **Value-Conscious Tier (Discounting):** Drive conversion and retention by targeting "deal-seekers" with price-sensitive offers.

---

## 🛠️ Methodology & Feature Engineering
I trained three models—**Linear Regression, XGBoost, and Decision Tree Regressor**—using the following feature sets:

* **Demographics:** Age, Gender, Country.
* **Behavioral:** Traffic source, historical spend, and session frequency.
* **Temporal:** Purchase timing (Weekday vs. Weekend).

---

## 📊 Model Performance & Insights

| Model | RMSE | $R^2$ | Key Observations |
| :--- | :--- | :--- | :--- |
| **Linear Regression** | 86.37 | 0.07 | Struggled with non-linear patterns; high multicollinearity (VIF > 5). |
| **Decision Tree** | 84.75 | 0.11 | Improved via Target Encoding for 'Country'. |
| **XGBoost** | **82.50** | **0.153** | **Best Performer**: captured complex non-linear relationships. |

### 🔍 Key Findings
* **Data Distribution:** 48% of customers had zero spend, resulting in a **heavily right-skewed distribution**. This explains the low $R^2$, as models struggled to differentiate between "no-spend" and "low-spend" users.
* **Feature Importance:** Behavioral data (historical sessions and past spend) proved far more predictive than demographic data (age, gender, country).
* **Multicollinearity:** High VIF scores in the Linear model for specific countries and traffic sources (e.g. Search) indicated redundant features.



---

## 🚀 Future Improvements

To further improve model accuracy, the next iterations will focus on:

1.  **Implementing a "Hurdle" Model:**
    * **Stage 1:** A Binary Classifier (e.g., XGBClassifier) to predict *if* a customer will spend ($Spend > 0$).
    * **Stage 2:** A Regressor to predict *how much* they will spend, trained only on the spending population.
3.  **Target Transformation:** Applying **Log Transformation** to the target variable to normalize the right-skewed spend distribution.
4.  **Advanced Feature Engineering:** Creating "Recency" features (days since last session) to complement the frequency data.
