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

![Pasted image 20241030131249](https://github.com/user-attachments/assets/ee589776-e81d-4de6-bc65-2847c3af29ac)


- Decision tree

## The Decision Tree 
**Simple supervise machine learning model**
- map a vector of attribute values (inputs) to a single value (output)
- "attribute values" == "features"

![Pasted image 20241030131409](https://github.com/user-attachments/assets/8d46ec96-b503-44e8-aacf-7ed44c871bef)

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

![Pasted image 20241030132458](https://github.com/user-attachments/assets/1eaaf0e7-03f9-4309-b506-b837f3a85460)




![Pasted image 20241030132524](https://github.com/user-attachments/assets/9befefda-9246-4fb0-aac0-53b59801480b)


- We can split with patrons which gets us closer to homogeneous subsets 

## Decision Tree Algorithm

![Pasted image 20241030132606](https://github.com/user-attachments/assets/a8a191a4-2fe0-443d-b861-248bcd4c3aa4)


- need to figure out the behavior of these two functions, plurality value and importance 
	- **Plurality value**: tells us once we have a leaf node, what's the prediction for that leaf node?
	- **Importance**: tells us how important is this feature to split the remaining data 

## What do with leaf nodes?

![Pasted image 20241030132811](https://github.com/user-attachments/assets/2d95ec44-907d-4eee-a4d4-e98ea81dce61)


- If we're at 50/50 we can just pick one and apply uniformly
- In a homogenous node then we predict whatever that label is 
- Case of mi (not 50/50) we predict the majority
- If it's 50/50 mixed then we do an arbitrary tie breaker and predict the result of that all the time 

## Determining Feature Importance 


![Pasted image 20241030133033](https://github.com/user-attachments/assets/6a767a12-de15-45ff-be37-cdf1a179a29d)


- The random variable we are trying to predict is the label 
- It's 50/50 we're highly uncertain about what we should predict 
- If its homogenous we have high certainty 


![Pasted image 20241030133238](https://github.com/user-attachments/assets/17960577-734f-4c56-bafa-43f81331f214)


- derive q
	- Just a rate of positive in our leaf node over the total


- The idea is finding the entropy after splitting 
- Type had 4 distinct attributes which split into subsets (burger, French, Italian,)


![Pasted image 20241030133602](https://github.com/user-attachments/assets/5b39a2e9-8254-4e7e-87be-9581b715ed81)


- Its the expected reduction in entropy 


![Pasted image 20241030133704](https://github.com/user-attachments/assets/5740c726-d81f-413d-9b16-540646b47b80)


- We'll choose the feature that is most informative
- The one that will reduce the entropy the most 


![Pasted image 20241030133845](https://github.com/user-attachments/assets/b93634b6-3c14-4cd4-8a1c-daa5ab38a0c4)


- If you have no examples to learn from → just make a guess based on what was most common before
- If all your examples have the same answer → use that answer (no need to split further)
- If you have no more features to split on → pick the most common answer in your remaining examples
- Otherwise:
	- Find the most informative feature to split on (the one that best separates your data)
	- Create a new branch in the tree for each possible value of that feature
	- For each branch, take the subset of examples that match that value
	- Repeat this whole process for each branch

## Overfitting

![Pasted image 20241030134156](https://github.com/user-attachments/assets/1515bbca-f601-4786-99cd-06d72dc8c1f6)


- Overfitting occurs when your model tries too hard to fit every single data point perfectly, leading it to learn the noise in your training data rather than the true underlying pattern

- The blue dots are the actual data points, and the green and red lines are different models trying to fit this data.

- As M (the complexity of the model) increases from 0 to 9, you can see how the model (red line) behaves:
	- M=0: Underfitting (too simple, straight line)
	- M=1,3: Good fit (captures the general trend)
	- M=9: Overfitting (model is too complex, fits noise)
- The M=9 graph shows this clearly - the line wiggles unnaturally to hit every point, but would likely perform poorly on new data.

- The green line appears to represent the true underlying function that generated the data, showing what we're actually trying to approximate.


![Pasted image 20241030134521](https://github.com/user-attachments/assets/aab54f1f-4a7d-4b91-95e2-1159df3f8555)


## Pavlov's Dogs

![Pasted image 20241030135813](https://github.com/user-attachments/assets/eedebe7e-570d-47da-9823-9c6ac703b82a)


- Is this intelligent?
- Yes in a sense with correlation with the fork and food


## Overfitting

![Pasted image 20241030140227](https://github.com/user-attachments/assets/74a87fa2-d4ed-4da1-924f-acf2a64390ee)


- Bottom tree gets 100% performance 
- What do we have to do to get 100% performance?
	- Make more splits
- Symptom that tends to go along with overfitting is spending a lot of model complexity for little performance improvement 
- The decision tree is overfit because we spent so much model complexity just to one more example

## Preventing Overfitting - Regularization 

![Pasted image 20241030140441](https://github.com/user-attachments/assets/0a656110-ec0f-41ef-a4da-26d752b3fd22)


- Regularization counteracts the irregularity that comes from being overfit 

## Regularization Methods
- Every time the model decides to add more parameters or increase complexity during training, if we penalize that, we'll end up with a model that's simpler and more regular 
- If we cut back the tree we create irregularity 

## Chi-Squared Pruning

![Pasted image 20241030140740](https://github.com/user-attachments/assets/bdd4d7bf-7696-4a34-9b05-c111eacc9597)


- Technique tries to choose whether to split the tree or not in an informed way in a particular way 
- How small?
	- We'll test for statistically significance on the information gain
	- Want to know whether the tree after the split is better or more before the split 

## Hypothesis Testing 

![Pasted image 20241030140952](https://github.com/user-attachments/assets/d36cffd5-2ebe-4f28-80d6-2f8ee957c5a9)


- Type feature in the restaurant problem leads to zero information gain 


![Pasted image 20241030141042](https://github.com/user-attachments/assets/0e446ed7-acd5-409b-ad77-f05ec2c4ff08)


- We're interested in drawing the conclusion that the proportion of the nodes after splitting is different 
- The split made our leaf nodes more homogenous or that we gain more information 


![Pasted image 20241030141157](https://github.com/user-attachments/assets/019c65a3-01cd-4efd-948b-42f0705907a0)



![Pasted image 20241030141248](https://github.com/user-attachments/assets/936b98b1-8c6d-4a72-8fc5-a2ea9909a531)


- We see how much info we actually gain and then compare it to this distribution 
- The chance we would see an information gain of that much or more is the area under (blue shaded part on graph)

## Chi-Squared Pruning
![Pasted image 20241030141532](https://github.com/user-attachments/assets/5ab38090-b3ec-4181-af59-2b01bca869d2)


- We'll fit the tree until all the leaf nodes are homogeneous 
- We'll fit the complete tree, work backwards from the leaf nodes 
- For each split we'll check whether it reduces the prediction uncertainty

## Pruning vs. Early Stopping
![Pasted image 20241030141848](https://github.com/user-attachments/assets/f0a1fc07-7bfd-4591-be89-458f43d6fba2)


- We can learn relationships using a decision tree with paths that include a split on one feature and then a split on the next feature 
- Chi squared pruning is a regularization technique for decision trees specifically 
- Could also set the max depth of the tree and that would have the function of regularization 
- Regularization applies to all kinds of machine learning algorithms 
	- Just constrains the model and penalizes it for getting too complex 


![Pasted image 20241030142746](https://github.com/user-attachments/assets/bdd0cfe3-a0ad-4d16-8112-65c873283ba8)


- Thru training we are narrowing down the space of hypotheses about which model fits the data until you wind up with just one 
- **All possible models**
	- All the different ways you could construct a decision tree for some problem 
	- There are many trees that fit but choose just one 
- **Stationary Assumption:**
	- The likelihood is not changing 
	- The distribution we are sampling from is the same over time 
	- We also make the assumption that the example is not conditioned 


![Pasted image 20241030180217](https://github.com/user-attachments/assets/37f677ec-50ed-447d-901e-07b06c3b66a9)


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
![Pasted image 20241030181514](https://github.com/user-attachments/assets/d90bf592-2db9-42a9-a0b3-f5dc9f0071f6)

- We need some unseen data that helps us choose the right hyperparameter values
- We'll split the data into test and train and then take that training data and split it again into train and validation
	- This is done multiple times called cross-validation 
- validation is used for setting the hyperparameter values 
- Testing is used only for evaluating the generalization of that model 

![Pasted image 20241030183613](https://github.com/user-attachments/assets/b91ab2d0-26bb-4500-8f50-9e26e691e435)



