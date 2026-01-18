# Pandas Learning Guide: Data Analysis Fundamentals

## Overview
This notebook covers Pandas library from basics to advanced data analysis techniques. Pandas is essential for data manipulation, cleaning, and analysis.

**What is Pandas?**
- Python library for data manipulation and analysis
- Built on NumPy
- Provides data structures: Series and DataFrame
- Handles missing data, data alignment, reshaping

---

# Part 1: Installation and Setup

## Installation
```bash
pip install pandas numpy matplotlib seaborn
```

## Import Pandas
```python
import pandas as pd
import numpy as np
```

```python
# Import necessary libraries
import pandas as pd
import numpy as np

# Display version
print(f"Pandas version: {pd.__version__}")
print(f"NumPy version: {np.__version__}")
```

# Part 2: Pandas Series

## What is a Series?
- 1-dimensional labeled array
- Similar to Python list but with labels (index)
- Can contain any data type
- Built on NumPy arrays

## Key Characteristics
- **Index**: Labels for each element
- **Values**: The actual data
- **dtype**: Data type of values

```python
# Example: Creating Series

# From list
s1 = pd.Series([10, 20, 30, 40, 50])
print("Series from list:")
print(s1)
print(f"Index: {s1.index.tolist()}")
print(f"Values: {s1.values.tolist()}")

# With custom index
s2 = pd.Series([90, 85, 88, 92, 78], index=['Alice', 'Bob', 'Charlie', 'Diana', 'Eve'])
print("\nSeries with custom index (Student Grades):")
print(s2)

# From dictionary
s3 = pd.Series({'A': 100, 'B': 200, 'C': 300})
print("\nSeries from dictionary:")
print(s3)
```

```python
# Example: Accessing Series elements

s = pd.Series([10, 20, 30, 40, 50], index=['a', 'b', 'c', 'd', 'e'])

# By index
print(f"Element at index 'c': {s['c']}")
print(f"First element: {s[0]}")

# Slicing
print(f"\nSlice [0:3]: {s[0:3].tolist()}")
print(f"Slice ['a':'c']: {s['a':'c'].tolist()}")

# Boolean indexing
print(f"\nElements > 25: {s[s > 25].tolist()}")

# Series operations
print(f"\nSum: {s.sum()}")
print(f"Mean: {s.mean()}")
print(f"Max: {s.max()}")
print(f"Describe: \n{s.describe()}")
```

# Part 3: Pandas DataFrame

## What is a DataFrame?
- 2-dimensional labeled data structure (like Excel table)
- Rows and columns with labels
- Can have different data types in each column
- Most used Pandas data structure

## Key Components
- **Rows**: Indexed by row labels
- **Columns**: Named columns
- **Index**: Row labels
- **Columns**: Column names

```python
# Example: Creating DataFrames

# From dictionary
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana', 'Eve'],
    'Age': [25, 30, 28, 35, 22],
    'Salary': [50000, 60000, 55000, 75000, 48000],
    'Department': ['HR', 'IT', 'Finance', 'IT', 'HR']
}

df = pd.DataFrame(data)
print("DataFrame:")
print(df)
print(f"\nShape: {df.shape}")
print(f"Columns: {df.columns.tolist()}")
print(f"Dtypes:\n{df.dtypes}")
```

```python
# Example: Accessing DataFrame elements

# Access column
print("Access column 'Name':")
print(df['Name'].tolist())

# Access multiple columns
print("\nAccess columns ['Name', 'Salary']:")
print(df[['Name', 'Salary']])

# Access row by index
print("\nAccess row at index 0:")
print(df.loc[0])

# Access by location (integer)
print("\nAccess by iloc (first 3 rows):")
print(df.iloc[0:3])

# Access specific cell
print(f"\nCell at row 1, column 'Name': {df.loc[1, 'Name']}")
print(f"Cell at row 2, column 2 (iloc): {df.iloc[2, 2]}")
```

# Part 4: Data Loading and Inspection

## Loading Data
- `pd.read_csv()`: Read CSV files
- `pd.read_excel()`: Read Excel files
- `pd.read_json()`: Read JSON files
- `pd.read_sql()`: Read from SQL database
- `pd.read_html()`: Read HTML tables

