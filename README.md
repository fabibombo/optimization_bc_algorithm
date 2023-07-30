# Branch and Cut Knapsack Solver

This repository contains a Python implementation of a Branch and Cut algorithm for solving the 0/1 Knapsack Problem.

## Problem Description

The Knapsack Problem is a classic optimization problem, where given a set of items with associated profits and weights, the goal is to determine the subset of items to include in a knapsack with a limited capacity such that the total profit is maximized while not exceeding the capacity.

In this implementation, the problem is stated as follows:
- Capacity: `c` (integer) - the maximum weight the knapsack can hold.
- Prices: `p` (list of integers) - the profits associated with each item.
- Weights: `w` (list of integers) - the weights associated with each item.

## Algorithm

The Branch and Cut algorithm is used to find an optimal solution to the Knapsack Problem. It explores the solution space by branching on decisions and cutting off parts of the solution space that cannot lead to an optimal solution, thus reducing the search space.

The algorithm works as follows:

1. Start with an empty branch in which leaves (items) will be appended. The algorithm always tries to append item 1.
2. Branch and Cut iterations are performed until the algorithm finds the optimal solution or reaches the maximum number of iterations (`iter_max`).
3. At each iteration, the algorithm performs three types of steps: NEW LEAF, END OF BRANCH, and AFTER PRUNE OR END OF BRANCH.
4. During the NEW LEAF step, the algorithm adds a new item to the branch if it fits within the knapsack's capacity. The branch's upper bound (UB) is calculated by solving the Knapsack Problem relaxation with the remaining items.
5. The END OF BRANCH step is executed when the algorithm reaches the last item. It calculates the lower bound (LB) of the branch and updates the best solution if a better one is found.
6. The AFTER PRUNE OR END OF BRANCH step is taken when the upper bound (UB) of a branch is less than the current best lower bound (LB). It prunes the branch by moving back to the previous item and exploring other possibilities.

## How to Use

1. Make sure you have Python installed (this code is compatible with Python 3.6 and above).
2. Install the required dependencies: `pandas`, `numpy`, and `gurobipy`.
3. Modify the values of `c`, `p`, and `w` to represent your specific Knapsack Problem instance.
4. Run the script, and it will output the best solution found along with the corresponding branch (subset of items) that maximizes the profit within the knapsack's capacity.

## Example

```python
import pandas as pd
import numpy as np
from gurobipy import *

# ... (copy the knapsack_solver.py code here)

c = 12
p = [12, 12, 11, 6, 2, 10, 8]
w = [4, 5, 3, 3, 2, 1, 2]

print("### Knapsack Problem ###\n")
print("Capacity:\t",c,"\nPrices:\t\t", p,"\nWeights:\t", w)
print("\n### Start Branch & Cut ###\n")

# Run the Branch and Cut algorithm
# ... (the rest of the code)

print("\n### Final solution:",lb,"###")  
print("### Solution branch:",best_branch,"###")
```
