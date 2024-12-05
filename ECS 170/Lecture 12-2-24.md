### Notes on Reinforcement Learning Lecture (12/02/24):
---
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