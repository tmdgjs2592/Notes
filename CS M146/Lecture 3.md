# Logistic Regression

**Gradient Descent**
When will this converge?
Convex: we can get to a global minimum using gradient descent
Non-convex: Multiple local minima may exist $\rightarrow$ no guarantee
all you are guaranteed is that you will get to a stationary point.

**Convex funciton**
A function is convex if
$$f(\lambda a + (1-\lambda)b) \leq \lambda f(a) + (1-\lambda) f(b) \text{ }\forall 0\leq \lambda \leq 1$$
$\rightarrow$ when you draw a line between two points on the graph, if the line is above the graph, a function is convex.

A function is also convex if
$$f''(w) \geq 0$$
**For multivariate functions**
Multi-variate function $f$ is convex if the Hessian is positive semi-definite $H \geq 0$.

**Positive semi-definite**
A symmetric matrix $H$, $(H)_{ij} = (H)_{ji}$ is positive semi definite if $\forall z, z^THz \geq 0$.

**Error**
$e_n = \{h_{\theta} (x_n) - y_n\}$ is called error for the nth training sample
 