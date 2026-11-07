# Python Libraries: NumPy & Pandas

Complete ML Lab Notes | Easy English | Code Execution, Concepts, Formulas, Outputs & Viva

I'll explain every code statement by breaking it into what is called, what input it takes, what operation happens, and what gets returned.

# Part 1: Python Libraries

## 1. What is a Python Library?

A Library is a collection of pre-written code that helps us perform tasks without writing everything from scratch.

Examples:

- NumPy: Numerical calculations and array operations.
- Pandas: Structured data handling and analysis.

### Importing Libraries

```
import numpy as npimport pandas as pd
```

Code breakdown:

| Code     | Meaning          |
| -------- | ---------------- |
| `import` | Loads a library  |
| `numpy`  | Library name     |
| `as`     | Assigns an alias |
| `np`     | Alias of NumPy   |
| `pandas` | Library name     |
| `pd`     | Alias of Pandas  |

Execution: Python loads the libraries and makes their functions and features available through `np` and `pd`.

# Part A: NumPy

## 2. What is NumPy?

NumPy (Numerical Python) is a Python library used for numerical calculations. It provides a special data structure called an array.

### Creating a NumPy Array

```
import numpy as npar = np.array([2, 7, 9, 4, 10])print(ar)
```

Output:

```
[ 2  7  9  4 10]
```

### Code Breakdown

Let's understand this statement:

```
ar = np.array([2, 7, 9, 4, 10])
```

| Part               | Meaning                                  |
| ------------------ | ---------------------------------------- |
| `np`               | NumPy library alias                      |
| `.`                | Accesses a library attribute/function    |
| `array()`          | NumPy function called to create an array |
| `[2, 7, 9, 4, 10]` | Input Python list                        |
| `=`                | Assignment operator                      |
| `ar`               | Variable storing the returned array      |

### Execution Flow

1. Python accesses the `array()` function from NumPy.
2. The Python list `[2, 7, 9, 4, 10]` is passed as an argument.
3. NumPy creates an ndarray using the input values.
4. The function returns the newly created array.
5. Assignment stores the returned array in `ar`.

Execution visualization

`[2, 7, 9, 4, 10]`

Input Python list

`np.array()`

Function call

`[2 7 9 4 10]`

Returned NumPy array (ndarray)

`ar =`

Stored in variable ar

### Checking the Data Type

```
print(type(ar))
```

Output:

```
<class 'numpy.ndarray'>
```

- `type()` → Built-in Python function that checks the data type.
- `ar` → Argument passed to `type()`.
- `print()` → Displays the returned type information.
- `ndarray` → N-dimensional array.

Remember: `np.array()` creates a new NumPy array from the supplied sequence. The original Python list remains unchanged.

## 3. Basic NumPy Functions

Suppose:

```
ar = np.array([2, 7, 9, 4, 10])
```

### a. `sum()`

Finds the total of all elements.

```
print(ar.sum())
```

Output:

```
32
```

Code breakdown:

- `ar` → Array object.
- `.sum()` → Calls the array's sum method.
- `()` → Executes the method.
- `print()` → Displays the returned result.

Execution: The method adds all array elements and returns their total.

\\[ 2+7+9+4+10=32 \\]

### b. `min()`

Finds the smallest element.

```
print(ar.min())
```

Output: `2`

Execution: Calls the `min()` method of the array and returns the smallest element.

### c. `max()`

Finds the largest element.

```
print(ar.max())
```

Output: `10`

Execution: Calls the `max()` method and returns the largest element.

### d. `mean()`

Calculates the average of all elements.

```
print(ar.mean())
```

Output: `6.4`

Execution: Calls `mean()` and returns the arithmetic average.

Formula:

\\[ \text{Mean}=\frac{\text{Sum}}{\text{Number of elements}} \\]

\\[ =\frac{32}{5}=6.4 \\]

### e. `std()`

