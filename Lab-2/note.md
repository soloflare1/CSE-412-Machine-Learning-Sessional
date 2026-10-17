# Python Libraries: NumPy & Pandas

## 1. What is a Python Library?

A **library** is a collection of pre-written code that helps us perform tasks without writing everything from scratch.

For example:
- **NumPy:** Used for numerical calculations and working with arrays.
- **Pandas:** Used for working with structured data, such as tables and CSV files.

### Importing Libraries

```python
import numpy as np
import pandas as pd
```

**Concept:**
- `import` loads a library so we can use its functions.
- `np` is a short name (alias) for NumPy.
- `pd` is a short name (alias) for Pandas.

These aliases make the code shorter and easier to write.

---

# Part A: NumPy

## 2. What is NumPy?

**NumPy (Numerical Python)** is a Python library used for numerical calculations. It provides a special data structure called an **array** and allows us to perform mathematical operations on its elements easily.

### Creating a NumPy Array

```python
import numpy as np

ar = np.array([2, 7, 9, 4, 10])

print(ar)
```

Output:

```text
[ 2  7  9  4 10]
```

**Concept:**
- `np.array()` converts the given sequence of values into a NumPy array.
- `ar` is the variable that stores the array.
- An array stores multiple values in a single structure.

Unlike a normal Python list, a NumPy array supports efficient numerical operations on all its elements.

## 3. Basic NumPy Functions

Suppose we have this array:

```python
ar = np.array([2, 7, 9, 4, 10])
```

### a. `sum()`

Finds the total of all elements.

```python
print(ar.sum())
```

Output:

```text
32
```

Calculation: 2 + 7 + 9 + 4 + 10 = 32.

### b. `min()`

Finds the smallest element.

```python
print(ar.min())
```

Output:

```text
2
```

### c. `max()`

Finds the largest element.

```python
print(ar.max())
```

Output:

```text
10
```

### d. `mean()`

Finds the average of all elements.

```python
print(ar.mean())
```

Output:

```text
6.4
```

Formula:

Average = Sum of all elements ÷ Number of elements

Here, 32 ÷ 5 = 6.4.

### e. `std()`

Finds the **standard deviation**, which measures how spread out the values are around their mean.

```python
print(ar.std())
```

Output:

```text
2.870540018881465
```

**Easy concept:** A smaller standard deviation generally means the values are closer to the mean. A larger standard deviation means they are more spread out.

---

## 4. Arithmetic Operations on NumPy Arrays

NumPy allows us to perform arithmetic operations on every element of an array.

```python
ar = np.array([2, 7, 9, 4, 10])

print(ar + 5)
print(ar - 5)
print(ar * 5)
print(ar / 5)
```

Output:

```text
[ 7 12 14  9 15]
[-3  2  4 -1  5]
[10 35 45 20 50]
[0.4 1.4 1.8 0.8 2. ]
```

### How does it work?

When we write `ar + 5`, NumPy adds 5 to every element.

| Operation | Meaning | First element calculation |
|---|---|---|
| `ar + 5` | Add 5 to every element | 2 + 5 = 7 |
| `ar - 5` | Subtract 5 from every element | 2 - 5 = -3 |
| `ar * 5` | Multiply every element by 5 | 2 × 5 = 10 |
| `ar / 5` | Divide every element by 5 | 2 ÷ 5 = 0.4 |

This is called **element-wise operation** because the operation is applied to each array element.

## 5. Power and Square Root

### a. Power

Power means raising a number to a particular exponent.

For example, \(2^2 = 2 \times 2 = 4\).

```python
print(np.power(ar, 2))
```

Output:

```text
[  4  49  81  16 100]
```

Each element is squared.

### b. Square Root

The square root of a number is a value that, when multiplied by itself, gives the original number.

```python
print(np.sqrt(ar))
```

Output:

```text
[1.41421356 2.64575131 3.         2.         3.16227766]
```

For example:
- Square root of 9 = 3
- Square root of 4 = 2

NumPy performs the operation on every element.

## 6. Array Slicing

**Slicing** means selecting a portion of an array.

```python
ar = np.array([2, 7, 9, 4, 10])

print(ar[2:4])
```

Output:

```text
[9 4]
```

### Understanding `ar[start:end]`

- `start` is the index where selection begins.
- `end` is the index where selection stops, but the end index is **not included**.
- Python indexing starts from `0`.

| Index | 0 | 1 | 2 | 3 | 4 |
|---|---:|---:|---:|---:|---:|
| Value | 2 | 7 | 9 | 4 | 10 |

In `ar[2:4]`, Python selects the values at indexes 2 and 3.

Therefore, the result is `[9 4]`.

**Remember:** The starting index is included, but the ending index is excluded.

---

# Part B: Pandas

## 7. What is Pandas?

**Pandas** is a Python library used for handling, organizing, analyzing, and manipulating structured data.

For example, student information can be stored in a table containing names, ages, and marks. Pandas helps us read and work with this kind of data.

