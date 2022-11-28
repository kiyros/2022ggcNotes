- parameters : Weights and Bias
- a = output of the previous layer
- w = weight
- b = bias

- the output of the previous layer is the input of the next layer
- after calculation in a unit/node it will go through an activation function which then becomes the output
- common Activation functions:
	- ![[Pasted image 20221014163958.png]]




## How does a NN learn its parameters
- Optimization
- Cost/loss Function to measure the model's performance in training
	- Also called Loss
	- ![[Pasted image 20221028141028.png]]
- **Gradient Descent**: Find parameters that minimize the cost, user (variants of) 
- **Backpropagation**: A Celebrated Algorithm to compute the gradient of a neural network's cost function.
- ![[Pasted image 20221028141413.png]]
- ![[Pasted image 20221028141438.png]]
- Learning Rate:
- ![[Pasted image 20221028142443.png]]
### Vectorized NN Computation
- ![[Pasted image 20221028150914.png]]
- 