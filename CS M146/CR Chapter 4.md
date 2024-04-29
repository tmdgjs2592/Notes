# Linear Regression, Non-linear Regression and Regularization

The label is a real number instead of it being discrete.
Linear Regression differs from classification, which considers categorical labels.

**Absolute difference**: measures how far off the prediction is from the label.
$$e_{abs} = |predicted \text{ }value - true \text{ } value| $$
**Squared difference**: takes the square of the difference
$$e_{sqr} = (predicted \ value - true \ value)^2 $$
$\theta$ is just $w$ with the bias term added in the start of the vector.
$\overset{\sim}{x}$ is $x$ with 1 added to the beginning.

**Cost function:: Residual Sum of Squares (RSS)**
$$RSS = \sum ^{N}_{i=1}(y_n - f(x_n))^2$$
This cost function allows us to determine levels of correctness, which differs from 0-1 loss function.

# Closed form solution

1. Determine if the cost function is convex by checking if the hessian function is positive semi-definite.
$$\nabla^2_{\theta}J(\theta) \geq 0 \rightarrow \text{P.S.D} \rightarrow \text{$J(\theta)$ is convex.}$$
2. If the cost function is convex, set the first derivative with respect to $\theta$ equal to zero. Solve for $\theta$ to find the closed form solution.

*Computing this way is not efficient for a large data set as the computing complexity is as large as $O(D^3)$.*

# Gradient Descent

More efficient than closed-form solution when D or N is large.
Gradient descent converges to the same solution as using matrix inversion because $J(\theta)$ is a convex function in $\theta$.

$\eta$ $\rightarrow$ step size, the parameter that controls how much the function can change at each iteration. 

Update rule:
$$
\begin{align}
J(\theta^{(t)}) &= \sum_n(x_n^T\theta^{(t)}-y_n)x_n \\
\theta ^{t+1} &= \theta ^{(t)} - \eta \nabla J(\theta^{(t)}) 

\end{align}
$$
Computational Complexity: $O(ND)$

# Stochastic Gradient Descent

Stochastic gradient descent approximates the gradient by calculating the gradient at a random data point in each iteration. ($\rightarrow$ better computational complexity)

**Algorithm**
Randomly choose a training sample
Compute $g_t = (x^T_{i(t)} \theta^{(t)}-y_{i(t)})x_{i(t)}$ and $\theta^{(t+1)} = \theta^{(t)}-\eta g_t$ 
until Stop criteria

*SGD only calculates the gradient for one sample $\rightarrow$ $O(D)$*
*Possible to step in wrong direction

# Maximum Likelihood Estimation for Probabilistic Generative Model

**Maximum Likelihood Estimation (Bernoulli)**
$$\overset{\sim}{\theta} = \frac {\sum^N_{i=n }x_n}{N}$$
**Maximum Likelihood Estimation (Gaussian)**


