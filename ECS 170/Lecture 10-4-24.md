# Search Problems
## Towers of Hanoi Myth
- Disks are stacked on one needle in decreasing order of size 
- Move the entire stack onto another needle, moving only one disk at a time and never placing a larger disk onto a smaller one
- Due to exponential growth of moves required, even at a rate of one disk per second, the task would take over 500 billion years to complete

## State Graph
![Pasted image 20241008151445](https://github.com/user-attachments/assets/d7161262-3251-4342-8b38-d718083ccd26)

- State graph for all the possible connection to get the one ring to peg C

![Pasted image 20241008151531](https://github.com/user-attachments/assets/4d65518a-b12d-470b-95f3-534c9637e832)

- Here are the legal rules for moving the rings from on peg to another
- The yellow highlighted states show the 2 rings stacked up on a single peg


![Pasted image 20241008151807](https://github.com/user-attachments/assets/0b70013f-e830-4032-a46a-556e762d97fe)

- The solution to the problem is a path in the graph
- We need to find a sequence of moves to get from the start state to the end state 
- The sequence of moves is the subset of the edges in the graph
- Should be a path 

- The efficient solution would be starting from any of the highlighted states and just go diagonal (straight line down)

## Formalizing a Search Problem
- **State Representation**: How do we write down the current state?
- We can write it in plain English, draw out a diagram, or data structure

ENGLISH: "Ring 2 is on pole a, Ring 1 is on pole b. No rings on pole c"

![Pasted image 20241008152453](https://github.com/user-attachments/assets/e4e72dc1-748d-454d-bd9f-a44f5586ced8)


Data structure
```python
{"a": [2,], "b": [1,], "c": [],}
```

## State Space
- Set of all possible states

![Pasted image 20241008151807](https://github.com/user-attachments/assets/0bea0bc0-0cbe-4aeb-aadd-e07854bd0c4b)

- All the nodes in this diagram is the state space 


- **Actions**: What can we do from some state S?
	- Basically a set of symbols
	- Ex: Moving one of the rings from peg a to peg c
- **Transition Model**: What does each action do?
	- What happens when an action is applied 
	- Function that maps from state action pairs to resulting states 
- **Action Cost Function**: How much does each action cost?
	- It takes in an action and tells you how expensive it is to perform it
- **Initial State**: Where we start out
	- Ex: start with all three rings on peg a
- **Goal State:** Where we want to end
	- Ex: all three rings on peg c


## Abstraction 
- Avoid the messy details, focus on what matters

## Tile Puzzle

![Pasted image 20241008154140](https://github.com/user-attachments/assets/ba443724-af25-4261-9f44-67868b2ed5b4)

- **State Representation**: 3D array or one dimensional list
- **State Space:** The 8 spaces in the array
- **Actions**: Moving up, down, left and right if there is an empty space to move to
- **Transition Function**: Functions that accepts an array and select tile 6 we should return a new 3x3 array 
- **Initial state:** Scramble tiles that are not in order
- **Goal State**: Tiles that are in order in ascending order 
- **Action Cost**: Uniform, cost 1 

## Route Finding Problem
- **State Representation:** Weighted graph, Adjacency matrix, the current location of the agent
- **State Space**: The set of all possible locations that the agent can reach
- **Actions:** The available movement options (highway connections between cities)
- **Transition**: Choosing a highway sets you on a course for the next city
- **Initial State**: Arad
- **Goal State:** Bucharest
- **Action Cost**: The cost associated with each action (distance, or time,  or fuel consumption)
