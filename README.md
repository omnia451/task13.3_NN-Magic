# task 13.3
## Notes
1. **Preceptons:** a type of artificial neurons that takes several binary inputs and produces a single binary output
   * The neuron's output, 0 or 1, is determined by whether the weighted sum ∑wx is less than or greater than some threshold value, where x is the binary input and w is its weight
   * Just like the weights, the threshold is a real number which is a parameter of the neuron
   * A precepton's bias is a measure of how easy it is to get the perceptron to output a  1, whereas for a perceptron with a really big bias, it's extremely easy to output a 1, but if the bias is very negative, then it's difficult for it to output a 1
   * We can use perceptrons to compute any logical function
     
2. **Sigmoid:** another type of artificial neuron similar to perceptrons, but modified so that small changes in their weights and bias cause only a small change in their output
   * Just like preceptons they have several binary inputs with their designated weights, but they can give off an output of any value between 0 and 1 unlike preceptons which are either 0 or 1
   * The output of a sigmoid is a sigmoid function which is:   **σ(z)≡ 1/(1 + e<sup>-z</sup>)**
   * the shape of the sigmoid function when plotted is a smoothed out version of a step function, while the shape of a percepton is in fact a step function, the smoothness of **σ** means that small changes **Δw<sub>j</sub>** in the weights and **Δb** in the bias will produce a small shift **Δoutput** in the output from the neuron
   * **Δoutput** is a linear function of the changes **Δw<sub>j</sub>** and **Δb** in the weights and bias. This linearity makes it easy to choose small changes in the weights and biases to achieve any desired small change in the output

3. **feedforward neural networks:** neural networks where the output from one layer is used as input to the next layer, which means there are no loops in the network - information is always fed forward, never fed back

4. We need to find weights and biases so that the output from the network approximates y(x) for all training inputs x, to quantify how well we're achieving this goal we define a **cost function**:   **C(w,b) ≡ (1/2n) ∑<sub>x</sub> ∥y(x) − a∥<sup>2</sup>**
   * w denotes the collection of all weights in the network
   * b all the biases
   * n is the total number of training inputs
   * a is the vector of outputs from the network when x is input
   *  and the sum is over all training inputs x
-> We aim to get to C(w,b)≈0, which means that our training algorithm has done a good job if it can find weights and biases, and on the contrary, it wouldn't be doing so well if C(w,b) is large, which would mean that y(x) is not close to the output a for a large number of inputs
  
5. **Gradient descent:** an optimization algorithm for finding a global minimum of a differentiable function, we use it to find the weights and biases which minimize the cost in the cost function, and so helping the net learn

6. **Stochastic gradient descent:** the idea behind it is to estimate the gradient ∇C by computing ∇C<sub>x</sub> for a small sample of randomly chosen training inputs, by averaging over this small sample we can quickly get a good estimate of the true gradient ∇C, which helps speed up gradient descent, and thus learning
   * stochastic gradient descent works by picking out a randomly chosen mini-batch of training inputs, and training with those, then we pick out another randomly chosen mini-batch and train with those. And so on, until we've exhausted the training inputs
     

## How It Works
### Classify each individual digit
  * To recognize individual digits a three-layer neural network is used, where:
    - The input layer contains 784=28×28 neurons, as the training data for the network consists of 28 by 28 pixel images of scanned handwritten digits
    - The second layer of the network is a hidden layer containing n neurons
    - The output layer of the network contains 10 neurons each corresponding to a digit from 0 to 9
  
