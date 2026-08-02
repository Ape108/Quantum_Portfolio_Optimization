# A Quantum-Classical Hybrid Approach To Portfolio Optimization

## Overview
This repository explores the application of Noisy Intermediate-Scale Quantum (NISQ) technologies to quantitative finance, specifically targeting the mean-variance portfolio optimization problem. Traditional classical optimization, such as the Markowitz model, faces significant computational hurdles as feature spaces grow. This project investigates whether quantum algorithms—specifically the Quantum Approximate Optimization Algorithm (QAOA)—can be utilized to identify high-growth portfolios.

## Methodology & Mathematical Formulation
This project involves an end-to-end pipeline of financial data ingestion, Principal Component Analysis (PCA) for dimensionality reduction, and quantum portfolio optimization. 

To process this on a quantum computer, the classical continuous mean-variance objective was mapped onto a Quadratic Unconstrained Binary Optimization (QUBO) model. The cost function was designed to balance expected returns against the covariance matrix (risk) using binary variables. The energy function formulated for the quantum processor is:

$$E(x)=x^{T}Qx=\sum_{i}Q_{ii}x_{i}+\sum_{i \lt j}Q_{ij}x_{i}x_{j}$$

Where $x\in\{0,1\}^{n}$ represents the binary decision vector for asset selection, and $Q\in\mathbb{R}^{n\times n}$ is the upper-triangular matrix encoding the risk-adjusted returns. 

## Hardware Implementation
The algorithm was successfully executed on a physical IBM Quantum processor rather than relying exclusively on noiseless simulators. Moving from simulation to reality required resolving transpile errors, optimizing circuit depth, and deriving a specific Ising Hamiltonian to correctly encode the cost function into the phase-separator unitary. 

## Results & Performance Metrics
The primary evaluation metrics were the Sharpe Ratio, expected annual return, and volatility.

| Method | Sharpe Ratio | Expected Return | Volatility |
| :--- | :--- | :--- | :--- |
| **Markowitz (Classical Benchmark)** | 2.374 | 18.63% | 7.85% |
| **QAOA (Quantum IBM Processor)** | 0.827 | 18.45% | 22.31% |

**Key Insights:**
* The QAOA circuit identified a portfolio with expected returns (18.45%) nearly identical to the classical baseline (18.63%), validating the correctness of the Hamiltonian formulation. 
* The quantum solution experienced nearly triple the volatility (22.31% vs 7.85%) and a lower Sharpe ratio. This disparity serves as a quantifiable measure of the "noise penalty" (gate errors and decoherence) currently inherent in NISQ devices.

## Future Work
Future iterations of this repository will focus on implementing error mitigation techniques to reduce the hardware noise floor. Specifically, I plan to apply Zero-Noise Extrapolation (ZNE) to better estimate the expectation values of the QAOA Hamiltonian, aiming to move this quantum solution closer to a competitively stable financial tool.

## Detailed Report
For a complete breakdown of the theoretical framework, mathematical derivations, and hardware debugging processes, please refer to the complete report: [`report.pdf`](./report.pdf).