Calculates the Standard Deviation, which measures how spread out the values are around their mean.

```
print(ar.std())
```

Output:

```
2.870540018881465
```

Execution: Calls the `std()` method and returns the population standard deviation by default for a NumPy array.

Formula:

\\[ \sigma=\sqrt{\frac{\sum(x_i-\mu)^2}{N}} \\]

Where:

- \\(x_i\\) = Each value.
- \\(\mu\\) = Mean.
- \\(N\\) = Number of values.

Concept:

- Smaller standard deviation → Values are closer to the mean.
- Larger standard deviation → Values are more spread out.

### Quick Function Breakdown

| Code        | What is called? | What is returned?  |
| ----------- | --------------- | ------------------ |
| `ar.sum()`  | `sum()` method  | Total              |
| `ar.min()`  | `min()` method  | Smallest value     |
| `ar.max()`  | `max()` method  | Largest value      |
| `ar.mean()` | `mean()` method | Average            |
| `ar.std()`  | `std()` method  | Standard deviation |

## 4. Arithmetic Operations on NumPy Arrays

NumPy supports element-wise arithmetic operations.

```
ar = np.array([2, 7, 9, 4, 10])print(ar + 5)print(ar - 5)print(ar * 5)print(ar / 5)print(ar)
```

Output:

```
[ 7 12 14  9 15]
[-3  2  4 -1  5]
[10 35 45 20 50]
[0.4 1.4 1.8 0.8 2. ]
[ 2  7  9  4 10]
```

### What happens internally?

For:

```
ar + 5
```

- `ar` → NumPy array.
- `+` → Addition operator.
- `5` → Scalar operand.
- NumPy broadcasts `5` across every array element.
- Addition happens element by element.
- A new array is returned.

| Operation | First element | Result |
| --------- | ------------- | ------ |
| `ar + 5`  | 2 + 5         | 7      |
| `ar - 5`  | 2 - 5         | -3     |
| `ar * 5`  | 2 × 5         | 10     |
| `ar / 5`  | 2 ÷ 5         | 0.4    |

### Original vs New Array

These operations return new arrays. They do not modify `ar`.

```
print(ar)
```

Output:

```
[ 2  7  9  4 10]
```

But:

```
ar = ar + 5
```

Here:

1. `ar + 5` returns a new array.
2. `=` assigns that returned array to `ar`.
3. The variable `ar` now refers to the updated array.

## 5. Power and Square Root

### a. Power – `np.power()`

Raises each element to a specified exponent.

```
print(np.power(ar, 2))
```

For the original array, output:

```
[  4  49  81  16 100]
```

Code breakdown:

| Part      | Meaning                     |
| --------- | --------------------------- |
| `np`      | NumPy alias                 |
| `.`       | Accesses a function         |
| `power()` | NumPy function called       |
| `ar`      | First argument: input array |
| `2`       | Second argument: exponent   |

Execution: NumPy applies the power operation to every element and returns a new array.

\\[ [2^2,7^2,9^2,4^2,10^2] \\]

### b. Square Root – `np.sqrt()`

Calculates the square root of every element.

```
print(np.sqrt(ar))
```

Output:

```
[1.41421356 2.64575131 3.         2.         3.16227766]
```

Code breakdown:

- `np` → NumPy alias.
- `sqrt()` → NumPy function called.
- `ar` → Input array.
- Returned value → New array containing the square roots.

Examples:

\\[ \sqrt{9}=3,\qquad \sqrt{4}=2 \\]

## 6. Array Slicing

Slicing means selecting a portion of an array.

### Formula

```
array[start : stop : step]
```

- `start` → Starting index (included).
- `stop` → Ending index (excluded).
- `step` → Interval between selected elements (default = 1).

### Example

```
ar = np.array([2, 7, 9, 4, 10])print(ar[2:4])
```

Output:

```
[9 4]
```

Code breakdown:

