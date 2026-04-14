import pandas as pd

# Create dataset
data = {
    "Name": ["AMIT", "RIYA", "JOHN"],
    "Math": [80, 90, 60],
    "Science": [70, 88, 65],
    "English": [85, 92, 70]
}

# Create DataFrame
df = pd.DataFrame(data)

# 1. Calculate average marks per student
df["Average"] = df[["Math", "Science", "English"]].mean(axis=1)

# 2. Find topper
topper = df.loc[df["Average"].idxmax()]

# 3. Count students above overall average
overall_avg = df["Average"].mean()
above_avg_count = df[df["Average"] > overall_avg].shape[0]

# BONUS 1: Add grade column
def get_grade(avg):
    if avg >= 90:
        return "A"
    elif avg >= 75:
        return "B"
    elif avg >= 60:
        return "C"
    else:
        return "D"

df["Grade"] = df["Average"].apply(get_grade)

# BONUS 2: Subject-wise average
subject_avg = df[["Math", "Science", "English"]].mean()

# ---------------- OUTPUT ----------------
print("Student Data:\n", df, "\n")

print("Topper:")
print(topper, "\n")

print("Overall Average Marks:", overall_avg)
print("Students Above Average:", above_avg_count, "\n")

print("Subject-wise Average:\n", subject_avg)
