# customer-spend-forecast
**Project Objective**
The goal of this project is to build a predictive regression model to estimate future customer spend using e-commerce data. By segmenting customers based on predicted value, we can optimise marketing spend through targeted strategies:

High-Value Tier (Upselling): Increase Average Order Value (AOV) by promoting premium products and loyalty rewards.
Value-Conscious Tier (Discounting): Drive conversion and retention by targeting "deal-seekers" with price-sensitive offers.

**Methodology & Feature Engineering**
I trained three models—Linear Regression, XGBoost, and Decision Tree Regressor—using the following features:

Demographics: Age, Gender, Country.
Behavioral: Traffic source, historical spend, and session frequency.
Temporal: Purchase timing (Weekday vs. Weekend).

**Model Performance & Insights**
Model
Linear Regression: 
RMSE:	86.37	
R_Squared:0.07	
It is because of non-linear patterns and high multicollinearity (VIF > 5).

Decision Tree: 
RMSE:	84.75	
R_Squared:0.11	
Improved performance via Target Encoding for 'Country'.

XGBoost: 
RMSE:	82.50	
R_Squared:0.153	
It is the best performer and effectively captured non-linear relationships.

**Findings:**
Data Distribution: 48% of customers had zero spend, resulting in a heavily right-skewed distribution. This explains the lower R_squared as the models struggled to differentiate between "no-spend" and "low-spend" users.
Feature Importance: Behavioral data (historical sessions and past spend) proved far more predictive than demographic data (age, gender, country).
Multicollinearity: High VIF scores were observed for specific countries and traffic sources (Search), suggesting redundant information in the linear model.

Next steps:  (From AI)
3 Suggestions to Improve Your Project
Address the "Zero-Spend" Issue (The "Hurdle" Model): Since 48% of your data is zero, a single regression model will always struggle.

Improvement: Try a Two-Stage Model. First, a Classifier (Logistic Regression/XGBClassifier) to predict if they will spend (Yes/No). Second, a Regressor to predict how much they will spend, trained only on the customers who actually bought something.

Log Transformation: You mentioned log transformation in your text—did you actually apply it? If you log-transform the target variable (Spend), it usually helps Linear Regression handle that "right-skew" much better.

Visualizations: Add a Feature Importance Plot from your XGBoost model to your GitHub. It’s the first thing a data lead will look for to see if the model "makes sense."
