**Logistic Regression (cont)**

Gradient descent:
$\nabla J(\theta) = \sum _n \{h_\theta(x_n)-y_n\}x_n$

Hessian:
$H = \sum [h_\theta(x_n) \cdot (1-h_\theta(x_n))]x_nx_n^T$      ($[h_\theta(x_n) \cdot (1-h_\theta(x_n))]$ is a scalar, say $\alpha$)
$\forall z$, $z^t[\sum_n \alpha_n x_n x_n^T]z = \sum \alpha_n |z^Tx|^2 \geq 0$. $\rightarrow$ $J(\theta)$ is convex.

Update:
$$\theta^{(t+1)} = \theta^{(t)} - \eta \sum_n \{\sigma({\theta^{(t)}}^T x_n)-y_n\}x_n \text{ , ($\{\sigma({\theta^{(t)}}^T x_n)-y_n\}x_n$ is $\nabla J(\theta)$)}$$
# Linear Regression
Key difference:
* We can measure closenesss of prediction and labels.
* Choose a prediction which is real valued and measure its distance to the true label
- Find a line that has the minimum error (distance) from the data points.

**Loss function**
$$J(\theta) = \sum ^N _{n=1} |\hat{y_i}-y_i|^2$$
**Prediction**
$${y_i} = \theta^Tx_i$$
Goal: to find the theta that minimzes $J(\theta)$

**Gradient Descent**
**Gradient**
$$\nabla J(\theta) = \sum_n 2(\theta^Tx_n-y_n)x_n$$
**Hessian**
$$\nabla^2J(\theta) = 2 \sum_n x_n\cdot x_n^T$$
$\rightarrow$ $z^THz = 2 \cdot \sum_n |z^Tx_n|^2 \geq 0$ $\forall z$ $\rightarrow$ $J(\theta)$ is convex.

**Update rule**
$$\theta^{(t+1)} = \theta^{(t)} - \eta \sum_n (h_\theta (x_n)-y_n)x_n$$
**Analytical solution**
We want to solve for $\theta$ from $J(\theta) = 0$
$$ \begin{align}
\theta &= (\sum_n x_n x_n^T)^{-1} \sum_n y_nx_n \text{ (If $\sum_n x_n x_n^T$ is invertible)} \\
\theta &= (X^TX)^{-1}X^Ty
\end{align}$$
Complexity of matrix inverse: $O(m^3)$ 
Implication: If $D$ is large, cost is very expensive.
Complexity of gradient descent: $O(ND) \cdot$(# of iterations) (Still expensive)

**Stochastic gradient descent**
Instead of computing the whole matrix, pick only one point.
$g_t = (x^T_{i(t)}\theta^{(t)}-y_{i(t)})x_{i(t)}$ $\rightarrow$ $\theta^{(t+1)} = \theta^{(t)}- \eta g_t$
Complexity: $O(D)$ $\cdot$(# of iteration)
This may solve non-convex functions.