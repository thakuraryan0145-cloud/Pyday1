import pandas as pd
import matplotlib.pyplot as plt

# Sample dataset (you can replace with CSV using pd.read_csv)
data = {
    "Day": ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
    "Sales": [200, 220, 250, 270, 300, 350, 400]
}

df = pd.DataFrame(data)

# Create subplots (Bonus)
plt.figure(figsize=(12, 8))

# 1. Line Chart (Trend)
plt.subplot(2, 2, 1)
plt.plot(df["Day"], df["Sales"], marker='o')
plt.title("Sales Trend")
plt.xlabel("Day")
plt.ylabel("Sales")

# 2. Bar Chart (Comparison)
plt.subplot(2, 2, 2)
plt.bar(df["Day"], df["Sales"])
plt.title("Sales Comparison")
plt.xlabel("Day")
plt.ylabel("Sales")

# 3. Histogram (Distribution)
plt.subplot(2, 2, 3)
plt.hist(df["Sales"], bins=5)
plt.title("Sales Distribution")
plt.xlabel("Sales")
plt.ylabel("Frequency")

# 4. Boxplot (Outlier Detection - Bonus)
plt.subplot(2, 2, 4)
plt.boxplot(df["Sales"])
plt.title("Outlier Detection")

plt.tight_layout()
plt.show()

# -------- INSIGHTS --------
print("INSIGHTS:")
print("1. Sales show an increasing trend throughout the week.")
print("2. Highest sales occur on Sunday.")
print("3. Data distribution is slightly right-skewed.")
print("4. No major outliers detected in this dataset.")
