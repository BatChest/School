# Recall Search Problems
- State representation
- Actions
- State space
- Transition Model
- Initial State
- Action Cost
- Goal State

# Implicit vs. Explicit
- **Implicit**: The whole thing isn't written down, but we have a way to figure it out
- **Explicit**: The whole thing is written down

# Search Algorithms
## Input-Output behavior
- Accept a "search problem" as input, and return a solution or an indication of failure 
- What is a solution for these problems?, **a Path**
- Many search algorithms use a search tree

# Terminology
- **Node**: a node in a search tree corresponds to a state in the state space
	- Can expand it and get all the successors and child nodes that are reachable from that node

- **Expanding**: a node means considering all the actions available to us in the state, and seeing where they would lead
	- Think about all the actions that are available to us and see where they will lead 

- Expanding a node generates a **successor node** (child node) for each of the state that are one action from the current state 
	- We are getting information about its successors

- The **frontier** is the set of nodes that are one action away from an already expanded node 
	- We know we can reach them but we haven't actually gone there and looked yet

- The frontier separates the **interior** and **exterior** of the problem 


# Core problem in search 
- **What to expand first?** Out of all the actions I can take in this state, which one should I pick? Out of all the nodes in the frontier, which one to expand next?

- **Search algorithms differ** in how they solve this dilemma

- Search problem differ in which strategy is optimal

- **"Best-First Search"**
	- A broad class of search algorithms 

- **Best-first search algorithms** expand the node in the frontier that is the best according to some function:
$$f(n) : \text{Node} \rightarrow \mathbb{R}$$
- We can call $f(n)$ the **evaluation function**

# Uninformed Best-First Search Algorithms
- Uninformed means these algorithms do not utilize heuristics 
- Informed means it uses a heuristics
- What's heuristic?
	- Its role is to inform the search algorithm about where it should go next

- Some Uninformed Algorithms 
```ad-example
- Breadth-first search (BFS)
- Depth-first search (DFS)
- Uniform-cost Search (Dijkstra's; UCS)
```

# Informed Search Algorithms 
- Informed Search algorithms use **heuristics** to guide the search process
- Greedy Best-first Search 
- A-star search 

# Properties of Search Algorithm
- **Time Complexity**
	- How long it takes to find a solution?
	- Measures the **number of operations** or **time** taken by an algorithm as a function of input size
- **Space Complexity**
	- How much memory is needed to perform the search?
	- Measures of the **amount of memory** used by an algorithm as a function of input size 
- **Completeness**
	- Is the algorithm guarantee to find a solution if one exists, or report failure if there is no solution?
	- To be complete, the search algorithm must be **systematic**
```ad-note
**Systematic:** the algorithm can eventually reach any state that is connected to the initial state

The algorithm "leaves no stone unturned"

Thing about a detailed-oriented friend who won't make a decision until they know all their options
```

- **Cost Optimality**
	- Does the algorithm find the best (lowest path cost) solution?
- **Action Optimality**
	- Does the algorithm find the solution requiring the fewest number of actions?

# Worst/Best/Typical Case
- **Worst case**: What happens if everything doesn't go in favor of the AI system
- **Typical Case**: What happens in a typical scenario
- **Best Case**: What happens if everything goes in favor of the AI system
- All three are useful, but we are often particularly concerned with **worst-case behavior**

# Branching Factor and Depth
- In uninformed search, time and space complexity depend on the branching **factor** and depth **of** the search time 
	- **Branching factor ($b$)**
		- The average number of successor for a state in the search tree
		- Higher branching factor leads to a larger number of nodes to explore, increasing time complexity
	- **Depth ($d$)**
		- Typical number of moves between the initial state and goal state 
		- Moves between the initial state and goal state 
	- **Branching Factor: Example**
![[Pasted image 20241009204430.png]]


# What is the Naïve Solution
- The very first way to solve something
- Usually never the most efficient way, typically done in brute force 

# Exhaustive Search
- Look at every single state
- **Time Complexity:** $O(|S|)$ where $S$ is the state space
- **Space Complexity:** $O(|S|)$
- **Cost Optimality:** Optimal (we'll eventually find the optimal solution)
- **Action Optimality:** Optimal 
- **Completeness:** Complete for finite state spaces 

# Breadth-first Search
- **Algorithm Behavior** 
	- Expand the shallowest node first
![[Pasted image 20241009205417.png]]

- **Complexity**
	- **Time Complexity**: $O(b^d)$ where $b$ is the branching factor and $d$ is the depth of the shallowest goal node
	- **Space Complexity:** $O(b^d)$ where $b$ is the branching factor and $d$ is the depth of the shallowest goal node
- **Optimality** 
	- **Cost Optimality:** Optimal only if all actions have the same cost, not in general
	- **Action Optimality:** Action-Optimal!
- **Completeness** 
	- It is Complete

# Dijkstra's Algorithm (Uniform-Cost Search)
- **Algorithm Behavior:** Expand the node with the lowest cumulative cost from the root node to the current node 
- **Time Complexity:** $O(b^{1 + [C^*/ \epsilon]})$, where C* is the cost of the optimal solution, and $\epsilon$ is a lower bound on the cost of each action
- **Space Complexity:** $O(b^{1 + [C^*/ \epsilon]})$
- **Cost Optimality:** Optimal
- **Action Optimal:** Optimal 
- **Completeness:** Complete if costs are non-negative and $b$ is finite 

# Depth-first search
- **Algorithm Behavior:** Expand the deepest node first
- **Complexity:** 
	- **Time Complexity:** $O(b^m)$ where $b$ is the branching factor and $m$ is the maximum depth of the search tree
	- **Space Complexity:** $O(bm)$ 
- **Cost Optimality:** NOT cost-optimal 
- **Action Optimality:** NOT cost-optimal
- **Completeness:** Not complete in general

