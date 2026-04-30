import pandas as pd
import matplotlib.pyplot as plt

# -----------------------------
# 1. Load Dataset
# -----------------------------
# Replace with your file name
df = pd.read_csv("sales_data.csv")

# -----------------------------
# 2. Data Cleaning
# -----------------------------
print("Before Cleaning:\n", df.isnull().sum())

# Handle missing values
df['Sales'] = df['Sales'].fillna(df['Sales'].mean())
df['Product'] = df['Product'].fillna("Unknown")
df['Region'] = df['Region'].fillna("Unknown")

# Convert Date column
df['Date'] = pd.to_datetime(df['Date'])

print("\nAfter Cleaning:\n", df.isnull().sum())

# -----------------------------
# 3. Aggregation
# -----------------------------

# Total Sales per Product
product_sales = df.groupby('Product')['Sales'].sum().sort_values(ascending=False)
print("\nTotal Sales per Product:\n", product_sales)

# Region-wise Performance
region_sales = df.groupby('Region')['Sales'].sum().sort_values(ascending=False)
print("\nRegion-wise Sales:\n", region_sales)

# -----------------------------
# 4. Visualization
# -----------------------------

# Sales Trend (Line Chart)
daily_sales = df.groupby('Date')['Sales'].sum()

plt.figure()
plt.plot(daily_sales.index, daily_sales.values)
plt.title("Sales Trend Over Time")
plt.xlabel("Date")
plt.ylabel("Sales")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Top Products (Bar Chart)
top_products = product_sales.head(5)

plt.figure()
plt.bar(top_products.index, top_products.values)
plt.title("Top 5 Products")
plt.xlabel("Product")
plt.ylabel("Sales")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# -----------------------------
# 5. Bonus Analysis
# -----------------------------

# Monthly Growth
df['Month'] = df['Date'].dt.to_period('M')
monthly_sales = df.groupby('Month')['Sales'].sum()

growth = monthly_sales.pct_change() * 100
print("\nMonthly Growth (%):\n", growth)

# Best Performing Region
best_region = region_sales.idxmax()
print("\nBest Performing Region:", best_region)

# -----------------------------
# 6. Key Insights
# -----------------------------
print("\n🔍 Key Insights:")

print(f"1. Top selling product: {product_sales.idxmax()}")
print(f"2. Best region: {best_region}")
print(f"3. Highest monthly growth: {growth.max():.2f}%")
print(f"4. Lowest monthly growth: {growth.min():.2f}%")
print(f"5. Average sales: {df['Sales'].mean():.2f}")
