# Minimax
- General idea of Minimax is that what's good for you is bad for your opponent and vice versa
- In a turn taking game the state tree will have alternating levels where each person will try to maximize the levels during their turn
- And at another turn the opponent will try to minimize the levels towards us
- At every level, we'll choose the best thing for us and our opponent will choose the worst thing for us
## Limitations
- We are evaluating every node 
- Branching factor can be high, complexity: $O(b^d)$ which can get expensive 
- **Pruning** can get rid of this limitation
	- We can cut off section of the trees so we don't need to evaluate every node
 
![Pasted image 20241015141834](https://github.com/user-attachments/assets/6ee12deb-1ed0-4176-978c-ad75cb3956b1)


# Alpha-Beta Pruning
- Does the same as minimax with less computational effort 
- We start by evaluating to the first child similar to Depth-First Search 
- If upper bound for a child is less than or equal to this number then we can prune 
- Most pruning occurs for max when the successor states are evaluated in descending order of value 
- Optimal pruning occurs when min and max evaluate what is best for them first 
	- Evaluate one child to completion and prune the rest 
- Best case scenario, $\frac{O(b^d)}{2}$
- We can't guarantee optimal pruning 
- No pruning occurs for max when the successor states are evaluated in ascending order 
- The best thing for min is ascending order but the worst for Max as we have to go all the way to the end to realize that we could have pruned 
- Likewise will occur when we flip


# MIT Notes
## Minimax
![Pasted image 20241016181325](https://github.com/user-attachments/assets/e76b5fc1-2ffe-4cc5-92d1-c7a2f9c573be)

- Above we have a game tree with values at the bottom 
- We have player one (MAX) who wants to get to value 8 
- Then player two (MIN) who wants the situation that's small as possible because they are the opposite as the MAX player

![Pasted image 20241016181551](https://github.com/user-attachments/assets/3b19c9a4-7191-41fe-8a97-fedc1d1388af)

 - Above we are looking at the perspective of the MIN player 
 - On either branch of the game tree they are going to be choosing the smallest value out of the two choices 

![Pasted image 20241016181702](https://github.com/user-attachments/assets/168bde17-0e9b-4113-8079-72604364a154)

- When going back a branch we are at the perspective of the MAX player
- They see that if they choose the right side they'll get 1 
- If they go the left side then they'll get 2 
- So they will choose 2 and end up getting 2
- Adversarial game where both players are competing with each other


## Alpha-Beta 
![Pasted image 20241016182500](https://github.com/user-attachments/assets/e8466456-9fd3-4a49-9646-8ebe4cbb8957)

- Here the maximizer doesn't need to know every value on the right hand side 
- The minimizer will always be taking 1 if the maximizer were to choose the right hand side 
- The minimizer turn is already determined and so the maximizer will always choose the left hand side since they will end up with the value of 2 instead of 1

![Pasted image 20241016183849](https://github.com/user-attachments/assets/78e04417-1472-48ba-ab2d-dced4a38d19f)

- How much energy do you save from doing this
- In the optimal situation it will take 
$$2b^\frac{d}{2}$$
- In a practical situation it will be close to what the optimal situation will run
