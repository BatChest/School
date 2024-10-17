Search has limitations 
- It frames intelligence as navigation through a state space
- But it makes the assumption that the agent is in full control 
- If there is a transition then the agent can make that action

# Adversarial Search
- We have a setting where two players are taking turns manipulating the game state 
- Each player is trying to direct the game tree to get to a state that's a goal for them and loss for the other player
- Two agents that play the game
- Sequential game (take turns)
- Assumption that the agents are rational (do the thing that gets them the highest payoff)
- The successor state is always the same 
- Perfect information (all agents have full visibility of the states the entire time)
- Zero sum assumption (what's good for you is bad for the opponent, vice versa)

# Approach
- Assume we have the rules for the game
- Consider what the opponent will do to restrict us from winning
- Working backwards from the working states to the terminal states

# Depth
- Adding more depth can be more costly to compute that much further forward

# Design Evaluation Function
- Zero sum assumption 
- It can be anything and no proof required for admissibility or consistency 
- There is no guarantee for optimality 

# Tick-Tac-Toe Evaluation Function
- Count number of ways to win 
- Needs to consider who's turn it is 
## Quality vs. Quantity
- Functions with high fidelity, they are good at estimating value of state 
- Choosing expensive evaluation function we can't look ahead that far 
- Simpler functions are cheaper so expand the tree deeper down but be less faithful to the chances of winning the game
- **Deep Blue** uses a mix of both

# Alpha Beta Printing 
- Figure out some parts of this search tree are not useful to us then we can cut down on the amount of work that we have to do 