## Inspecting Data
- `head()`, `tail()`: First/last rows
- `info()`: Data info and dtypes
- `describe()`: Statistical summary
- `shape()`: Dimensions
- `dtypes`: Data types
- `isnull()`: Missing values

```python
# Example: Data Inspection

# First few rows
print("First 3 rows:")
print(df.head(3))

# Last few rows
print("\nLast 2 rows:")
print(df.tail(2))

# DataFrame info
print("\nDataFrame Info:")
print(df.info())

# Statistical summary
print("\nStatistical Summary:")
print(df.describe())
```

```python
# Example: Missing values

# Create DataFrame with missing values
data_with_na = {
    'Name': ['Alice', 'Bob', None, 'Diana', 'Eve'],
    'Age': [25, None, 28, 35, 22],
    'Salary': [50000, 60000, 55000, None, 48000]
}

df_na = pd.DataFrame(data_with_na)
print("DataFrame with missing values:")
print(df_na)

# Check for null values
print("\nNull values count:")
print(df_na.isnull().sum())

# Check for non-null values
print("\nNon-null values count:")
print(df_na.notnull().sum())
```

# Part 5: Data Cleaning

## Handling Missing Data
- `dropna()`: Remove rows/columns with missing values
- `fillna()`: Fill missing values
- `isnull()`: Check for null values

## Data Type Conversion
- `astype()`: Convert data types
- `pd.to_numeric()`: Convert to numeric
- `pd.to_datetime()`: Convert to datetime

## Handling Duplicates
- `drop_duplicates()`: Remove duplicates
- `duplicated()`: Identify duplicates

```python
# Example: Handling missing values

df_clean = df_na.copy()

# Drop rows with any null value
print("After dropna():")
print(df_clean.dropna())

# Fill missing values
print("\nAfter fillna(0):")
print(df_na.fillna(0))

# Fill with forward fill (propagate last value)
print("\nAfter fillna(method='ffill'):")
print(df_na.fillna(method='ffill'))

# Fill specific column
print("\nFill 'Age' with median:")
df_na['Age'].fillna(df_na['Age'].median())
```

```python
# Example: Data type conversion

df_type = pd.DataFrame({
    'A': ['1', '2', '3', '4'],
    'B': [1.5, 2.5, 3.5, 4.5],
    'C': ['2024-01-01', '2024-01-02', '2024-01-03', '2024-01-04']
})

print("Original dtypes:")
print(df_type.dtypes)

# Convert string to integer
df_type['A'] = df_type['A'].astype(int)

# Convert to datetime
df_type['C'] = pd.to_datetime(df_type['C'])

print("\nAfter conversion:")
print(df_type.dtypes)
```

```python
# Example: Handling duplicates

df_dup = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Alice', 'Charlie', 'Bob'],
    'Age': [25, 30, 25, 28, 30]
})

print("Original DataFrame:")
print(df_dup)

# Check for duplicates
print("\nDuplicated rows:")
print(df_dup.duplicated())

# Drop duplicates
print("\nAfter drop_duplicates():")
print(df_dup.drop_duplicates())
```

# Part 6: Data Selection and Filtering

## Selection Methods
- `loc[]`: Label-based selection
- `iloc[]`: Integer location-based selection
- `at[]`, `iat[]`: Single value selection
- `[]`: Column selection

## Filtering
- Boolean indexing
- `isin()`: Check membership
- `query()`: String-based filtering
- `filter()`: Select columns by name pattern

```python
# Example: Filtering data

print("Original DataFrame:")
print(df)

# Boolean indexing
print("\nEmployees with Age > 25:")
print(df[df['Age'] > 25])

# Multiple conditions
print("\nEmployees in IT with Salary > 55000:")
print(df[(df['Department'] == 'IT') & (df['Salary'] > 55000)])

# Using isin()
print("\nEmployees in HR or Finance:")
print(df[df['Department'].isin(['HR', 'Finance'])])

# Using query()
print("\nUsing query():")
print(df.query('Age > 25 and Salary > 50000'))
```