```python
import pandas as pd
```

## 8. What is a DataFrame?

A **DataFrame** is a two-dimensional data structure in Pandas that organizes data into rows and columns, similar to a spreadsheet or database table.

For example:

| Country | Age | Salary | Purchased |
|---|---:|---:|---|
| France | 44 | 72000 | No |
| Spain | 27 | 48000 | Yes |
| Germany | 30 | 54000 | No |

Here:
- Each **row** represents one record.
- Each **column** represents a variable or attribute.
- `Country`, `Age`, `Salary`, and `Purchased` are column names.

A DataFrame is useful because we can select columns, inspect data, find missing values, and remove unnecessary columns.

## 9. Reading a CSV File

### What is a CSV file?

CSV stands for **Comma-Separated Values**. It is a file format used to store tabular data. Values are commonly separated by commas, and the first row often contains column names.

Example:

```text
Country,Age,Salary,Purchased
France,44,72000,No
Spain,27,48000,Yes
Germany,30,54000,No
```

### Reading a CSV file with Pandas

```python
import pandas as pd

path = "/content/drive/MyDrive/Colab Notebooks/ML/Pandas & numpy/Data.csv"

df = pd.read_csv(path)
```

**Concept:**
- `path` stores the location of the file.
- `pd.read_csv(path)` reads the CSV file.
- `df` stores the resulting DataFrame.

The file must exist at the specified location for this code to work.

## 10. Selecting Columns

Sometimes we need only specific information from a DataFrame.

### a. Selecting one column

```python
print(df["Age"])
```

This selects the `Age` column.

**Concept:** A single pair of square brackets with a column name selects one column as a Pandas Series.

### b. Selecting multiple columns

```python
print(df[["Age", "Salary", "Country"]])
```

This selects the `Age`, `Salary`, and `Country` columns.

**Concept:** The inner list contains the names of the columns we want. The outer square brackets are used to select those columns from the DataFrame.

**Remember:**
- `df["Age"]` → one column
- `df[["Age", "Salary"]]` → multiple columns

The selected columns appear in the order specified in the list.

## 11. Displaying Data with `head()`

The `head()` function displays the first few rows of a DataFrame.

### a. First five rows

```python
print(df.head())
```

By default, `head()` displays the first **5 rows**.

### b. First nine rows

```python
print(df.head(9))
```

This displays the first 9 rows.

**Concept:** We use `head()` to quickly inspect a dataset without displaying the entire table.

## 12. Understanding `shape`

The `shape` attribute returns the number of rows and columns in a DataFrame.

```python
print(df.shape)
```

Output from the given dataset:

```text
(10, 4)
```

**Concept:**
- `10` means the DataFrame has 10 rows.
- `4` means the DataFrame has 4 columns.

The format is:

```text
(number_of_rows, number_of_columns)
```

**Important:** `shape` is an attribute, not a function. Therefore, we write `df.shape`, not `df.shape()`.

## 13. Understanding `describe()`

The `describe()` function generates summary statistics for suitable columns, such as numerical columns.

```python
print(df.describe())
```

For numerical data, the output commonly includes:

| Statistic | Meaning |
|---|---|
| `count` | Number of non-missing values |
| `mean` | Average |
| `std` | Standard deviation |
| `min` | Minimum value |
| `25%` | First quartile |
| `50%` | Median |
| `75%` | Third quartile |
| `max` | Maximum value |

**Why is it useful?**

Instead of calculating every statistic manually, we can quickly understand the distribution of numerical data.

The exact output depends on the columns and their data types.

## 14. Understanding `info()`

The `info()` method displays structural information about a DataFrame.

```python
df.info()
```

It provides information such as:
- Number of rows
- Column names
- Number of non-null values in each column
- Data types
- Memory usage

**Concept:** `info()` helps us check the structure of a dataset and identify columns that contain missing values.

### `describe()` vs. `info()`

| `describe()` | `info()` |
|---|---|
| Shows summary statistics | Shows structural information |
| Useful for understanding numerical data | Useful for understanding columns and data types |
| Displays values such as mean and maximum | Displays non-null counts and data types |

---

# Part C: Missing Values in Pandas

## 15. What Are Missing Values?

A **missing value** means that a particular field has no available value in the dataset.

For example:

| Country | Age | Salary |
|---|---:|---:|
| France | 44 | 72000 |
| Spain | NaN | 48000 |
| Germany | 30 | NaN |

Here, `NaN` represents a missing or unavailable value.

Missing values may occur because information was not collected, was not entered, or was unavailable in the original data.

They need to be identified before many data analysis or machine learning tasks.

## 16. Detecting Missing Values with `isna()`

```python
print(df.isna())
```

**Concept:** `isna()` checks every cell and returns a Boolean DataFrame:
- `True` means the value is missing.
- `False` means the value is present.

Example:

| Country | Age | Salary |
|---|---|---|
| France | False | False |
| Spain | True | False |
| Germany | False | True |

This lets us identify the locations of missing values.

