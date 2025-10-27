# Pandas notes for Data Analysts

Instructor: Nikhil Kumar Mishra 
It covers all the essential operations with simple examples to help you quickly recall concepts during practice or revision.



## What is Pandas?

Pandas is an open-source Python library built on top of NumPy, designed for data manipulation, analysis, and cleaning.  
It provides two main data structures:
- Series: One-dimensional labeled array.
- DataFrame: Two-dimensional table similar to Excel or SQL table.



## 1. Importing Pandas

```python
import pandas as pd




## 2. Importing Files

### Read CSV / Excel / JSON Files

```python
# Read CSV file
df = pd.read_csv('data.csv')

# Read Excel file
df = pd.read_excel('data.xlsx', sheet_name='Sheet1')

# Read JSON file
df = pd.read_json('data.json')
```

Tip: Use `pd.read_*()` functions for various file formats like `read_html`, `read_sql`, etc.



## 3. Exporting Files

### Save DataFrame to Files

```python
df.to_csv('output.csv', index=False)
df.to_excel('output.xlsx', index=False)
df.to_json('output.json')
```

---

## 4. Creating Series and DataFrames

### Create a Series

```python
s = pd.Series([10, 20, 30, 40], name="Sales")
print(s)
```

### Create a DataFrame

```python
data = {
    'Name': ['Amit', 'Priya', 'Rohan'],
    'Age': [25, 22, 28],
    'City': ['Delhi', 'Mumbai', 'Pune']
}
df = pd.DataFrame(data)
print(df)
```

---

## 5. Indexing and Selection

```python
# Access a column
df['Name']

# Access multiple columns
df[['Name', 'Age']]

# Access rows using loc and iloc
df.loc[0]         # By label
df.iloc[0]        # By index position
```

---

## 6. Slicing Data

```python
# Select specific rows
df[0:2]

# Conditional filtering
df[df['Age'] > 23]

# Multiple conditions
df[(df['Age'] > 23) & (df['City'] == 'Delhi')]
```

---

## 7. Merging and Joining

```python
sales = pd.DataFrame({'ID': [1, 2, 3], 'Sales': [200, 300, 400]})
customers = pd.DataFrame({'ID': [1, 2, 3], 'Name': ['A', 'B', 'C']})

merged = pd.merge(sales, customers, on='ID', how='inner')
print(merged)
```

Note: `how` parameter options - `inner`, `outer`, `left`, `right`

---

## 8. Concatenation

```python
df1 = pd.DataFrame({'City': ['Delhi', 'Pune'], 'Sales': [100, 200]})
df2 = pd.DataFrame({'City': ['Mumbai', 'Chennai'], 'Sales': [150, 180]})

pd.concat([df1, df2], ignore_index=True)
```

---

## 9. GroupBy and Aggregations

```python
df.groupby('City')['Sales'].sum()
df.groupby('City').agg({'Sales': ['sum', 'mean', 'count']})
```

GroupBy helps you summarize and analyze data by category.

---

## 10. Pivot Tables

```python
df = pd.DataFrame({
    'Region': ['North', 'South', 'North', 'East'],
    'Month': ['Jan', 'Jan', 'Feb', 'Feb'],
    'Sales': [250, 300, 200, 150]
})

pivot = df.pivot_table(values='Sales', index='Region', columns='Month', aggfunc='sum', fill_value=0)
print(pivot)
```

---

## 11. Data Cleaning Shortcuts

```python
df.dropna(inplace=True)         # Remove missing rows
df.fillna(0, inplace=True)      # Replace NaN with 0
df.rename(columns={'Old': 'New'}, inplace=True)
```

---

## 12. Using ExcelWriter

ExcelWriter allows saving multiple sheets in one Excel file.

```python
with pd.ExcelWriter('report.xlsx') as writer:
    df.to_excel(writer, sheet_name='Data', index=False)
    pivot.to_excel(writer, sheet_name='Pivot', index=False)
```

---

## References

* Official Pandas Docs: [https://pandas.pydata.org/docs/](https://pandas.pydata.org/docs/)
* DataCamp Pandas Cheat Sheet: [https://www.datacamp.com/cheat-sheet/pandas-cheat-sheet](https://www.datacamp.com/cheat-sheet/pandas-cheat-sheet)
* Kaggle Pandas Tutorials: [https://www.kaggle.com/learn/pandas](https://www.kaggle.com/learn/pandas)

Linkedin-https://www.linkedin.com/in/nikhilkumarmishra-
