# Given logs
logs = [
    "ERROR DISK FULL",
    "INFO STARTED",
    "ERROR FILE MISSING",
    "WARNING MEMORY LOW"
]

# Initialize counters
counts = {
    "ERROR": 0,
    "INFO": 0,
    "WARNING": 0
}

# Count log types (case-insensitive)
for log in logs:
    log = log.upper()   # ignore case
    
    if "ERROR" in log:
        counts["ERROR"] += 1
    elif "INFO" in log:
        counts["INFO"] += 1
    elif "WARNING" in log:
        counts["WARNING"] += 1

# Find most frequent log type
most_frequent = max(counts, key=counts.get)

# Output
print("Log Counts:")
for key, value in counts.items():
    print(f"{key}: {value}")

print("\nMost Frequent Log Type:", most_frequent)
