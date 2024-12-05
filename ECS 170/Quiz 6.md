### **Key Concepts in RL:**

1. **Markov Decision Process (MDP):**
    
    - Defined as a **five-tuple (S, A, R, T, P₀)**:
        - **S**: State space.
        - **A**: Action space.
        - **R**: Reward function mapping _(state, action, successor state)_ to a scalar.
        - **T**: Transition function providing probabilities for next states.
        - **P₀**: Distribution over initial states.
2. **Policy (π):**
    
    - **Definition**: Mapping from states to actions.
    - Types:
        - **Deterministic**: Always produces the same action for a given state.
        - **Stochastic**: Outputs a probability distribution over actions.
3. **Utility Function (U):**
    
    - Maps states to their value (expected cumulative discounted rewards under a policy).
    - Example: **Grid World Problem**:
        - A toy environment with a grid of states.
        - Rewards assigned for transitions (e.g., +1, -1, or 0).
        - State values depend on proximity and paths to high-reward states.
4. **Quality (Q) Function:**
    
    - Maps _(state, action)_ pairs to their **expected total rewards**.
    - Guides decision-making by selecting actions with maximum quality.

---

### **Bellman Equations:**

1. **Utility Bellman Equation**:
    
    - Decomposes state utility into:
        - Reward for a state transition.
        - Discounted utility of the subsequent state.
    - Uses probabilities from the **transition model** and policy.
2. **Quality Bellman Equation**:
    
    - Similar decomposition but operates on _(state, action)_ pairs.
    - Incorporates rewards and the utilities of successor states.
3. **Optimal Bellman Equations**:
    
    - Focus on the **optimal policy**.
    - Replace summation with a **max operation** to choose the best action.

---

### **Value Iteration Algorithm:**

1. **Purpose**:
    - Solve MDPs with **dynamic programming** to estimate state values.
2. **Procedure**:
    - Initialize all state values to 0.
    - Iteratively update each state’s value using the Bellman equation.
    - Continue until values converge.
3. **Outcome**:
    - Derive the **optimal policy** by selecting actions leading to states with the highest values.

---

### **Types of RL Algorithms:**

1. **Model-Free vs. Model-Based**:
    
    - **Model-Free**: Learns a policy without modeling the transition function.
    - **Model-Based**: Builds an estimate of the environment's dynamics.
2. **Active vs. Passive Learning**:
    
    - **Passive**:
        - Learns from observing actions and rewards without changing the policy.
        - Example: Inferring from fixed trajectories.
    - **Active**:
        - Learns a policy while interacting with the environment and updating actions.
3. **On-Policy vs. Off-Policy**:
    
    - **On-Policy**: Learns using the same policy being evaluated.
    - **Off-Policy**: Evaluates and improves a policy different from the one generating the data.
4. **Hybrid Approaches**:
    
    - **Experience Replay**:
        - Revisits earlier trajectories to avoid forgetting challenging scenarios.

---

**Applications:**

- Example: A **robot vacuum** determining optimal motor actions to navigate efficiently without disrupting objects.

---

### **Further Topics in Reinforcement Learning Lecture:**

**Recursive Consistency in Bellman Equations:**

- The **utility** of a state considers:
    - **Reward** for transitioning to successor states.
    - **Utility of successor states**, weighted by probabilities of transitions and actions.
- Recursive formulation enables RL algorithms to compute state utilities incrementally.

**Continuous vs. Discrete Time in RL:**

- **Discrete Time**:
    - Models time in distinct steps (e.g., `t = 0, 1, 2...`).
    - Reward summation uses **discrete summation**.
- **Continuous Time**:
    - Models time as a continuous variable.
    - Replaces summation with **integrals** over time.
- Practical preference: Discrete time aligns with computational systems' finite precision and step-by-step processing (e.g., CPU cycles).

**Optimal Value and Policy Derivation:**

- The **optimal value** at a state assumes taking the best possible action.
- Relationship:
    - Utility at a state is the **maximum quality value** for available actions at that state.
