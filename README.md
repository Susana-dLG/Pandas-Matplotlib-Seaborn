---

## 🌍 GDP Per Capita Analysis with Pandas, Matplotlib & Seaborn

This project performs a complete **Exploratory Data Analysis (EDA)** on the *GDP (Nominal) per Capita* dataset using Python libraries such as **Pandas**, **Matplotlib**, and **Seaborn**. It demonstrates techniques for inspecting, cleaning, grouping, and visualizing country-level economic data.

---

## 📌 Project Overview

The purpose of this project is to understand and explore global GDP per capita figures. Using publicly available data, the analysis identifies trends, handles missing values, groups countries by characteristics, visualizes distributions, and detects outliers. This is a foundational EDA project ideal for data science and analytics learners.

---
## 📁 Dataset

* **GDP (Nominal) per Capita**: Includes GDP values per country (may also include regional classification, year, etc.)

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
df.head()
```
![image](https://github.com/user-attachments/assets/52371af4-b049-437e-8c04-03bd53884c61)

df.info()

![image](https://github.com/user-attachments/assets/2917ccdb-8a99-4e70-96ae-5927f8a8343a)

df.describe()
![image](https://github.com/user-attachments/assets/19034b0d-01c6-42f0-84b0-a08e4b37b31e)

df.dtypes
![image](https://github.com/user-attachments/assets/138c175b-0f43-407d-a73c-f582c13328ba)

---

### 📊 b. GroupBy Operation

* Grouped data by region or other classification to compute aggregated metrics like:

```python
df.groupby("UN_Region")["IMF_Estimate"].mean().sort_values()
```
![image](https://github.com/user-attachments/assets/c6cf7e91-1aaa-4446-b85d-d9dac4dca1df)

df.groupby("UN_Region")["IMF_Estimate"].mean().sort_values(ascending=False)

![image](https://github.com/user-attachments/assets/7ce18c5f-3207-461e-a4bc-f2df1d9abcb6)

---

### 🧩 c. Filling 0 Values by Mean

* Identified GDP values reported as 0 and replaced them with the country/regional average:

```python
df["IMF_Estimate"] = df["IMF_Estimate"].replace(0, np.nan)
```
![image](https://github.com/user-attachments/assets/ba50adb7-3313-4339-8034-57d3066fe514)


---

### ❗ d. Checking Missing Values

* Verified missing or null entries with:

```python
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/03ed7199-6490-40f5-9ce2-d63a0ee22837)

---

### 📈 e. Visualizations

#### 1. Histogram of GDP

```python
df.hist(figsize=(10,8))
plt.show()
```
![image](https://github.com/user-attachments/assets/36b66542-654f-43d8-8059-17dfab0e9e0f)


#### 2. Boxplot to Check Outliers

```python
sns.boxplot(x=df["UN_Estimate"])

plt.show()
```
![image](https://github.com/user-attachments/assets/d9efecc2-303b-4072-9eec-e229729fe083)


#### 3. GDP by Region – Bar Chart

```python
sns.barplot(x="UN_Region", y="WorldBank_Estimate", data=df, errorbar=None)
plt.show()
```
![image](https://github.com/user-attachments/assets/f1de994c-f79e-44a3-bf5a-2e47755b30f8)

---

### 🧹 f. Removing Outliers

* Used IQR (Interquartile Range) to detect and remove extreme outliers from the dataset:
```
Q1 = df["GDP"].quantile(0.25)
Q3 = df["GDP"].quantile(0.75)
IQR = Q3 - Q1
df = df[(df["GDP"] >= Q1 - 1.5 * IQR) & (df["GDP"] <= Q3 + 1.5 * IQR)]
```
lower_q = df["UN_Estimate"].quantile(0.25)
lower_q #lower edge of the box

``
![image](https://github.com/user-attachments/assets/6c8a92b3-2c20-4912-938c-eb28d7e7d325)

---

### ✅ Results & Learnings

* Learned how to treat zeros and nulls in numeric datasets
* Explored global GDP patterns and inequalities
* Understood the importance of removing outliers to preserve trend clarity
* Practiced visual exploration using Matplotlib and Seaborn
* Reinforced grouping and aggregation skills using Pandas

---

---
Created by Susana-dLG
June 2025

