

## Logistic Regression
- One of the most used classifiers
- Very simple but generalizes to neural networks
- Basic version is a linear binary classifier
- related to linear regression
- But it is a algorithm for classification and not regression



## Linear Regression
- Model Parameters
- On input x = [x1, ....., xn], the model outputs


Decision Boundary
![[Pasted image 20220916140555.png]]



![[Pasted image 20220916140636.png]]

Decision Boundary
- Generalizes to high dimensions & multi-class  
classification



Logistic Regression
- One of the most used classifiers  
- Very simple but generalizes to neural networks  
- Basic version is a linear binary classifier  
- Related to linear regression  
- But Note: It is an algorithm for classification, not regression


- Softmax Regression



Support Vector Machine (SVM)
- Maximizes the margin
	- Gives the maximum separation between the two classes
	- ![[Pasted image 20220923141157.png]]



Hyperparameters of SVM
- Kernel
- c : The regularization parameter as for logistic regression
- Gamma (Y) : Decides the curvature of the decision boundary
- Both C and Y control the bias variance tradeoff
- smaller C,y = less prone to overfitting = more prone to underfitting
- larger C,y = more prone to overfitting = less prone to underfitting




### K Nearest neighbors
- Data examples represented as points Euclidean space
- A Lazy Algorithm - does nothing during the training other than storing the training data and their labels

- K is a tuned hyperparameter 
- KNN
	- ![[Pasted image 20220923151623.png]]
	- 