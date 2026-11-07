
# Linear Regression Using Python 

This code demonstrates Linear Regression using the Canada Per Capita Income dataset. We use `pandas` for data handling, `matplotlib` for visualization, and `scikit-learn` to train the Linear Regression model.


## 1. Import Libraries

```
import pandas as pdimport numpy as npimport matplotlib.pyplot as pltfrom sklearn.linear_model import LinearRegression
```

| Library             | Purpose                           |
| ------------------- | --------------------------------- |
| `pandas`            | Read and manipulate datasets      |
| `numpy`             | Numerical calculations            |
| `matplotlib.pyplot` | Create graphs and plots           |
| `LinearRegression`  | Apply Linear Regression algorithm |

## 2. Load Dataset

```
path = "/content/drive/MyDrive/canada_per_capita_income.csv"df = pd.read_csv(path)df.head(3)
```

- `path` → Location of the CSV file.
- `pd.read_csv(path)` → Loads the CSV file into a DataFrame.
- `df` → Stores the dataset.
- `df.head(3)` → Displays the first 3 rows.

Example dataset:

| year | per capita income (US$) |
| ---- | ----------------------- |
| 1970 | 3399                    |
| 1971 | 3768                    |
| 1972 | 4251                    |

## 3. Rename Column

```
df = pd.read_csv(path)df.rename(    columns={'per capita income (US$)': 'pci'},    inplace=True)
```

- `df.rename()` → Changes column names.
- `columns={}` → Specifies which column name to change.
- `inplace=True` → Modifies the original DataFrame directly.
- `inplace=False` → Keeps the original DataFrame unchanged and returns a modified DataFrame.

Now we can access the income column using `df['pci']`.

## 4. Scatter Plot

```
plt.xlabel('Year')plt.ylabel('PCI')plt.scatter(df['year'], df['pci'], color='pink')plt.show()
```

Purpose: Visualize the relationship between Year and Per Capita Income.

- `plt.xlabel()` → Sets the X-axis label.
- `plt.ylabel()` → Sets the Y-axis label.
- `plt.scatter()` → Creates a scatter plot.
- `color='pink'` → Sets the point color.
- `plt.show()` → Displays the graph.

