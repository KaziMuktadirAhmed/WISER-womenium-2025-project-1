# Quantum Walk Monte Carlo Simulation

This repository hosts a Jupyter notebook that implements a discrete-time quantum walk for Monte Carlo sampling, with a focus on circuit design, methodology, and supporting utilities. It was developed for the WISER Womenium 2025 quantum computing program.

---

# Circuit Methodology

The simulation is based on a multi-layer quantum circuit inspired by a Galton board.

## Quantum Coin Operator: C(θ)

A single-qubit rotation that “flips” the coin:

$$
C(\theta) = 
\begin{pmatrix}
\cos(\theta) & -\sin(\theta) \\
\sin(\theta) &  \cos(\theta)
\end{pmatrix}
$$

Adjusting $(\theta)$ biases the probability of stepping left vs. right.

---

## Shift Operator \( S \)

A controlled operation on the position register, conditioned on the coin qubit:

$$
S = 
\sum_x \left( |x+1\rangle\langle x| \otimes |0\rangle\langle 0| \right)
+
\sum_x \left( |x-1\rangle\langle x| \otimes |1\rangle\langle 1| \right)
$$

---

## Layer Composition

One time-step unitary:

$$
U_{\text{step}} = S \cdot \left( C(\theta) \otimes I_{\text{pos}} \right)
$$

For an \( n \)-step walk:

$$
U = \left( U_{\text{step}} \right)^n
$$

---

## Initial State

$$
|0\rangle_{\text{pos}} \otimes |0\rangle_{\text{coin}}
$$

(Custom superpositions may be used.)


---

## Notebook Implementation

### 1. Setup & Imports  
Load Qiskit, NumPy, Matplotlib, and define global parameters.

### 2. Gate Definitions  
- **`build_coin(theta)`** returns a `QuantumCircuit` with the single-qubit rotation on the coin qubit.  
- **`build_shift(num_qubits)`** constructs multi-controlled X gates to shift the binary-encoded position register.

### 3. Circuit Builder  
- **`build_walk_circuit(n_steps, theta, num_position_qubits)`**  
  1. Initializes registers.  
  2. Iterates `n_steps` times: appends `build_coin(theta)`, then `build_shift()`.  
  3. Adds measurements on the position register.

### 4. Sampling Procedure  

```python
counts = {}
for sample in range(num_samples):
qc = build_walk_circuit(n_steps, theta, num_position_qubits)
result = execute(qc, backend=simulator, shots=1).result()
outcome = max(result.get_counts(), key=result.get_counts().get)
counts[outcome] = counts.get(outcome, 0) + 1
```


Aggregates counts into an empirical distribution.

### 5. Noisy Simulation  
- Load a noise model from Qiskit’s `noise` module (e.g., depolarizing channels).  
- Execute the same circuit on a noisy simulator to observe decoherence effects.  
- Compare results against the ideal (noise-free) distribution to quantify robustness.

### 6. Distribution Generators  
Helper functions for target distributions:  
- **`gaussian_dist(x, mu, sigma)`**  
- **`exponential_dist(x, lambda)`**  
- **`custom_hadamard_dist(x)`** for standard Hadamard-walk shapes.

### 7. Data Processing & Utility Functions  
- **`normalize_counts(counts, num_samples)`** converts raw counts to probabilities.  
- **`plot_histogram(probs, title)`** wraps Matplotlib calls to produce labeled histograms.  
- **`compute_tvd(p, q)`** computes total variation distance:  
  \[
    \mathrm{TVD}(p,q)=\tfrac{1}{2}\sum_x |p(x)-q(x)|.
  \]  
- **`compare_distributions(empirical, target)`** returns TVD, KL divergence, and chi-square statistic.

---

## Compare Distributions Workflow

1. **Empirical vs. Target:**  
   - Normalize measurement counts.  
   - Compute TVD, KL divergence, and chi-square.

2. **Visualization:**  
   - Overlay empirical and theoretical histograms.  
   - Annotate with metric values.

3. **Interpretation:**  
   - Lower TVD indicates closer match.  
   - KL divergence highlights asymmetry if one distribution has zero entries.  
   - Chi-square tests statistical significance of deviation.

---

## Requirements

- Python 3.7 or later  
- Qiskit  
- NumPy  
- Matplotlib  
- Jupyter Notebook

---

## Installation & Execution

```bash
git clone https://github.com/KaziMuktadirAhmed/WISER-womenium-2025-project-1.git
cd WISER-womenium-2025-project-1
pip install -r requirements.txt
jupyter notebook WISER-quantum-walk-monte-carlo.ipynb
```




---

## Author

Kazi Muktadir Ahmed <br>
Tasfia Zaman Samiha <br>
Asif Mohammed Saad