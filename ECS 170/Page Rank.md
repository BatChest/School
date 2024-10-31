## Information Retrieval 
- You just filter documents that contain the user query words 
- Find the documents that are relevant to a user query
- Consider the set of documents that contain all the words in the user query
- "Retrieve and Rerank", from 1 million documents, find the most relevant 100 then rank the 100 according to some ranking function 

## PageRank
- We can teach the documents we have as a directed graph 
- We can just total the number of links going to a web page as a measure of its importance 
	- **Problem**: create a bunch of fake web pages that can all point to a single node making a certain website the most popular one 
	- **Fix**: It doesn't matter how many people are pointing to you but if they are popular themselves 

Let $L_{ij} = 1$ if webpage $j$ links to webpage $i$ (written $j \rightarrow i$) and $L_{ij} = 0$ otherwise 

![Pasted image 20241029171016](https://github.com/user-attachments/assets/068b106d-361b-4a1f-968d-603e700fc27f)



![Pasted image 20241029171139](https://github.com/user-attachments/assets/ca707854-05f8-4a8b-8298-07ef570bc6f9)


- Each element in p represent a pagerank score for each website 
- Eigenvalues: the eigenvectors are vectors where if you multiply by the matrix all it does is scale the vector 

- Matrix may not have a solution that exists and might not be unique
- We want a ranking of these web pages 
- If there are two different rankings then that makes things harder 
- We want to know that there is a solution and a unique one 


**Theorem:** If markov chain is **strongly connected**(any state can be reached from any other state) then the stationary distributions exists and is unique 

## **Stationary distribution:** 
- How likely am I to be in any state when I start my process, how likely am I at to be at a state in the beginning 
- Certain kind of processes have stable long term behavior, after a while they just end up revisiting the same set of states with the same frequencies 
- Stationary distribution might be equivalent to the page rank so there's the interpretation that broken rank is the proportion of time a random surfer spends on web page if you let them go forever  
- It's stable (doesn't change) if you start at some state distribution and take a transition given by the transition matrix you should end up in the same probability distribution 

## Why BrokenRank is broken
- If we have a markov chain that's not strongly connected there still might be a stationary distribution, we can still come up with a page rank vector but it's not unique 
### Example:

![Pasted image 20241029173929](https://github.com/user-attachments/assets/ecff880e-2e77-4777-ab88-a1791200123b)


## Modification to BrokenRank
- We're going to add a small epsilon
$$p_{i}= \frac{1-d}{n}+d\sum\limits_{j=1}^{n}\frac{L_{ij}}{m_{j}}p_{j}$$
where $0 < d <1$  is a constant 
In matrix notation:
$$p = (\frac{1-d}{n}E + dLM^{-1})p$$
where E is the $n \times n$ matrix of 1s, subject to the constraint
$$\sum\limits_{i=1}^{n}p_{i} = 1$$

- We have effectively turned the graph into one giant component 
- The paging vector P has become unique 

![Pasted image 20241029174553](https://github.com/user-attachments/assets/8733c866-8611-46ca-ac23-8d16c2e7c24f)


## Computing PageRank vector

![Pasted image 20241029175113](https://github.com/user-attachments/assets/261ea6ed-1bad-429e-b963-09fa108428fa)


- A in $A_{p}^{(0)}$ is the transition matrix and the vector P that are looking for is the stationary distribution 
- You can start from anywhere and end up in a stationary distribution just by making transitions over and over again 
- We'll apply matrix A to any initial distribution and keep going and if our graph is strongly connected then we'll end up in $p^{(t)}$

![Pasted image 20241029180327](https://github.com/user-attachments/assets/46e9a716-88f8-4754-90e2-8df9792b0928)


- Sparsity, a few webpages links to only a few other web pages 
- There are not many iterations required for this multiplication if A has a large **spectral gap** 
	- spectral gap, difference between the first and second largest eigen values 

## Relate to searching the internet
- We're going to compute the Page rank vector once
- Compute vector P and save it somewhere 
- Then search query where we can do the retrieve step which is find all the pages on the internet that have the query terms 
	- Gives us a smaller group of documents that we need to rank somehow 
- Sort the document by page rank and then the first page of the results will just be the top $K$ results from the sorted list 

## Variations to Page Rank
**Hubs and authorities**: 
- uses link structure to determine who hubs and authorities are 
- Uses link structure 
- Hubs contribute more to the score

**Intelligent surfing:** 
- Pointing surfer towards textually relevant webpages 
- They are equally likely to go any outgoing link 
- It will select the links based on what they are trying to do 

**Trust Rank**:
- Pointing surfer away from spam
- Avoid clicking on the spam



![Pasted image 20241029182055](https://github.com/user-attachments/assets/bdc630ec-7b72-4836-a853-2951272b2716)


**Markov Chain**
- Matrix representation that captures a process on the graph and by processes, we're moving from one node to another 
- Captures the probabilities associated with those state transitions in a transition matrix 

**Initial distribution**
- The initial probability of being in each state

**Stationary distribution**:
- Some probability being in a given state in the long run 
- captures the long run stable behavior 
- It's important as it gives us a matrix LM inverse and the stationary distribution is an eigenvector of the transition matrix with eigen value 1 
- Viewing it as an eigenvector problem helps us find guarantees on the uniqueness of a solution 

