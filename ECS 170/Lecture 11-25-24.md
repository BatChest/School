### Notes on Reinforcement Learning Lecture (Continued):

---

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