# Part 7: Data Manipulation

## Adding/Removing Columns
- Add new column: `df['new_col'] = ...`
- Drop column: `drop()`
- Rename column: `rename()`

## Transformations
- `apply()`: Apply function to rows/columns
- `map()`: Map values (Series only)
- `str.methods()`: String operations
- `astype()`: Change data type

## Sorting
- `sort_values()`: Sort by column values
- `sort_index()`: Sort by index

```python
# Example: Adding and manipulating columns

df_manip = df.copy()

# Add new column
df_manip['Bonus'] = df_manip['Salary'] * 0.1
print("After adding Bonus column:")
print(df_manip)

# Add calculated column
df_manip['Salary_Category'] = df_manip['Salary'].apply(lambda x: 'High' if x > 60000 else 'Low')
print("\nAfter adding Salary_Category:")
print(df_manip)

# Drop column
df_manip = df_manip.drop('Bonus', axis=1)
print("\nAfter dropping Bonus column:")
print(df_manip)
```

```python
# Example: Sorting data

# Sort by single column
print("Sorted by Age (ascending):")
print(df.sort_values('Age'))

# Sort by multiple columns
print("\nSorted by Department, then Salary (descending):")
print(df.sort_values(['Department', 'Salary'], ascending=[True, False]))

# Sort by index
print("\nSort by index:")
print(df.sort_index(ascending=False))
```

# Part 8: GroupBy and Aggregation

## GroupBy
- `groupby()`: Group by one or more columns
- `agg()`: Apply aggregation functions
- `transform()`: Apply function to group
- `filter()`: Filter groups

## Common Aggregations
- `sum()`, `mean()`, `median()`, `std()`, `var()`
- `min()`, `max()`, `count()`, `size()`
- `first()`, `last()`
- `describe()`

```python
# Example: GroupBy operations

# Group by single column
print("Average salary by Department:")
print(df.groupby('Department')['Salary'].mean())

# Multiple aggregations
print("\nDepartment statistics:")
print(df.groupby('Department')['Salary'].agg(['count', 'mean', 'min', 'max']))

# Group by multiple columns
df_multi = df.copy()
df_multi['Seniority'] = ['Junior', 'Senior', 'Junior', 'Senior', 'Junior']
print("\nSalary by Department and Seniority:")
print(df_multi.groupby(['Department', 'Seniority'])['Salary'].mean())
```

```python
# Example: Aggregation with multiple functions

agg_dict = {
    'Age': ['mean', 'min', 'max'],
    'Salary': ['sum', 'mean'],
    'Name': 'count'
}

print("Custom aggregations by Department:")
print(df.groupby('Department').agg(agg_dict))
```

# Part 9: Merging and Joining

## Merge Types
- `pd.merge()`: SQL-like join
- `join()`: Join on index
- `concat()`: Concatenate DataFrames
- `append()`: Add rows (deprecated, use concat)

## Join Types
- `inner`: Only matching rows
- `left`: All rows from left DataFrame
- `right`: All rows from right DataFrame
- `outer`: All rows from both DataFrames

```python
# Example: Merging DataFrames

# Create two DataFrames
df1 = pd.DataFrame({
    'ID': [1, 2, 3, 4],
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana']
})

df2 = pd.DataFrame({
    'ID': [1, 2, 3, 5],
    'Salary': [50000, 60000, 55000, 70000]
})

print("DataFrame 1:")
print(df1)
print("\nDataFrame 2:")
print(df2)

# Inner merge (only matching)
print("\nInner merge:")
print(pd.merge(df1, df2, on='ID', how='inner'))

# Left merge
print("\nLeft merge:")
print(pd.merge(df1, df2, on='ID', how='left'))

# Outer merge
print("\nOuter merge:")
print(pd.merge(df1, df2, on='ID', how='outer'))
```

