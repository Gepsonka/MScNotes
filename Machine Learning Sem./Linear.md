
Linear -> 
Linearis fuggveny : Ax + B = y

2 sulyt keressuk liearis regresszional: A, B

Legkisebb negyzetek modszere -> hiba minimalizalasa


$$
\frac{\partial}{\partial \Theta_j}J(\Theta_{0}, \Theta_{1})=\frac{\partial}{\partial \Theta_j}\frac{1}{2m} \sum_{i=1}^{m}(h_0(x^{(i)})-y^{(i)})^2 =
$$
$$
\frac{\partial}{\partial \Theta_{j}} \frac{1}{2m} \sum_{i=1}^{m} (\Theta_{0}+\Theta_{1}, x^{(i)}-y^{(i)})^2
$$


## "Batch" Gradient Descent

Each step of GD uses all the training examples

$$
\sum_{i=1}^{m}(h_0(x^{(i)})-y^{(i)})
$$

## Fetaure Scaling

Idea: Make sure features are on a similar scale

$$
-1 \le x_{i}\le 1
$$
### Mean normalization

$$
x_{1} \leftarrow \frac{x_{1} - \gamma_1}{S_1}
$$

## Making sure GD is working correctly

Plotting the error function


## Multiple Variables
