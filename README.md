import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load your CSV file
df = pd.read_csv("traffic.csv")

# Convert date column to datetime
df['Date'] = pd.to_datetime(df['Date'])

# Line chart: Page Views over Time
plt.figure(figsize=(12, 6))
sns.lineplot(data=df, x='Date', y='Page Views', marker='o')
plt.title('Page Views Over Time')
plt.xlabel('Date')
plt.ylabel('Page Views')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Line chart: Sessions Over Time
plt.figure(figsize=(12, 6))
sns.lineplot(data=df, x='Date', y='Sessions', marker='o', color='orange')
plt.title('Sessions Over Time')
plt.xlabel('Date')
plt.ylabel('Sessions')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Histogram: Bounce Rate Distribution
plt.figure(figsize=(8, 5))
sns.histplot(df['Bounce Rate'], bins=20, kde=True)
plt.title('Bounce Rate Distribution')
plt.xlabel('Bounce Rate (%)')
plt.tight_layout()
plt.show()

# Traffic Source breakdown (Pie Chart)
if 'Traffic Source' in df.columns:
    source_counts = df['Traffic Source'].value_counts()
    plt.figure(figsize=(6, 6))
    plt.pie(source_counts.values, labels=source_counts.index, autopct='%1.1f%%', startangle=140)
    plt.title('Traffic Source Distribution')
    plt.tight_layout()
    plt.show()
