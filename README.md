# Quantum Portfolio Optimization

## About The Project
Portfolio optimization is a classic challenge in finance: how to best allocate investments among various assets to maximize returns for a given level of risk. As the number of assets grows, this becomes an NP-hard problem, making it computationally intensive for classical computers to find the truly optimal solution.

This project aims to tackle this challenge by:

1. Reframing a classical finance model (e.g., Mean-Variance Optimization) into a Quadratic Unconstrained Binary Optimization (QUBO) problem. This mathematical formulation is essential for making the problem compatible with quantum annealers and certain gate-based quantum algorithms.

2. Implementing the Quantum Approximate Optimization Algorithm (QAOA), a hybrid quantum-classical algorithm, to solve the QUBO. The algorithm will be designed to find the optimal asset weights that maximize the portfolio's risk-adjusted return.

3. Demonstrating a potential quantum advantage for a practical, real-world optimization task that pushes the limits of classical computation.

The entire workflow, from data ingestion to quantum circuit execution, will be developed within this project.
