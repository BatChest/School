# Convolutional Neural Networks
## Core Concepts
- Specialized neural networks designed primarily for processing grid-like data (images, pixel arrays)
- Inspired by biological processes in the visual cortex
- Main operations: Convolution, Pooling, and Fully Connected layers
## Key Components
### Convolutional Layer
- Applies filters/kernels to input data
- Features:
    - Local connectivity
    - Parameter sharing
    - Translation invariance
- Detects patterns: edges, textures, shapes
### Pooling Layer
- Reduces spatial dimensions
- Types:
    - Max pooling (most common)
    - Average pooling
- Benefits:
    - Reduces computation
    - Controls overfitting
    - Provides spatial invariance
### Fully Connected Layer
- Usually at the end of the network
- Performs classification based on features extracted by previous layers
## Limitations
What to do about HD-Images 
- 4k resolution
	- Each pixel has an RGB value
	- 3840* 2160 * 3 = 24883200 input neurons
- We don't need multiple layers
- **Translation Invariance**
	- Image of cat is still a cat even when you move it around
	- Translated the content of the image and the image is invariant to that translation 
- Some of these pixels are related 
- Create a new kind of neuron, a convolutional filter


- Input of our network architecture has as many neurons as we have features in our data 
	- If we have 2 million features then we have 2 million input nodes 
	- If we have 2 million nodes then we have 2 million weights going from those nodes to any subsequent layers 
	- More parameters = more risk of overfitting
- We're relying on early layers to learn something informative and useful for the later layers 
- Nodes are coupled to locations 


## Convolutional Filter
- It accepts some small region in the input image
- Will apply the same convolutional filter to all the locations of the image
- Once we focus on one part of the image (ex: eye of a cat)
	- If that filter has learned a representation like activate itself on top of an eye then we'll get eye activation 

