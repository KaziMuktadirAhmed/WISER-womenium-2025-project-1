## Project 1: Quantum Walks and Monte Carlo


### Team Name: Quantum Probability Pioneers

---

### Team members’ Name & WISER Enrollment ID

- Kazi Muktadir Ahmed, WISER Enrollment ID: <i>gst-DMAX36KxZhsV8kl</i>

- Tasfia Zaman Samiha, WISER Enrollment ID: <i>gst-kRHto5A3fb43ghV</i>

- Asif Mohammed Saad, WISER Enrollment ID: <i>gst-kepn3SoE4kfxABb</i>




### Summary

---

This notebook simulates a quantum random walk using Qiskit, blending quantum superposition and interference with classical Monte Carlo sampling. It compares ideal and noisy simulations to highlight quantum behavior and hardware limitations.

1. **Setup**: Installs and imports Qiskit, Aer, NumPy, and Matplotlib.
2. **Circuit Design**: Uses Hadamard for superposition; controlled shifts simulate quantum steps; measurements extract position data.
3. **Ideal Simulation**: Runs noiseless trials (e.g., 10,000 shots); outputs show quantum interference and faster spread.
4. **Noisy Simulation**: 12 IBM fake backend systems were used to simulate realistic imperfections. Among these, FakeTorino yielded better results for gaussian, hadamard, and exponential distributions, while FakeCusco performed well specifically for the gaussian distribution. Both Qiskit’s transpiler optimization level 3 and the Qiskit AI-transpiler with optimization level 3 were used to optimize the circuit architecture.
5. **Execution & Visualization**: Compares noisy vs. ideal distributions; noise reduces interference, resembling classical randomness.
6. **Analysis**: Computes Total Variation Distance (TVD) and Jensen-Shannon Divergence (JSD) to quantify differences.

#### Key Takeaways

---

- Quantum walks exhibit interference and non-classical spread.
- Monte Carlo sampling enables probabilistic estimation.
- Noise significantly alters quantum behavior, revealing hardware constraints.



#### Potential Extensions

---

To build on this:

- Model the probability distribution derived from a specified probability density function using the Quantum Galton Board Model.
- Run on real IBM Quantum hardware if you have access.
- Add error correction methods to reduce noise.




### Project Presentation deck

---
[Quantum Walks & Monte Carlo Project](https://docs.google.com/presentation/d/1O9KLAqwzCrZOyzNyJj0-fSRWQg6A5aqN/edit?usp=sharing&ouid=105140124381249478954&rtpof=true&sd=true)
