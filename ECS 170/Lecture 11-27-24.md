
---
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