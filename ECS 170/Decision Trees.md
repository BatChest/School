## Approaches to Intelligence 
- Intelligence as search through a state space 
- Intelligence as game-playing
	- We're intelligent if we can navigate to goal states efficiently 

**Function Approximation:**
- if we can replicate a data-generating process, based on observations of its outputs 

**Discovering Structure:**
- If we can find a "simple explanation" for seemingly-complex phenomena

**Prediction:**
- If we can say something true beyond what's obvious from direct observation 

## Machine Learning
**Goal:** develop a model of some process based on observations of the process 

- observations == data 
- trying to use the data to create future predictions

### Types of machine learning 

**Supervised ML**
- Have lables
- What is a label?
	- Some variable that is some particular interest to you
	- Can you set it as the prediction target 
	- some are harder to predict

**Unsupervised ML**
- Have no labels 
- You don't have any particular thing that you want to predict but still you can learn how to describe your data in a more interesting way

**Reinforcement Learning**
- Have a function that "labels" word states 


![[Pasted image 20241030131249.png]]
- Decision tree

## The Decision Tree 
**Simple supervise machine learning model**
- map a vector of attribute values (inputs) to a single value (output)
- "attribute values" == "features"
![[Pasted image 20241030131409.png]]
- Goals: 
	- One to put observations into a discrete set of classes 
	- Regression is to predict continuous value 

## Decision Tree: Core Idea
- **Select** an "informative" feature 
	- Want to use nodes in the tree to make the decisions
- **Split** the data based on feature values 
	- Split on the feature values for that node 
	- Start with just one split and one layer of children 
- **Repeat** until the data is separated by output label 
	- Repeat on each of the leaf nodes until we have leaf nodes that are completely separated by the output label 
## Features we should use?
![[Pasted image 20241030132458.png]]

![[Pasted image 20241030132524.png]]
- We can split with patrons which gets us closer to homogeneous subsets 

## Decision Tree Algorithm
![[Pasted image 20241030132606.png]]
- need to figure out the behavior of these two functions, plurality value and importance 
	- **Plurality value**: tells us once we have a leaf node, what's the prediction for that leaf node?
	- **Importance**: tells us how important is this feature to split the remaining data 

## What do with leaf nodes?
![[Pasted image 20241030132811.png]]
- If we're at 50/50 we can just pick one and apply uniformly
- In a homogenous node then we predict whatever that label is 
- Case of mi (not 50/50) we predict the majority
- If it's 50/50 mixed then we do an arbitrary tie breaker and predict the result of that all the time 

## Determining Feature Importance 
![[Pasted image 20241030133033.png]]
- The random variable we are trying to predict is the label 
- It's 50/50 we're highly uncertain about what we should predict 
- If its homogenous we have high certainty 

![[Pasted image 20241030133238.png]]
- derive q
	- Just a rate of positive in our leaf node over the total


- The idea is finding the entropy after splitting 
- Type had 4 distinct attributes which split into subsets (burger, French, Italian,)

![[Pasted image 20241030133602.png]]
- Its the expected reduction in entropy 

![[Pasted image 20241030133704.png]]
- We'll choose the feature that is most informative
- The one that will reduce the entropy the most 

![[Pasted image 20241030133845.png]]
- If you have no examples to learn from → just make a guess based on what was most common before
- If all your examples have the same answer → use that answer (no need to split further)
- If you have no more features to split on → pick the most common answer in your remaining examples
- Otherwise:
	- Find the most informative feature to split on (the one that best separates your data)
	- Create a new branch in the tree for each possible value of that feature
	- For each branch, take the subset of examples that match that value
	- Repeat this whole process for each branch

## Overfitting
![[Pasted image 20241030134156.png]]
- Overfitting occurs when your model tries too hard to fit every single data point perfectly, leading it to learn the noise in your training data rather than the true underlying pattern

- The blue dots are the actual data points, and the green and red lines are different models trying to fit this data.

- As M (the complexity of the model) increases from 0 to 9, you can see how the model (red line) behaves:
	- M=0: Underfitting (too simple, straight line)
	- M=1,3: Good fit (captures the general trend)
	- M=9: Overfitting (model is too complex, fits noise)
- The M=9 graph shows this clearly - the line wiggles unnaturally to hit every point, but would likely perform poorly on new data.

- The green line appears to represent the true underlying function that generated the data, showing what we're actually trying to approximate.

![[Pasted image 20241030134521.png]]

