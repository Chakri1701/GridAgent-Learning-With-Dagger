# GridWorld Reinforcement Learning and DAgger Implementation

This project implements **Reinforcement Learning algorithms** — specifically **Value Iteration**, **Policy Iteration**, and the **DAgger (Dataset Aggregation)** imitation learning approach — in a custom **4x4 GridWorld environment**.  
It was developed as a part of the **Mini Project 1** for the course at **Oregon State University**.

---

## 👤 Author
**Chakradhar Reddi Vitta**  
ID: 934595987  
Email: vittac@oregonstate.edu

---

## 🧩 Project Overview

The agent operates in a 4x4 grid aiming to reach the goal at **(3, 3)** while avoiding fire and water states.

### Environment Rules
- **Goal**: Reach `(3, 3)` to receive `+100` reward.
- **Fire cells**: `(0, 1)`, `(0, 2)` → reward `-10`
- **Water cells**: `(2, 1)`, `(2, 2)` → reward `-5`
- **Each move**: reward `-1` (to encourage shorter paths)
- The agent can move **Up, Down, Left, Right**.
- Each action has a chance to **slip** into adjacent directions with given probabilities.

---

##  Algorithms Implemented

### 1️ Value Iteration
- Computes optimal state values using the Bellman update equation.
- Evaluated for different discount factors:  
  - γ = 0.3 → Focuses on short-term rewards (avoids risk).  
  - γ = 0.95 → Focuses on long-term rewards (accepts short-term loss to reach goal faster).

### 2️ Policy Iteration
- Alternates between **policy evaluation** and **policy improvement** until convergence.
- Produces the same optimal policy as Value Iteration but converges faster.

### 3️ DAgger (Dataset Aggregation)
- An imitation learning algorithm where the agent learns from an expert (optimal policy).
- Uses a **Decision Tree Classifier** to learn from collected trajectories.
- Evaluates performance for `N = {5, 10, 20, 30, 40, 50}` iterations.
- Plots **accuracy vs. number of learning cycles**.

---

##  Results Summary

- **Low γ (0.3):** Agent prioritizes avoiding hazards, taking safer but longer routes.
- **High γ (0.95):** Agent values long-term gains, sometimes crossing hazards for faster completion.
- **DAgger:** Accuracy fluctuates with more training data — more data doesn’t always improve performance due to noisy exploration.

