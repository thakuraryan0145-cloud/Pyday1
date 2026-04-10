#data.csv
NAME,AGE,MARKS
AMIT,20,85
RIYA,21,90

data_list = []

# Open and read file
with open("data.csv", "r") as file:
    lines = file.readlines()

# Extract headers
headers = lines[0].strip().split(",")

# Process remaining lines
for line in lines[1:]:
    values = line.strip().split(",")
    
    # Handle missing values
    if len(values) < 3:
        continue
    
    # Create dictionary
    record = {
        headers[0]: values[0],
        headers[1]: int(values[1]),
        headers[2]: int(values[2])
    }
    
    data_list.append(record)

# Print result
print("Data as List of Dictionaries:")
print(data_list)

# Bonus: Calculate average marks
total_marks = 0
for record in data_list:
    total_marks += record["MARKS"]

average = total_marks / len(data_list)
print("\nAverage Marks:", average)