![Pasted image 20241110134553](https://github.com/user-attachments/assets/de14bb54-50b3-4c99-aa9a-db1ec0f91ce2)


- Left side assume its a zoomed part of an image
- On the right is our filter which is defined as 5 by 5
- Black squares have value of 0 and white squares have value of 1
- If we do some elementwise multiplication with the pixel values from the left and right 
	- If the values are similar then we should get a high score overall 
	- If values differ then we should get a low score 

![Pasted image 20241110134608](https://github.com/user-attachments/assets/39a1fc98-4dc9-4029-9737-c58356bf72ce)


### More Convolutional filters

![Pasted image 20241110134646](https://github.com/user-attachments/assets/0929163f-3012-4d9b-b07e-daf89cde9fbc)


- Identity filter
	- Does nothing 
	- take the 9 values and multiply them by the underline value
	- Then we take an average 
- Edge detection
	- Define filters that have high activation on regions of the image with high contrast 
- Sharpen:
	- More fine details 
- Blurry:
	- Fine detail is loss
	- moving average
	- uniform weights 
	- Smooths out the image with taking the average of the values
- Gaussian blur:
	- Gaussian distribution 
	- More intense in the middle and less intense in the outer areas 
# Standard Deep learning (For Images, Sound, Etc)

![Pasted image 20241110135026](https://github.com/user-attachments/assets/9cc7f322-16ff-409a-8d51-f84b55d29d1b)


- Define convolutional layers as a set of layers 
- One filter that have some weights 
- We'll have a single filter and one layer will have multiple filters 
	- Filter 0, 1, 2
	- If the filter size is 3 by 3 has 9 values in it 
	- We'll make these values in trainable parameters for the network 
	- Network will learn what network I should use at each layer 
	- Weights in the filter are adjustable
	- If we have multiple weights in terms of producing the filter map, each one will **result in some matrix** 
	- There will be a matrix for each filter and be different as the network learned different weights for each of the filters 
	- Stack them and talk about tensor(matrix in more than one dimension) 
	- weights in the filter are learned
- In the above image we have filters that are 11 by 11 where each filter map is 55 by 55 where we have 96 filters 

![Pasted image 20241113212538](https://github.com/user-attachments/assets/188607fa-39a4-4678-b0fd-70e902a98b12)



![Pasted image 20241110143856](https://github.com/user-attachments/assets/86060b27-8db9-41db-ad97-1181ef15e949)


- One dimension
- Here we have an input in the grey line
- Vertical axis is signal intensity 
- One row of pixels at the top of the image
- Filter contains of 1/3, 1/3, 1/3
- This a uniform blur filter
- What happens when applying it

![Pasted image 20241110144024](https://github.com/user-attachments/assets/eda17a04-cf65-45af-8246-ba0958a93e21)


- The first location we can apply the filter with the first two 1/3 values
- It gets multiplied by intensity 10 
- We take the convolutional filter and slide it over the input in all the locations where it fits
- If we plot these values we get the following

![Pasted image 20241110145944](https://github.com/user-attachments/assets/50d8233d-26db-4c05-8868-5597bd9ac962)


- What do you notice about the f and y?
- The sharp dip have been smoothen out 
- Y bears some similarity with more smoothness
- The equivalent operation in 2 dimensions is by sliding all our filter along the horizontal axis

- Convolution in 2d we have 4 by 4 input and 2 by 2 filter 
- We'll get a 5 by 5 output by zero padding
- **zero padding**: add zeros around the margin to be able to process the edge of the input with the convolution concept
- When to apply it: practitioner choice, hyperparameter
- The weights in our filter are learned


- **Gradient descent update rule**:
	- Have some old value of the weight by taking a step in the negative gradient 
	- We take the partial derivative of our loss function with respect to the weight multiply by learning rate 
	- Subtract from original value of the weight 
- Convolutional neural networks are trained the exact same way 
- We have an extension of back propagation to CNN's

## Convolutional Filter Again
- One common we have is classifying images
- We want to get the probability of the image being a cat and image not being a cat
- Want to condense our output down to two vectors 

![Pasted image 20241110150833](https://github.com/user-attachments/assets/93f5fc92-027b-4cd6-a52a-ea694c7a76b1)


Convolutional layers are a set of filters that are where each of them get applied to the input 
- Each results in a matrix in the filter map
- We can stack up the filter maps of all the filters to produce some output volume
	- We can do this in series 
- Eventually get down to a 2 vector
	- Unravel the values 
	- Take the values and turn into one long vector
	- Choose a shape of a fully connected layer

- What it means to unravel:

![Pasted image 20241114091018](https://github.com/user-attachments/assets/94acc5a6-56e0-4ec9-ae8e-bf4f33658be7)

  

## Pooling
Simplifying data by grouping together nearby pixels
- Max pooling 
	- Over a n,m area, pixel is the max

![Pasted image 20241110152849](https://github.com/user-attachments/assets/0b17db5f-eb40-4d55-8d05-6390a2d1e1d4)


- If we have a 2 by 2 regions
- We can reduce to single pixel by 
- **Average pooling:**
	- Over n,m area, pixel is the average
- **Min pooling**
	- Over a n,m area, pixel is the average 

![Pasted image 20241110153022](https://github.com/user-attachments/assets/fc70a99f-ca66-483e-8dc6-6a9553d32088)


## Dropout Layer

![Pasted image 20241110153040](https://github.com/user-attachments/assets/1e7fd696-bcb5-4723-bf4d-2658818aa9ec)


- At random with some probability we will remove the post activation to be process by the next layer
- Intuition: forces the network not to rely on any single neuron too much 
- It acts a form of regularization 
- becomes more difficult for the network to learn some kind of some substructure to really finely tuned to this specific training data 
- In dropout in each forward pass we randomly select like 10% to have their outputs set to 0 
- They don't contribute to the error during the prediction 
- Also weights that are the outputs don't get updated 
- Do one step of gradient descent 
- Other step we do some other random subset of nodes to have their output zero


![Pasted image 20241110153522](https://github.com/user-attachments/assets/3a294042-d787-4c99-b8b0-9bdb2272dee8)
![Pasted image 20241110153558](https://github.com/user-attachments/assets/1e55a2e9-f948-4ca2-9035-eb253ca37382)


- Another instance of representative learning 
- Early layers identified kind of salient features in the image 
- having some type of score of what's in the image 

![Pasted image 20241110160439](https://github.com/user-attachments/assets/e0d29cb4-97eb-43c7-88be-d019ee11c92e)


- Sequential dependencies

# Recurrent Neural Networks (RNNs)

![Pasted image 20241110160459](https://github.com/user-attachments/assets/3be0d3b4-9f62-41b6-9b11-2894d1f72707)


- Main idea:
	- Sequential data and sort of dependents we want to process each step in the sequence in series 
	- Trying to predict the weather, design some neural network that takes the entire sequence history as its input and spits some output 
	- As input size grows our network size grows where we need to expand the network bigger and bigger to accommodate longer history
	- We only use the full network when using all the data
	- **Have one neural network processing one of the step**
		- We're going to design a network of the same fashion 
		- At each step we have some vector input 
		- Have some network that accepts it and produces some hidden representation 

![Pasted image 20241114092509](https://github.com/user-attachments/assets/cf61ba8c-058e-4a42-a256-d71af303eceb)


- We can reuse the network at different time steps 
- Statistically size neural network that can handle dynamically sized inputs
- we set up some hidden value for the initial state usually a vector of all zeros 

![Pasted image 20241110161348](https://github.com/user-attachments/assets/439176dc-bd80-4af7-baa2-5421e0f8d548)


- **How do we get predictions**
![Pasted image 20241110161705](https://github.com/user-attachments/assets/aa084895-afa2-44ff-971c-e6a51a3800e3)
![Pasted image 20241110161851](https://github.com/user-attachments/assets/6994fff6-b21e-4d5c-a755-9f1d185a60ae)
![Pasted image 20241110161921](https://github.com/user-attachments/assets/a2eeb59d-6f8e-4948-b95e-6a4d586ab168)

- Take pixel values and turn to one long vector

## **Issues:**
- All context embedded into the vector 
- Can only look so far (usually sequence of about 2, depends on data)

![Pasted image 20241110162026](https://github.com/user-attachments/assets/93283c51-9194-4f33-864a-a99e498cc5e1)


- We have some hidden vector, v
- It has all the information that was in step 3 and to understand what was going in steps 1 and 2
- If we have inputs that are 100 steps long then we're asking the network to squeeze more and more information through this narrow bottleneck

- We can add another hidden state to fix this problem

![Pasted image 20241114093219](https://github.com/user-attachments/assets/8a93f847-dccc-446b-ba23-d8a0d150c9a8)


- Network can pass info through this hidden vector
- Behavior is similar to a cache 
- Network can pass information through this hidden vector

**Benefits:**
- Overcome vanishing/exploding gradients a bit
- Has a window of about 5

- **vanishing**
	- End up with terms that is close to zero
	- Network wouldn't learn
- We can have some hidden vector and sideload each information from each step
- We provide residual connections to get rid of vanishing 

**Drawbacks:**
- Many more parameters 
- Hidden state may not be big enough 


![Pasted image 20241110162626](https://github.com/user-attachments/assets/082c7a96-65e1-48ca-a3b6-a5b616e83217)

- Combine both predictions then get some final predictions 
- When doing a forward pass, input is a series of vectors
- Have one vector in each step in some sequence 

## Core Concepts

- Designed for sequential/temporal data
- Has "memory" of previous inputs
- Processes sequences one element at a time
- Can handle variable-length sequences

## Key Components

### 1. Hidden State

- Carries information from previous time steps
- Acts as network's memory
- Updated at each time step

### 2. Types of RNNs

1. Simple RNN
    - Basic form with single hidden state
    - Suffers from vanishing gradient problem
2. LSTM (Long Short-Term Memory)
    - Has gates: forget, input, output
    - Better at capturing long-term dependencies
    - More complex but more effective
3. GRU (Gated Recurrent Unit)
    - Simplified version of LSTM
    - Has reset and update gates
    - Often similar performance to LSTM

## Common Applications

- Natural Language Processing
- Speech recognition
- Machine translation
- Time series prediction
- Music generation

## Key Differences Between CNNs and RNNs

### CNNs

- Spatial relationships
- Parallel processing
- Fixed input size
- No temporal memory

### RNNs

- Temporal relationships
- Sequential processing
- Variable input size
- Has memory of past inputs

## Common Exam Topics

1. Architecture Components
    - CNN: Convolution, pooling, filters
    - RNN: Hidden states, gates, memory cells
2. Use Cases
    - CNN: Image-related tasks
    - RNN: Sequence-related tasks
3. Advantages/Disadvantages
    - CNN: Good at spatial features, requires large datasets
    - RNN: Good at sequential data, can have gradient problems
4. Training Considerations
    - CNN: Number of filters, kernel size, stride
    - RNN: Sequence length, hidden state size, gate types
