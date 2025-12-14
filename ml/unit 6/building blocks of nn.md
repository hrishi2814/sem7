**Building Blocks of Neural Networks**

Neural networks are composed of several fundamental components that work together to learn patterns from data. The main building blocks are:

1. **Neuron (Artificial Neuron)**  
    The basic unit of a neural network. A neuron receives multiple inputs, multiplies each by a weight, adds a bias, and passes the result through an activation function to produce an output.
    
2. **Weights and Bias**
    
    - **Weights** determine the strength and importance of each input signal.
        
    - **Bias** allows the model to shift the activation function, helping the network fit data more flexibly.  
        These parameters are learned during training.
        
3. **Activation Function**  
    Introduces non-linearity into the network, enabling it to learn complex patterns. Common examples include ReLU, Sigmoid, and Tanh. Without activation functions, a neural network would behave like a linear model.
    
4. **Layers**  
    Neural networks are organized into layers:
    
    - **Input layer** receives raw data.
        
    - **Hidden layers** perform intermediate computations and feature extraction.
        
    - **Output layer** produces the final prediction or classification.
        
5. **Loss Function**  
    Measures how far the network’s predictions are from the actual target values. Examples include Mean Squared Error for regression and Cross-Entropy Loss for classification. It guides the learning process.
    
6. **Optimizer / Learning Algorithm**  
    Algorithms such as Gradient Descent or Adam adjust the weights and bias to minimize the loss function during training.
    

**In summary**, neurons, weights, biases, activation functions, layers, loss functions, and optimizers together form the core building blocks that enable neural networks to learn from data.