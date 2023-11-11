
### Loss

$$\frac{1}{m}\sum_{i=1}^{m} -y_{i}*log(H_{\Theta}(x_i))-(1-y_i)*log(1-H_{\Theta}(x_i)) + \left(\frac{\lambda}{2m}\left(\sum \Theta_{1}^{2}\sum \Theta_{2}^{2}\right)\right)\leftarrow reguralization$$


## Back Propagation

$$\Delta^4 = o_{4}-y$$
$$\Delta^{3}= \Delta^{4} * \Theta^{3}*sigmoid'(in_3)$$
$$\Delta^{2}= \Delta^3*\Theta_2*sigmoid'(in_2)$$
nnCostFunction.py
```python
def nnCostFunction(nn_params, input_layer_size, hidden_layer_size, num_labels, X, y, Lambda):

"""

nnCostFunction Implements the neural network cost function for a two layer

neural network which performs classification

nnCostFunction computes the cost and gradient of the neural network. The

parameters for the neural network are "unrolled" into the vector

nn_params and need to be converted back into the weight matrices.

  

The returned parameter grad should be a "unrolled" vector of the

partial derivatives of the neural network.

"""

  

# Reshape nn_params back into the parameters Theta1 and Theta2, the weight matrices

# for our 2 layer neural network

	Theta1 = np.reshape(nn_params[:hidden_layer_size * (input_layer_size + 1)],
	(hidden_layer_size, input_layer_size + 1), order='F').copy()
	
	  
	Theta2 = np.reshape(nn_params[hidden_layer_size * (input_layer_size + 1):],
	(num_labels, (hidden_layer_size + 1)), order='F').copy()
	
	  
	
	# Setup some useful variables
	m = X.shape[0]
	Theta1_grad = np.zeros(Theta1.shape)
	Theta2_grad = np.zeros(Theta2.shape)

  

"""

====================== YOUR CODE HERE ======================

Instructions: You should complete the code by working through the

following parts.

Part 1: Feedforward the neural network and return the cost in the

variable J. After implementing Part 1, you can verify that your

cost function computation is correct by verifying the cost

computed in ex4.py

Part 2: Implement the backpropagation algorithm to compute the gradients

Theta1_grad and Theta2_grad. You should return the partial derivatives of

the cost function with respect to Theta1 and Theta2 in Theta1_grad and

Theta2_grad, respectively. After implementing Part 2, you can check

that your implementation is correct by running checkNNGradients

Note: The vector y passed into the function is a vector of labels

containing values from 1..K. You need to map this vector into a

binary vector of 1's and 0's to be used with the neural network

cost function.

Hint: We recommend implementing backpropagation using a for-loop

over the training examples if you are implementing it for the

first time.

Part 3: Implement regularization with the cost function and gradients.

Hint: You can implement this around the code for backpropagation.

That is, you can compute the gradients for the regularization

separately and then add them to Theta1_grad and Theta2_grad from Part 2.

"""

  

	X = np.c_[np.ones(m), X] # Add ones to the X data matrix
	in2 = np.dot(X, Theta1.T)
	o2 = np.c_[np.ones(m), sigmoid(in2)]
	in3 = np.dot(o2, Theta2.T)
	o3 = sigmoid(in3)
	
	for i in range(0,m):
	one_hot = np.zeros(num_labels)
	one_hot[y[i]-1] = 1
	J = J + np.sum(-one_hot*np.log(o3[i])-(1-one_hot)*np.log(1-o3[i]))
	J/=m
	# regularization memeber
	reg = Lambda/(2*m) * np.sum(Theta1[:,1:]**2) + np.sum(Theta2[:,1:]**2)
	J+=reg
	  
	
	# =========================================================================
	
	  
	
	# Unroll gradient
	
	grad = np.hstack((Theta1_grad.T.ravel(), Theta2_grad.T.ravel()))
	
	  
	
	return J, grad
	```

sigmoid.py

```python
g = 1/(1+exp(-z))

return g
```


