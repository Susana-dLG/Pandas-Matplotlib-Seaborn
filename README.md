---

# 🌍 GDP Per Capita Analysis with Pandas, Matplotlib & Seaborn

This project performs a complete **Exploratory Data Analysis (EDA)** on the *GDP (Nominal) per Capita* dataset using Python libraries such as **Pandas**, **Matplotlib**, and **Seaborn**. It demonstrates techniques for inspecting, cleaning, grouping, and visualizing country-level economic data.

---

## 📌 Project Overview

The purpose of this project is to understand and explore global GDP per capita figures. Using publicly available data, the analysis identifies trends, handles missing values, groups countries by characteristics, visualizes distributions, and detects outliers. This is a foundational EDA project ideal for data science and analytics learners.

---

## 🛠️ Tools and Libraries Used

| Tool / Library      | Purpose                               |
| ------------------- | ------------------------------------- |
| **Python**          | Programming Language                  |
| **Pandas**          | Data cleaning, manipulation, grouping |
| **Matplotlib**      | Plotting and charting                 |
| **Seaborn**         | Advanced statistical visualization    |
| **Jupyter / Colab** | Notebook environment for development  |

---

## 🎯 Project Objectives

1. Load and inspect a GDP per capita dataset
2. Perform initial exploration of the data structure and stats
3. Handle and fill missing or zero values
4. Group countries based on relevant features
5. Create visualizations for pattern and trend discovery
6. Identify and remove outliers in the dataset

---

## 📊 Exploratory Data Analysis (EDA)

### 🔍 a. Explore and Inspect Dataset

* Loaded the dataset using `pd.read_csv()`
* Inspected column names, data types, and basic statistics
* Checked the number of rows and columns, unique values, and types

```python
df.info()
df.describe()
df.head()
```

---

### 📊 b. GroupBy Operation

* Grouped data by region or other classification to compute aggregated metrics like:

```python
df.groupby("Region")["GDP"].mean()
```

---

### 🧩 c. Filling 0 Values by Mean

* Identified GDP values reported as 0 and replaced them with the country/regional average:

```python
df["GDP"] = df["GDP"].replace(0, np.nan)
df["GDP"].fillna(df["GDP"].mean(), inplace=True)
```

---

### ❗ d. Checking Missing Values

* Verified missing or null entries with:

```python
df.isnull().sum()
```

---

### 📈 e. Visualizations

#### 1. Histogram of GDP

```python
plt.hist(df["GDP"])
plt.title("Distribution of GDP per Capita")
plt.xlabel("GDP")
plt.ylabel("Frequency")
```

#### 2. Boxplot to Check Outliers

```python
sns.boxplot(x=df["GDP"])
plt.title("Boxplot of GDP per Capita")
```

#### 3. GDP by Region – Bar Chart

```python
df.groupby("Region")["GDP"].mean().plot(kind='bar')
plt.title("Average GDP per Region")
plt.ylabel("GDP")
```

---

### 🧹 f. Removing Outliers

* Used IQR (Interquartile Range) to detect and remove extreme outliers from the dataset:

```python
Q1 = df["GDP"].quantile(0.25)
Q3 = df["GDP"].quantile(0.75)
IQR = Q3 - Q1
df = df[(df["GDP"] >= Q1 - 1.5 * IQR) & (df["GDP"] <= Q3 + 1.5 * IQR)]
```

---

## ✅ Results & Learnings

* Learned how to treat zeros and nulls in numeric datasets
* Explored global GDP patterns and inequalities
* Understood the importance of removing outliers to preserve trend clarity
* Practiced visual exploration using Matplotlib and Seaborn
* Reinforced grouping and aggregation skills using Pandas

---

## 📁 Dataset

* **GDP (Nominal) per Capita**: Includes GDP values per country (may also include regional classification, year, etc.)

---

Let me know if you want this in `.md` file format or would like GitHub badge suggestions (e.g., `Made with Python`, `Pandas`, `Seaborn`).