## Pavlov's Dogs
![[Pasted image 20241030135813.png]]
- Is this intelligent?
- Yes in a sense with correlation with the fork and food


## Overfitting
![[Pasted image 20241030140227.png]]
- Bottom tree gets 100% performance 
- What do we have to do to get 100% performance?
	- Make more splits
- Symptom that tends to go along with overfitting is spending a lot of model complexity for little performance improvement 
- The decision tree is overfit because we spent so much model complexity just to one more example

## Preventing Overfitting - Regularization 
![[Pasted image 20241030140441.png]]
- Regularization counteracts the irregularity that comes from being overfit 

## Regularization Methods
- Every time the model decides to add more parameters or increase complexity during training, if we penalize that, we'll end up with a model that's simpler and more regular 
- If we cut back the tree we create irregularity 

## Chi-Squared Pruning
![[Pasted image 20241030140740.png]]
- Technique tries to choose whether to split the tree or not in an informed way in a particular way 
- How small?
	- We'll test for statistically significance on the information gain
	- Want to know whether the tree after the split is better or more before the split 

## Hypothesis Testing 
![[Pasted image 20241030140952.png]]
- Type feature in the restaurant problem leads to zero information gain 

![[Pasted image 20241030141042.png]]
- We're interested in drawing the conclusion that the proportion of the nodes after splitting is different 
- The split made our leaf nodes more homogenous or that we gain more information 

![[Pasted image 20241030141157.png]]

![[Pasted image 20241030141248.png]]
- We see how much info we actually gain and then compare it to this distribution 
- The chance we would see an information gain of that much or more is the area under (blue shaded part on graph)

## Chi-Squared Pruning
![[Pasted image 20241030141532.png]]
- We'll fit the tree until all the leaf nodes are homogeneous 
- We'll fit the complete tree, work backwards from the leaf nodes 
- For each split we'll check whether it reduces the prediction uncertainty

## Pruning vs. Early Stopping
![[Pasted image 20241030141848.png]]
- We can learn relationships using a decision tree with paths that include a split on one feature and then a split on the next feature 
- Chi squared pruning is a regularization technique for decision trees specifically 
- Could also set the max depth of the tree and that would have the function of regularization 
- Regularization applies to all kinds of machine learning algorithms 
	- Just constrains the model and penalizes it for getting too complex 


![[Pasted image 20241030142746.png]]
- Thru training we are narrowing down the space of hypotheses about which model fits the data until you wind up with just one 
- **All possible models**
	- All the different ways you could construct a decision tree for some problem 
	- There are many trees that fit but choose just one 
- **Stationary Assumption:**
	- The likelihood is not changing 
	- The distribution we are sampling from is the same over time 
	- We also make the assumption that the example is not conditioned 

![[Pasted image 20241030180217.png]]
- I.i.d examples mean that you're making this assumption about the samples

## Selecting Models 
**Assume** that the data distribution is stationary and samples are independent -> IID assumption

**Define** the "best model" to be the model that minimizes **error rate** on future unseen data (**the real goal**)

**Error rate** says how often our prediction does not match the truth

**Estimate the error rate** by testing our model on a set of examples not seen **during training or hyperparameter tuning** - the "test set"

How to come up with the test set?
- Often work with what data you have on hand 
- You will need to come up with a way to have some test data even though you have the data already 
- You can split the data, one component for training the models 
- Second component for evaluating the models (**this is the test data**)
- Often split is 80% training, 20% test or 70/30 split 


## Hyperparameters
- Devs are responsible for
- How do we know which splits end up in the trees?
	- Happens automatically through training procedure 
- We choose splits on information gain 
- If using chi-squared pruning we can get rid of splits based on the significance for the information gain 
- An algorithm is choosing the splits for us
- There is a trick tho, we need to set some threshold $t$ for the probability distribution 
- The splits are the parameters of the model that dictate model behavior
- They're what selects this model out of this large space of possible models 
- T as well because the optimization procedure is not going to choose it for us, it's one level above the base parameter, its a hyperparameter 

## Splitting the data
![[Pasted image 20241030181514.png]]
- We need some unseen data that helps us choose the right hyperparameter values
- We'll split the data into test and train and then take that training data and split it again into train and validation
	- This is done multiple times called cross-validation 
- validation is used for setting the hyperparameter values 
- Testing is used only for evaluating the generalization of that model 

![[Pasted image 20241030183613.png]]


