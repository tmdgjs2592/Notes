# Kernel Methods
* We want more expressability in our models
* we map feature vectors to an expanded version
* $\phi (x) : \mathbb R^d \rightarrow H$ 
* use $\phi(x)$ as non-linear input to our linear model
* The computational cost in the higher-dimensional space can be expensive, to which we introduce **Kernel function**.

**Kernel function**
$$k(x,u) := (1+x^Tu)^2$$
Kernel function satisfies
$$\begin{align} k(x_m,x_n)&=k(x_n,x_m) \\ k(x_m,x_n) &= \phi(x_m)^T\phi(x_n)\end{align}$$
**Gaussian kernel**
$$k(x_m,x_n) = e^{-||x_m-x_n||^2_2/2\sigma^2}$$
**Polynomial kernel with degree d**
$$k(x_m,x_n) = (x_m^Tx_n+c)^d$$
**Inhomogeneous polynomial**
$$k(x,x') = (<x,x'> +c)^p$$

**Kernel function properties**
Let $k_1, k_2$ be kernel functions on $X \times X$. Then,
- $ck_1$ is a kernel for $c>0$
- $\alpha k_1+ \beta k_2$ is a kernel for $\alpha, \beta \geq 0$
- $k_1 k_2$ is a kernel
- $e^{k_1}$ is a kernel

**Informal Mercer's theorem**
A symmetric function $K: X\times X \rightarrow \mathbb R$ is a valid kernel function if and only if its Kernel matrix is positive definite; i.e. for all $x_1,...,x_N,$ and for all $N$, the matrix $K$ whose elements are $(K)_{m,n} = K(x_m, x_n)$ is a positive definite matrix.