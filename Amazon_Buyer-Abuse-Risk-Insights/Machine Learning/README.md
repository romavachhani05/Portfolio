## 🤖 Machine Learning

import sqlite3
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report, confusion_matrix
from sklearn.preprocessing import LabelEncoder

# Load data from SQLite
db_path = "buyer_abuse_simulation.db"  # Update path if necessary
conn = sqlite3.connect(db_path)
df = pd.read_sql_query("SELECT * FROM buyer_transactions", conn)
conn.close()

# Feature Engineering
df['return_flag'] = df['return_date'].notnull().astype(int)
df['location_mismatch'] = (df['buyer_location'] != df['ip_location']).astype(int)
df['refund_ratio'] = df['refund_amount'] / df['order_amount']

# Encode device_type
le_device = LabelEncoder()
df['device_encoded'] = le_device.fit_transform(df['device_type'])

# Select features and target
features = [
    'order_amount', 'refund_amount', 'return_flag',
    'location_mismatch', 'refund_ratio', 'device_encoded'
]
target = 'is_abusive'

X = df[features].fillna(0)
y = df[target]

# Train/Test Split
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=42, stratify=y
)

# Train model
model = RandomForestClassifier(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

# Evaluate model
y_pred = model.predict(X_test)
report = classification_report(y_test, y_pred)
conf_matrix = confusion_matrix(y_test, y_pred)

# Print results
print("=== Classification Report ===")
print(report)

print("\n=== Confusion Matrix ===")
print(conf_matrix)


![image](https://github.com/user-attachments/assets/b4f7e43e-d8c2-4ccb-a864-d354d42123fd)
