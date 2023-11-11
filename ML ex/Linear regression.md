
### Model to fit to

$$Y = mX + c$$
### Loss function

Has to be minimised (Mean Squared Error)
$$E = \frac{1}{n} \sum_{i=0}^{n} (y_{i}-\overline{y}_i)^2$$

where $\overline{y}_i$ is the predicted value and $y_i$ is the actual value:
$$E = \frac{1}{n} \sum_{i=0}^{n}{(y_{i}-(mx_{i}+c))^2}$$
# Gradient Descent

Iterative optimization algorithm

1. Initially let $m$ and $c$ be $0$.
2. Calculate the `partial derivatives` of the loss function in respect to $m$ and $c$.

Partial derivative respect to $m$.
$$D_{m}= \frac{1}{n}\sum_{i=0}^{n}2(y_{i}-(mx_{i}+c)(-x_i))$$
$$\downarrow$$
$$D_{m}= \frac{-2}{n}\sum_{i=0}^{n}x_i(y_{i}-(mx_{i}+c))$$
Partial derivative respect to $c$.
$$D_{c}= \frac{-2}{n} \sum_{i=0}^{n}(y_{i}-(mx_{i}+c))$$
3. Update $m$ and $c$ at each iteration with $L$ learning rate.
$$m = m-L * D_m$$

$$c = c - L * D_c$$

4. After fitting return the $c$ and $m$ thetas -> $\Theta = [m, c]$
5. Checking the Loss with the resulted thetas.

Example code: 
```python
import numpy as np

X = [1,4,6,32, 43, 123] # independent values
Y = [2, 5,67, 89, 147, 274] # dependent values

n = len(X) # number of sample data

alpha = 1000 # num of iterations
LR = 0.01 # learning rate

# init theta values (fitting to model Y = mX + c)
m = 0
c = 0


# Gradient Descent

for i in range(alpha):
	Y_pred = m * X + c # predicted values of Y for each X values (hypothesis)

	# parial derivative in respect to m
	dm = (-2/n) * np.sum(X * (Y - Y_pred))
	dc = (-2/n) * np.sum(Y - Y_pred)

	m = m - LR * dm
	c = c - LR * dc

# Calculating the loss (Mean Squared Error)
mse = (1/n) * np.sum(Y - (m * X + c))**2


```