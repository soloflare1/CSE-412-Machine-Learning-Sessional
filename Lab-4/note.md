# Multiple Linear Regression with Gradient Descent

This code implements Multiple Linear Regression in two ways:

1. Using Scikit-learn (`LinearRegression`)
2. Using a manually implemented Gradient Descent algorithm

The dataset is `homeprices.csv`, which contains house information such as area, bedrooms, age, and price.


## 1. Import Libraries

```
import pandas as pdimport numpy as npimport matplotlib.pyplot as pltfrom sklearn.linear_model import LinearRegression
```

| Library            | Purpose                              |
| ------------------ | ------------------------------------ |
| `pandas`           | Load and manipulate datasets         |
| `numpy`            | Mathematical calculations and arrays |
| `matplotlib`       | Data visualization                   |
| `LinearRegression` | Build a Linear Regression model      |

## 2. Load Dataset

```
path = "/content/drive/MyDrive/Copy of homeprices.csv"df = pd.read_csv(path)df.head(5)
```

- `pd.read_csv(path)` reads the CSV file.
- `df` stores the dataset as a DataFrame.
- `df.head(5)` displays the first five rows.

Example dataset structure:

| area | bedrooms | age | price  |
| ---- | -------- | --- | ------ |
| 2600 | 3        | 20  | 550000 |
| 3000 | 4        | 15  | 565000 |
| 3200 | 3        | 18  | 610000 |
| 3600 | 4        | 30  | 595000 |
| 4000 | 5        | 8   | 760000 |

Here:

- Features (X): area, bedrooms, age
- Target (y): price

The model uses the features to predict the house price.

## 3. Data Preprocessing – Handling Missing Values

First, calculate the median of the `bedrooms` column.

```
df.bedrooms.median()
```

What is Median?

Median is the middle value of a dataset after sorting it.

For example:

`2, 3, 4, 5, 6`

Median = 4.

Now fill the missing values:

```
df.bedrooms = df.bedrooms.fillna(df.bedrooms.median())df
```

Explanation:

- `df.bedrooms` selects the bedrooms column.
- `.fillna()` replaces missing values (`NaN`).
- `df.bedrooms.median()` calculates the median.
- The result is assigned back to the original column.

Why use median?

Machine Learning models generally cannot work properly with missing values. Median is one way to handle missing numerical data and is less affected by extreme values than the mean.

## 4. Multiple Linear Regression Using Scikit-learn

```
reg = LinearRegression()reg.fit(    df.drop('price', axis='columns'),    df.price)
```

### What is Multiple Linear Regression?

Multiple Linear Regression predicts one dependent variable using two or more independent variables.

General equation:

\\[ y = w_1x_1+w_2x_2+w_3x_3+b \\]

For this dataset:

\\[ Price = w_1(Area)+w_2(Bedrooms)+w_3(Age)+b \\]

Where:

- \\(x_1,x_2,x_3\\) = input features
- \\(w_1,w_2,w_3\\) = weights or coefficients
- \\(b\\) = bias or intercept
- \\(y\\) = predicted price

### Understanding `fit()`

```
df.drop('price', axis='columns')
```

Removes the `price` column and keeps the input features.

`axis='columns'` means we want to drop a column.

```
df.price
```

Selects the target column.

```
reg.fit(X, y)
```

Trains the model using the input features and target values.

### Coefficients (Weights)

```
reg.coef_
```

Returns the weights of the input features.

For example:

```
[weight_area, weight_bedrooms, weight_age]
```

Each coefficient indicates how the predicted price changes when its corresponding feature increases by one unit, keeping other features constant.

### Intercept (Bias)

```
reg.intercept_
```

Returns \\(w_0\\) or the bias.

It represents the predicted price when all input features are zero.

### Prediction

```
reg.predict([[3000, 4, 15]])
```

Predicts the price of a house with:

- Area = 3000
- Bedrooms = 4
- Age = 15

The model uses the learned weights and bias to calculate the predicted price.

## 5. Gradient Descent

Important concept

What is Gradient Descent?

Gradient Descent is an optimization algorithm used to find the best weights and bias by minimizing the prediction error (cost).

In simple words:

The model initially makes predictions with some weights. It calculates the error and gradually updates the weights to reduce that error.

### Step 1: Define the function

```
def gradient_descent(X, y, learning_rate=0.05, iterations=20000):
```

| Parameter       | Meaning                          |
| --------------- | -------------------------------- |
| `X`             | Input features                   |
| `y`             | Actual target values             |
| `learning_rate` | Controls how much weights change |
| `iterations`    | Number of update steps           |

### Step 2: Extract rows and columns

```
m, n = X.shape
```

- `m` = Number of rows (samples).
- `n` = Number of columns (features).

For example, if the dataset contains 10 houses and 3 features:

```
m = 10
n = 3
```

### Step 3: Initialize weights and bias

```
weights = np.zeros(n)bias = 0
```

Initially, all weights and bias are zero.

For three features:

```
weights = [0, 0, 0]
bias = 0
```

### Step 4: Store cost history

```
cost_history = []
```

Stores the cost value after each iteration.

```
best_cost = float('inf')best_weights = weights.copy()best_bias = bias
```

- `float('inf')` means infinity.
- `best_cost` stores the lowest cost found so far.
- `best_weights` and `best_bias` store the parameters associated with that cost.

### Step 5: Make predictions

```
y_pred = X @ weights + bias
```

Here, `@` means matrix multiplication.

Mathematically:

\\[ \hat{y}=XW+b \\]

Where:

- \\(X\\) = Input feature matrix
- \\(W\\) = Weight vector
- \\(b\\) = Bias
- \\(\hat{y}\\) = Predicted output

