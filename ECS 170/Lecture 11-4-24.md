- **Review:**
	- Value of the weights control the behavior of a neural network
# Backpropagation Algorithm
- Have weights $w$, activations $n$

![Pasted image 20241104195138](https://github.com/user-attachments/assets/79cb5e37-51fa-4679-9e90-284abce12121)


# Gradient Descent
- Assume using a neural network for regression
- Two features $x_{1}$ and $x_{2}$ and get back prediction y'
- All possible weights, pairwise connections
- Using sigmoid activation, except for last one (using identity function)
	- Don't want to squash values between 0 and 1
- Establish notations for each of the weights $w$

- **How would we use gradient Descent to find the minimum?**

![Pasted image 20241104200458](https://github.com/user-attachments/assets/d483131d-e2f1-4e96-b1a1-68b69f71595d)


- Start with some starting point 
- Labeled with star

![Pasted image 20241104200713](https://github.com/user-attachments/assets/a8176794-4c2c-43bd-948d-2dc43fd1f2c5)


- Gradient descent is kind of greedy taking steps one after another
- At best find local optima 
- Try multiple initialization, doing the process multiple times
- We're navigating in "weight space" that's in one dimensional


![Pasted image 20241104202416](https://github.com/user-attachments/assets/9d5793dd-95b3-4784-8be7-6350da789a5d)


- Its called gradient descent cause we're descending on the loss surface and always following the negative gradient direction where the gradient is just the vector of partial derivatives  
- Nothing changes between where we update two weights and where we update 10 weights

![Pasted image 20241104204444](https://github.com/user-attachments/assets/48fb475f-9dc8-4358-8cc9-58a0dce03e9a)


![Pasted image 20241104210311](https://github.com/user-attachments/assets/5d735464-9429-40d9-8971-d0fddf8270a8)


![Pasted image 20241107095812](https://github.com/user-attachments/assets/beadc912-0c1c-4dae-a4ed-d13a4f130374)


- Weight space
- Y gradient descent
- Backpropagation
	- Relies on chain rule 

# Vanishing Gradient Problem
![Pasted image 20241107100452](https://github.com/user-attachments/assets/1ccc8fb2-200e-4b7a-8184-c7e74fb8dfbf)


- We have zero gradient in two spots in the graph
- Too many $\sigma/dz$ terms that are near zero then you end up with partial derivatives also being near zero
- If $dl/dw$ is close to zero then the weights dont change
- Then the network is not learning anything
- **How to get rid of this?**
 - **Skip connection**:
	- Have two paths in the signal flow of the network
	- Identity function, take it and just add
