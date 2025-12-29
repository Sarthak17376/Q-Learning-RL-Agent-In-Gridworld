# Q-Learning-RL-Agent-In-Gridworld 🤖

A customizable Q-Learning reinforcement learning agent that learns to navigate a gridworld with obstacles to find the optimal path.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1NfQLZlgLnGkTYrbTFvt_mrNF-9bn8Svb?usp=sharing)

## 📌 Project Overview

This repository contains a Python implementation of the **Q-Learning** algorithm. The agent learns to navigate a grid (default 5x5) from a **Start State** to a **Goal State** while avoiding **Obstacles**.

The project allows for:
1.  **Customizable Environments:** Users can define grid size, obstacles, and rewards.
2.  **Hyperparameter Tuning:** Users can experiment with Learning Rate ($\alpha$), Discount Factor ($\gamma$), and Exploration Rates ($\epsilon$).
3.  **Policy Visualization:** The final policy is printed as a grid of arrows representing the optimal action at every state.

## 🛠️ Dependencies

To run this project locally, you need Python installed along with the following libraries:

* `numpy` (for matrix operations)
* `pandas` (for displaying the Q-Table)

You can install the dependencies using pip:

```bash```
pip install numpy pandas

## 🚀 How to Run the Q-Learning Simulation

You can run the simulation immediately in your browser using Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1NfQLZlgLnGkTYrbTFvt_mrNF-9bn8Svb?usp=sharing)

When you run the script, you'll first be asked if you want to enter your own parameters or use the default example.

`Does The User Want to Take Manual Input: (Y/N) :`

* Enter `Y/y` to customize the simulation.
* Enter `N/n` (or any other key) to run the default 5x5 grid example.

---

### Entering Custom Values

If you choose `Y`, you will be prompted to enter the following parameters. **Pay close attention to the format!**

* **Grid Dimension**
    * **What it is:** The size of your square grid world.
    * **Format:** A single whole number.
    * **Default:** `5`

* **Start State / Goal State**
    * **What it is:** The agent's starting and target coordinates. The top-left corner is `(0,0)`.
    * **Format:** A Python tuple with no spaces: `(row,column)`.
    * **Defaut:** `(0,0)`

* **Obstacles**
    * **What it is:** A list of coordinates the agent should be penalized for entering.
    * **Format:** A Python list of tuples with no extra spaces: `[(r1,c1),(r2,c2)]`.
    * **Default:** `[(1,1),(1,3),(3,1),(3,3)]`

* **Rewards**
    * **What they are:** The points the agent gets for certain actions. A high goal reward and negative step/obstacle penalties encourage efficient paths.
    * **Format:** Whole numbers (can be negative).
    * **Default (Goal):** `100`
    * **Default (Normal Move):** `-1`
    * **Default (Obstacle):** `-10`

* **Alpha (Learning Rate)**
    * **What it is:** Controls how much the agent learns from new experiences.
    * **Format:** A decimal number between 0.0 and 1.0.
    * **Default:** `0.3`

* **Gamma (Discount Factor)**
    * **What it is:** Determines the importance of future rewards. A value close to 1 makes the agent farsighted.
    * **Format:** A decimal number between 0.0 and 1.0.
    * **Default:** `0.99`

* **Number of Episodes**
    * **What it is:** The total number of training runs from start to goal.
    * **Format:** A large whole number.
    * **Default:** `10000`

* **Epsilon Values**
    * **What they are:** A list of exploration rates to test. A higher value means more random exploration.
    * **Format:** A Python list of decimals: `[value1,value2]`.
    * **Default:** `[0.3,0.5,0.7]`

## 🧮 The Algorithm

The agent updates its Q-values using the Bellman Equation:

$$Q(s, a) \leftarrow Q(s, a) + \alpha [R + \gamma \max_{a'} Q(s', a') - Q(s, a)]$$

Where:
* $Q(s, a)$: Current Q-value for state $s$ and action $a$.
* $\alpha$: Learning rate.
* $R$: Reward received.
* $\gamma$: Discount factor.
* $\max_{a'} Q(s', a')$: Maximum expected future reward.

## 📈 Example Output

The script generates a **Policy Grid** showing the best action for each cell:

```text
 v  >  v  <  v 
 v  X  v  X  v 
 >  >  v  >  v 
 ^  X  v  X  v 
 ^  >  >  >  G
```

(Where ^, >, v, < represent movement direction, X is an obstacle, and G is the goal)
