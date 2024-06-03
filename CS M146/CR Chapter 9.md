# Ensemble Methods & Boosting
* The high level idea of boosting is to combine a lot of weak learners into a single yet strong one with high accuracy, where the weak learner, or basic learner, refers to the hypothesis which performs only slightly better than random guessing, while a strong learner is able to arrive at complex decision boundaries and output a predicted outcome that is correct on almost all instances.
- bagging: training same classifier on multiple datasets.
- boosting: combining a lot of classifers.

**Multiple Classifiers on the same Dataset**
train predictors $\overset{\sim}{h_1}, ..., \overset{\sim}{h_L}$ and then combine their predictions as majority vote: $h = sign(\overset{\sim}{h_1} +...+ \overset{\sim}{h_L})$, $\overset{\sim}{h_l} \in \{+1, -1\}$

**Same Classifier on Multiple Datasets**
Split original training dataset into multiple datasets and train a classifier on each of them.

# AdaBoost Algorithm
* The main idea is to use weak or base classifiers to arrive at a strong classifier with a low empirical risk.
* $y_n \in \{+1,-1\}$
* each example is assigned a weight.
* $n^{th}$ example at the $t^{th}$ iteration is denoted by $w_t(n)$
* $w_0(i)$ is initialized to $\frac{1}{N}$

Weighted classification error for the $l^{th}$ weak classifier at the $t^{th}$ iteration:
$$\epsilon_{t,l} = \sum_n w_t(n) II$$
