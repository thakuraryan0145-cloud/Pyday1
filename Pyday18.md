import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset (make sure your CSV file has columns: Movie, Rating, Genre, Revenue)
df = pd.read_csv("movies.csv")

# Display first few rows
print(df.head())

# -------------------------------
# 1. Highest Rated Movies
# -------------------------------
highest_rated = df.sort_values(by="Rating", ascending=False)
print("\nTop 5 Highest Rated Movies:\n", highest_rated.head(5))

# -------------------------------
# 2. Most Profitable Genres
# -------------------------------
genre_profit = df.groupby("Genre")["Revenue"].sum().sort_values(ascending=False)
print("\nMost Profitable Genres:\n", genre_profit)

# -------------------------------
# 3. Visualization: Genre vs Revenue
# -------------------------------
plt.figure()
genre_profit.plot(kind='bar')
plt.title("Genre vs Revenue")
plt.xlabel("Genre")
plt.ylabel("Total Revenue")
plt.xticks(rotation=45)
plt.show()

# -------------------------------
# 4. Rating Distribution
# -------------------------------
plt.figure()
sns.histplot(df["Rating"], bins=10, kde=True)
plt.title("Rating Distribution")
plt.xlabel("Rating")
plt.ylabel("Frequency")
plt.show()

# -------------------------------
# 5. Correlation between Rating & Revenue
# -------------------------------
correlation = df["Rating"].corr(df["Revenue"])
print("\nCorrelation between Rating & Revenue:", correlation)

# Scatter Plot
plt.figure()
sns.scatterplot(x="Rating", y="Revenue", data=df)
plt.title("Rating vs Revenue")
plt.show()

# -------------------------------
# 6. Top 5 Movies (by Revenue)
# -------------------------------
top_movies = df.sort_values(by="Revenue", ascending=False).head(5)
print("\nTop 5 Movies by Revenue:\n", top_movies)