[8  Visualizing data](https://images.openai.com/static-rsc-4/MfWbHh-0k1LFlam86iefbE3xBdIgBmM3YvkzoV5ArcX1VaGnZq1H37WyCq3Huy5xvH8tXJ19FMBTpXhxdgfMt6bCtpL_h4lePx57xRaEv5m1lUa5_6oVGWWzzkR7pbwK_enDBM-w7nU-psz1HdTLFQ_XVh8m0lpUmBZDkGW5DHo?purpose=inline)

[pfaffelh.github.io](https://pfaffelh.github.io/python_for_data/08_visualizing_data.html?utm_source=chatgpt.com)

Observation: As the year increases, per capita income generally increases. This suggests a positive linear relationship.

## 5. Apply Linear Regression

```
reg = LinearRegression()year = df[['year']]pci = df[['pci']]reg.fit(year, pci)
```

Step 1: Create the model

```
reg = LinearRegression()
```

Creates a Linear Regression model.

Step 2: Separate input and output

```
year = df[['year']]pci = df[['pci']]
```

| Variable | Meaning           | Role       |
| -------- | ----------------- | ---------- |
| `year`   | Year              | Input (X)  |
| `pci`    | Per capita income | Output (Y) |

Here:

- Independent Variable (X) = Year
- Dependent Variable (Y) = PCI

Step 3: Train the model

```
reg.fit(year, pci)
```

- `fit(input, output)` → Trains the model using input and output data.
- The model learns the relationship between Year and PCI.

\\(\hat{y} = b_0 + b_1x\\)

\\(\hat{y} = \text{8.49} - \text{0.54}x\\)

Estimated intercept · R-squared = 0.72

Fit

InterceptThrough origin

Focus

DataLinePredictionsResiduals

Generate new data

Drag a point to refit the line.

2468102468PredictorResponse

Give feedback

The model learns the best-fit straight line:

\\[ \hat{y} = b_0 + b_1x \\]

Where:

- \\(b_0\\) = Intercept
- \\(b_1\\) = Slope
- \\(x\\) = Year
- \\(\hat y\\) = Predicted PCI

## 6. Find Slope and Intercept

Slope (m):

```
reg.coef_
```

Returns the slope of the regression line.

Intercept (c):

```
reg.intercept_
```

Returns the intercept of the regression line.

The equation becomes:

\\[ y = mx + c \\]

- Slope tells us how much PCI changes when the year increases by one.
- Intercept represents the predicted PCI when Year = 0.

## 7. Prediction

```
reg.predict([[2026]])
```

Purpose: Predict Canada's per capita income for the year 2026.

- `predict()` → Predicts output using the trained model.
- `[[2026]]` → Input year.

The model uses the learned slope and intercept to estimate the income.

## 8. Find R-squared Score

```
rsq = reg.score(year, pci)rsq
```

Purpose: Evaluate how well the Linear Regression model fits the given data.

- `reg.score()` → Returns the coefficient of determination (R²).
- `rsq` → Stores the R² score.

| R² Score   | Interpretation                                      |
| ---------- | --------------------------------------------------- |
| Close to 1 | Good fit                                            |
| Close to 0 | Weak explanatory power                              |
| Negative   | Worse than predicting the mean (on evaluation data) |

## 9. Plot Best Fit Line

```
x_plot = year.sort_values('year')y_plot = reg.predict(x_plot).ravel()plt.figure(figsize=(9, 5))plt.scatter(    df['year'], df['pci'],    color='pink',    label='Actual income')plt.plot(    x_plot['year'], y_plot,    color='blue',    label='Best Fit Line')plt.xlabel('Year')plt.ylabel('per capita income (US$)')plt.show()
```

Let's understand the new functions:

| Code                        | Purpose                                |
| --------------------------- | -------------------------------------- |
| `sort_values('year')`       | Sorts data by year                     |
| `reg.predict(x_plot)`       | Predicts income for each year          |
| `.ravel()`                  | Converts a 2D prediction array into 1D |
| `plt.figure(figsize=(9,5))` | Sets figure size                       |
| `plt.scatter()`             | Displays actual data points            |
| `plt.plot()`                | Draws the best-fit line                |
| `label`                     | Sets the legend name                   |

[Unlocking the Secrets of Regression: A Comprehensive Guide](https://images.openai.com/static-rsc-4/-l3e0GJysf4hjRthl_04zuZymJ29Wy6SwapBgdX38D5U6Zjs68o7fjIG-tymoipGT831lCwRRh-9_BvjWNFoHtiEHd2ywLXttSUvk7cH8rrvKuVpZqtvUK0S-TmBDQZj_-tb8XUxQQWa4xgGeTM_Go_Wj1WYmYKY36dtMrbsrbI?purpose=inline)

[numberanalytics.com](https://www.numberanalytics.com/blog/unlocking-the-secrets-of-regression-a-comprehensive-guide?utm_source=chatgpt.com)

Graph interpretation:

- Pink dots = Actual income values.
- Blue line = Predicted income values.
- The blue line represents the model's best-fit line.

## Important Lab Viva Questions

| Question                   | Short Answer                                                 |
| -------------------------- | ------------------------------------------------------------ |
| What is Linear Regression? | A supervised ML algorithm used to predict continuous values. |
| What is `fit()`?           | Trains the model.                                            |
| What is `predict()`?       | Predicts output for new input.                               |
| What is `coef_`?           | Returns the slope.                                           |
| What is `intercept_`?      | Returns the intercept.                                       |
| What is `score()`?         | Returns R² for Linear Regression.                            |
| What is `scatter()`?       | Creates a scatter plot.                                      |
| What is `plot()`?          | Draws a line or curve.                                       |
| What is `ravel()`?         | Converts an array into a 1D array.                           |
| What is `df.head(3)`?      | Displays the first 3 rows.                                   |

Remember the complete workflow:

Load Dataset (`read_csv`)

Preprocess Data (`rename`)

Visualize Data (`scatter`)

Train Model (`fit`)

Prediction (`predict`)

Evaluate & Visualize (`score`, `plot`)

One important note: This model is trained and evaluated on the same dataset in this code. For a proper ML evaluation, we generally split the data into training and testing sets.r 
