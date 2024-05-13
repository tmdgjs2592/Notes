**The learning problem**
- The goal is to find a prediction function that maps the set of features to the set of targets (labels)
- The learning algorithm uses past data or training data to design the prediction function.

**Learning Methods**
Three types: Supervised, Unsupervised, Reinforcement
Supervised Learning
- uses the past relationship between the features and targets to learn
- The algorithm tries to predict a target for new unseen data.
- can be used to predict if a cell is cancerous by comparing the structure of a cell with past data
Unsupervised learning
- Only used for classfication
- Attempts to learn the intrinsic structure of data
- These algorithms choose categories that best fit the new data based on the past data seen.
Reinforcement learning
- Interactive learning method
- Optimizes a policy for maximum rewards
- Given the input features, it chooses output targets and learns based on the rewards (feedback)

**Supervised learning method**
- Given the training set, it outputs a prediction rule h that can be used for unseen data.
- h is restricted to a set of hypotheses that is based on the prior knowledge
- This restriction is called inductive bias
- loss function measures a cost of predicting the label with $h(x)$
- Risk function: $R(h) = \mathbb E_{(x,y)~D}[\mathscr l(y,h(x))]$  
- The goal of the learner is to find $h_{opt}(x) = argminR(h)$ 
- Since we do not know the distribution, we introduce empirical risk.
- $R^{EMP}(h) = \frac{1}{m} \sum^m_{i=1} l (y_i, h(x_i))$ 
- Assume the training set $S=\{(x_1,y_1), \dots , (x_m,y_m)\}$ such that $(x_i,y_i)$ are i.i.d $\sim D$. 
- From the law of large numbers, the average of the results obtained from a large number of tests should be equal to the expected value.