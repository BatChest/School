### Notes on Reinforcement Learning Lecture:

**Introduction:**

- Focus: **Reinforcement Learning (RL)** with key topics including functions, **value iteration**, and types of RL.
- Approach is **mathematical**, involving policies and their implications.

---

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
