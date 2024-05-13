**Transform the input / feature**
$$
\phi (x) : x \in \mathbb R^2 \rightarrow z = x_1 \cdot x_2
$$
Take an original space and map it to a new one.
$\phi(x): x \in R^D \rightarrow z \in \mathbb R^M$
*M: dimensionality of the new feature. M can be either greater than D or less than or the same*
This can be useful as it makes other algorithms possible.
Ex) linearly non-separable $\rightarrow$ linearly separable

Challnge
- How to find $\phi(x)$ properly for the data
Caveat: we also want to compute efficietly -> kernel function 

Regression with nonlinear basis
data matrix: n * d+1 matrix
$$
\phi: \mathbb R^{D+1} \rightarrow \mathbb R^{M}
$$
you can go to more complex feature space but might not be the best necessarily.
coefficients large --> sign of overfitting
stable hypothesis -> not overfitting

**How to detect overfitting**
- do some testing (run it on unseen data)
- If training error and test error diverge $\rightarrow$ overfitting
you want to operate in the regime that's not overfitting or underfitting
Overfitting is relative to the amount of data you have.

# Regularization
**how do you choose a proper parameter**
- Algorithm $\rightarrow$  regularization
	- think about a inductive bias
		- A simpler model is one where most of the weights are zero
		- A simpler model is one with smaller weights.
	- we want a cost function that encourages small weight solutions
	- change my features slightly -> prediction does not change
	- Approach: change the cost function 
	- you are adding a regularization $\lambda$ $\sum_{d=1}^{D} \theta_d ^2$  $$\tilde{J}(\theta) = J(theta) +\lambda ||\theta||^2$$ 
* $\overset{\sim}{J}(\theta)$  is convex for all $\lambda$ $\geq$ 0
- $\nabla \tilde{J}(\theta) = \nabla J(\theta) + 2\lambda \theta$
- $H = \nabla^2 J(\theta) + 2\lambda I$ 
- Close form solution: $\hat {\theta} = (X^TX+\lambda I)^{-1} X^Ty$
- $(X^TX+\lambda I)^{-1}$ is always invertible since you are adding $\lambda I$ and $\lambda > 0$.

**How do you find lambda ?**
- $\lambda$ is $hyperparameter$
- underfitting -> bigger lambda
- overfitting -> lambda is close to zero
- Evaluation $\rightarrow$  cross validation
overfitting is relative to the complexity of the model and the data

# Bias-variance tradeoff
$\textbf{Bias of an estimator}$: Difference between an estimators expected value and true value.
Variance: caputres prediction variation over dataset
Bias: captures how prediction misses true value
Noise: the inherent unpredictability
$$ \mathbb E_D R$$
To improve generalization performance
- Choose better models using validation
- Regularization

Hyperparameters
- Model hyperparameters: choices in $H$ and feature maps $\phi(\cdot)$ 
- Algorithmic hyperparameters: Influence model training, learning, rate/step size, batch size, regularization coefficient etc.
	- better step size $\rightarrow$ faster the convergence
	- larger batch size $\rightarrow$ smoother the path to optimal
Final evaluation must be based on the unseem data

# k-fold Cross-validation
**Cross-validation**
idea: Split the dataset into three parts: training, validation, and test data.
**k-fold**
idea: Partition the data set and choose one as validation and rest as the data
use this to choose best hyperparameters
test set should be untouched until the end to evaluate performance of final model.
