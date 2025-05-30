# SQL Insight

## The following SQL insights have been generated from your synthetic buyer abuse dataset:
	1. Top 10 Buyers by Number of Returns
	2. Abuse Rate by Device Type
	3. Top 5 Locations by Abuse Count
	4. Average Refund Amount for Abusive vs Non-Abusive Buyers
	5. Mismatch Rate Between Buyer Location and IP Location

### 1.buyer_abuse_insights.sql
#### 1. Top 10 Buyers by Number of Returns
SELECT 
    buyer_id, 
    COUNT(*) AS return_count
FROM buyer_transactions
WHERE return_date IS NOT NULL
GROUP BY buyer_id
ORDER BY return_count DESC
LIMIT 10;


#### 2. Abuse Rate by Device Type
SELECT 
    device_type, 
    COUNT(*) AS total_transactions,
    SUM(is_abusive) AS total_abuse,
    ROUND(SUM(is_abusive) * 1.0 / COUNT(*), 3) AS abuse_rate
FROM buyer_transactions
GROUP BY device_type;


#### 3. Top 5 Locations by Abuse Count
SELECT 
    buyer_location, 
    COUNT(*) AS abuse_count
FROM buyer_transactions
WHERE is_abusive = 1
GROUP BY buyer_location
ORDER BY abuse_count DESC
LIMIT 5;


#### 4. Average Refund Amount for Abusive vs Non-Abusive Buyers
SELECT 
    is_abusive,
    COUNT(*) AS transactions,
    ROUND(AVG(refund_amount), 2) AS avg_refund
FROM buyer_transactions
GROUP BY is_abusive;


#### 5. Mismatch Rate Between Buyer Location and IP Location
SELECT 
    COUNT(*) AS total_mismatches
FROM buyer_transactions
WHERE buyer_location != ip_location;
![image](https://github.com/user-attachments/assets/a2286ed5-8c40-4526-ae13-6a77ffa0d5b6)
