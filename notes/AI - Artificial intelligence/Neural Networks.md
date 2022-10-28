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
- Find parameters that minimize the cost, user (variants of) **Gradient Descent**
- ![[Pasted image 20221028141413.png]]
- ![[Pasted image 20221028141438.png]]