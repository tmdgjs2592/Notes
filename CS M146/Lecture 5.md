Linear regression does not fit the data well (line)

Transform the input / feature
$$
\phi (x) : x \in \mathbb R^2 \rightarrow z = x_1 \cdot x_2
$$
How to transform the input / feature ?
$$
\phi(x) : x \in \mathbb R^2 \rightarrow z = \
$$
Take an original space and map it to a new one.
$$
\textbf{$\phi$ has to be chosen carefully}
$$
only create the feature map based on the data you have
Challnge
- How to find $\phi(x)$ properly for the data
Caveat: we also want to compute efficietly -> kernal function 
Regression with nonlinear basis
data matrix: n * d+1 matrix
$$
\phi: \mathbb R^{D+1} \rightarrow \mathbb R^{M}
$$
you can go to more complex feature space but might not be the best necessarily.
coefficients large --> sign of overfitting
stable hypothesis -> not overfitting
fitting and stability
How to detect overfitting
- do some testing (run it on unseen data)
you want to operate in the regime that's not overfitting or underfitting
how do you choose a proper parameter
- Algorithm $\rightarrow$  regularization
	- think about a inductive bias
		- A simpler model is one where most of the weights are zero =
		- A simpler model 
	- we want a cost function that encourages small weight solutions
	- change my features slightly -> prediction does not change
	- Approach: change the cost function 
	- you are adding a regularization $\lambda$ $\sum_{d=1}^{D} \theta_d ^2$ 
	- $\overset{\sim}{J}(\theta)$  is convex for all $\lambda$ $\geq$ 0
	- how do you find lambda ?
	- $\lambda$ is referred as $hyperparameter$
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
Hyperparameters
- Model hyperparameters: choices in $H$ and feature maps $\phi(\cdot)$ 
- Algorithmic hyperparameters: Influence model training, learning, rate/step size, batch size, regularization coefficient etc.
	- better step size $\rightarrow$ faster the conversion 
	- larger batch size 
Final evaluation must be based on the unseem data

$\textbf{k-fold Cross-validation}$
idea: Use more than one split of the training data
*Partition the data set and choose one as validation and rest as the data* 

