# ==============================
# 📊 CAPSTONE PROJECT (ALL-IN-ONE)
# ==============================

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# ------------------------------
# 1. LOAD DATA
# ------------------------------
try:
    df = pd.read_csv("sales_data.csv")
    print("✅ Dataset Loaded Successfully\n")
except:
    print("❌ Error: Make sure 'sales_data.csv' is in the same folder")
    exit()

# ------------------------------
# 2. DATA CLEANING
# ------------------------------
print("🔹 Cleaning Data...")

# Remove duplicates
df.drop_duplicates(inplace=True)

# Handle missing values
df.fillna(method='ffill', inplace=True)

# Standardize column names
df.columns = df.columns.str.strip().str.lower()

# Convert date column
if 'date' in df.columns:
    df['date'] = pd.to_datetime(df['date'])

print("✅ Cleaning Done\n")

# ------------------------------
# 3. DATA ANALYSIS
# ------------------------------
print("🔹 Performing Analysis...\n")

print("Basic Statistics:\n", df.describe())

if 'sales' in df.columns:
    total_sales = df['sales'].sum()
    avg_sales = df['sales'].mean()
    max_sales = df['sales'].max()
    min_sales = df['sales'].min()

    print(f"\nTotal Sales: {total_sales}")
    print(f"Average Sales: {avg_sales}")
    print(f"Max Sales: {max_sales}")
    print(f"Min Sales: {min_sales}")

if 'category' in df.columns:
    category_sales = df.groupby('category')['sales'].sum()
    print("\nSales by Category:\n", category_sales)

# ------------------------------
# 4. VISUALIZATION (DASHBOARD STYLE)
# ------------------------------
print("\n🔹 Generating Visualizations...")

plt.figure(figsize=(14,8))

# Plot 1: Sales Distribution
plt.subplot(2,2,1)
sns.histplot(df['sales'], bins=20)
plt.title("Sales Distribution")

# Plot 2: Category Sales
if 'category' in df.columns:
    plt.subplot(2,2,2)
    df.groupby('category')['sales'].sum().plot(kind='bar')
    plt.title("Sales by Category")

# Plot 3: Time Series
if 'date' in df.columns:
    plt.subplot(2,2,3)
    df.set_index('date')['sales'].plot()
    plt.title("Sales Trend Over Time")

# Plot 4: Correlation Heatmap
plt.subplot(2,2,4)
sns.heatmap(df.corr(numeric_only=True), annot=True)
plt.title("Correlation Heatmap")

plt.tight_layout()
plt.show()

# ------------------------------
# 5. INSIGHTS
# ------------------------------
print("\n🔹 INSIGHTS:\n")

if 'sales' in df.columns:
    print(f"👉 Average sales is {avg_sales:.2f}")
    print(f"👉 Highest sale recorded is {max_sales}")
    print(f"👉 Lowest sale recorded is {min_sales}")

if 'category' in df.columns:
    top_category = df.groupby('category')['sales'].sum().idxmax()
    print(f"👉 Top performing category is: {top_category}")

if 'date' in df.columns:
    print("👉 Sales trend visualization shows growth/decline patterns over time")

print("\n✅ Project Completed Successfully!")