- `ar` → Array variable.
- → Indexing/slicing operator.
- `2` → Starting index.
- `4` → Stopping index (excluded).
- `:` → Separates slicing parameters.

The selected indexes are 2 and 3.

| Index | 0 | 1 | 2 | 3 | 4  |
| ----- | - | - | - | - | -- |
| Value | 2 | 7 | 9 | 4 | 10 |

### More Slicing Examples

| Code       | Output         |
| ---------- | -------------- |
| `ar[0:3]`  | `[2 7 9]`      |
| `ar[1:4]`  | `[7 9 4]`      |
| `ar[:3]`   | `[2 7 9]`      |
| `ar[2:]`   | `[9 4 10]`     |
| `ar[::2]`  | `[2 9 10]`     |
| `ar[::-1]` | `[10 4 9 7 2]` |
| `ar[-1]`   | `10`           |
| `ar[-2:]`  | `[4 10]`       |

### View vs Copy

Basic NumPy slicing returns a View, not an independent copy.

```
ar = np.array([2, 7, 9, 4, 10])s = ar[2:4]s[0] = 100print(s)print(ar)
```

Output:

```
[100   4]
[  2   7 100   4  10]
```

What happened?

1. `ar[2:4]` creates a view of the original array.
2. `s` refers to the selected portion.
3. `s[0] = 100` changes the first element of that view.
4. Because the view shares the underlying data, `ar` also changes.

To create an independent copy:

```
s = ar[2:4].copy()
```

- `.copy()` → Calls the array's copy method.
- Returns → A new independent array.

# Part B: Pandas

## 7. What is Pandas?

Pandas is a Python library used for handling, organizing, analyzing, and manipulating structured data.

```
import pandas as pd
```

- `import` → Loads the library.
- `pandas` → Library name.
- `as pd` → Assigns the alias `pd`.

## 8. What is a DataFrame?

A DataFrame is a two-dimensional data structure that stores data in rows and columns.

Example:

| Country | Age | Salary | Purchased |
| ------- | --- | ------ | --------- |
| France  | 44  | 72000  | No        |
| Spain   | 27  | 48000  | Yes       |
| Germany | 30  | 54000  | No        |

- Row → One record.
- Column → One variable or attribute.
- DataFrame → Complete table.

### Creating a DataFrame

```
data = {    "Country": ["France", "Spain", "Germany"],    "Age": [44, 27, 30],    "Salary": [72000, 48000, 54000]}df = pd.DataFrame(data)print(df)
```

Code breakdown:

| Part                             | Meaning                             |
| -------------------------------- | ----------------------------------- |
| `data`                           | Dictionary variable                 |
| `{}`                             | Creates a dictionary                |
| `"Country"`                      | Dictionary key / column name        |
| `["France", "Spain", "Germany"]` | Column values                       |
| `pd`                             | Pandas alias                        |
| `DataFrame()`                    | Pandas constructor called           |
| `data`                           | Input argument                      |
| `df`                             | Variable storing returned DataFrame |

Execution:

1. A Python dictionary stores the column names and their values.
2. `pd.DataFrame()` receives the dictionary.
3. Pandas constructs a DataFrame.
4. The returned DataFrame is assigned to `df`.

## 9. Reading a CSV File

### What is CSV?

CSV stands for Comma-Separated Values.

It is a file format used to store tabular data.

Example:

```
Country,Age,Salary,Purchased
France,44,72000,No
Spain,27,48000,Yes
Germany,30,54000,No
```

### Loading a Dataset

```
import pandas as pdpath = "/content/drive/MyDrive/Colab Notebooks/ML/Pandas & numpy/Data.csv"df = pd.read_csv(path)
```

Code breakdown:

| Part         | Meaning                                 |
| ------------ | --------------------------------------- |
| `path`       | Variable storing file location          |
| `pd`         | Pandas alias                            |
| `read_csv()` | Pandas function called                  |
| `path`       | Argument passed to the function         |
| `df`         | Variable storing the returned DataFrame |