- **Value Iteration Algorithm**:
    - Works backward from terminal states to compute optimal utilities dynamically.

---

### **Value Iteration Example:**

1. **Setup**:
    
    - A **grid world** with positive/negative reward states and obstacles.
    - Start with state values initialized to 0.
2. **Iterative Updates**:
    
    - Apply Bellman equation:
        - Update state values based on:
            - Expected rewards for transitions.
            - Discounted values of successor states.
    - Continue iterations until values converge.
3. **Extracting the Optimal Policy**:
    
    - After convergence, derive the policy:
        - Choose the action leading to the adjacent state with the highest value.

---

### **Extensions to Reinforcement Learning Algorithms:**

**Advantage Function:**

- Measures how much better a specific action is compared to the average policy action.
- Formula:
    - **Advantage (A)** = Q(state, action) − U(state).
- Useful for **stochastic policies** where sampling actions introduces variability.

**Policy Extraction from Value Iteration:**

- Simple: Choose the **highest-value neighboring state** at each step.
- Can be visualized as a **policy grid** showing optimal paths from any state.

---

### **Practical Challenges in RL Algorithms:**

1. **Scalability**:
    
    - Value iteration is computationally intensive for large state spaces.
    - Requires full knowledge of **transition probabilities**.
2. **Dynamic Programming Trade-offs**:
    
    - Requires clear **termination conditions** to ensure convergence.
    - Works best in environments with well-defined rewards and transitions.
3. **Exploration vs. Exploitation**:
    
    - Balancing learning from new experiences versus relying on known high-value paths.

---

### **Real-World Applications and Hybrid Approaches:**

**Hybrid RL with Experience Replay:**

- Combines active learning with "replays" of earlier experiences:
    - Prevents over-reliance on recent successes.
    - Helps adapt to rare or previously encountered scenarios.

**Example Use Case**:

- **Robot Learning to Dock**:
    - Navigating without disrupting fragile items (e.g., plants).
    - Uses RL to compute a sequence of motor actions leading to success.

**On-Policy vs. Off-Policy RL:**

- **On-Policy**:
    - Learns from actions directly guided by the policy.
- **Off-Policy**:
    - Evaluates or learns an improved policy while following a different one.

**Concluding Thoughts**:

- RL offers flexibility in handling dynamic and stochastic environments.
- Future focus includes more advanced algorithms and real-world implementation details.

### **Overview and Goal of Reinforcement Learning (RL):**

- RL formalized as a **Markov Decision Process (MDP)**.
- **Goal**: Maximize **expected cumulative discounted reward**:
    - **Expected**: Accounts for all scenarios.
    - **Cumulative**: Considers long-term outcomes.
    - **Discounted**: Prioritizes immediate rewards over distant ones.

---

### **Key Reinforcement Learning Topics:**

#### **Offline vs. Online Learning:**

- **Offline Learning**:
    - Observes and learns from gameplay examples without active interaction.
- **Online Learning**:
    - Actively interacts with the environment, learning in real-time.

#### **Model-Based Learning:**

- Builds a **transition model** of the environment's dynamics:
    - Estimates probabilities of transitions between states.
    - Approximates reward functions based on observed rewards.
- Example: **Empirical MDP Construction**:
    - Count state-action transitions to calculate probabilities (e.g., transition from state C to D occurs 75% of the time).
    - Normalize counts to create a probability distribution.

---

### **Direct Evaluation (Passive RL):**

- Evaluates state values by **averaging observed discounted rewards** across trajectories.
- Example: State B value calculated from episode rewards experienced after visiting B.
- **Advantages**:
    - Simple to implement.
    - Does not require knowledge of transition or reward models.
- **Limitations**:
    - Inefficient for large state spaces or rare transitions.
    - Ignores relationships between states (e.g., Bellman equations).

---

### **Temporal Difference (TD) Learning:**

1. **Concept**:
    
    - Updates state value estimates based on immediate transitions rather than full trajectories.
    - Incorporates **exponential moving averages** with a learning rate parameter (**α**).
