

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
	- the inputs closest to the dividing hyperplane are used to make a dividing decision.


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



### Random Forest 
Random Forest, An ensemble of decision trees, takes an average of all the outputs of the decision trees, collection of weaker models to create a stronger model.


### Boosting
- Construct and combine an ensemble of weak learners into a strong learner
- Applies to any weak ML model as the base estimator
- Usually applied to shallow decision trees
	- Trees with a depth of 1,

- Boosting Algos
	- XGBoost
	- AdaBoost
	- Gradient Boosting

#### AdaBoost
- combines weak models to stronger
- Boosting and tuning the parameters are more difficult
- Slower than random forest. 
- look into Ada-boost Regression model


### Naive Bayes
- A classifier based on the bayes rule
- Assumes that all the features are conditionally independent given the class label
- limited range of applications
- but works well for document and spam

Neural Network
- Layers of interconnected "Neurons"
- Details later
- Significantly outperforms traditional models when data is large and the problem is complex
- But takes much longer to train. 