Execution:

1. Python accesses `read_csv()` from Pandas.
2. The file path is passed as an argument.
3. Pandas reads the CSV file.
4. The CSV contents are converted into a DataFrame.
5. The returned DataFrame is assigned to `df`.

## 10. Selecting Columns

### a. Selecting One Column

```
print(df["Age"])
```

Breakdown:

- `df` → DataFrame object.
- `["Age"]` → Selects the column named `Age`.
- Returns → A Pandas Series.
- `print()` → Displays the result.

### b. Selecting Multiple Columns

```
print(df[["Age", "Salary", "Country"]])
```

Breakdown:

- Inner `[ ]` → Python list containing column names.
- Outer `[ ]` → Selects the requested columns from `df`.
- Returns → A new DataFrame containing those columns.

| Code                    | Returned object |
| ----------------------- | --------------- |
| `df["Age"]`             | Series          |
| `df[["Age", "Salary"]]` | DataFrame       |

The selected columns appear in the requested order.

## 11. Displaying Data with `head()`

Displays the first few rows of a DataFrame.

### a. First Five Rows

```
print(df.head())
```

Breakdown:

- `df` → DataFrame.
- `.head()` → Calls the DataFrame method.
- No argument → Uses the default value of 5.
- Returns → A DataFrame containing the first five rows.

### b. First Nine Rows

```
print(df.head(9))
```

Here, `9` is passed as an argument.

It returns the first nine rows.

## 12. Understanding `shape`

Returns the dimensions of a DataFrame.

```
print(df.shape)
```

Example output:

```
(10, 4)
```

Breakdown:

- `df` → DataFrame.
- `.shape` → Accesses the shape attribute.
- Returns → A tuple `(rows, columns)`.

Here:

- 10 = Rows.
- 4 = Columns.

Important: `shape` is an attribute, not a method.

```
df.shape      # Correctdf.shape()    # Incorrect
```

## 13. Understanding `describe()`

Generates summary statistics for suitable columns.

```
print(df.describe())
```

Breakdown:

- `df` → DataFrame.
- `.describe()` → Calls the summary-statistics method.
- Returns → A DataFrame containing statistical information.

| Statistic | Meaning                      |
| --------- | ---------------------------- |
| `count`   | Number of non-missing values |
| `mean`    | Average                      |
| `std`     | Standard deviation           |
| `min`     | Minimum                      |
| `25%`     | First quartile               |
| `50%`     | Median                       |
| `75%`     | Third quartile               |
| `max`     | Maximum                      |

## 14. Understanding `info()`

Displays structural information about a DataFrame.

```
df.info()
```

Breakdown:

- `df` → DataFrame.
- `.info()` → Calls the information method.
- Displays → Rows, columns, non-null counts, data types and memory usage.

Difference between `describe()` and `info()`:

| `describe()`                | `info()`                                  |
| --------------------------- | ----------------------------------------- |
| Summary statistics          | Structural information                    |
| Mean, std, min, max         | Column names, data types, non-null counts |
| Returns statistical summary | Prints information about the DataFrame    |

# Part C: Missing Values

## 15. What Are Missing Values?

A Missing Value means that a particular field has no available value.

Example:

| Country | Age | Salary |
| ------- | --- | ------ |
| France  | 44  | 72000  |
| Spain   | NaN | 48000  |
| Germany | 30  | NaN    |

`NaN` commonly represents missing data.

## 16. Detecting Missing Values with `isna()`

```
print(df.isna())
```

Breakdown:

- `df` → DataFrame.
- `.isna()` → Calls the missing-value detection method.
- Returns → Boolean DataFrame.

Meaning:

- `True` → Missing value.
- `False` → Value exists.

Example:

