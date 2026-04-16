
import pandas as pd

# Read CSV file
df = pd.read_csv("employees.csv")

# 🔹 Apply filters:
# Salary > 50000 AND Age < 30
filtered_df = df[(df["SALARY"] > 50000) & (df["AGE"] < 30)]

# 🔹 Display filtered results
print("Filtered Data:")
print(filtered_df)

# 🔹 Bonus: Save filtered data to new file
filtered_df.to_csv("filtered_data.csv", index=False)

print("\nFiltered data saved to 'filtered_data.csv'")
