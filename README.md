## ✅ Step 1: Load the Dataset

### 🗂️ Download the Titanic Dataset

Save it as `titanic.csv` in the same folder where your Jupyter notebook is located.

### 📥 Load the Data in Notebook
```python
import pandas as pd

# Load the dataset
df = pd.read_csv('titanic.csv')

# Show the first few rows
df.head()
```

This reads the CSV file into a **DataFrame** and shows the top 5 rows.

---

## ✅ Step 2: Understand the Data Structure

### Check the general info:
```python
df.info()
```
This shows:
- Column names
- Data types (int, float, object)
- Non-null counts (missing data)

### Get basic statistics:
```python
df.describe()
```
This gives:
- Mean, min, max, std deviation of numerical columns

### Column names and data preview:
```python
df.columns
df.head()
df.tail()
```

### 🔍 Write Observations:
- How many rows and columns are there?
- Which columns have missing values?
- What data types are used?

---

## ✅ Step 3: Explore Each Column

### 🧮 For categorical columns:
```python
df['Sex'].value_counts()
df['Embarked'].value_counts()
df['Survived'].value_counts()
```
Use this to understand how many people fall into each category (e.g., how many males/females, how many survived/died).

### 🔢 For numerical columns:
```python
df['Age'].describe()
df['Fare'].describe()
```

📝 **Write down what you notice**:
- Average age
- Fare range
- Which values are most frequent (mode)

---

## ✅ Step 4: Clean the Data

### See how many missing values there are:
```python
df.isnull().sum()
```

### Fix missing values:
```python
# Fill missing 'Age' with median
df['Age'] = df['Age'].fillna(df['Age'].median())

# Drop rows where 'Embarked' is missing
df = df.dropna(subset=['Embarked'])
```

📝 **Note:** You can also drop columns if they’re mostly empty (like 'Cabin'):

```python
df = df.drop(columns=['Cabin'])
```

---

## ✅ Step 5: Visualize the Data

Now you use **Seaborn** and **Matplotlib** for charts.

### 📦 Import visualization libraries
```python
import matplotlib.pyplot as plt
import seaborn as sns

# Optional: makes plots look better
sns.set(style="whitegrid")
```

---

### 🟡 Pairplot (to see relationships)
```python
sns.pairplot(df[['Age', 'Fare', 'Survived', 'Pclass']], hue='Survived')
plt.show()
```

### 🟠 Heatmap (correlation between numeric features)
```python
plt.figure(figsize=(10, 6))
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
plt.title("Correlation Heatmap")
plt.show()
```

---

### 🟣 Histogram of Age
```python
df['Age'].hist(bins=30)
plt.title("Age Distribution")
plt.xlabel("Age")
plt.ylabel("Count")
plt.show()
```

---

### 🔵 Boxplot of Age by Class
```python
sns.boxplot(x='Pclass', y='Age', data=df)
plt.title("Age vs Passenger Class")
plt.show()
```

---

### 🔴 Count of Survivors
```python
sns.countplot(x='Survived', data=df)
plt.title("Survival Counts")
plt.show()
```

---

### ⚪ Survival by Gender
```python
sns.countplot(x='Sex', hue='Survived', data=df)
plt.title("Survival by Sex")
plt.show()
```

---

## ✅ Step 6: Interpret the Plots

Write simple takeaways:

- "Most women survived while most men didn’t."
- "Higher class passengers (Pclass = 1) had a better survival rate."
- "Younger children seemed more likely to survive."

---

## ✅ Summary: Final Deliverables

**1. Jupyter Notebook (`Titanic_EDA.ipynb`)**  
**2. PDF Report (includes plots + comments)**
**3. Theory explanation PDF( include code line + observation of output)** 
