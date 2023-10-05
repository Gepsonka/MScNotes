Hand written numbers
![[Screenshot 2023-10-02 at 12.49.02 PM.png]]

`0/1 -> 0, 1, 2, 3, ... ,9`

$$
\Theta_{0}1 + \Theta_{1}x_{1}+ \Theta_{2}x_{2} +  ... + \Theta_{400}x_{400} = \mathbb{Z}
$$
$$
Sigmoid(\mathbb{Z}) = \frac{1}{1+e^{-\mathbb{z}}}
$$
`0-255 -> pixel intensity`

### Loss function

$$
\mathbb{J} = \frac{1}{m} \sum_{i=1}^{m (=500)} -y*log(H_{\Theta}(x_i)) - (1 -y_i) * log(1-H_{\Theta}x_{i})
$$



$$
\lambda\frac{1}{2m} \sum_{j=1}^{n} \Theta^{2}
$$
`-> regulazitaion` (theta_0 is not in it)


$$
\frac{\mathbb{J}}{\partial \Theta_{i}}= \frac{1}{m} \left(\sum_{i=1}^{m} (H_{\Theta}(x) - y)\right) + \frac{\lambda}{m} * \sum_{j=1}^{n} \Theta_{j}
$$



```python
def lr_cost_function(theta, x, y, lam, alpha=1):

"""
Logistic Regression Cost Function.
  

Compute cost and gradient for logistic regression with regularization
  

m = size(y)
cost = 1/m * (sum(-y * log(h_x) - (1-y) * log(1-h_x))) + lambda * sum(theta^2))
  

k = size(theta)
regularized_gradient = [grad1, grad2, ... grad_k]

:param theta: theta parameters of the model
:param x: training set
:param y: training set labels
:param lam: lambda for regularization
:param alpha: alpha parameter for gradient
  

:return: (cost, gradient) for the given parameters of the model
"""

  

	m = np.size(y)

  

	hyp = sigmoid(np.dot(x, theta))
	J = np.dot(-1 * y, np.log(hyp)) - np.dot((1 - y), np.log(1 - hyp)) * (1 / m)
	reg = lam * np.sum(np.power(theta[1:], 2)) * (1 / 2*m)
	J = J + reg
	
	  
	
	grad = np.dot((hyp - y), x) / m
	grad[1:] = grad[1:] + (lam / m) * theta[1:]
	
	return J, grad
```


# One vs All
```python
import numpy as np

import scipy.optimize as optimize

  

from .lr_cost_function import lr_cost_function

  
  

def one_vs_all(X, y, num_labels, lam):

"""

One vs. All trains multiple logistic regression classifiers.

  

Returns all the classifiers in a matrix all_theta, where the i-th row of all_theta corresponds to the classifier

for label i.

  

:param X: the training set

:param y: the training set labels

:param num_labels: number of possible classes

:param lam: lambda for regularization

  

:return: all the classifiers in a matrix all_theta, where the i-th row of all_theta corresponds to the classifier

for label i

"""
m = np.size(X, 0) # 5000
n = np.size(X, 1) # 400

all_theta = np.zeros((num_labels, n + 1)) # 10 x 401

for i in range(0, 10):
	y_i = np.zeros(m) # 5000 x 1
	y_i[y == i + 1] = 1
	
	all_theta[i,:] = optimize.fmin_cg(f=cost, fprime=grad, x0=all_theta[i,:], args=(X, y_i), maxiter=50)
	
	return all_theta

  
  

def cost(theta, *args):

"""

Logistic Regression Cost function, used for fmin_cg during the one_vs_all training.

  

:param theta: theta parameters of the model

:param args: (x, y, lam) the training set, labels and lambda for regularization

:return: cost with given parameters

"""

	x, y, lam = args
	(J, g) = lr_cost_function(theta, x, y, lam)
	return J

  
  

def grad(theta, *args):

"""

Gradients based on the Logistic Regression Cost function, used for fmin_cg during the one_vs_all training.

  

:param theta: theta parameters of the model

:param args: (x, y, lam) the training set, labels and lambda for regularization

:return: cost with given parameters

"""

	x, y, lam = args
	(J, g) = lr_cost_function(theta, x, y, lam)
	
	return g
```