| Country | Age   | Salary |
| ------- | ----- | ------ |
| France  | False | False  |
| Spain   | True  | False  |
| Germany | False | True   |

## 17. Counting Missing Values with `isna().sum()`

```
print(df.isna().sum())
```

This combines two method calls.

### Step 1: `df.isna()`

Checks each cell and returns Boolean values.

### Step 2: `.sum()`

Calls the sum method on the resulting Boolean DataFrame.

In this calculation:

\\[ True=1,\qquad False=0 \\]

Therefore, `.sum()` counts the missing values in each column.

Example output:

```
Country      0
Age          1
Salary       1
Purchased    0
dtype: int64
```

## 18. Finding Rows Containing Missing Values

```
print(df[df.isna().any(axis=1)])
```

This selects all rows containing at least one missing value.

### Breakdown

Step 1:

```
df.isna()
```

Returns a Boolean DataFrame.

Step 2:

```
.any(axis=1)
```

- `.any()` → Checks whether at least one value is `True`.
- `axis=1` → Checks across columns for each row.
- Returns → A Boolean Series.

Step 3:

```
df[condition]
```

Uses Boolean indexing to select rows where the condition is `True`.

Final result: Only rows containing at least one missing value are returned.

Execution flow

`df.isna()`

Detect missing values

`.any(axis=1)`

Check each row

`df[condition]`

Select matching rows

# Part D: Dropping a Column

## 19. Removing a Column with `drop()`

Sometimes a column is unnecessary for analysis.

```
df = df.drop(columns=["Age"])print(df.head())
```

Code breakdown:

| Part      | Meaning                                       |
| --------- | --------------------------------------------- |
| `df`      | Original DataFrame                            |
| `.drop()` | DataFrame method called                       |
| `columns` | Keyword argument specifying columns to remove |
| `["Age"]` | List of column names to remove                |
| Returns   | New DataFrame without Age                     |
| `df =`    | Assigns the returned DataFrame back to `df`   |

Execution:

1. Pandas receives the column name `Age`.
2. `drop()` creates and returns a DataFrame without that column.
3. Assignment updates the variable `df`.

Important: The entire column is removed, not just its missing values.

# Part E: Complete Quick Revision

## 20. NumPy Functions

| Code              | Function/Operation | Purpose                       |
| ----------------- | ------------------ | ----------------------------- |
| `np.array()`      | Function           | Creates an array              |
| `ar.sum()`        | Method             | Calculates total              |
| `ar.min()`        | Method             | Finds minimum                 |
| `ar.max()`        | Method             | Finds maximum                 |
| `ar.mean()`       | Method             | Calculates average            |
| `ar.std()`        | Method             | Calculates standard deviation |
| `np.power(ar, 2)` | Function           | Squares elements              |
| `np.sqrt(ar)`     | Function           | Calculates square roots       |
| `ar + 5`          | Operator           | Adds 5 to each element        |
| `ar[2:4]`         | Slicing            | Selects part of an array      |
| `ar.copy()`       | Method             | Creates an independent copy   |

## 21. Pandas Functions and Attributes

| Code                    | Type             | Purpose                        |
| ----------------------- | ---------------- | ------------------------------ |
| `pd.DataFrame()`        | Constructor      | Creates a DataFrame            |
| `pd.read_csv()`         | Function         | Reads CSV file                 |
| `df["Age"]`             | Indexing         | Selects one column             |
| `df[["Age", "Salary"]]` | Indexing         | Selects multiple columns       |
| `df.head()`             | Method           | Displays first five rows       |
| `df.shape`              | Attribute        | Returns dimensions             |
| `df.describe()`         | Method           | Generates statistics           |
| `df.info()`             | Method           | Displays structure             |
| `df.isna()`             | Method           | Detects missing values         |
| `df.isna().sum()`       | Combined methods | Counts missing values          |
| `df.drop()`             | Method           | Removes specified rows/columns |

# Part F: Lab Viva Questions

