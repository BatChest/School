# Recap
- Most popular AI programming tools based on large language models (LLMs)
- LLM's are deep neural networks trained on large text datasets collected from the internet, crowd workers, and other sources 
- LLM's approximate a conditional probability distribution over the next word(s) in a sequence
- This simple learning mechanism leads to surprising "emergent" capabilities 
	- Code completion, summarization, chatbots, translation


- Model performance tends to scale with:
	- Model Size (number of parameters)
	- Training Data (Number of tokens)
	- Training data quality 
	- Compute

- Language models are conditional probability distribution of words 
- The input to a language model is a sequence of "tokens"
- **One token generally corresponds to 4 characters** of text for common English text
- **Tokenization** is the process of breaking down text into these smaller units (tokens) for processing by the LLM. 
	- For example, the sentence “The cat sat on the mat” might be tokenized into the following tokens: (“The”, “cat”, “sat”, “on”, “the”, “mat”).
- **Tokens** in the context of Large Language Models (LLMs) refer to the smallest units of text that the model can understand and generate. 
- A token can be as short as one character or as long as one word, depending on the language and the specific tokenization method used.


# Strength and Weakness
## Strengths:
- Complex completions
	- Multiple lines of code
	- Calling custom functions
- Error correction
- Explanation/interactivity
## Weaknesses
- No guarantee of correct output 
- Unpredictability
- Potential for subtle bugs 

![Pasted image 20240423171436](https://github.com/BatChest/School/assets/90287766/270f0403-83fc-4d34-94c0-475ee181b3b6)


- Since the LM is just a conditional probability distribution, the input "context" makes all the difference 

- What kind of context is useful?
	- High level problem statement 
	- Specific task description
	- Libraries Used
	- Style/Paradigm pointers ("Only use functional React")
	- Implementation of a specific function
	- What the code should do 
	- What the code is doing currently 
	- Specifications of inputs and output types 

![Pasted image 20240423172007](https://github.com/BatChest/School/assets/90287766/7c228931-4568-49f8-bbd0-4bd0b4aa25f4)

- What's important about this figure?
- It shows the current machine learning landscape 
- The idea is that we have these large models that we pre train on basically a big chunk of the Internet 
- Nobody wants to reduplicate that work 
- But we want customized behavior 
- We can do something called **fine tuning**
	- Taking an existing model and customizing it to your data set
	- You don't need as much data as it was required originally
	- If the original dataset is like 1 trillion tokens, you might only need like a few tens of millions of tokens to do some fine tuning 
- This makes it hard to trace intellectual property
- Security vulnerabilities as well 

# Privacy and Security Concerns 
- In industry settings, code is often proprietary
- Revealing proprietary code can have negative consequences

## Considerations:
- Does an AI-enabled editor send your code to a server?
- Are your interactions with the editor logged?
- What happens to the data? Is it deleted after use?

- People are copying company code into chatGPT and so that private code is then being saved into it's data base 

# LLM Thought-Action-Observation Agents (AI Agents)
- read current context 
- thought: generate description of a plan
- action:
	- generate text
	- generate code
	- "tool call"
		- Special syntax
	- request for user input (special syntax)
- **Observation**: if the generation contains a tool call, run the toll and put the result in the context 
## AI Agents vs. Chatbots
The main difference between the two is the **Autonomy**
- In terms of chatbots you are the driver/editor and have to babysit the chatbot to check whether the output is correct 
- AI agents take the LLM that can generate some nice completions and turn it into a system that sort of autonomously work on tasks by itself  
- Below is schematic how this sort of AI agent system would work
![Pasted image 20240423173421](https://github.com/BatChest/School/assets/90287766/29effd56-c2e1-40e6-aab7-27943128db55)
- You have a high level assignment like adding a sign up button to a home page
- You'll get some task list like needing to define the CSS style for the sign up button and define the react component and writing unit tests for the button 
	- These are specific things that need to be done for the general task to be completed 
- Each of those tasks can passed off to a task agent to work on them
	- This sub agent is working in a loop where it writes some code and then can evaluate what that code does in sort of a sandbox execution environment 
	- It does this relatedly until it gets closer to solving the sub tasks 
	- When it solves the subtask it can report to the main system that this item number on the task list has been completed 
- This is just a sample architect of AI agents 

![Pasted image 20240423174824](https://github.com/BatChest/School/assets/90287766/67f3f8c7-2ee8-431d-94ce-279d446c27d0)
- How the internet is being affect by AI chatbots


# Benchmarks
- there is some evaluations protocol that is standardized and tells you how well your system is performing 
![Pasted image 20240423175135](https://github.com/BatChest/School/assets/90287766/087008f4-f6d2-4152-ae77-d28c72b93fc0)

- Economics and working conditions of AI training 
- Copyright, intellectual property




