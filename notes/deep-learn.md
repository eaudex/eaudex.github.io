# Deep Learning

## Neural Networks and Deep Learning
* Neural Networks are a class of machine learning algorithms.
    1. Old-school way of constructing and training a network:
        * Input layer
        * Output layer
        * 1 or 2 hidden layers
        * => the data you present for training in the input layer is already
          in a format that allows a machine learning algo (e.g. neural networks)
          to recognize the important patterns.
          (Feature engineering is done by you before training.)
    2. New way of constructing and training a network:
        * Input layer
        * Output layer
        * **More** hidden layers --> that is why we call **deep** neural networks
        * => most feature engineering can be achieved by
          the machine learning algorithm itself.

* The concept of Deep Learning is NOT tied to Neural Networks
  but it is very well demonstrated through Neural Networks.

* https://www.quora.com/What-is-the-difference-between-Neural-Networks-and-Deep-Learning


## Design NN Architecture
### MLP NN
* Input layer:
    * #neurons == #features
* Output layer:
    * Classification:
        * #neurons == #classes
    * Regression:
        * 1 output neuron
* Hidden layer:
    1. #hidden layers
        * 0 hidden layer:
            * MLP with ZERO hidden layer can ONLY deal with linear separable cases.
        * 1 hidden layer:
            * MLP with ONE hidden layer can approximate any continous mapping
              from one finte space to another.
            * MLP with ONE hidden layer can solve the majority of problems.
        * 2 hidden layer:
            * MLP with TWO hidden layers can approximate any smooth mapping
              to any accuracy.
            * MLP with two hidden layers is rarely required in practice
              (before deep learning comes out).
            * MLP with more than one hidden layer is hard to train
              (before deep learning comes out).
            * There in no **theoretical** reason to use more than two hidden layers.
    2. #neurons in a hidden layer
        * #neurons is between input size and output size.

* [Ref] https://stats.stackexchange.com/questions/181/how-to-choose-the-number-of-hidden-layers-and-nodes-in-a-feedforward-neural-netw


# References
* http://cs231n.github.io/

