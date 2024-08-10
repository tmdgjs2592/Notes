# Neural Network
- inspired by the structure of neurons in the brain
- three parts: an input layer, hidden layer, and an output layer.

neural network represents a function $h_w : R^d \rightarrow R^k$, where d is the input feature dimension and k is the output dimension.

Training: updating the network weights $w$ to minimize a cost function $L(x)$.

**Backpropagation**
The process used to train a neural network

Two mechanisms
- Forward: starting from the first layer, we compute the function signals of each neuron and obtain the network output.
- Backward: From the output layer towards the first hidden layer, we recursively compute the gradient of each network weight and update them following gradient descent rules.

