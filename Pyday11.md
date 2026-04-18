import matplotlib.pyplot as plt

# Dataset
dates = ["MON", "TUE", "WED", "THU", "FRI"]
sales = [200, 250, 300, 280, 350]

# Find highest and lowest sales
max_sales = max(sales)
min_sales = min(sales)

max_day = dates[sales.index(max_sales)]
min_day = dates[sales.index(min_sales)]

# Plot line chart
plt.plot(dates, sales, marker='o')

# Highlight highest point
plt.scatter(max_day, max_sales)
plt.text(max_day, max_sales, f' Highest: {max_sales}', fontsize=10)

# Highlight lowest point
plt.scatter(min_day, min_sales)
plt.text(min_day, min_sales, f' Lowest: {min_sales}', fontsize=10)

# Labels and title
plt.xlabel("Days")
plt.ylabel("Sales")
plt.title("Weekly Sales Trend")

# Grid for better visualization
plt.grid()

# Show plot
plt.show()
