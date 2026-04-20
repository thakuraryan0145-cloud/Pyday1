import matplotlib.pyplot as plt
import numpy as np

students = ["AMIT", "RIYA", "JOHN"]

math = [85, 92, 78]
science = [80, 88, 75]

x = np.arange(len(students))  # positions
width = 0.35

# Bars
plt.bar(x - width/2, math, width, label='Math')
plt.bar(x + width/2, science, width, label='Science')

# Labels
plt.xlabel("Students")
plt.ylabel("Marks")
plt.title("Student Performance (Multiple Subjects)")
plt.xticks(x, students)
plt.legend()

plt.show()
