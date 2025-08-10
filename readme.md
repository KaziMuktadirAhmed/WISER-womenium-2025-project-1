### WISER Quantum Walk Monte Carlo Simulation


### Team Name


### Methodology Overview

This notebook simulates a quantum random walk using Qiskit, blending quantum superposition and interference with classical Monte Carlo sampling. It compares ideal and noisy simulations to highlight quantum behavior and hardware limitations.

1. **Setup**: Installs and imports Qiskit, Aer, NumPy, and Matplotlib.
2. **Circuit Design**: Uses Hadamard for superposition; controlled shifts simulate quantum steps; measurements extract position data.
3. **Ideal Simulation**: Runs noiseless trials (e.g., 10,000 shots); outputs show quantum interference and faster spread.
4. **Noisy Simulation**: Applies IBM device noise model (e.g., 'manhattan'); simulates realistic imperfections.
5. **Execution & Visualization**: Compares noisy vs. ideal distributions; noise reduces interference, resembling classical randomness.
6. **Analysis**: Computes Total Variation Distance (TVD) and Jensen-Shannon Divergence (JSD) to quantify differences.

#### Key Takeaways

- Quantum walks exhibit interference and non-classical spread.
- Monte Carlo sampling enables probabilistic estimation.
- Noise significantly alters quantum behavior, revealing hardware constraints.



#### Potential Extensions

To build on this:

- Model the probability distribution derived from a specified probability density function using the Quantum Galton Board Model.
- Run on real IBM Quantum hardware if you have access.
- Add error correction methods to reduce noise.




### Project Presentation deck