```python
# Example: Concatenating DataFrames

df_a = pd.DataFrame({
    'A': [1, 2],
    'B': [3, 4]
})

df_b = pd.DataFrame({
    'A': [5, 6],
    'B': [7, 8]
})

# Concatenate rows
print("Concatenate rows (axis=0):")
print(pd.concat([df_a, df_b], ignore_index=True))

# Concatenate columns
print("\nConcatenate columns (axis=1):")
print(pd.concat([df_a, df_b], axis=1))
```

# Part 10: Time Series Analysis

## DateTime Operations
- `pd.to_datetime()`: Convert to datetime
- `dt.accessor`: Access date/time components
- `date_range()`: Create date range
- `resample()`: Resample time series

## Components
- `dt.year`, `dt.month`, `dt.day`
- `dt.hour`, `dt.minute`, `dt.second`
- `dt.dayofweek`, `dt.week`

```python
# Example: DateTime operations

# Create date range
dates = pd.date_range('2024-01-01', periods=5, freq='D')
df_ts = pd.DataFrame({
    'Date': dates,
    'Sales': [100, 150, 120, 200, 180]
})

print("Time Series DataFrame:")
print(df_ts)

# Extract date components
df_ts['Year'] = df_ts['Date'].dt.year
df_ts['Month'] = df_ts['Date'].dt.month
df_ts['Day'] = df_ts['Date'].dt.day
df_ts['DayOfWeek'] = df_ts['Date'].dt.day_name()

print("\nAfter extracting components:")
print(df_ts)
```

```python
# Example: Resampling time series

# Create longer time series
dates = pd.date_range('2024-01-01', periods=30, freq='D')
df_resample = pd.DataFrame({
    'Date': dates,
    'Sales': np.random.randint(50, 200, 30)
})

# Set Date as index
df_resample.set_index('Date', inplace=True)

print("Daily Sales (first 5 rows):")
print(df_resample.head())

# Resample to weekly average
print("\nWeekly average sales:")
print(df_resample.resample('W').mean())

# Resample to monthly sum
print("\nMonthly total sales:")
print(df_resample.resample('M').sum())
```

# Part 11: Data Export

## Export Formats
- `to_csv()`: Export to CSV
- `to_excel()`: Export to Excel
- `to_json()`: Export to JSON
- `to_sql()`: Export to SQL database
- `to_html()`: Export to HTML
- `to_pickle()`: Export to pickle format

```python
# Example: Exporting data

# Export to CSV
df.to_csv('employees.csv', index=False)
print("Exported to CSV")

# Export to Excel
# df.to_excel('employees.xlsx', index=False)
# print("Exported to Excel")

# Export to JSON
df.to_json('employees.json', orient='records')
print("Exported to JSON")

# Read back from CSV
df_read = pd.read_csv('employees.csv')
print("\nRead from CSV:")
print(df_read)
```

# Part 12: Practice Exercises

## Exercise 1: Data Cleaning and Analysis
Given a dataset with missing values, clean it and perform analysis.

```python
# Exercise 1: Data Cleaning

# Create messy dataset
messy_data = {
    'ID': [1, 2, 3, 4, 5, 5],
    'Name': ['Alice', 'Bob', None, 'Diana', 'Eve', 'Eve'],
    'Score': [85, None, 90, 88, 92, 92],
    'Grade': ['A', 'B', 'A', None, 'A', 'A']
}

df_messy = pd.DataFrame(messy_data)
print("Original messy data:")
print(df_messy)

# Clean the data
df_clean = df_messy.drop_duplicates()
df_clean = df_clean.dropna()

print("\nCleaned data:")
print(df_clean)

# Analysis
print(f"\nAverage Score: {df_clean['Score'].mean():.2f}")
print(f"Grade distribution:\n{df_clean['Grade'].value_counts()}")
```

## Exercise 2: Filtering and Transformation
Filter specific data and create new columns.

```python
# Exercise 2: Filtering and Transformation

# Create sample sales data
sales_data = {
    'Product': ['A', 'B', 'C', 'A', 'B', 'C', 'A'],
    'Quantity': [10, 5, 8, 15, 3, 12, 7],
    'Price': [100, 200, 150, 100, 200, 150, 100]
}

df_sales = pd.DataFrame(sales_data)

# Add new columns
df_sales['Total_Sales'] = df_sales['Quantity'] * df_sales['Price']
df_sales['Category'] = df_sales['Total_Sales'].apply(lambda x: 'High' if x > 1000 else 'Low')

print("Sales data with new columns:")
print(df_sales)

# Filter high-value sales
high_sales = df_sales[df_sales['Category'] == 'High']
print("\nHigh-value sales:")
print(high_sales)
```

