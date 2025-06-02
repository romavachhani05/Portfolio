**This repository is licensed as "View Only – No reuse without permission."**

# 🛡️ Risk & Fraud Analytics for E-commerce Platforms

This project simulates a buyer abuse prevention analytics pipeline inspired by Risk & Fraud Analytics for E-commerce Platforms. It demonstrates data modeling, SQL analysis, machine learning, and business intelligence practices relevant to detecting abusive patterns in e-commerce transactions.

---

## 📌 Project Overview

**Objective:** Identify potential buyer abuse using simulated transaction data through:

- SQL-based behavioral analysis
- Exploratory data analysis (EDA)
- Machine Learning classification
- Business intelligence visualizations

---

## 🧪 Dataset Description

Simulated dataset contains 10,000 buyer transactions with fields:

- `buyer_id`, `order_id`, `product_id`
- `order_date`, `return_date`
- `refund_amount`, `order_amount`
- `buyer_location`, `ip_location`, `device_type`
- `return_reason`, `is_abusive` (target)

Additional features:
- `return_flag`, `location_mismatch`, `refund_ratio`

---

## 🔍 SQL Insights

Sample queries included:
- Top abusive buyers and locations
- Abuse rate by device type
- Refund behavior
- Location/IP mismatch statistics

See: [`SQL Insights`](https://github.com/romavachhani05/Portfolio/tree/main/03_Risk_Fraud_%20Analytics_for_Ecommerce_Platforms/SQL_Insights)


---

## 📊 Visual Analytics Using Python

Run `eda_analysis.py` to generate:

- Return rate by device
- Abuse hotspots by location
- Refund amount distribution

See: [`Visual Analytics Using Python`](https://github.com/romavachhani05/Portfolio/tree/main/03_Risk_Fraud_%20Analytics_for_Ecommerce_Platforms/Visual_Analytics_Using_Python)

Charts saved in `.png` files.


---

## 🤖 Machine Learning

Model: **Random Forest Classifier**  
Features used:
- Order amount, refund amount
- Return flag, location mismatch
- Refund ratio, encoded device type

Output:
- classification_report.csv
- confusion_matrix.csv

  
See: [` Machine Learning`](https://github.com/romavachhani05/Portfolio/tree/main/03_Risk_Fraud_%20Analytics_for_Ecommerce_Platforms/Machine_Learning)


---



## 📬 Contact

**Author:** Roma Vachhani  
Feel free to reach out via [LinkedIn](#) or GitHub for collaboration or feedback!
