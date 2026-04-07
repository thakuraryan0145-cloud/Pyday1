# Given marks
marks = [78, 85, 90, 67, 85, 92, 78]

# Function to calculate average
def calculate_average(marks):
    return sum(marks) / len(marks)

# Function to find highest and lowest marks
def find_highest_lowest(marks):
    return max(marks), min(marks)

# Function to count students above average
def count_above_average(marks, avg):
    count = 0
    for mark in marks:
        if mark > avg:
            count += 1
    return count

# Bonus: Grade distribution
def grade_distribution(marks):
    grades = {"A": 0, "B": 0, "C": 0, "Fail": 0}
    
    for mark in marks:
        if mark >= 90:
            grades["A"] += 1
        elif mark >= 75:
            grades["B"] += 1
        elif mark >= 50:
            grades["C"] += 1
        else:
            grades["Fail"] += 1
    
    return grades

# Main program
average = calculate_average(marks)
highest, lowest = find_highest_lowest(marks)
above_avg_count = count_above_average(marks, average)
grades = grade_distribution(marks)

# Output
print("Average Marks:", average)
print("Highest Marks:", highest)
print("Lowest Marks:", lowest)
print("Students Above Average:", above_avg_count)
print("Grade Distribution:", grades)
