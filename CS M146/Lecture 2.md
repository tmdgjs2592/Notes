
**Key issues**
- We want to think about representation
	- Choice of hypothesis and feature space
- Optimization
	- How do you solve for best hypothesis ? (=argmin R(h))
	- You need to have an efficient way
- How do you gauge the accuracy

**Perceptron Learning**
- Historically the first, done in 1940s ~ 1950s
- Idea: with different angles, the model gets trigerred
- Sign functoin: a function that outputs either -1 or 1
- Binary labels: $y \in \{-1, 1\}$ 

**Perceptron Predict**
- Activation: $a = \sum^{D}_{d=1}w_dx_d + b$ 
- Output: $\hat {y} = sign(a) = h(x)$
- To check if the prediction is correct
	- if $y_n \cdot a > 0$ $\rightarrow$ correct
	- if $y_n \cdot a \leq 0$  $\rightarrow$ incorrect (error in prediction)
	- If incorrect, $w_{new} = w_{OLD} +y_nx_n$ 
- why is  $w_{new} = w_{OLD} +y_nx_n$  a good method ?
	- when you plug in $w_{new}$, you are adding a positive number $\rightarrow$ improving

**Properties of perceptron learning**
- We are permuting the algorithm with data sequentially ($\rightarrow$ online algorithm)
- If the data is not lineraly separable $\rightarrow$ the algorithm does not converge
- If the data is linearly separable $\rightarrow$ the algorithm converges in a finite number of steps

**Perceptron convergence**
Linear separability of training set $\mathscr {D}$ : $\exists \mathscr {w}$ such that it gives zero empirical risk for the 0-1 loss function over the training set $\mathscr {D}$.

**Hard to Soft decisions $\rightarrow$ logistic regression**
- We want to give a notion of confidence and interpret a "trad".
- Even if the data is not linearly separable we can infer a trad.
- Hard output: $\{-1, 1\}$, Soft output: $[-1,1]$ 
- $h_{w,b}(x) = \sigma (a(x))$ 
- $\sigma(\cdot) = \frac {1} {1+e^{-a}}$  $\rightarrow$ sigmoid function
- 