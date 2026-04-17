# Given logs
logs = [
    "ERROR DISK FULL",
    "INFO STARTED",
    "ERROR FILE MISSING",
    "WARNING MEMORY LOW"
]

# Initialize counters
error_count = 0
info_count = 0
warning_count = 0

# Process logs (ignore case sensitivity)
for log in logs:
    log = log.lower()   # make case-insensitive
    
    if "error" in log:
        error_count += 1
    elif "info" in log:
        info_count += 1
    elif "warning" in log:
        warning_count += 1

# Print results
print("Counts:")
print("ERROR:", error_count)
print("INFO:", info_count)
print("WARNING:", warning_count)

# Bonus: Find most frequent log type
counts = {
    "ERROR": error_count,
    "INFO": info_count,
    "WARNING": warning_count
}

most_frequent = max(counts, key=counts.get)
print("\nMost Frequent Log Type:", most_frequent)
