# Support Vector Machine (SVM)
- Unlike perceptron which tries to find a hyperplane that classifies the data, SVM tries to find a hyperplane that classifies the data and maximizes the gap.
- SVM uses data points called support vectors to train decision boundary.
- support vectors are data points that lie on the boundary of the decision regions, within the decision regions, or are misclassified.

**Properties of Hyperplane**
- the vector $w$ is normal to the hyperplane $\mathcal H$ : $\{x: w^Tx+b = 0\}$ 
- The distance between a point $a$ and a hyperplane defined by $w^Tx+b=0$, with $||w|| =1$, is given by $|w^Ta+b|$.

**Signed distance**
$$w^T(a-a_0) = \frac{w}{||w||_2} (a-a_0) = \frac{1}{||w||_2}(w^Ta+b), \text{ ($w^Ta_0=-b$)}$$
**Unsigned distance**
$$d(\phi(x)) = \frac{|w^T\phi(x) +b|}{||w||_2} = \frac{y(w^T\phi(x) +b)}{||w||_2}$$
$\frac{y(w^T\phi(x) +b)}{||w||_2}$ is only true when the data is linearly separable $\rightarrow$ $y$ and $w^T\phi(x) +b$ have the same sign.

**Optimizing margin**
Margin: Smallest distance between the hyperplane and all data points.
$$MARGIN(w,b) = \underset{n}{min} \frac{y(w^T\phi(x) +b)}{||w||_2}$$
*The margin does not change if the parameters of the hyperplane(w,b) is scaled by a constant c*
Using the fact, we can convert the optimization problem to:
$$\underset{w,b}{max} \frac{1}{||w||_2}, s.t \text{ } \underset{n}{min} (y(w^T\phi(x) +b))$$
which is equivalent to, $$\underset{w,b}{min} \frac{1}{2} ||w||_2^2, s.t \text{ } y(w^T\phi(x) +b) \geq 1$$
Objective function is quadratic and the constraint functions are linear $\rightarrow$ the optimization is convex and can be solved efficiently.

**Slack variable**
$\rightarrow$ slack variable allows the constraints to be relaxed so that the problem can be feasible. (non-separable to separable)
$\rightarrow$ Constraints: $y(w^T\phi(x) +b) \geq 1-\xi_n$
$\rightarrow$ Objective: $\underset{w,b,\xi} {min} \frac{1}{2} ||w||^2_2 + C\sum_n \xi_n$ (restricting the size of slack variable)
**Hinge Loss**
$\ell(y,a(x)) = \begin{cases}0 & \text{ if }ya(x) \geq 1 \\ 1-ya(x) & otherwise \end{cases}$ 
$a(x) = w^T\phi(x)+b$ 
* Hinge loss is always greater than or equal to the 0/1 loss and is convex.
- The loss increases as the point is more misclassified. 
- e.g. x=1 $\rightarrow$ y=0 (correctly classified), x=0 $\rightarrow$ y=1 (misclassified), x=-2 $\rightarrow$ y=3 (worse)

**Kernelizing SVM**
Motivation
* Previous equations involve solving $\phi(x)$ directly, which is computationally expensive.
* To avoid this, we will use the dual of SVM.
Lagrange Multipliers
Given the optimization problem $\underset{x}{min}f_0(x)$ such that $f_i(x) \leq 0, i \in \{1,\dots m\}$ and $h_j(x) = 0 j\in \{1,\dots,p\}$, The Lagrangian for this primal problem is $L(x, \alpha, \beta) = f_0(x) + \sum_{i=1}^m \alpha_i f_i(x) + \sum^p_{i=1} \beta h_j(x)$.
To form a dual problem on the Lagrangian, we let g($\alpha, \beta$) = $\underset{x\in D}{min} L(x,\alpha, \beta)$.
Then, we form the dual problem by maximizing g, $max$ $g(\alpha, \beta)$.
Using Lagrangian on SVM, we obtain 
$$L(w,b,\xi,\alpha, \lambda) = C\sum^N_{n=1} \xi_n + \frac{1}{2}||w||_2^2 + \sum^N_{n=1} \alpha_n (1- y_n(w^T\phi(x_n)+b) -\xi_n) - \sum^N_{n=1}\lambda_n\xi_n$$
The dual problem for this Lagrangian
$$\underset{\alpha, \lambda} {max} \text{ }\underset{w,b,\xi}{min} L(w,b,\xi,\alpha,\lambda)$$
Solving the minimization by solving the gradient and plugging in the values, we obtain
$$L(w,b,\xi,\alpha,\lambda) = -\frac{1}{2} ||w||_2^2 + \sum^N_{n=1}\alpha_n= -\frac{1}{2}\sum^N_{n=1}\alpha_n \alpha_m y_ny_m\phi^T(x_n)\phi(x_m)+\sum^N_{n=1}\alpha_n$$
where we can replace $\phi^T(x_n)\phi(x_m)$ with $k(x_n,x_m)$.

