# Dimensionality Reduction

**Principal Component Analysis**
Goal: Given data $X = [x_1, x_2, ..., x_N]^T$, where $x_i \in R^d$, to project the $x_i$ onto an $l$-dimensional plane where $l < d$ 
Optimization problem:
$$\underset{U\in R^{d \times l}, W \in R^{l \times d}}{min} \sum^N_{i=1}||x_i - \overset{\sim}{x_i}||^2_2 = \underset{U\in R^{d \times l}, W \in R^{l \times d}}{min} \sum^N_{i=1} ||x_i-UWx_i||^2_2$$
We want to find U and W that minimizes the distance between $x_i$ and $\overset{\sim}{x}$.

Lemma 11.1: If U,W are solutions to the PCA objective, then the columns of U are orthonormal, i.e., $U^TU = I_l$ and $W=U^T$.

Lemma 11.2: The solution to the PCA objective is given by $U=[v_1, v_2, ..., v_l]$ where $V = [v_1, v_2, ..., v_d]$ are the principal eigenvectors of $\sum^N_{i=1} x_ix_i^T$.

# Kernel PCA
- mapping our dataset to another space before applying PCA.

Lemma 11.3: $N\lambda \alpha ^{(v)} = K\alpha ^{(v)}$ 
