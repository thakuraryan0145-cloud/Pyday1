import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# -------------------------------
# 1. LOAD DATA
# -------------------------------
# Sample CSV format:
# Date,Price
# 2024-01-01,100

df = pd.read_csv("stock_data.csv")

# Convert Date column to datetime
df['Date'] = pd.to_datetime(df['Date'])

# Sort by date
df = df.sort_values('Date')

# -------------------------------
# 2. MOVING AVERAGE
# -------------------------------
df['MA_5'] = df['Price'].rolling(window=5).mean()
df['MA_10'] = df['Price'].rolling(window=10).mean()

# -------------------------------
# 3. IDENTIFY PEAKS & DROPS
# -------------------------------
# Using simple logic
df['Peak'] = df['Price'][(df['Price'].shift(1) < df['Price']) & 
                        (df['Price'].shift(-1) < df['Price'])]

df['Drop'] = df['Price'][(df['Price'].shift(1) > df['Price']) & 
                        (df['Price'].shift(-1) > df['Price'])]

# -------------------------------
# 4. VOLATILITY (BONUS)
# -------------------------------
df['Returns'] = df['Price'].pct_change()
volatility = df['Returns'].std()

print("Volatility:", volatility)

# -------------------------------
# 5. VISUALIZATION
# -------------------------------
plt.figure(figsize=(12,6))

# Price line
plt.plot(df['Date'], df['Price'], label='Price')

# Moving averages
plt.plot(df['Date'], df['MA_5'], label='MA 5')
plt.plot(df['Date'], df['MA_10'], label='MA 10')

# Peaks & Drops
plt.scatter(df['Date'], df['Peak'], label='Peaks')
plt.scatter(df['Date'], df['Drop'], label='Drops')

plt.title("Stock Price Analysis")
plt.xlabel("Date")
plt.ylabel("Price")
plt.legend()
plt.grid()

plt.show()

# -------------------------------
# 6. MULTIPLE STOCKS (BONUS)
# -------------------------------
# Example: Compare multiple CSV files

files = ["stock1.csv", "stock2.csv"]

plt.figure(figsize=(12,6))

for file in files:
    data = pd.read_csv(file)
    data['Date'] = pd.to_datetime(data['Date'])
    data = data.sort_values('Date')
    
    plt.plot(data['Date'], data['Price'], label=file)

plt.title("Multiple Stock Comparison")
plt.legend()
plt.grid()
plt.show()
