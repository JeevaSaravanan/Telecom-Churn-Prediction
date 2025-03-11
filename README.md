# Telecom Customer Churn Prediction

This project aims to analyze customer churn in the telecommunications industry using machine learning. By accurately predicting churn, telecom companies can proactively implement retention strategies, minimize revenue loss, and improve customer satisfaction.

## Overview

**Churn** is a critical issue in the telecom industry, referring to the rate at which customers stop using a company's services. Due to increased competition, retaining existing customers has become significantly more cost-effective than acquiring new ones. This project employs advanced machine learning techniques to predict customer churn, enabling targeted retention strategies and efficient customer relationship management.

## Objectives

- Identify and understand key factors influencing customer churn.
- Build predictive models to accurately forecast customer churn.
- Provide actionable insights to help the company proactively retain valuable customers.

## Dataset Description

The analysis utilizes an **IBM Telco Customer Churn** dataset containing **7,043 customer records** from a fictional telecom company, detailing various demographic, geographic, and service-related attributes.

### Key Features:

- **Customer Demographics**:
  - Gender, Senior Citizen, Partner, Dependents.
  
- **Geographic Information**:
  - Country, State, City, Zip Code, Latitude, Longitude.

- **Customer Tenure & Financial Details**:
  - Tenure Months, Monthly Charges, Total Charges, Customer Lifetime Value (CLTV).

- **Service Subscription Details**:
  - Phone Service, Multiple Lines, Internet Service (DSL, Fiber Optic, Cable), Online Security, Online Backup, Device Protection, Tech Support, Streaming TV, Streaming Movies.

- **Contractual & Billing Information**:
  - Contract Type, Paperless Billing, Payment Method.

- **Churn Indicators**:
  - Churn Label (Yes/No), Churn Value (1/0), Churn Score (0-100), Churn Reason.

### Special Attributes:

- **Customer Lifetime Value (CLTV)**:  
  A predicted measure indicating the expected profitability of each customer. Higher CLTV implies higher customer value, thus necessitating stronger retention efforts.

- **Churn Score**:  
  Calculated via IBM SPSS Modeler, it quantifies the likelihood of churn based on multiple contributing factors.

