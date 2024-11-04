# Commodity Distribution Optimization in Directed Graph

This repository contains a Python implementation of a convex optimization solution to minimize the cost of distributing a commodity across a directed graph. The graph includes suppliers and consumers at various nodes, and the goal is to find the most cost-effective way to transfer the commodity from suppliers to consumers.

## Problem Overview

Consider a directed graph with vertices representing locations that either supply or consume a specific commodity. Each vertex has a known supply or demand, denoted by \( b \), with negative values indicating demand (consumers) and positive values indicating supply (suppliers). 

The edges between vertices represent possible transfer paths for the commodity, with each edge assigned a cost of transfer and a capacity limit of 6 units.

The objective of the optimization is to determine the quantity of the commodity that should be transferred along each edge to satisfy all supply and demand requirements while minimizing the total transfer cost.

## Solution

The Python solution uses the `cvxpy` library for formulating and solving the optimization problem. The problem is structured as follows:

- **Objective Function**: Minimize the total transfer cost across all edges.
- **Constraints**:
  - Flow constraints to ensure the correct amount of commodity flows into and out of each vertex according to the supply/demand vector \( b \).
  - Non-negativity and capacity constraints to ensure each edge transfer quantity remains between 0 and 6 units.

## Mathematical Formulation

The optimization problem is formulated with:

- **Cost vector** \( c \), containing the cost associated with each edge.
- **Flow constraints** represented by matrix \( A \) and vector \( b \).
- **Capacity constraints** for each edge.

The optimization problem is defined as:

$$
\text{minimize }\quad c^T x
$$
$$
\text{subject to: }\quad A x = b, \quad 0 \leq x \leq 6
$$

where \( x \) is the vector representing the quantity of commodity transferred across each edge.

## Code

The code to solve the optimization problem is structured as follows:

1. **Imports**:
   - `numpy` for array operations.
   - `cvxpy` for defining and solving the convex optimization problem.
2. **Parameter Definition**:
   - `c`: Cost vector for each edge.
   - `A_array`: Matrix defining flow constraints based on the graph structure.
   - `b_array`: Supply/demand vector for each vertex.
3. **Variable Declaration**:
   - `x`: Decision variable representing the amount of commodity to be transferred along each edge.
4. **Objective Function**:
   - Defined as the product of `c` and `x`, aiming to minimize the total cost.
5. **Constraints**:
   - Equality constraints to satisfy supply and demand at each vertex.
   - Capacity constraints for each edge.
6. **Solution and Output**:
   - The problem is solved, and the results are displayed, including the optimal transfer quantities for each edge.

## How to Run

To execute this code, ensure you have Python and `cvxpy` installed:

```bash
pip install numpy cvxpy
```

Run the Python script:

```bash
python optimization_solution.py
```

The script outputs:
- The minimized total cost.
- The optimal transfer quantities for each edge.
- Verification that the constraints are satisfied.

## Example Output

Upon running the code, you will see results similar to:

```
Optimal Cost: 98.0
Optimal Transfer Quantities: [6, 4, 6, 0, 0, 1, 4, 1, 5]
```

## Dependencies

- Python 3
- `cvxpy` library
- `numpy` library

## License

This repository is licensed under the MIT License. See `LICENSE` for details.