2. **Key Properties**:
    
    - Learns values without needing transition or reward models.
    - Handles **online learning** effectively (one transition at a time).
    - Emphasizes recent experiences, which are more relevant in improving policies.
3. **Example Calculation**:
    
    - **New Value (V)** = Old Value + α * (Observed Reward + γ * Successor Value − Old Value).
    - Example: Starting with `V(B) = 0` and observing a transition from B to C with reward −2:
        - Updated `V(B) = 0.5 * (−2 + 0 − 0) = −1`.
4. **Advantages**:
    
    - Requires fewer samples than direct evaluation.
    - Implicitly encodes the transition model through repeated sampling.

- **Limitation**:
    - Converges slower than model-based approaches.

---

### **Q-Learning (Active RL):**

- **Goal**: Learn optimal **state-action values (Q-values)** for all state-action pairs without needing explicit models.
- **Key Steps**:
    - Observe a transition: _(State, Action) → (Reward, Successor State)_.
    - Update Q-value using:
        - **Q(S, A)** = Old Q + α * [Observed Reward + γ * max(Q(S', A')) − Old Q].
        - _(max term assumes the best action at the next state)_.
- **Properties**:
    - Converges to the **optimal policy** with sufficient exploration and appropriately tuned learning rate.
    - Supports **off-policy learning** (learns optimal policy even while following a suboptimal one).

---

### **Comparisons and Challenges:**

#### **Model-Based vs. Model-Free RL:**

- **Model-Based**:
    - Explicitly learns environment dynamics.
    - Requires complex computations but may converge faster.
- **Model-Free**:
    - Learns directly from experiences.
    - Scalable but slower to converge.

#### **Exploration vs. Exploitation**:

- Balancing between exploring new states and exploiting known high-reward paths.

#### **Learning Rate (α):**

- Controls update size:
    - Too large: Unstable convergence.
    - Too small: Slow learning.

---

### **Takeaways:**

- **Direct Evaluation** works well for simple tasks but scales poorly.
- **TD Learning** and **Q-Learning** overcome model dependencies and scale better for real-time systems.
- **Q-Learning** is particularly robust, learning optimal policies even from suboptimal initial conditions.

### **Introduction & Recap**:

- Reviewed **Temporal Difference (TD) Learning** and **Q-Learning**:
    - Learn **state-action values (Q-values)** iteratively from experience without a transition model.
    - Advantage: Handles environments with unknown dynamics.
- Challenges:
    - Explicitly learning a table for all state-action pairs is infeasible for large or infinite state spaces.
    - Real-world problems, e.g., **backgammon** (~10²⁰ states), far exceed practical limits (~10⁶ states).
    - Limitations in scalability and parameter count: Number of parameters equals the number of state-action pairs.

---

### **Generalization in Reinforcement Learning**:

1. **Parameterization of Utility Functions**:
    
    - Represent utility functions using parameterized models:
        - Utility function U(s)U(s)U(s) estimated as $$U^θ(s)\hat{U}_\theta(s)U^θ​(s)$$, where $$θ\thetaθ$$ are learned parameters.
    - Introduces **features (f₁, f₂, ..., fₙ)** that encode state information (e.g., sensory inputs).
    - Example: In a **grid world**, features like **Manhattan distance** to the goal and number of walls define state similarity.
    - Goal: Generalize across states with similar features, reducing the parameter count.
2. **Learning Features**:
    
    - Parameters $θ\thetaθ are learned via **gradient descent**:
        - θnew=θold+α⋅ΔU⋅∂U^θ∂θ\theta_{new} = \theta_{old} + \alpha \cdot \Delta U \cdot \frac{\partial \hat{U}_\theta}{\partial \theta}θnew​=θold​+α⋅ΔU⋅∂θ∂U^θ​​.
        - Similar to the **Widrow-Hoff rule** or **Delta rule** in supervised learning.

---

### **Challenges with Generalization**:

- **Catastrophic Forgetting**:
    
    - Sequential updates overwrite earlier knowledge.
    - Solutions:
        - **Weight Decay**: Gradual reduction of parameter values to maintain balance.
        - **Epsilon-Greedy Exploration**: Forces random actions occasionally to revisit less-explored areas.
        - **Experience Replay**: Revisit and update using earlier training trajectories to retain diverse knowledge.
- **Representation Bottlenecks**:
    
    - Limited number of parameters in θ\thetaθ restricts the complexity of the learned utility function.
    - Linear assumptions about relationships between features and utility can limit expressiveness.

---

### **Deep Reinforcement Learning**:

1. **From Linear to Nonlinear Approximations**:
    
    - Incorporate **nonlinear transformations** of features (e.g., using neural networks).
    - Enables modeling of complex relationships between state features and utilities.
2. **Deep Q-Learning**:
    
    - Neural network predicts Q-values directly from **state-action pairs**:
        - Inputs: Encoded state and action features (e.g., pixel data for games).
        - Outputs: Quality values Q(s,a)Q(s, a)Q(s,a).
    - Trained using a **gradient descent-based update** similar to Q-learning.
3. **Applications**:
    
    - Atari video games (e.g., **Space Invaders**) as a benchmark.
    - Representations can include:
        - **High-level game states**: Encoded as scalar coordinates (e.g., position of aliens in Space Invaders).
        - **Raw pixel data**: Processed via **Convolutional Neural Networks (CNNs)** to extract features.

---

### **Example Problem: Space Invaders**:

- **State Representation**:
    - Pixels (RGB channels, e.g., 3 × 100 × 200 matrix) or high-level variables (positions of entities).
    - Pixel data often leads to **extremely large state spaces**, requiring feature extraction via CNNs.
- **Deep Q-Networks (DQNs)**:
    - Use CNNs to process pixel data into feature maps.
    - Fully connected layers predict Q-values for possible actions (e.g., move left, right, shoot).
    - Success demonstrated in Atari games and complex environments like **Minecraft** and **GTA**.

---

### **Takeaways**:

- Moving from **tabular methods** to **parameterized representations** enables RL to handle large/infinite state spaces.
- Deep Q-Learning combines the strengths of neural networks and Q-learning for complex problems.
- Importance of designing effective state representations and balancing exploration vs. exploitation.

### **Introduction and Recap:**
- Lecture focus: **Policy Gradient Methods** and a brief discussion of **AlphaGo** and **AlphaZero**.
- Previous topics reviewed:
    - **Q-Learning**: Learning quality (Q) functions for state-action pairs.
    - **Temporal Difference (TD) Learning**: Used to update Q-values without requiring a transition model.
    - Transition to **Policy Search/Gradient**:
        - Forego learning Q-values or utility functions.
        - Optimize policies directly by searching **policy space**.

---
### **Policy Gradient Methods:**
1. **Core Idea**:
    - A **policy** (denoted as π(s,a)\pi(s, a)π(s,a)) gives the probability of taking action $a$ in state $s$.
    - Policies are parameterized by $\theta$, representing a location in **policy space**.
    - Optimize policy parameters ($\theta$) to improve performance using **gradient-based optimization**.

1. **Deterministic vs. Stochastic Policies**:
    - **Deterministic Policy**:
        - Selects the action with the highest quality for a state.
    - **Stochastic Policy**:
        - Assigns probabilities to actions using techniques like **softmax**.
        - **Temperature Scaling**:
            - Controls exploration vs. exploitation.
            - Higher temperature → **flatter probabilities** (more exploration).
            - Lower temperature → **sharper probabilities** (more exploitation).

1. **Optimization Goal**:
    - Maximize the **policy value** (ρθ\rho_\thetaρθ​):
        - The expected **cumulative discounted reward** under the policy.
    - Approach:
        - Estimate the gradient of ρθ\rho_\thetaρθ​ with respect to θ\thetaθ.
        - Use gradient ascent to adjust θ\thetaθ.

