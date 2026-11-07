## 1. Python Libraries & Modules Used

| Library / Module | Import Statement                                      | What & Why?                                                |
| ---------------- | ----------------------------------------------------- | ---------------------------------------------------------- |
| NumPy            | `import numpy as np`                                  | Numerical calculations, arrays and mathematical operations |
| Pandas           | `import pandas as pd`                                 | Loading, handling and analyzing datasets                   |
| Matplotlib       | `import matplotlib.pyplot as plt`                     | Creating graphs and visualizing data                       |
| Scikit-learn     | `from sklearn.linear_model import LinearRegression`   | Building Linear Regression models                          |
| Scikit-learn     | `from sklearn.linear_model import LogisticRegression` | Building Logistic Regression models                        |
| Scikit-learn     | `from sklearn.preprocessing import StandardScaler`    | Feature Scaling / Standardization                          |
| Math             | `import math`                                         | Mathematical functions such as `exp()`                     |

### Important Functions

| Function               | Purpose                           |
| ---------------------- | --------------------------------- |
| `np.array()`           | Creates NumPy array               |
| `pd.read_csv()`        | Reads CSV file                    |
| `plt.plot()`           | Creates line graph                |
| `LinearRegression()`   | Creates Linear Regression model   |
| `LogisticRegression()` | Creates Logistic Regression model |
| `StandardScaler()`     | Creates feature scaler            |
| `math.exp()`           | Calculates exponential value      |

Remember:

- NumPy, Pandas and Matplotlib are Python libraries.
- Scikit-learn (`sklearn`) is a Machine Learning library.
- `math` is a built-in Python module.

## 2. NumPy Basics

What: NumPy works with numerical arrays.

How: It provides built-in functions and element-wise operations.

Why: To perform mathematical calculations easily.

| Code            | What it does                   |
| --------------- | ------------------------------ |
| `np.array()`    | Creates an array               |
| `ar.sum()`      | Calculates total               |
| `ar.min()`      | Finds minimum                  |
| `ar.max()`      | Finds maximum                  |
| `ar.mean()`     | Calculates average             |
| `ar.std()`      | Calculates standard deviation  |
| `ar + 5`        | Adds 5 to every element        |
| `np.pow(ar, 2)` | Squares every element          |
| `np.sqrt(ar)`   | Finds square root              |
| `ar[2]`         | Accesses an element (Indexing) |
| `ar[2:4]`       | Accesses a range (Slicing)     |

## 3. Pandas Basics

What: Pandas handles structured data in rows and columns.

How: Uses DataFrame and Series.

Why: To load, clean and analyze datasets.

| Code                   | What it does                         |
| ---------------------- | ------------------------------------ |
| `pd.read_csv()`        | Loads CSV dataset                    |
| `df.head()`            | Shows first 5 rows                   |
| `df.shape`             | Shows rows and columns               |
| `df.info()`            | Shows column information             |
| `df.describe()`        | Shows statistical summary            |
| `df.isnull()`          | Identifies missing values            |
| `df.isnull().sum()`    | Counts missing values                |
| `df['age']`            | Selects one column (Series)          |
| `df[['age', 'price']]` | Selects multiple columns (DataFrame) |
| `df.drop()`            | Removes rows or columns              |

## 4. Machine Learning Basics

What: Machine Learning allows computers to learn patterns from data and make predictions.

How: The model learns from examples during training.

Why: To predict outcomes from new, unseen data.

| Term         | What does it mean?                      |
| ------------ | --------------------------------------- |
| Dataset      | Collection of data                      |
| Feature (X)  | Input used for prediction               |
| Target (y)   | Actual output to predict                |
| Training     | Model learns from data                  |
| Testing      | Evaluates performance on unseen data    |
| Validation   | Helps tune and select a model           |
| Fit          | Learns the relationship between X and y |
| Overfitting  | Learns training data too closely        |
| Underfitting | Fails to learn important patterns       |

### Types of Supervised Learning

| Regression                | Classification              |
| ------------------------- | --------------------------- |
| Predicts numerical values | Predicts classes/categories |
| House price               | Insurance: 0 or 1           |
| Income                    | Spam: Yes or No             |

## 5. Linear Regression

What: A Supervised Learning algorithm used to predict continuous numerical values.

How: Finds a linear relationship between input Feature (X) and Target (y).

Why: To estimate numerical values, such as price or income.

\\[ y=b_0+b_1x \\]

| Term | Meaning              |
| ---- | -------------------- |
| `x`  | Input Feature        |
| `y`  | Predicted output     |
| `b1` | Coefficient / Weight |
| `b0` | Intercept / Bias     |

Code – What each line does

| Code                 | Purpose                   |
| -------------------- | ------------------------- |
| `LinearRegression()` | Creates the model         |
| `X = df[['year']]`   | Selects input Feature     |
| `y = df['pci']`      | Selects Target            |
| `reg.fit(X, y)`      | Trains the model          |
| `reg.coef_`          | Gets Weight               |
| `reg.intercept_`     | Gets Bias                 |
| `reg.predict()`      | Predicts numerical output |
| `reg.score()`        | Calculates R² score       |

