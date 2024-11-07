# Supervised Machine Learning
- Machine learning always start with a system we are trying to analyze
- This is system is generating data it'll be our training data
- If we have labels on our training data with our inputs but also the thing we are trying to predict
- If so we have supervised learning
- We are trying to build a model that capitulate a known label truth in the future we can deploy the algorithm on some new data
- Is the model continuous or discrete label?
## Discrete supervised machine learning
- If we are trying to distinguish dogs or cats that is a discrete categorization of two classes 
- These are classification class
- Classify between one or the other
## Continuous supervised machine learning
- Continuous that can be some numerical value which is a regression task like linear regression, logistic

# Unsupervised Machine Learning
- If there are no labels 
- More like data mining, trying to learn patterns to built models to analyze future data
## Discrete Unsupervised Machine Learning
### Clustering
- Data that lives in discrete clusters 
- Data can be represented by multiple real value futures
- Use clustering algorithms to find a group of objects that correlate with each other
- 
![[Pasted image 20241102165505.png]]

## Continuous Unsupervised Machine Learning 
- Embedding, to allow models to learn from new data without needing to be retrained


# ANN: Artificial Neural Network
![[Pasted image 20241103113052.png]]
- Pre-activation is the result of the weighted sum
	- Input to the activation function

![[Pasted image 20241103113212.png]]
- the basic unit of a neural network
- It takes one or more inputs, performs a weighted sum of those inputs,
- then applies a non-linear activation function to produce an output.
- 3 different decision factors ($x_{1}, x_{2}, x_{3}$) that are inputs
- 3 weights ($w_{1}, w_{2}, w_{3}$) how much we care about the each decision factor
- Net value is calculated as a weighted sum of the decision factors, using the weights
- Final decision 'o' is determined by net value, which is then passed through some functions to produce the output 
- This a single layer perceptron with a single input layer and single output layer

![[Pasted image 20241103113414.png]]

![[Pasted image 20241103113444.png]]
- We'll take several perceptron and stack them into a layer 
- They receive inputs of the nodes from the previous layer and
- Broadcast their results in the next layer 
- **Deep learning:**
	- 4+ hidden layers
	- 1+ hidden layers


![[Pasted image 20241103113635.png]]
- Input layer take in the feature and broadcast the feature values to the hidden layer
- Everything in between the input and output is the hidden layer 
- **Problems to solve:**
	- Classification: put our inputs into a set of classes C
	- Regression: Common to have one node in output, output is just the predicted value
- **Classification:**
	- Process images into animal classification
	- 1 for each output class


![[Pasted image 20241103115618.png]]
- **ANN**: Artificial Neural Network
- Perspective of task decomposition 
	- Neural networks can learn to break up a problem into component sub problems and recognize patterns 
	- Sometimes we need multiple layers 
- ANN learn basic patterns, then more complex ones, and finally recognizable 
- Neural network can learn simple things and build to create better abstractions 

![[Pasted image 20241103120311.png]]
- Neural network are often overparameterized 
- They don't always overfit all the time 


![[Pasted image 20241103120406.png]]
- As we increase the complexity of the model the training goes down meaning that our model can perfectly capture the training data 
- Test risk goes up, more likely to overfit

![[Pasted image 20241103121005.png]]
- Might be computationally expensive, other times not
- We're running into a risk of overfitting from updating too much
- Over parameterization, possible to train it and not overfit by regularization 

![[Pasted image 20241104173635.png]]
- We don't want to make the same updates the same weights across the network
- Want a partial derivative to the error with respect to the each of the weights
## Calculating Error
![[Pasted image 20241104174034.png]]
## How much should we update
![[Pasted image 20241104174048.png]]
- Want to update the old weight by adjusting the weight according to the partial derivative with respect to weight 
- Multiply by the learning rate to control how quickly this update happens 
- **why subtracting?**
	- Partial derivative tells us how the loss will decrease
	- We want to minimize the loss function so decreasing the loss value 

![[Pasted image 20241104174501.png]]
- Apply chain rule 
- The loss function from previous slide is the mean squared error 
- Mean square error is a function of our predictions $(y_i-y_i`)$
$$\frac{\delta y'}{\delta w_{i}} \text{ A function of the current weight value}$$
- Take the derivative of the loss function and get $2(y_{i}-y'_{i})$ which is directly proportional to the error 
- Now compute the network output with respect to weight

## Gradient Descent
![[Pasted image 20241104174900.png]]
- Trying to get to lowest altitude point of the "landscape"
- Take small steps to get to lowest point
- Big steps, can lead to other side of the landscape which make us bounce around and never get to the bottom
- Small steps will get us to the bottom but takes too long

