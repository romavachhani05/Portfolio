# 🛡️ Amazon Buyer Abuse Risk Detection and Analytics

This project simulates a buyer abuse prevention analytics pipeline inspired by Amazon's Buyer Abuse Prevention (BAP) team. It demonstrates data modeling, SQL analysis, machine learning, and business intelligence practices relevant to detecting abusive patterns in e-commerce transactions.

---

## 📌 Project Overview

**Objective:** Identify potential buyer abuse using simulated transaction data through:

- SQL-based behavioral analysis
- Exploratory data analysis (EDA)
- Machine Learning classification
- Business intelligence visualizations

---

## 📂 Project Structure

```
buyer-abuse-risk-insights/
│
├── data/                            # Simulated SQLite database
├── eda_analysis.py                 # Python EDA script (visuals)
├── abuse_prediction_model.py       # ML model for abuse classification
├── sql/
│   └── buyer_abuse_insights.sql    # Insightful SQL queries
├── dashboards/                     # Power BI or Tableau (optional)
├── classification_report.csv       # Model performance summary
├── confusion_matrix.csv            # Prediction breakdown
├── README.md
└── requirements.txt
```

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

See: [`SQL Insights`](https://github.com/romavachhani05/Portfolio/tree/main/03_Amazon_Buyer-Abuse-Risk-Insights/SQL_Insights)




---

## 📊 Visual Analytics Using Python

Run `eda_analysis.py` to generate:

- Return rate by device
- Abuse hotspots by location
- Refund amount distribution

See: [`Visual Analytics Using Python`](https://github.com/romavachhani05/Portfolio/tree/main/03_Amazon_Buyer-Abuse-Risk-Insights/Visual_Analytics_Using_Python)

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

  
See: [` Machine Learning`](https://github.com/romavachhani05/Portfolio/tree/main/Amazon_Buyer-Abuse-Risk-Insights/Machine%20Learning)


---

## 🚀 How to Run

1. Clone the repo
2. Ensure Python 3.x is installed
3. Install dependencies:
    ```
    pip install -r requirements.txt
    ```
4. Run analysis:
    ```
    python eda_analysis.py
    python abuse_prediction_model.py
    ```

---

## 🎯 Role Alignment

This project aligns with the responsibilities of a **Business Analyst on Amazon's Buyer Abuse Prevention (BAP)** team by demonstrating:

- Data modeling and EDA on abusive patterns
- Collaboration with ML for risk scoring
- Business-oriented insights through SQL and BI tools
- Practical storytelling through visualizations and metrics

---

## 🛠️ Future Enhancements

- Deploy model via Flask or Streamlit for scoring
- Integrate AWS S3 and Lambda for real-time ingestion
- Add Power BI dashboards

---

## 📬 Contact

**Author:** Roma Vachhani  
Feel free to reach out via [LinkedIn](#) or GitHub for collaboration or feedback!
