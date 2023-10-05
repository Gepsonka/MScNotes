
$$
x \rightarrow y
$$
$$
P: 2
$$
$$
Ax + B = y
$$
$$
A = \Theta_1
$$
$$
B = \Theta_{0} \space (Bias)
$$

## Loss function
$$
\frac{1}{2n} \sum_{i=1}^{n} (\bar{y_{i}}- y_i)^2
$$
```python
J = np.sum((np.dot(X, theta) - y) ** 2) / (2 * m)
```




## Hipotesis function

$$
h_0(x)
$$

For a given x gives an output, and measure the distance from the true x, if there is a better weight then we adjust -> Supervised learning

We want to get to the loss function's minimum -> Descent Gradiens

![[Figure_1.png]]

We have to adjust the weights to minimize the error. (Blue line end will raise, will become steeper)

$$\frac{1}{2n} \sum_{i=1}^{n} ( (\Theta_{0} * 1 + \Theta_{1} * 1 ) - y_i)^2$$

Need to find the partial derivative of the loss fn.

# Gradient Descent

```python
def gradientDescent(X, y, theta, alpha, num_iters):
# GRADIENTDESCENT Performs gradient descent to learn theta
# theta = GRADIENTDESCENT(X, y, theta, alpha, num_iters) updates theta by
# taking num_iters gradient steps with learning rate alpha

  
	# Initialize some useful values
	m = y.shape[0] # number of training examples
	J_history = np.zeros(num_iters)
	
	
	for iter in range(num_iters):
	# ====================== YOUR CODE HERE ======================
	# Instructions: Perform a single gradient step on the parameter vector
	# theta.
	#
	# Hint: While debugging, it can be useful to print out the values
	# of the cost function (computeCost) and gradient here.
	#
	# tmp = [0 0];
	# tmp(1) = theta(1) - alpha*(sum((X*theta-y)*X(:,1)')/m);
	# tmp(2) = theta(2) - alpha*(sum((X*theta-y)*X(:,2)')/m);
	# theta = tmp;
	
	hipotesis = np.dot(X, theta)
	theta[0] = theta[0] - alpha * (np.dot(hipotesis - y, X[:, 0]) / m)
	theta[1] = theta[1] - alpha * (np.dot(hipotesis - y, X[:, 1]) / m)
	
	  
	# ============================================================
	
	  
	# Save the cost J in every iteration
	J_history[iter] = computeCost(X, y, theta)
	
	  
	return theta
```

## Result

![[Figure_1 1.png]]


The algorithm was successful.

### Here is how the learning converges to optimal weights

![[fig.png]]