1. **REINFORCE Algorithm**:
    - A popular **policy gradient method**.
    - Estimates the gradient using sampled trajectories:
        - Gradient estimate ∝R⋅∇π(s,a)/π(s,a)\propto R \cdot \nabla \pi(s, a) / \pi(s, a)∝R⋅∇π(s,a)/π(s,a), where:
            - RRR: Observed reward.
            - π(s,a)\pi(s, a)π(s,a): Policy probability of taking action aaa in state sss.
    - **Key Properties**:
        - More frequent actions lead to smaller updates (scaled by 1/π(s,a)1 / \pi(s, a)1/π(s,a)).
        - High variance in estimates can affect training stability.
---
### **Challenges in Policy Gradient Methods**:
1. **High Variance**:
    
    - Gradient estimates can vary significantly across trajectories.
    - Solutions:
        - Use larger sample sizes (but increases compute cost).
        - Employ **correlated sampling** to reduce variance.
2. **Training Instability**:
    
    - Policies change dynamically during online learning.
    - Standardize gradient estimation using fixed benchmark trajectories (e.g., **Pegasus algorithm**).

---

### **AlphaGo: Case Study of RL in Practice**:

1. **Overview**:
    
    - Developed by DeepMind, AlphaGo defeated top human Go players.
    - Combines:
        - **Supervised Learning** (human gameplay data).
        - **Policy Gradient Methods** (self-play training).
        - **Monte Carlo Tree Search (MCTS)** for planning.
2. **Workflow**:
    
    - **Supervised Learning**:
        - Train a **policy network** on 30 million board positions from human games.
        - Architecture: 13 convolutional layers with **ReLU** activations and **softmax** output.
    - **Self-Play**:
        - Use the supervised network to bootstrap policy.
        - Train against itself with policy gradients.
    - **Value Network**:
        - Predicts the likelihood of winning from any board position.
        - Facilitates MCTS by evaluating leaf nodes.
3. **Monte Carlo Tree Search**:
    
    - Balances exploration and exploitation.
    - Uses value estimates to back-propagate updated quality values.

---

### **AlphaZero: Simplified and Improved AlphaGo**:

1. **Key Differences**:
    
    - Discards human gameplay data and engineered features.
    - Trains a single network for both policy and value estimation.
    - Relies solely on self-play with raw board positions.
    - Achieved superior performance to AlphaGo in just 72 hours of training on 5,000 TPUs.
2. **Key Takeaways**:
    
    - Simplification and compute power outperformed handcrafted features and optimizations.
    - Example of the **Bitter Lesson**:
        - General-purpose methods with higher compute often outperform domain-specific optimizations.

---

### **Broader Implications and Applications**:

1. **StarCraft AI**:
    
    - Example of applying RL to complex, continuous state-space games.
    - Demonstrates challenges in scaling RL to real-time, multi-agent scenarios.
2. **Economic Considerations**:
    
    - High costs of training AI systems (e.g., AlphaGo/Zero training requiring weeks of GPU/TPU compute).
    - Long-term goals of achieving **Artificial General Intelligence (AGI)**.
### **Challenges in Reinforcement Learning (Highlighted in AlphaGo/AlphaZero)**:

1. **Compute vs. Efficiency**:
    
    - Training AlphaGo required:
        - **50 GPUs** for supervised learning (~3 weeks).
        - Additional resources for value network and self-play phases.
    - Training AlphaZero required:
        - **5,000 TPUs** over 72 hours.
    - Implications:
        - High computational requirements limit accessibility and generalization.
        - Efficiency improvements critical for broader applications.
2. **Training Stability**:
    
    - Maintaining consistency during updates:
        - AlphaGo utilized **experience replay** to avoid catastrophic forgetting.
        - Stabilized training with **target and Q networks** for quality estimates.
3. **Real-World Applicability**:
    
    - AlphaGo and AlphaZero excel in structured domains (e.g., board games) but:
        - Limited generalization to open-ended, ambiguous environments.
        - **StarCraft** AI addressed some limitations by introducing:
            - **Continuous state spaces** and **simultaneous moves**.
            - Multi-agent learning scenarios for real-time strategy.

---

### **Monte Carlo Tree Search (MCTS) in AlphaGo**:

1. **Purpose**:
    
    - Enables effective decision-making by evaluating possible game trajectories.
    - Balances:
        - **Exploration**: Searching new nodes.
        - **Exploitation**: Focusing on high-value nodes.
2. **Steps in MCTS**:
    
    - **Selection**:
        - Use existing policy and value networks to prioritize paths.
        - Criteria include:
            - Number of visits to a node.
            - UCB (Upper Confidence Bound) for exploration.
    - **Expansion**:
        - Add new nodes to the tree, simulating potential moves.
    - **Evaluation**:
        - Estimate node quality using:
            - **Rollout policies** (faster but less accurate).
            - **Value networks** for deeper analysis.
    - **Backup**:
        - Propagate updated values back through the tree to refine decision-making.
3. **Key Contributions of MCTS**:
    
    - Introduced probabilistic approaches for deeper, flexible planning.
    - Allowed AlphaGo to evaluate non-deterministic outcomes in Go.

---

### **Methodological Takeaways from AlphaGo**:

1. **Self-Play**:
    
    - Train networks by competing against themselves.
    - Benefits:
        - Avoids reliance on external data.
        - Gradual improvement without human bias.
        - Supports dynamic adaptation during training.
2. **Bootstrapping**:
    
    - Initialize training using **human gameplay** for faster convergence.
    - Subsequent iterations (e.g., AlphaZero) eliminated this step by relying solely on raw data.
3. **Exploration vs. Exploitation**:
    
    - Carefully managed trade-off:
        - Rollout networks prioritize speed, even at the cost of accuracy.
        - Policy networks maximize precise evaluation.
4. **Scalability**:
    
    - Parallelization and TPU/GPU clusters accelerated computation.
    - Highlights the importance of infrastructure for modern AI systems.

---

### **From AlphaGo to AlphaZero: Simplifying and Generalizing**:

1. **Key Advancements in AlphaZero**:
    
    - Unified policy and value networks into a single architecture.
    - Dropped reliance on human-engineered features.
    - Adopted an end-to-end self-play framework with raw board states as inputs.
2. **Performance Highlights**:
    
    - AlphaZero decisively outperformed AlphaGo across 100 games.
    - Reduced training time significantly (3 days with extensive compute resources).
3. **Reflections on AI Development**:
    
    - Shift from domain-specific optimizations to compute-driven, generalized frameworks.
    - Aligns with **Richard Sutton’s Bitter Lesson**:
        - Simple, scalable solutions eventually outperform handcrafted, specialized methods.

---

### **Economic and Philosophical Considerations**:
1. **Costs of Advanced AI**:
    - Development expenses (e.g., AlphaZero's infrastructure) are immense.
    - Raises questions about accessibility and practical applications beyond research.

1. **Artificial General Intelligence (AGI)**:
    - Defined as intelligence matching or exceeding human performance across diverse tasks.
    - DeepMind’s mission: **Solve AI, then solve everything else**.
    - Concerns:
        - Feasibility of transitioning from narrow AI to general-purpose systems.
        - Economic implications of achieving AGI.

---

### **Speculative Applications and Future Directions:**
1. **Game AI Beyond AlphaGo**:
    - Use of RL in complex games like **StarCraft**:
        - Highlights challenges of simultaneous moves and continuous states.
        - Demonstrates potential for generalizing to real-world tasks.
2. **Generalization in AI**:
    - Debate over task-specific vs. adaptable intelligence.
    - Broader applicability requires AI capable of transitioning across domains.
3. **Emerging Trends**:
    - Large language models (e.g., GPT-series) offer broader generalization than game-specific AIs.
    - Convergence of reinforcement learning and supervised techniques in areas like natural language processing.

---

### **Concluding Thoughts**:
- **AlphaZero’s Legacy**:
    - Showcases the power of combining raw computation with simplified methodologies.
    - Challenges traditional views on domain-specific AI design.

- **The Path Forward**:
    - Continued focus on scalability, efficiency, and generalization.
    - Ongoing debate on the practicality and ethical implications of AGI.