## Exercise 3: GroupBy Analysis
Analyze data by groups.

```python
# Exercise 3: GroupBy Analysis

# Summary by product
print("Sales summary by product:")
summary = df_sales.groupby('Product').agg({
    'Quantity': 'sum',
    'Price': 'first',
    'Total_Sales': ['sum', 'mean']
})
print(summary)

# Product with highest average sale
avg_by_product = df_sales.groupby('Product')['Total_Sales'].mean()
top_product = avg_by_product.idxmax()
print(f"\nProduct with highest average sale: {top_product} (${avg_by_product[top_product]:.2f})")
```

## Exercise 4: Merging Datasets
Merge two related datasets.

```python
# Exercise 4: Merging datasets

# Create customer and order data
customers = pd.DataFrame({
    'CustomerID': [1, 2, 3, 4],
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana'],
    'City': ['NYC', 'LA', 'Chicago', 'Boston']
})

orders = pd.DataFrame({
    'OrderID': [101, 102, 103, 104, 105],
    'CustomerID': [1, 2, 1, 3, 2],
    'Amount': [500, 300, 250, 400, 350]
})

print("Customers:")
print(customers)
print("\nOrders:")
print(orders)

# Merge
merged = pd.merge(customers, orders, on='CustomerID', how='left')
print("\nMerged data:")
print(merged)

# Analysis: Total amount by customer
print("\nTotal amount by customer:")
print(merged.groupby('Name')['Amount'].sum())
```

## Exercise 5: Time Series Aggregation
Aggregate time series data by periods.

```python
# Exercise 5: Time Series Analysis

# Create daily sales data
dates = pd.date_range('2024-01-01', periods=30, freq='D')
ts_sales = pd.DataFrame({
    'Date': dates,
    'Sales': np.random.randint(100, 500, 30)
})

ts_sales.set_index('Date', inplace=True)

print("Daily sales (first 5 rows):")
print(ts_sales.head())

# Weekly aggregation
weekly_sales = ts_sales.resample('W').agg({'Sales': ['sum', 'mean', 'max']})
print("\nWeekly sales summary:")
print(weekly_sales)

# Total monthly sales
print("\nTotal monthly sales:")
print(ts_sales.resample('M').sum())
```

# Key Pandas Concepts Summary

## Data Structures
1. **Series**: 1D labeled array (like list with index)
2. **DataFrame**: 2D labeled table (like Excel sheet)

## Key Operations
| Operation | Method | Example |
|-----------|--------|----------|
| Load data | `pd.read_csv()` | Read from file |
| View data | `head()`, `tail()` | See first/last rows |
| Inspect | `info()`, `describe()` | Get data info/stats |
| Clean | `dropna()`, `fillna()` | Handle missing values |
| Filter | `df[condition]` | Select rows |
| Select | `loc[]`, `iloc[]` | Access by label/position |
| Sort | `sort_values()` | Arrange data |
| Group | `groupby()` | Aggregate by groups |
| Merge | `merge()`, `join()` | Combine datasets |
| Export | `to_csv()` | Save to file |

## Analysis Workflow
1. **Load**: Import data from various sources
2. **Explore**: Understand data structure and content
3. **Clean**: Handle missing values and duplicates
4. **Transform**: Create new columns and prepare data
5. **Analyze**: GroupBy, aggregations, statistical analysis
6. **Visualize**: Create charts and plots
7. **Export**: Save results

## Best Practices
- Always check data types and missing values first
- Use `copy()` to avoid modifying original data
- Use `inplace=True` carefully (modifies original)
- Validate data after transformations
- Use meaningful column names
- Document your data cleaning steps
- Test code on sample data first

---

**Happy Data Analysis! 📊**
