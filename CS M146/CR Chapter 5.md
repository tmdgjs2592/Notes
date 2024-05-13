# Decision Tree

**Possible Algorithm for decision tree training**
- Random
- Highest accuracy 
- Max-gain

**Information gain**
$\rightarrow$ difference between the entropy of the label before and after split.
$\rightarrow$ Information gain increases as entropy decreases

**Entropy**
Given discrete random variables $a_1, a_2, ..., a_k$, its entropy is given by
$$H[X] = - \sum^K_{i=1} P(X=a_i) \cdot \log (P(X=a_i))$$

The entropy of a discrete random variable Y with different M values $b_1,b_2, ... , b_M$ conditioned on the discrete random variable X taking a certain value $a_i$ is 
$$H[Y|X=a_i] = -\sum^M_{j=1} P(Y=b_j|X=a_i) \cdot \log (P(Y=b_j|X=a_i)$$
**Conditional Entropy**
The entropy of a discrete random variable Y with diferent M values $b_1, b_2, ... b_M$ conditioned on the discrete random variable X with different K values $a_1, a_2, ..., a_K$ is
$$H[Y|X] = -\sum^M_{j=1} \sum^K_{i=1} P(X=a_i) P(Y=b_j|X=a_i) \cdot \log (P(Y=b_j|X=a_i)$$
**Information gain**
The information gain between two discrete random variable X and Y is
$$GAIN = I(X;Y) = H[Y] - H[Y|X]$$
**ID3 (Iterative Dischotomizer)**
$\rightarrow$ Information maximizing greedy approach, that selects the feature with the maximum information gain to split on.

# Regression Trees

**Centroid**
$\rightarrow$ the squared-error minimizing constant for a region, mean of all the training labels in the region.
$$\hat{c_m} = \frac{1}{K} \sum _{x_n \in R_m} y_n $$
**Accuracy**
*Accuracy is the highest when the squared error is the lowest*
$$A(D;h) = - \sum_{x_n,y_n \in D} (y_n - h(x_n))^2$$
If the data size is too large, every $x_n$ will have its corresponding $R_m$, reaching 0 error, which is likely that it's overfitting.
Solution:
- max depth or max value of M

**Example of noisy data**
- when two instances have the same feature but different class label or some of features or labels are incorrect.

**Avoiding overfitting**
- Getting more training data
- Removing irrelevant features
- pruning the trees

**Pruning**
$\rightarrow$ prune the tree from bottom up and use the validation set to determine if a subtree needs to be pruned or not. Compare the performance before and after pruning validation set.


