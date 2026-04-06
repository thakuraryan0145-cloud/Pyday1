# Original data
data = [10, None, 20, 10, "", 30, None, 40]

# Step 1: Remove invalid values (None and empty string)
cleaned_data = []
removed_count = 0

for item in data:
    if item is None or item == "":
        removed_count += 1
    else:
        cleaned_data.append(item)

# Step 2: Remove duplicates
unique_data = []
for item in cleaned_data:
    if item not in unique_data:
        unique_data.append(item)
    else:
        removed_count += 1

# Step 3: Sort the final list
unique_data.sort()

