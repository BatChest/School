## AI For Code
- Focused on creating machines that can think
- **Marvin Minsky** one of the grandfathers of AI

## Machine Learning
- Subset of AI that focuses on creating algorithms that can learn from and make predictions based on data 
- No explicit programming, just give the machine data and let it learn from it
![[Pasted image 20240423160314.png]]
- Machine Learning is a subfield of AI that makes computer to be smart using data

## Neural Networks 
- Neural networks are a type of machine learning algorithm 
- Consist of many layers of nodes, each layer connected to the next
- Trained by adjusting the weights of the connections between nodes 
### Making Predictions with neural networks 
- Each node in each layer computes a weighted sum of the outputs from the previous layer, then applies a non-linear activation function

## Increasing Compute
- A report from Epoch AI divides AI into three eras
	- Until 2010, compute on AI kept pace with Moore's Law 
	- Since 2010, AI compute roughly doubles every 6 months 

## Predictable Scaling
- Training perplexity for "foundation models" decreases predictably with compute
- As you add more compute and more data to your neural network training the performance on the training set improves of a predictable fashion 
- You want your losses to be lower which means better predictability 
- There's a predictable return on investment for mode data and more compute 

# Language Modeling 
- Idea behind neural network modes is to model how human language works using a neural network 
- A way to do this is try to predict the probability that a certain word will follow any other sequence of words 
- Markov Assumption:
	- Assumption about statistical dependence 
	- For any sequence of words 
	- Ex: "I went to the store"
	- Each word could be presented as $W_i$
	- The probability for all: $P(w_{1},...,w_{5})$

![Pasted image 20240423161903](https://github.com/BatChest/School/assets/90287766/6ac982e8-3cbc-48ea-884a-1aea9e109225)
- Putting in some information into your network 
- You get a kind of hidden representation of H
- Meaning a vector of values that represent what's going on in this sentence, network gives you a plausible continuation based on that hidden state  
- Idea: compressing all the stuff that you've seen so far, (long sequence of words) into one vector 
- And from that vector you try to predict what's the most likely next word that's going to follow 
- Get a probability distribution over all the words in the vocabulary 

## Why we care about language modeling?
- It assigns probabilities to a sequence of words 
- The idea is that you can predict a likely next sequence of words from the words that you put in 
- You can leverage this format to do all kinds of tasks 
	- Trying to generate a book in a style of a particular author you might put in the author as part of the conditioning, part of the input words
	- You'll get back a document in that style 

## What does the data look like?
- If we're going to train some language model we need to think about where we're getting the data 
- We'll collect a lot of sentences in English or a variety of languages 
- We apply web-scraping to large swaths of the Internet and collect all of those pages together 
	- What happens:
		- Take a sequence of words
		- Pick a sentence in our training data that has millions of sentences
		- We look at one of them 
		- And put it is in our input to our neural network 
		- Then try to get it to predict our next word 
		- It'll produce a probability distribution from the vocabulary and we want to look at the probability for the next word 
		- ![Pasted image 20240423162958](https://github.com/BatChest/School/assets/90287766/7697cc54-b409-46a8-bbfe-6ef59ba41cfa)
		- You can model that's good at this text completion task 
		- Writing in a couple of sentences and then it writes some plausible continuations for the sentences 

## Decoding
- Often we want to generate not just one next word but a sequence of next words 
- Sometimes the sequences of going with the next immediate word  that's more likely is not the best option
- We want to generate not just a word that's likely but a whole string of them 
- If the vocabulary size is 50,000 then we're dealing with a $50,000^4$ search space 
### Beam Search
- We'll only consider the two or three most likely next completions 
- We'll expand a word like say the next word is beer, then the words that can follow that could be "drink" and "I"
- If its "I" then words that can follow that are "drink" and "like"
- We kind create a live hypothesis of what the sentence could be and trim down the rest
- Ignoring the the unlikely words from the search space 
- It's a compromise from an exhaustive global search and a greedy search  

## ChatGPT
![Pasted image 20240423164240](https://github.com/BatChest/School/assets/90287766/1143a275-dfb2-4b8e-ba39-a634d57abc35)
- Rough rough drawing of how ChatGPT is set up or chatbots in general
### Limitations 
- When asking AI to help write code for you there are limitations?
- Sometimes you have projects that have multiple files and you don't want to write every single bit of code into ChatGPT 
- What are some ways to lessen the load of information:
	- Only use the relative information 
- If we do this what is the problems we could run into:
	- Too much data
	- ChatGPT becomes slower/longer the process
	- Language models have context tokens 
		- The maximum number of tokens that it can accept at a time 
		- If you paste in 3 python files it'll fit in the context window
		- If you paste in 300 python files, you'll exceed the context window 
			- The **context window**:
				- in Large Language Models (LLMs) refers to the amount of input text the model takes into account when predicting the next token. 
				- It’s essentially the “memory” of the model, representing how much of the past input it can consider when generating an output.
		- The cost of running a language model tends to scale with the amount of words you tend to put in
		- If you pay for the API, you pay per token, like per word you put into the model 
		- If longer prompts the models sometimes get confused in a way, they loose coherence over longer sequences 
	- Ways to reduce volume:
		- Split the project into smaller tasks
		- Edit history
	- The more creative we are with our prompts the more it'll be able to help you

# Summary
## AI
- Multi paradigm field 
- but the most recent approach that has been worked is machine learning 
- Machine learning learns from data 
- One popular machine learning algorithm is the neural network
- Investments in neural networks and training bigger and bigger ones has increased since 2010
## ChatGPT/Language Models
- LLMs are type of artificial intelligence model that have been trained on a vast amount of text data. 
- They are designed to generate human-like text based on the input they’re given.
- The functionality of LLMs revolves around understanding and generating text
- They are large neural network models 
- Train on data from all over the internet 
- Data includes examples of people helping each other with code and that's where the system get its coding capabilities 
- There's no guarantee of correctness that's intrinsic to the system 
- Just cause it looks at all of this data doesn't mean its all correct
- There's wrong code examples 
- They are used for answering questions, translations, content creation(images), code creation

# Conditional Language Modeling
**Conditional language modeling** 
- task in natural language processing that involves generating text given some condition or context. 
- In the case of Large Language Models (LLMs), the condition is typically a sequence of text that the model uses as a prompt to generate a continuation
- For example, if you provide the beginning of a sentence as a condition, such as “Once upon a time”, the LLM will generate text that logically or stylistically continues from that starting point, like “Once upon a time, there was a brave knight who…”.
- makes its predictions based on the statistical patterns it learned during training. 
- It estimates the probability of each possible next word based on the given context and selects the word with the highest probability.

**Next word prediction** 
- involves predicting the most likely next word in a sequence of words.
- Given a sequence of words, the LLM estimates the probability of each possible next word in its vocabulary based on the given context (the sequence of words it has seen so far). 
- The word with the highest probability is selected as the next word
- For example, given the input “The cat sat on the”, the LLM might predict “mat” as the next word because, in its training data, “mat” frequently followed the sequence “The cat sat on the”.


