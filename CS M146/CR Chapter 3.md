****
# Logistic Regression

**Goal** $\rightarrow$ predict the class y to which a given input $x \in \mathbb R^D$ and $y_i \in \{0,1\}$ for every $i \in [N]$.

We proceed with estimating the probability of $y=1$ using 
$$h_{w,b}(x) = P(y=1|x;b,w)$$
When $h_{w,b}(x) \geq 0.5$, we assign $y=1$.
When $h_{w,b}(x) < 0.5$, we assign $y=0$.
It can be mathematically expressed as 
$$y=I(h_{w,b}(x) \geq 0.5) \text{ (I is the indicator function)}$$
In the case of logistic regression, we use
$$
\begin{align}
h_{w,b}(x) &= \sigma (w^Tx +b) \\
\sigma(\cdot) &= \frac {1}{1+exp(-a)}
\end{align}
$$
*The decision boundary is $w^Tx +b = 0$ 

Loss function for logistic regression
$$J(w) = - \sum^{N}_{i=1}(y_i\log h_{w}(x_i) + (1-y_i)\log [1-h_w(x_i)])$$
*Optimal $w$ minimizes this loss function*
****
# Gradient Descent

A first-order iterative optimization algorithm that aims to minimize a given loss function through repeated attempts to descent to a lower point given the current point.

Process:
Determine descent direction at $x^{(t)}$ for the $t$-th iteration
Choose a step size $\eta$
Update the value of $x^{t+1}$ with a function of $x^{(t)}$ and $\eta$
Until **convergence**

Update rule:
$$x^{(t+1)} := x^{(t)}-\eta \nabla f(x^{(t)})$$
*$\eta$ (learning rate) has to be chosen appropriately since a very large $\eta$ does not guarantee the convergence*
*****
# Convex Functions

A function $f: X\subset \mathbb R^n \rightarrow R$ is convex if for every $x,y \in X$ and $\lambda \in [0,1]$, $\lambda x + (1-\lambda)y \in X$ and 
$$f(\lambda x+(1-\lambda)y \leq \lambda f(x) + (1-\lambda) f(y)$$
$f$ is convex if this inequality holds whenever $x \neq y$ and $\lambda \in (0,1)$ 

**If for every $x <y \in X$, the line connecting $(x,f(x))$ and $(y,f(y))$ lies above the graph, the function is convex.**

The algorithm might converge to a local minima instead of a global minimum if multiple local minima exist.

However, for convex functions, following are equivalent
*  $x$ is a stationary/critical point of $f: \nabla f(x) =0$
*  $x$ is a local minima of $f$
*  $x$ is a global minimum of $f$ 
Therefore, the critical point is guaranteed to be the global minimum.

**Hessian matrix**
$H = \nabla^2 f(x)$ is positive semi-definite, if for any $z \in \mathbb R^n$ 
$$z^THz = \sum_{j,k} H_{j,k}z_jz_k \geq 0$$
**Theorem 3.1**
A sufficient condition for $f$ to be convex is that for every $x \in X$ 
$$\nabla^2f(x) \geq 0 \rightarrow z^THz \geq 0$$