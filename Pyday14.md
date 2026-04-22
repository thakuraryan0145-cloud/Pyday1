import matplotlib.pyplot as plt

# Data
categories = ["FOOD", "TRAVEL", "SHOPPING"]
expenses = [500, 300, 200]

# Find index of highest expense
max_index = expenses.index(max(expenses))

# Explode (highlight highest category)
explode = [0.1 if i == max_index else 0 for i in range(len(expenses))]

# Plot pie chart
plt.figure(figsize=(6,6))
plt.pie(
    expenses,
    labels=categories,
    autopct='%1.1f%%',   # percentage labels
    explode=explode,
    shadow=True,
    startangle=90
)

plt.title("Category Breakdown of Expenses")
plt.axis('equal')  # makes circle perfect

plt.show()
