import csv
from collections import defaultdict

# Step 1: Read CSV data
data = [
    ["PRODUCT", "QUANTITY", "PRICE"],
    ["A", "2", "100"],
    ["B", "1", "200"],
    ["A", "3", "100"],
    ["C", "5", "50"]
]

# Step 2: Convert data (skip header)
records = []
for row in data[1:]:
    product = row[0]
    quantity = int(row[1])
    price = int(row[2])
    total = quantity * price  # new column
    records.append({
        "product": product,
        "quantity": quantity,
        "price": price,
        "total": total
    })

# Step 3: Calculate total sales per product
sales_per_product = defaultdict(int)

for r in records:
    sales_per_product[r["product"]] += r["total"]

# Step 4: Total revenue
total_revenue = sum(r["total"] for r in records)

# Step 5: Top-selling product
top_product = max(sales_per_product, key=sales_per_product.get)

# Step 6: Sort by revenue
sorted_products = sorted(sales_per_product.items(), key=lambda x: x[1], reverse=True)

# Output
print("Total Sales per Product:")
for product, total in sales_per_product.items():
    print(product, ":", total)

print("\nTotal Revenue:", total_revenue)

print("\nTop Selling Product:", top_product)

print("\nSorted by Revenue:")
for product, total in sorted_products:
    print(product, ":", total)