## 17. Counting Missing Values with `isna().sum()`

```python
print(df.isna().sum())
```

**Concept:** Two operations are combined here.

1. `df.isna()` identifies missing values using `True` and `False`.
2. `.sum()` counts the `True` values in each column because Boolean `True` behaves like `1` and `False` behaves like `0` in this calculation.

Example output:

```text
Country      0
Age          1
Salary       1
Purchased    0
dtype: int64
```

This means:
- `Country` has 0 missing values.
- `Age` has 1 missing value.
- `Salary` has 1 missing value.
- `Purchased` has 0 missing values.

The numbers above are an illustrative example; actual counts depend on the dataset.

## 18. Finding Rows That Contain Missing Values

```python
print(df[df.isna().any(axis=1)])
```

This code selects all rows containing at least one missing value.

Let's break it down:

**Step 1: `df.isna()`**

Checks every cell and returns `True` for missing values.

**Step 2: `.any(axis=1)`**

Checks each row to see whether at least one value is `True`.

- `axis=1` means the operation is performed across the columns of each row.
- `any()` returns `True` if at least one value in that row satisfies the condition.

**Step 3: `df[...]`**

Uses the resulting Boolean values to select only the matching rows.

**Result:** The output contains only rows where at least one column has a missing value.

---

# Part D: Dropping a Column

## 19. Removing a Column with `drop()`

Sometimes a column is unnecessary for our analysis. Pandas allows us to remove it using `drop()`.

```python
df = df.drop(columns=["Age"])

print(df.head())
```

**Concept:**
- `columns=["Age"]` specifies the column to remove.
- `drop()` returns a DataFrame without that column.
- `df =` assigns the resulting DataFrame back to `df`.

After this operation, `Age` is no longer present in the updated `df`.

**Important:** This code removes the entire `Age` column, including all its values. It does not simply remove the missing values from that column.

If you want to remove a column permanently from the current variable, assigning the result back to `df` is one common approach.

---

# Part E: Quick Revision

## 20. Important Functions and Attributes

| Code | Purpose |
|---|---|
| `np.array()` | Creates a NumPy array |
| `ar.sum()` | Calculates the sum |
| `ar.min()` | Finds the minimum |
| `ar.max()` | Finds the maximum |
| `ar.mean()` | Calculates the mean |
| `ar.std()` | Calculates the standard deviation |
| `np.power(ar, 2)` | Raises each element to a power of 2 |
| `np.sqrt(ar)` | Calculates the square root of each element |
| `ar[2:4]` | Selects elements from index 2 up to, but not including, index 4 |
| `pd.read_csv(path)` | Reads a CSV file into a DataFrame |
| `df["Age"]` | Selects one column |
| `df[["Age", "Salary"]]` | Selects multiple columns |
| `df.head()` | Displays the first five rows |
| `df.shape` | Returns the number of rows and columns |
| `df.describe()` | Generates summary statistics |
| `df.info()` | Displays DataFrame structure |
| `df.isna()` | Detects missing values |
| `df.isna().sum()` | Counts missing values in each column |
| `df[df.isna().any(axis=1)]` | Selects rows containing missing values |
| `df.drop(columns=["Age"])` | Returns a DataFrame without the `Age` column |

## 21. Lab Viva Questions

**Q1. What is NumPy?**

NumPy is a Python library used for numerical calculations and array operations.

**Q2. What is Pandas?**

Pandas is a Python library used for data manipulation and analysis.

**Q3. What is a DataFrame?**

A DataFrame is a two-dimensional structure containing rows and columns.

**Q4. What is the difference between NumPy and Pandas?**

NumPy mainly focuses on numerical arrays and mathematical operations, while Pandas focuses on structured data manipulation and analysis.

**Q5. What is the difference between `head()` and `shape`?**

`head()` displays the first few rows, whereas `shape` returns the number of rows and columns.

**Q6. What does `axis=1` mean in `.any(axis=1)`?**

It means the condition is evaluated across the columns of each row.

**Q7. What is the difference between `isna()` and `isna().sum()`?**

`isna()` identifies missing values, while `isna().sum()` counts the missing values in each column.

**Q8. Why do we use `pd.read_csv()`?**

We use it to load data from a CSV file into a Pandas DataFrame.

**Q9. Why is `df.shape` written without parentheses?**

Because `shape` is an attribute, not a method.

**Q10. What does `df.drop(columns=["Age"])` do?**

It returns a DataFrame without the `Age` column.

**Q11. Why do we use array slicing?**

Slicing allows us to select a specific portion of an array.

**Q12. What does `ar.mean()` calculate?**

It calculates the average of the array elements.

---

- **NumPy** helps us calculate.
- **Pandas** helps us organize, inspect, and manipulate data.
- An **array** stores multiple values.
- A **DataFrame** organizes data into rows and columns.
- **Slicing** selects part of an array.
- **Missing-value functions** help us identify incomplete data.
- **`drop()`** helps us remove unwanted rows or columns.
