# Polynomial Regression

Polynomial regression is an extension of linear regression that allows you to model relationships between variables using higher-degree polynomial functions. While linear regression assumes a linear relationship between variables, polynomial regression is suitable for cases where the relationship is curvilinear or nonlinear.

## Key Concepts

- **Polynomial Degree:** The degree of a polynomial determines the curve's complexity. A linear regression model has a polynomial degree of 1, while quadratic regression has a degree of 2, cubic has a degree of 3, and so on.

- **Polynomial Equation:** In polynomial regression, the equation becomes `y = b0 + b1x + b2x^2 + ... + bnx^n`, where `x` is the independent variable, `b0`, `b1`, `b2`, ..., `bn` are the coefficients, and `n` is the degree of the polynomial.

- **Overfitting and Underfitting:** Choosing the right polynomial degree is crucial. Too high a degree can lead to overfitting, where the model fits the noise in the data rather than the underlying pattern. Too low a degree can result in underfitting, where the model fails to capture important relationships.

## Steps to Perform Polynomial Regression

**1. Data Collection and Preprocessing:** Collect and clean the data, as you would for linear regression.

**2. Feature Engineering:** Create additional features by raising the existing features to different powers.

**3. Visualization:** Plot the data and observe its nature to decide on the appropriate polynomial degree.

**4. Model Building:** Fit the polynomial regression model using the polynomial features.

**5. Model Evaluation:** Use appropriate evaluation metrics like R-squared, mean squared error, and visualization to assess the model's performance.

## Libraries for Polynomial Regression

- Scikit-Learn: Scikit-Learn's PolynomialFeatures can be used to create polynomial features, and the rest of the regression process remains similar to linear regression.

## Example Code (using Scikit-Learn)

```
import numpy as np
import matplotlib.pyplot as plt
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Simulated data
X = np.random.rand(100, 1) * 10
y = 0.5 * X**2 - 3 * X + 5 + np.random.randn(100, 1) * 2

# Create polynomial features
degree = 2
poly_features = PolynomialFeatures(degree=degree)
X_poly = poly_features.fit_transform(X)

# Initialize linear regression model
model = LinearRegression()

# Fit the model to the polynomial features
model.fit(X_poly, y)

# Predict on the same range of X values
X_pred = np.linspace(X.min(), X.max(), 100).reshape(-1, 1)
X_pred_poly = poly_features.transform(X_pred)
y_pred = model.predict(X_pred_poly)

# Calculate mean squared error
mse = mean_squared_error(y, model.predict(X_poly))
print(f"Mean Squared Error: {mse}")

# Plot the data and polynomial regression curve
plt.scatter(X, y, label="Data")
plt.plot(X_pred, y_pred, color='r', label=f'Degree {degree} Fit')
plt.xlabel("X")
plt.ylabel("y")
plt.title("Polynomial Regression")
plt.legend()
plt.show()
```

## Practical Applications

- **Physics:** Modeling physical phenomena where linear relationships are insufficient.

- **Finance:** Analyzing stock prices, interest rates, or market trends.

- **Biology and Medicine:** Investigating growth patterns, population dynamics, or disease spread.
