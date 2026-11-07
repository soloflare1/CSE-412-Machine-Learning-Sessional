# Logistic Regression – Short Conceptual Notes

## 1. What is Logistic Regression?

- Logistic Regression is a Supervised Learning algorithm.
- It is used for Classification, especially Binary Classification (0 or 1).
- It predicts the probability of an event occurring.

Example: Predict whether a person will buy insurance based on their age.

- `0` = Not bought insurance
- `1` = Bought insurance

## 2. Import Libraries and Load Dataset

```
import pandas as pdimport numpy as npimport matplotlib.pyplot as pltpath = "/content/drive/MyDrive/Colab Notebooks/ML/Logistic Regression/insurance_data.csv"df = pd.read_csv(path)df
```

- `pandas`: Load and manage dataset.
- `numpy`: Numerical operations.
- `matplotlib`: Data visualization.

## 3. Check Missing Values

```
df.isnull()df.isnull().sum()
```

- `isnull()` identifies missing values (`True` means missing).
- `sum()` counts missing values in each column.

## 4. Apply Logistic Regression

```
from sklearn.linear_model import LogisticRegressionlr = LogisticRegression()inp = df[['age']]o = df['bought_insurance']lr.fit(inp, o)
```

- `inp` = Input Feature (age).
- `o` = Target (bought_insurance).
- `fit()` trains the model using the input and actual output.

## 5. Get Model Parameters

```
lr.coef_lr.intercept_
```

- `coef_` = Weight (\\(w_1\\))
- `intercept_` = Bias (\\(w_0\\))

## 6. Model Prediction

```
lr.predict(df[['age']])
```

Predicts whether each person will buy insurance (`0` or `1`).

```
actual = np.array(df['bought_insurance'])print(actual, sep=" ")
```

Displays the actual output for comparison.

## 7. Sigmoid Function

Why does the Sigmoid Function give values between 0 and 1?

The Sigmoid Function converts any real-valued input into a probability between 0 and 1.

\\(P(Y=1\mid x)=\frac{1}{1+e^{-(\beta_0+\beta_1x)}}\\)

\\(z=\text{-0.5},\quad P(Y=1\mid x)=\text{38\\%}\\)

Below the 0.5 threshold: class 0

\\(x\\)

\\(\beta_1\\)

-4-2240.20.40.60.81Predictor x0.5 thresholdx₅₀ = 0.42P = 38%Class-1 probability · observed: 0 / 1

Give feedback

- Very large positive input → output approaches `1`.
- Very large negative input → output approaches `0`.
- Input `0` → output is `0.5`.

This makes it suitable for predicting probabilities in Binary Classification.

## 8. Manual Probability Calculation

Your final calculation has two issues:

- `w0` and `w1` are assigned in reverse.
- You need parentheses around the denominator.

Corrected code:

```
import mathw0 = lr.intercept_[0]w1 = lr.coef_[0][0]age = 50sig = 1 / (1 + math.exp(-(w0 + w1 * age)))if sig < 0.5:    print(0)else:    print(1)
```

Understanding the variables:

- `w0` = Intercept (Bias)
- `w1` = Coefficient (Weight)
- `age` = Input Feature
- `sig` = Predicted probability

Why use 0.5?

- Probability below `0.5` → Class `0`
- Probability equal to or above `0.5` → Class `1`

Remember: `lr.predict()` directly predicts the class, while the Sigmoid calculation gives the probability first.
