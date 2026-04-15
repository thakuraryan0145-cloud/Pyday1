import pandas as pd

# Create dataset
data = {
    "Name": ["A", "B", "C", "D"],
    "Dept": ["IT", "HR", "IT", "HR"],
    "Salary": [50000, 40000, 60000, 45000]
}

# Convert to DataFrame
df = pd.DataFrame(data)

print("Original Data:\n", df, "\n")

# 1. Average salary per department
avg_salary = df.groupby("Dept")["Salary"].mean()
print("Average Salary per Department:\n", avg_salary, "\n")

# 2. Highest paid employee per department
highest_paid = df.loc[df.groupby("Dept")["Salary"].idxmax()]
print("Highest Paid Employee per Department:\n", highest_paid, "\n")

# 3. Count employees per department (BONUS)
count_emp = df.groupby("Dept")["Name"].count()
print("Employee Count per Department:\n", count_emp, "\n")

# 4. Sort departments by average salary (BONUS)
sorted_avg = avg_salary.sort_values(ascending=False)
print("Departments sorted by Avg Salary:\n", sorted_avg)
