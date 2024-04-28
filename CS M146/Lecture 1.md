**Modeling the problem**
Feature space: Set of possible instances $X$
Label space: Set of possible labels $Y$ 
Hypothesis function: $h(x):X \rightarrow Y \in \mathscr {H}$ 

**Empirical Risk**
Risk: $R[h(x)] = \sum _{x,y} l(h(x), y) = \mathbb {E}_{x,y} [l(h(x), y)]$ 
*We do not know the true distribution of the dataset $\rightarrow$ we cannot compute the expected value*
Empirical Risk:
$$R^{EMP}[h(x)] = \frac {1}{N} \sum_n l(h(x_n), y_n)$$ Converted by the Law of Large Numbers.
