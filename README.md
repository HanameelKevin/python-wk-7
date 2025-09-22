# python-wk-7
Data analysis
# ============================================
# Assignment: Data Analysis with Pandas & Matplotlib
# ============================================

# Task 0: Import Libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Optional: display settings
pd.set_option("display.max_columns", None)
sns.set_style("whitegrid")

# -------------------------------
# Task 1: Load and Explore Dataset
# -------------------------------
try:
    # Example: Load the Iris dataset directly from seaborn
    df = sns.load_dataset("iris")
    # If using your own CSV, replace with:
    # df = pd.read_csv("your_dataset.csv")
    
    print("✅ Dataset loaded successfully!")
except FileNotFoundError:
    print("❌ File not found. Please check the path.")

# Display first few rows
print("\nFirst 5 rows:")
display(df.head())

# Explore structure
print("\nDataset info:")
print(df.info())

print("\nMissing values per column:")
print(df.isnull().sum())

# Clean dataset (example: drop missing values)
df = df.dropna()

# -------------------------------
# Task 2: Basic Data Analysis
# -------------------------------

# Statistical summary
print("\nStatistical summary:")
display(df.describe())

# Example grouping (by species, compute mean petal_length)
grouped = df.groupby("species")["petal_length"].mean()
print("\nAverage petal length per species:")
print(grouped)

# Interesting finding example:
# In the Iris dataset, setosa has the smallest petals, virginica the largest.

# -------------------------------
# Task 3: Data Visualization
# -------------------------------

# 1. Line chart (using sepal length as an example "trend")
plt.figure(figsize=(8,5))
plt.plot(df.index, df["sepal_length"], label="Sepal Length")
plt.title("Line Chart: Sepal Length Over Index")
plt.xlabel("Index")
plt.ylabel("Sepal Length (cm)")
plt.legend()
plt.show()

# 2. Bar chart (mean petal length per species)
plt.figure(figsize=(8,5))
sns.barplot(x="species", y="petal_length", data=df, ci=None)
plt.title("Bar Chart: Average Petal Length by Species")
plt.xlabel("Species")
plt.ylabel("Average Petal Length (cm)")
plt.show()

# 3. Histogram (distribution of sepal width)
plt.figure(figsize=(8,5))
plt