### Step 6: Calculate Cost

```
cost = np.mean((y_pred - y) ** 2)cost_history.append(cost)
```

This calculates Mean Squared Error (MSE).

\\[ MSE=\frac{1}{m}\sum\_{i=1}^{m}(\hat{y}\_i-y_i)^2 \\]

- `y_pred - y` = Prediction error.
- `** 2` = Square of the error.
- `np.mean()` = Calculates the average.

Goal: Minimize the cost.

### Step 7: Track the best parameters

```
if cost < best_cost:    best_cost = cost    best_weights = weights.copy()    best_bias = bias
```

If the current cost is lower than the previous best cost, save the current weights and bias.

### Step 8: Calculate Gradients

```
dw = (2/m) * (X.T @ (y_pred - y))db = (2/m) * np.sum(y_pred - y)
```

These calculate the gradients of the cost function.

| Variable | Meaning                          |
| -------- | -------------------------------- |
| `dw`     | Gradient with respect to weights |
| `db`     | Gradient with respect to bias    |
| `X.T`    | Transpose of the feature matrix  |

Gradients indicate the direction in which weights and bias should change to reduce the cost.

### Step 9: Update weights and bias

```
weights = weights - learning_rate * dwbias = bias - learning_rate * db
```

This is the main Gradient Descent update rule.

\\[ W\_{new}=W\_{old}-\alpha dw \\]

\\[ b\_{new}=b\_{old}-\alpha db \\]

Where \\(\alpha\\) represents the learning rate.

### Step 10: Return results

```
return best_weights, best_bias, cost_history
```

Returns:

- Best weights
- Best bias
- Cost history

## 6. Feature Scaling Using StandardScaler

Why do we need Feature Scaling?

Our input features have different ranges.

For example:

- Area = 3000
- Bedrooms = 4
- Age = 15

Area has a much larger numerical range than the other features.

This difference can make Gradient Descent converge slowly or behave poorly.

Feature Scaling brings features to a comparable scale.

### Code

```
from sklearn.preprocessing import StandardScalerX = df.drop('price', axis='columns').valuesy = df['price'].valuesscaler = StandardScaler()X_scaled = scaler.fit_transform(X)print(X_scaled)
```

Explanation:

1. `X` contains all input features.
2. `y` contains the target price.
3. `StandardScaler()` creates a scaling object.
4. `fit_transform(X)` calculates the mean and standard deviation of each feature and transforms the data.

Standardization formula:

\\[ z=\frac{x-\mu}{\sigma} \\]

Where:

- \\(x\\) = Original value
- \\(\mu\\) = Mean
- \\(\sigma\\) = Standard deviation
- \\(z\\) = Scaled value

After scaling, each feature has approximately zero mean and unit standard deviation.

## 7. Train the Gradient Descent Model

```
weights, bias, cost_history = gradient_descent(    X_scaled,    y=y,    learning_rate=0.05,    iterations=6000)
```

This calls our manually created Gradient Descent function.

| Argument      | Value      |
| ------------- | ---------- |
| Input         | `X_scaled` |
| Target        | `y`        |
| Learning rate | 0.05       |
| Iterations    | 6000       |

Now:

```
print(weights)print(bias)print(cost_history)
```

Displays the learned weights, bias, and cost values.

## 8. Predict House Price Using Gradient Descent

```
house = np.array([[3000, 4, 15]])
```

Creates a new house with three input features.

But remember: the Gradient Descent model was trained using scaled features.

Therefore, we must scale the new house too.

```
house_scaled = scaler.transform(house)
```

Important difference:

- `fit_transform()` learns scaling parameters and transforms the training data.
- `transform()` uses the previously learned scaling parameters to transform new data.

Now make the prediction:

```
prediction_gd = house_scaled @ weights + bias
```

Uses the Gradient Descent equation:

\\[ \hat{y}=XW+b \\]

## 9. Prediction Using Scikit-learn

```
prediction_sklearn = reg.predict(    pd.DataFrame(        [[3000, 4, 15]],        columns=df.drop(columns='price').columns    ))
```

This predicts the same house price using the Scikit-learn model.

Here, `pd.DataFrame()` creates a DataFrame with the same feature column names and order used during training.

## 10. Compare Both Predictions

```
print("Sklearn Prediction:", prediction_sklearn[0])print("Gradient Descent Prediction:", prediction_gd[0])
```

Displays the predictions from both approaches.

Expected concept:

Both predictions should be approximately equal if Gradient Descent has converged properly.

Small differences can occur due to optimization settings and numerical precision.

## 11. Complete Workflow

Load Dataset

Read homeprices.csv

Data Preprocessing

Fill missing bedrooms values using median

Train Linear Regression

Scikit-learn model

Feature Scaling

StandardScaler

Gradient Descent

Calculate cost, gradients and update parameters

Predict House Price

Using both models

Compare Predictions

Scikit-learn vs Gradient Descent

## 12. Important Lab Viva Questions

Test your understanding

1\. What is Multiple Linear Regression?

2\. What is the target variable in this dataset?

3\. Why do we use median to fill missing values?

4\. What is Gradient Descent?

5\. What is the cost function used here?

6\. What is the learning rate?

7\. What happens if the learning rate is too high?

8\. What is StandardScaler?

9\. Why do we use transform() for a new house?

10\. What is the difference between Scikit-learn and manual Gradient Descent here?

Reveal all answers

One important note: This code uses the same dataset for training and prediction comparison. That is fine for understanding the algorithms, but it does not measure how well the model performs on unseen houses. For a proper evaluation, use a train-test split. Also, `cost_history` can be plotted to observe whether the Gradient Descent cost decreases over iterations.