## 22. Important Questions & Answers

Q1. What is NumPy?

NumPy is a Python library used for numerical calculations and array operations.

Q2. What is Pandas?

Pandas is a Python library used for data manipulation and analysis.

Q3. What is `ndarray`?

It stands for N-dimensional array, which is the main array data structure of NumPy.

Q4. What does `np.array()` do?

It takes a sequence as input and returns a NumPy array.

Q5. What is the difference between a Python list and a NumPy array?

A Python list is a general-purpose collection, whereas a NumPy array supports efficient numerical and element-wise operations.

Q6. What is an element-wise operation?

An operation applied individually to every element of an array.

Q7. Does `ar + 5` change the original array?

No. It returns a new array.

Q8. What is slicing?

Selecting a portion of an array.

Q9. What is the slicing formula?

`array[start:stop:step]`

Q10. What is the difference between View and Copy?

View shares the original array's underlying data, while Copy creates independent data.

Q11. What does `np.power(ar, 2)` do?

It squares every element of the array.

Q12. What does `np.sqrt(ar)` do?

It calculates the square root of every element.

Q13. What is a DataFrame?

A two-dimensional data structure containing rows and columns.

Q14. What is a Series?

A one-dimensional labeled data structure in Pandas.

Q15. What is CSV?

Comma-Separated Values, a file format used for tabular data.

Q16. What does `pd.read_csv(path)` do?

It reads a CSV file and returns a Pandas DataFrame.

Q17. What is the difference between `df["Age"]` and `df[["Age"]]`?

`df["Age"]` returns a Series, while `df[["Age"]]` returns a DataFrame.

Q18. What does `head()` do?

Displays the first five rows by default.

Q19. What does `shape` return?

A tuple containing the number of rows and columns.

Q20. Why is `shape` written without parentheses?

Because it is an attribute, not a method.

Q21. What does `describe()` do?

Generates summary statistics.

Q22. What does `info()` do?

Displays structural information about a DataFrame.

Q23. What is a missing value?

A value that is absent or unavailable in a dataset.

Q24. What does `isna()` do?

Detects missing values and returns Boolean results.

Q25. What does `isna().sum()` do?

Counts missing values in each column.

Q26. What does `axis=1` mean?

It specifies an operation across columns for each row.

Q27. What does `.any()` do?

Returns `True` if at least one element satisfies the condition.

Q28. What does `df[df.isna().any(axis=1)]` do?

Selects rows containing at least one missing value.

Q29. What does `drop(columns=["Age"])` do?

Returns a DataFrame without the `Age` column.

Q30. What is the difference between `sum()` and `mean()`?

`sum()` calculates the total, whereas `mean()` calculates the average.

## Final Revision: What to Remember

| Topic            | Main concept                                    |
| ---------------- | ----------------------------------------------- |
| Library          | Collection of pre-written code                  |
| Import           | Loads a library                                 |
| Alias            | Short name for a library                        |
| Function         | Reusable block of code called to perform a task |
| Method           | Function associated with an object or class     |
| Argument         | Input passed to a function or method            |
| Return           | Result produced by a function or method         |
| Array            | NumPy data structure                            |
| Element-wise     | Operation on each element                       |
| Slicing          | Selecting a portion of an array                 |
| View             | Shares underlying data                          |
| Copy             | Independent data                                |
| DataFrame        | Two-dimensional table                           |
| Series           | One-dimensional labeled data                    |
| CSV              | Tabular file format                             |
| Missing Value    | Absent or unavailable data                      |
| Boolean Indexing | Selecting data using True/False conditions      |

One important distinction for your lab:

- `np.array()` → Function call.
- `ar.sum()` → Method call.
- `df.shape` → Attribute access.
- `ar + 5` → Arithmetic operation.
- `ar[2:4]` → Slicing operation.
- `df["Age"]` → Column selection.
- `df = ...` → Assignment.
