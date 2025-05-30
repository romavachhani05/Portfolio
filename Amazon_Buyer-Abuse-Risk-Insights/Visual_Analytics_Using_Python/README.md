# eda_analysis.py

import sqlite3
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load data from SQLite
db_path = "buyer_abuse_simulation.db"  # Update if path changes
conn = sqlite3.connect(db_path)
df = pd.read_sql_query("SELECT * FROM buyer_transactions", conn)
conn.close()

# Convert date columns
df['order_date'] = pd.to_datetime(df['order_date'])
df['return_date'] = pd.to_datetime(df['return_date'])

# Add helper columns
df['return_flag'] = df['return_date'].notnull().astype(int)
df['location_mismatch'] = (df['buyer_location'] != df['ip_location']).astype(int)

# Plot 1: Return Rate by Device Type
plt.figure(figsize=(6, 4))
sns.barplot(x='device_type', y='return_flag', data=df)
plt.title('Return Rate by Device Type')
plt.ylabel('Return Rate')
plt.xlabel('Device Type')
plt.tight_layout()
plt.savefig("plot_return_rate_by_device.png")
plt.close()

# Plot 2: Abuse Rate by Buyer Location (Top 10)
top_locations = df['buyer_location'].value_counts().head(10).index
subset = df[df['buyer_location'].isin(top_locations)]
abuse_by_location = subset.groupby('buyer_location')['is_abusive'].mean().sort_values(ascending=False)

plt.figure(figsize=(8, 4))
abuse_by_location.plot(kind='bar')
plt.title('Abuse Rate by Buyer Location (Top 10)')
plt.ylabel('Abuse Rate')
plt.xlabel('Buyer Location')
plt.tight_layout()
plt.savefig("plot_abuse_rate_by_location.png")
plt.close()

# Plot 3: Refund Amount Distribution
plt.figure(figsize=(6, 4))
sns.histplot(df[df['refund_amount'] > 0]['refund_amount'], bins=30, kde=True)
plt.title('Refund Amount Distribution')
plt.xlabel('Refund Amount')
plt.tight_layout()
plt.savefig("plot_refund_distribution.png")
plt.close()

print("Charts saved as PNG files.")

![image](https://github.com/user-attachments/assets/e65496a1-fd96-44a7-913a-d8be83015a8a)
