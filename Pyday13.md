import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# -----------------------------
# Step 1: Create Sample Dataset
# -----------------------------
# You can replace this with real data
np.random.seed(42)

# Example: Student Marks (Normal distribution)
marks = np.random.normal(loc=70, scale=10, size=200)

# Convert to DataFrame
df = pd.DataFrame({"Marks": marks})

# -----------------------------
# Step 2: Plot Histogram + KDE
# -----------------------------
plt.figure(figsize=(8, 5))

sns.histplot(df["Marks"], kde=True)

plt.title("Distribution of Student Marks")
plt.xlabel("Marks")
plt.ylabel("Frequency")

plt.show()

# -----------------------------
# Step 3: Identify Skewness
# -----------------------------
skewness = df["Marks"].skew()

print("Skewness:", skewness)

# Interpretation
if skewness > 0:
    print("Data is Positively Skewed (Right Skewed)")
elif skewness < 0:
    print("Data is Negatively Skewed (Left Skewed)")
else:
    print("Data is Symmetrical")
