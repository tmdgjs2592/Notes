# Perceptrons

**Goal**
$\rightarrow$ to create a binary classifier, a predictor function $h(x)$ that correctly classifies the set of data into two classes $y \in \{-1,1\}$.
# Linear Separability

A dataset $D$ is linearly separable if there exists a hyperplane ($\overset {\sim}{w}, b$) such that $y_n(\overset{\sim}{w}^T \overset{\sim}{x_n})$ > 0, $\forall(\overset{\sim}{x_n}, y_n)$. 
$\rightarrow$ There exists a hyperplane that gives zero empirical risk for the 0-1 loss function over $D$.

*For the perceptron to function properly, the two classes $C_1$ and $C_2$ must be linearly separable or distinguishable by a single linear hyperplane boundary.

# Algorithm

**Goal** $\rightarrow$ to have a weight vector $\overset{\sim}{w}$ such that 
$$
\begin{align}
	&\overset{\sim}{w}^T \cdot \overset{\sim}{x} > 0, \text{ if the vector $\overset{\sim}{x}$ belongs to class $C_1$} \\
	&\overset{\sim}{w}^T \cdot \overset{\sim}{x} < 0, \text{ if the vector $\overset{\sim}{x}$ belongs to class $C_2$} \\
\end{align}
$$
Misclassified points:
$$ sign((\overset{\sim}{w}^{(t)})^T \cdot \overset{\sim}{x} \neq y_n$$
Update:
$$\overset{\sim}{w}^{(t+1)} = \overset{\sim}{w}^{(t)} + y_n\overset{\sim}{x_n}$$
Why it works?
A point is misclassified when $y_n  ((\overset{\sim}{w}^{(t)})^T \cdot \overset{\sim}{x_n} ) < 0$. Then, we proceed to update by adding $y_n \overset{\sim}{x_n}$ to the weight. This yields the following prediction for the update weight vector 
$$ y_n((\overset{\sim}{w}^{(t+1)})^T \cdot \overset{\sim}{x})=
y_n ((\overset{\sim}{w}^{(t)} +y_n\overset{\sim}{x}^T) \overset{\sim}{x})$$
Since we are adding a non-negative term, the updated vector will be closer to convergence.

**Theorem 2.1**
For linearly separable dataset $D$ with margin $\gamma$ and $R = max_i ||\overset{\sim}{x_i}||$, the perceptron algorithm converges in at most $\frac {R^2}{\gamma ^2}$ updates.

*It does not converge to the optimal margin maximizing hyperplane, instead can converge to any solution that separates the data*