### Dataset Source:
- **IBM Telco Customer Churn**  
  - [Dataset Description](https://community.ibm.com/community/user/businessanalytics/blogs/steven-macko/2019/07/11/telco-customer-churn-1113)
  - [Dataset Download](https://community.ibm.com/accelerators/?context=analytics&query=telco%20churn&type=Data&product=Cognos%20Analytics)


## Methodology

The project includes several stages:

### Exploratory Data Analysis (EDA)
   ![](/Images/churn.png)

   In the dataset, 73.5% of customer are retained and 26.5% has churned.

   - **CLTV Analysis**:  
  High-value customers identified via CLTV are highlighted for proactive churn prevention strategies.

![](/Images/dist-cltv-churn.png)

- The violin plot compares the distribution of **Customer Lifetime Value (CLTV)** between churned and non-churned customers.
- Both groups exhibit similar CLTV distributions overall, indicating that churn affects customers across various value levels.
- However, churned customers have a slightly denser distribution around moderate CLTV values, highlighting that churn occurs frequently among moderately valuable customers.
- Notably, some high-value customers also churn, emphasizing the importance of monitoring churn even among high-value segments.

   ![](/Images/cali-map.png)

   ![](/Images/churn-reason.png)
   In the 26.5% churned customer, 19.6% showed dissatisfaction with Customer Support, 18.2% showed dissatisfaction with Product and Service, where 33.3% showed interest with competitors.

   Closer look on citywise 

![](/Images/la-churn.png)

![](/Images/iw-churn.png)

![](/Images/tenure.png)

As can be seen, most of the monthly contracts last for a few months, while the 2 years contracts tend to last for years, with a great increase towards the greater values of tenure in this dataset. This implies that customers with a great commitment at the beginning, like a 2-year contract, tend to stay with the company for a longer period of time. Long-term contracts usually have contractual fines. Therefore, customers have to wait until the end of the contract to churn. It is not clear if it is the case. A time-series data would be better to study this.

![](/Images/monthly-charges.png)

Customer with high monthly charges tend to leave, while the customers with minimum monthly charges tends to stay. 

![](/Images/totalcharge.png)

- Churned customers tend to have lower total charges, typically below $2000, suggesting these customers generally leave earlier or spend less during their tenure.
- Non-churned customers show a wider spread, with higher total charges indicating longer-term relationships and cumulative spending.


Understanding Churn with Tenure, Charges and Payment Methods:

![](/Images/contract.png)

Here we could understand the customers with Month-to-Month leave more compared to people with long term commitments.

![](/Images/payment-method.png)

Here we could understand the customers with Electronic Check as payment method leaves indicating the hasle in traditional payment methodolgies. More data on this will help us built a better picture.


## Results & Insights

- **Model Performance**:  
  Evaluation and comparison of multiple models identified key models with high predictive accuracy and good generalization capabilities.

| Model                | Test AUC | Test Accuracy | Test F1 | Test Precision | Test Recall |
|----------------------|----------|---------------|---------|----------------|-------------|
| Logistic Regression  | 0.853    | 0.747         | 0.626   | 0.515          | 0.797       |
| Random Forest        | 0.850    | 0.781         | 0.641   | 0.568          | 0.736       |
| Support Vector Machine | 0.669    | 0.730         | 0.372   | 0.486          | 0.301       |
| Gradient Boosting    | 0.852    | 0.795         | 0.574   | 0.639          | 0.520       |
| XGBoost              | 0.854    | 0.802         | 0.590   | 0.654          | 0.538       |
| LightGBM             | 0.851    | 0.802         | 0.561   | 0.680          | 0.478       |
| Random Forest        | 0.850    | 0.781         | 0.641   | 0.568          | 0.736       |


- **Feature Importance**:  
  SHAP plots indicate which features significantly contribute to predicting customer churn, providing actionable insights.

![](/Images/shap.png)

This **SHAP beeswarm plot** visualizes the impact of each feature on predicting customer churn using the machine learning model:

- **Contract Month-to-month** and **High Monthly Charges** strongly increase churn likelihood.
- **Longer Tenure Months** and **Dependents** significantly reduce churn likelihood.
- **Fiber Optic Internet** and **Electronic Check Payment** methods positively correlate with churn.
- Other factors, like **CLTV**, **Tech Support**, and **Online Security**, have moderate but meaningful impacts.

This visualization helps clarify which customer characteristics drive churn predictions most significantly.


## Business Action Plan

Based on predictive modeling insights, the following strategic actions are recommended:

- **Proactive Retention Campaigns**:
  - Target customers with high churn probability and high CLTV.

- **Enhanced Customer Engagement**:
  - Offer personalized incentives and improved customer service experiences.

- **Periodic Monitoring**:
  - Regularly update the churn model and monitor customer behavior to quickly adapt to changing churn patterns.



## Technologies Used

- **Python** (Pandas, NumPy, Scikit-Learn, Seaborn, Matplotlib)
- **Machine Learning Models**: Logistic Regression, Random Forest, SVM, KNN, Decision Tree, Gradient Boosting, XGBoost, LightGBM, CatBoost
- **SHAP** for explainability and feature importance.


## Project Structure

```
project-root/
│
├── data/
│   └── telecom_data.csv
│
├── notebooks/
│   ├── 01_Exploratory_Data_Analysis.ipynb
│   ├── 02_Preprocessing.ipynb
│   ├── 03_Model_Training_and_Evaluation.ipynb
│   └── 04_Model_Explainability.ipynb
│
├── Modules/
│   ├── Constants.py
│   ├── Helper_function.py
│   ├── Utils.py
│
├── Images/
│   └── CLTV_Churn_Violin.png
│
└── README.md
```
## References

- [IBM Telco Customer Churn Dataset Description](https://community.ibm.com/community/user/businessanalytics/blogs/steven-macko/2019/07/11/telco-customer-churn-1113)
- [IBM Cognos Analytics Accelerators](https://community.ibm.com/accelerators/?context=analytics&query=telco%20churn&type=Data&product=Cognos%20Analytics)


