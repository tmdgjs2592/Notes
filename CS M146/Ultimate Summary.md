# K-means
- the solution depends on initialization
- converges to a local minimum
- run many times with different initializations and pick the best
- Low Inertia and low K is desirable
- Inertia: Sum of squared distances of datapoints to cluster centers
- As K increases, inertia decreases
- Choose K when the drop rate of Inertia slows down.
- Increasing K will $\underline{always}$ decrease the optimal value of the K-means objective.
- K-means is sensitive to outliers $\rightarrow$ K-median
- We want the prototypes to be one of the points $\rightarrow$ K-medoids.

# K-medoids and K-median
K-medoids
1. initialize $\mu_k$ by randomly selecting K of the N points
2. Assume $\mu_k$ fixed and assign points to clusters ($r_{nk} = 1$ if assigned to k, else 0)
3. Assume $r_{nk}$ and update the centroid to the data point that is closest to all other data points in the cluster.
4. $\mu_k = x_k$ (center has to be a data point)
K-median
1. Same initializaton as K-medoids
2. Assume $\mu_k$ and assign points to clusters but the crietria is $||\cdot||_2$ 
3. $\mu_k = arg min \sum_n r_{nk}||x_n-\mu_k||_2$ 

# Gaussian mixture models
Marginal distribution
$$p(x) = \sum^K_{k=1} w_k N(x|\mu_k,C_k)$$
$\mu_k$: mean, $C_k$: covariance, $w_k$: mixture weights - represent how much each componenet contributes to the final distribution.
For incomplete data, whose labels we do not know, there is no simple way to optimize MLE.
Expectation-Maximization(EM) algorithm comes in.
- E: guess values of the $z_n$ using existing values of $\theta$.
- M: solve for new values of $\theta$ given imputed values for $z_n$.
**E-step**
- define $\gamma_{nk}$ as $p(z_n=k|x_n, \theta)$
 - This is a soft assignment of $x_n$ to k-th componenet $\gamma_{n,k} \in [0,1]$
**M-step**
- update $\theta = \{w_k, \mu_k, C_k\}$
$$
\begin{align}
w_k &= \frac{\sum_n \gamma_{nk}} {\sum_k \sum_n \gamma_{nk}}, \mu_k = \frac{1}{\sum_n \gamma_{nk}} \sum_n \gamma_{nk} x_n \\
C_k &= \frac{1}{\sum_n \gamma{nk}} \sum_n \gamma_{nk} (x_n - \mu_k) (x_n-\mu_k)^T
\end{align}$$Alternate between estimating $\gamma_{nk}$ and estimating $\theta$, until convergence.
K-means is often called hard GMM or GMM is called soft K-means
EM algo converges but to local optimum

# Principal component analysis (PCA)
- the goal is to find a hyperplane that minimizes $\sum^N_{i=1} ||x_i-\overset{\sim}{x_i}||^2$
- $y_i = Wx_i$ where $W \in \mathbb R^{l \times d}$
- $\overset{\sim}{x_i} = Uy_i$ where $U \in \mathbb R^{d \times l}$
- If U, W are solutions to the PCA objective, then the columns of U are orthogonal
- i.e., $\underline{U^TU=I_l}$ and $\underline{W=U^T}$
- PCA objective rewritten: 
$$min \sum^N_{i=1} ||x_i - UU^T x_i||^2_2$$
- Simplification
	- min $\sum^N _{i=1} ||x_i||^2 - trace(U^Tx_ix_i^TU)$
	- = max $\sum^N _{i=1} trace(U^Tx_ix_i^TU)$ 
	- = trace($U^TAU$) (A = $\sum^N _{i=1} x_i x_i^T$ )
	- = $\underset{U \in \mathbb R^{d \times l}} {max} trace(U^TAU)$ (Objective)
- Eigen decomposition 
	- A = $\sum^N _{i=1} x_i x_i^T = V \Lambda V^T$ where A, V $\in \mathbb R^{d \times d}$
	- $\Lambda = diag(\lambda_1, ... , \lambda_d)$ where $\lambda_1 \geq \lambda_2 \geq ... \lambda_d \geq 0$.
- Solution to the Objective: U = $[v_1, ... , v_l]$, where V=$[v_1, ...,v_d]$ ordered according to eigenvalues $\lambda_1 \geq \lambda_2 \geq ... \lambda_d \geq 0$.
- The solution is the eigenvectors of A corresponding to eigenvalues $\lambda_1, ..., \lambda_l$ which are the l-largest.

**Steps**
1. Compute $A$ 
2. Compute eigendecomposition $A=V\Lambda V^T$.
3. Return top $l$ eigenvectors $U=[v_1, ..., v_l]$ as principal components
4. For any point x, the low-dimensional representation is $y=Wx = U^tx$.

Explained variance: the relative importance of each eigenvector.
$$EV_i = \frac {\lambda_i}{\sum^d_{j=1} \lambda_j}$$

# Kernel PCA
Goal: Compute the principal componenets of $\Phi = \phi(x_1), ... , \phi(x_n)$ 
Eigendecomposition: $C = \frac{1}{n} \sum^N_{i=1} \phi(x_i) \phi^T(x_i)$ 
With $v:$ eigenvector of C, $Cv = \lambda v$ = $\frac{1}{n} \sum^N_{i=1} \phi(x_i) \phi^T(x_i)v$ = $\lambda v$.
$$\rightarrow v = \sum^N _{i=1} \frac {1}{N\lambda} \phi(x_i) \phi^T(x_i)v = \sum^N_{i=1} \alpha_i^{(v)} \phi(x_i) = \Phi \alpha^{(v)}, \text{where }\alpha = \frac {1}{N\lambda} <\phi(x_i), v>$$
Claim: $K \alpha^{(v)} = N\lambda \alpha^{(v)}$ 
Eigenvectors $v_1, ..., v_n$ of eigenvalues of C, are characterized by $\alpha^{(v_1)}, ..., \alpha^{(v_N)}$, eigenvectors of K of eigenvalues $N\lambda_1, ..., N\lambda_N$.
Compuite eigendecomposition of K to find $\alpha$.