## 6. Multiple Linear Regression

What: Linear Regression with multiple input Features.

How: Uses several Features together to predict one numerical Target.

Why: Real-world predictions often depend on multiple factors.

Example: House price depends on area, bedrooms and age.

\\[ \hat y=w_1x_1+w_2x_2+w_3x_3+b \\]

- `x1, x2, x3` = Input Features
- `w1, w2, w3` = Weights
- `b` = Bias

Main difference: Linear Regression uses one Feature in the simple example; Multiple Linear Regression uses multiple Features.

## 7. Gradient Descent

What: An optimization algorithm used to minimize model error.

How: Repeatedly updates Weight and Bias to reduce prediction error.

Why: To find better model parameters and improve predictions.

### Training Steps

1. Initialize Weight and Bias.
2. Calculate predicted output.
3. Calculate error (MSE).
4. Calculate gradients.
5. Update Weight and Bias.
6. Repeat until the iterations finish or the model converges.

### Important Terms

| Term              | Purpose                                   |
| ----------------- | ----------------------------------------- |
| MSE               | Measures average squared prediction error |
| Gradient          | Shows how parameters affect the error     |
| Learning Rate (α) | Controls the update size                  |
| Iterations        | Number of update steps                    |
| Weight            | Controls Feature contribution             |
| Bias              | Adjusts the prediction                    |

### Feature Scaling – StandardScaler

What: Converts Features to a similar scale.

How: Uses mean and standard deviation.

\\[ z=\frac{x-\mu}{\sigma} \\]

Why: Prevents large-scale Features from dominating Gradient Descent and helps it converge faster.

| Code               | Purpose                                        |
| ------------------ | ---------------------------------------------- |
| `StandardScaler()` | Creates scaler                                 |
| `fit_transform(X)` | Learns scaling values and scales training data |
| `transform(X)`     | Scales new data using the same values          |

## 8. Logistic Regression

What: A Supervised Learning algorithm used for Classification, especially Binary Classification.

How: Calculates a probability using the Sigmoid Function, then assigns a class using a threshold.

Why: To predict categories such as Yes/No or 0/1.

Example: Predict whether a person will buy insurance based on age.

- Feature (X) = Age
- Target (y) = Bought Insurance
- `0` = No
- `1` = Yes

### Sigmoid Function

What: Converts the model's raw output into a probability between 0 and 1.

Why: Classification needs a probability to decide the class.

\\[ P(Y=1|x)=\frac{1}{1+e^{-(w_0+w_1x)}} \\]

- `w0` = Intercept / Bias
- `w1` = Coefficient / Weight
- `x` = Input Feature
- `e` = Euler's number

\\(P(Y=1\mid x)=\frac{1}{1+e^{-(\beta_0+\beta_1x)}}\\)

\\(z=\text{-0.5},\quad P(Y=1\mid x)=\text{38\\%}\\)

Below the 0.5 threshold: class 0

\\(x\\)

\\(\beta_1\\)

-4-2240.20.40.60.81Predictor x0.5 thresholdx₅₀ = 0.42P = 38%Class-1 probability · observed: 0 / 1

Give feedback

### Classification Threshold

| Probability           | Predicted Class |
| --------------------- | --------------- |
| Below 0.5             | 0               |
| Equal to or above 0.5 | 1               |

### Important Code

| Code                   | Purpose                |
| ---------------------- | ---------------------- |
| `LogisticRegression()` | Creates the model      |
| `lr.fit(X, y)`         | Trains the model       |
| `lr.coef_`             | Gets Weight            |
| `lr.intercept_`        | Gets Bias              |
| `lr.predict(X)`        | Predicts class         |
| Sigmoid calculation    | Calculates probability |

## 9.  Quick Revision

| Topic                      | What does it do?                          | Why is it used?        |
| -------------------------- | ----------------------------------------- | ---------------------- |
| NumPy                      | Numerical calculations                    | Fast operations        |
| Pandas                     | Handles datasets                          | Data management        |
| Matplotlib                 | Creates graphs                            | Visualization          |
| Linear Regression          | Predicts numbers                          | Regression             |
| Multiple Linear Regression | Uses multiple Features to predict numbers | More input factors     |
| Gradient Descent           | Updates Weight and Bias                   | Minimizes error        |
| StandardScaler             | Scales Features                           | Better optimization    |
| Logistic Regression        | Predicts classes                          | Classification         |
| Sigmoid                    | Calculates probability                    | Converts output to 0–1 |
| MSE                        | Measures prediction error                 | Model optimization     |
| R² Score                   | Measures regression fit                   | Model evaluation       |

Most important concept to remember:

- Training: Model learns from Features (X) and Target (y).
- Prediction: Model uses learned patterns to predict output for new input.
- Regression: Predicts a number.
- Classification: Predicts a category.
