# Clustering

* Widely used techniques for exploratory data analysis and an unsupervised learning task. (It aims to descfribe the hidden structure of the object)
* By clustering, we aim to produce a partition of the data.
* Goal is to find the clustering of minimal cost.

# K-Means
- The data points assigned to cluster k should be close to the $k^{th}$ center $\mu_k$.

**Distortion measure**
To quantify how close all the data points are to their assigned centers $\mu_k$.
$$J(\{r_{nk}\}, \{\mu_k\}) = \sum^N_{n=1} \sum^K_{k=1} r_{nk} ||x_n - \mu_k || ^2_2$$
where $r_{nk} \in \{0,1\}$ is an indicator variable.
$\rightarrow$ $r_{nk} =1$ if and only if the n-th data point is assigned to cluster k.
Optimization problem:
$$
\begin{align}
&\underset{\{r_{n,k}\}, \{\mu_k\}}{\text{minimize}} \text{ }J(\{r_{n,k}\} \{\mu_k\})\\
&\text{subjet to } r_{nk} \in \{0,1\}, \sum^K_{k=1} r_{nk} =1
\end{align}
$$
Since in each iteration the objective function strictly decreases due to changing $\{r_{nk}\}$ and $\{\mu_k\}$ and there is a finite number of possible choices for $\{r_{nk}\}$ and $\{\mu_k\}$, the algorithm is guaranteed to terminate.
*k-means algorithm converges to a local minimum and the solution depends on the initialization.*

Too large of K is analogous to over-fitting in supervised learning.

**K-Means ++**
- k-means++ has a better initialization of the centroids, finding a solution that is most close to the optimal solution of k-means.
Steps:
1. Choose one point randomly.
2. Compute the distance $S(x)$, between each data point and the centroid $c_1$.
3. Pick the next centroid from the data points with probability of $\frac{S(x)}{\sum_{x\in D} S(X)}$.
	- Most likely to pick the point that is farthest away from the nearest centroid.
4. Repeate step 2 and 3 until k centroids have been selected.
5. Perform the k-means clustering

**K-Medoids and K-Medians**
- k-medoids: data points are centroids
- k-medians: K-Means is sensisitive to outliers.

K-Medoids:
1. Initialize $\mu_k$ by randomly choosing K of the N points.
2. Fix $\mu_k$ and assign points to clusters
$$r_{nk} = \begin{cases} 1 \text{ if } k=argmin_j||x_n-\mu_j||^2_2 \\ 0 \text{ otherwise } \end{cases}$$
3. Fix $r_{nk}$ and update the center for each cluster k. In k-medoids, the center for a cluster is the data point that is closest to all other data points in the cluster:
$$
\begin{align}
&k^* = \underset{m:r_{mk}=1}{argmin} \sum_n r_{nk} ||x_n -x_m||^2_2 \\
&\mu_k = x_k
\end{align}
$$
4. Stop if the objective function J stays the same

K-Medians:
1. Initialize $\mu_k$ by randomly selecting K of the N points.
2. Fix $\mu_k$ and assign points to clusters
$$r_{nk} = \begin{cases} 1 \text{ if } k=argmin_j||x_n-\mu_j||_2 \\ 0 \text{ otherwise } \end{cases}$$
3. Fix $r_{nk}$ and update the center for each cluster k. In k-medians, we use $||\cdot||_2$ instead of squared norm:
$$\mu_k = argmin \sum_n r_{nk} ||x_n-\mu_k||_2$$
4. Stop if the objective function J stays the same. Otherwise, return to Step1.

# Gaussian Mixture models
- K-means finds the hard margins of k different groups
- GMM is soft margins by using a probabilistic interpretation of clustering.
- Assume the data points are to be generated by sampling from a specific parametric distribution