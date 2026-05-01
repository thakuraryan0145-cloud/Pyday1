# Import libraries
import pandas as pd
import matplotlib.pyplot as plt

# -----------------------------
# Step 1: Create Sample Dataset
# -----------------------------
data = {
    "Customer_ID": range(1, 21),
    "Age": [22, 25, 47, 52, 46, 56, 34, 29, 40, 41, 23, 31, 38, 45, 50, 27, 33, 36, 42, 48],
    "Spending": [200, 450, 800, 1500, 1200, 700, 650, 300, 900, 1100, 250, 500, 750, 1300, 1400, 350, 600, 850, 1000, 1250],
    "Visits": [5, 10, 15, 20, 18, 12, 11, 6, 14, 16, 4, 9, 13, 17, 19, 7, 10, 12, 15, 18]
}

df = pd.DataFrame(data)

# -----------------------------
# Step 2: Create Spending Segments
# -----------------------------
def segment_spending(spending):
    if spending >= 1000:
        return "High"
    elif spending >= 500:
        return "Medium"
    else:
        return "Low"

df["Segment"] = df["Spending"].apply(segment_spending)

# -----------------------------
# Step 3: Identify Customers
# -----------------------------
high_value = df[df["Spending"] >= 1000]
low_engagement = df[df["Visits"] < 8]

print("High Value Customers:\n", high_value)
print("\nLow Engagement Customers:\n", low_engagement)

# -----------------------------
# Step 4: Visualization
# -----------------------------

# Spending Distribution
plt.figure()
plt.hist(df["Spending"])
plt.title("Spending Distribution")
plt.xlabel("Spending")
plt.ylabel("Frequency")
plt.show()

# Customer Categories Count
segment_counts = df["Segment"].value_counts()

plt.figure()
segment_counts.plot(kind='bar')
plt.title("Customer Segments")
plt.xlabel("Segment")
plt.ylabel("Number of Customers")
plt.show()

# -----------------------------
# Step 5: Business Insights
# -----------------------------
print("\nBusiness Insights:")
print("- High spending customers should be targeted with premium offers.")
print("- Medium segment can be converted to high with discounts.")
print("- Low engagement users need marketing campaigns or reminders.")
