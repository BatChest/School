- **Review:**
	- Value of the weights control the behavior of a neural network
# Backpropagation Algorithm
- Have weights $w$, activations $n$
![[Pasted image 20241104195138.png]]

# Gradient Descent
- Assume using a neural network for regression
- Two features $x_{1}$ and $x_{2}$ and get back prediction y'
- All possible weights, pairwise connections
- Using sigmoid activation, except for last one (using identity function)
	- Don't want to squash values between 0 and 1
- Establish notations for each of the weights $w$

- **How would we use gradient Descent to find the minimum?**
![[Pasted image 20241104200458.png]]
- Start with some starting point 
- Labeled with star
![[Pasted image 20241104200713.png]]
- Gradient descent is kind of greedy taking steps one after another
- At best find local optima 
- Try multiple initialization, doing the process multiple times
- We're navigating in "weight space" that's in one dimensional

![[Pasted image 20241104202416.png]]
- Its called gradient descent cause we're descending on the loss surface and always following the negative gradient direction where the gradient is just the vector of partial derivatives  
- Nothing changes between where we update two weights and where we update 10 weights

![[Pasted image 20241104204444.png|710]]

![[Pasted image 20241104210311.png|700]]

![[Pasted image 20241107095812.png]]

- Weight space
- Y gradient descent
- Backpropagation
	- Relies on chain rule 

# Vanishing Gradient Problem
![[Pasted image 20241107100452.png]]
- We have zero gradient in two spots in the graph
- Too many $\sigma/dz$ terms that are near zero then you end up with partial derivatives also being near zero
- If $dl/dw$ is close to zero then the weights dont change
- Then the network is not learning anything
- **How to get rid of this?**
 - **Skip connection**:
	- Have two paths in the signal flow of the network
	- Identity function, take it and just add