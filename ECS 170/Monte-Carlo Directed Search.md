This algorithm can be understood in 4 steps:
- Selection
- Expansion
- Simulation
- Backpropagation 

![Pasted image 20241019125704](https://github.com/user-attachments/assets/e807bdd7-5167-4109-95d7-687eac75fe12)

## Selection
- Start at the root of the game and tree and get to a particular depth
- Depth is set by getting to a point where we haven't expanded any of the successors for this node 
- We don't know what happens for any of the moves that follow this one 
- Select a node to expand 

## Expansion
- Choose a move that follows from this node that we've selected 
- Also decide what move to play 

## Simulation
- Actually running the game at the leaf node until you get to that terminal condition 
- Then we can see who won in that simulation of the game 
- Basically taking a game all the way through completion through some simulated play   

## Backpropagation
- Looks at the result of the game and sees who won
- If the first player wins (MAX) then we'll update the nodes in way that be a good path since it led to a win  
- IF MAX lost then we'll update the nodes to in way to tell that wasn't a good path

# Monte Carlo methods
- Repeated random sampling to obtain numerical results
- Broad class of computational algorithms  

# Exploration vs. Exploitations tradeoff 
- Exploration: try something new
- Exploitation: do the thing that you already know

# Selection vs. Expansion
## Selection
- We do this with Pure Monte Carlo Selection
- Select nodes in which we select at random 
- Building a game tree at random and choosing different path every time 
- Need a way to direct expansion towards important parts of the game tree
- Basic Idea:
	- Select a node to expand based on two factors
	- How good the node looks give our previous expansion
	- How often we have been there


- UTC1 Selection Criterion:
	- $w_i$ : wins from state $i$
	- $s_i$ : number of times state $i$ played 
	- c - balance term
	- $s_p$ : number of times parent visited 
	- can also include an evaluation function

![Pasted image 20241019131427](https://github.com/user-attachments/assets/41d5e527-6dfd-46d5-a3dd-0179d6763648)


- Use the above as a score to determine which node to select 


![Pasted image 20241019131609](https://github.com/user-attachments/assets/89b7df9a-3bb7-4653-bf2f-48c09ed9c877)


## Simulation
- From this play of the game two simulated opponents and see who wins
- Simulate a "random" game to a terminal node
- Observe which player won
- Repeat 
- What kind of game? How do we model each player?
	- (Uniform) random moves?
	- Intelligent moves?
	- Good moves? Bad moves?
	- Human moves? AI moves?

- Playout Policy, controls the simulation
- For Go and other games, playout policies haven been successfully learned from self-play by using neural networks 
- Sometimes game-specific heuristics are used, such as "consider capture moves" in Chess

- **Bottom Policy**
- Playout policy controls the simulation
- Treat this as a black box that can simulate whatever game we're interested in 
- Do $N$ simulations starting from the current state of the game 
- Track which moves get the highest win percentage 
- Want to converge to optimal play as $N$ increases



![Pasted image 20241019133137](https://github.com/user-attachments/assets/bbb9eb98-83e7-45dc-abbd-292cd1f4032a)


- Want to converge to optimal play as $N$ increases 
- This is new! Instead of looking for:
	- A satisfactory solution or
	- An optimal solution
- We try to converge incrementally towards an optimal solution 
- We run Monte Carlo to get better estimates

# Example

![Pasted image 20241019133621](https://github.com/user-attachments/assets/acaf6f22-de21-4a8d-8bc0-e9755fa55c15)


- Numerator is the number of games that we've won from this node 
- Denominator 100 is the number of games where that node was selected 


![Pasted image 20241019134509](https://github.com/user-attachments/assets/b4715c6d-8ca9-4691-841f-ce960291de3a)


- we need to update the win ratio from the root node to the Orange win

![Pasted image 20241019135333](https://github.com/user-attachments/assets/a0b07757-5326-4f87-aa29-8c4ae560a266)


- Since the search starts from Purple's perspective 
- We increment the denominator only 
- (If purple had won, we would increment the numerator and denominator)


![Pasted image 20241019135442](https://github.com/user-attachments/assets/3e3c3d55-889b-4108-8f67-1b789ac81530)


- Remember: SELECT and SIMULATE functions are "swappable"


![Pasted image 20241019135554](https://github.com/user-attachments/assets/8533ed39-9e31-4701-a8dd-af298d5ed198)



![Pasted image 20241019135604](https://github.com/user-attachments/assets/9c8bb919-ef23-4dbd-975e-0181eae3667c)



![Pasted image 20241019135647](https://github.com/user-attachments/assets/a0a04ea3-fd2f-4f97-bf6f-546e40e3f8ae)



![Pasted image 20241019135747](https://github.com/user-attachments/assets/f242269d-c915-40b7-b4a3-ffb6a89759c8)


**Informed Search**: How to direct a search path between our current state and the goal when we have full control

**Adversarial Search**: How to take action to lead us to a goal from our current state when we have a rational adversary 
