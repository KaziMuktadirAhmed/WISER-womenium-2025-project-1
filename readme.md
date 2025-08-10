
# WISER Quantum Walk Monte Carlo Simulation

## Project Overview

This Jupyter notebook demonstrates a simulation of a quantum random walk on a line, built using the Qiskit framework. A quantum random walk is like a classical random walk—where you flip a coin to decide whether to step left or right—but with quantum effects that allow the walker to explore multiple paths at the same time through superposition and interference. The project uses Monte Carlo methods, which involve running many repeated trials to estimate probabilities, to sample results from quantum circuits. It compares simulations without any errors (ideal conditions) to those with realistic errors from actual quantum computers, helping to show how noise affects quantum behaviors.

## Prerequisites

Before running the notebook, set up your environment to avoid common issues like package conflicts or runtime errors:

- Use Python 3.12 or a similar version that works well with the libraries.
- Install the required packages by running these commands in the notebook:
  ```
  !pip install -q qiskit qiskit-aer matplotlib pylatexenc
  !pip install qiskit-ibm-runtime
  ```
- After installation, restart the runtime (go to Runtime > Restart session in Colab or Jupyter). This step is important because some libraries need a fresh start to load correctly.
- The notebook relies on Qiskit Aer for local simulations and can pull noise models from IBM Quantum devices, but no internet access beyond package installation is needed for basic runs.

These steps ensure the notebook runs smoothly, allowing you to focus on the quantum concepts rather than technical glitches.

## Methodology

The notebook follows a clear, step-by-step process to build, run, and analyze the quantum walk simulation. Each part combines quantum computing ideas with classical techniques like Monte Carlo sampling, making it easier to see how theory meets practice. Below is a detailed breakdown.

### 1. Package Installation and Imports

The process starts by installing and loading the tools needed for the simulation. This includes libraries for creating quantum circuits, running them, and displaying results.

- Installation handles packages like Qiskit (for quantum operations), Qiskit Aer (for simulating circuits on your computer), Matplotlib (for drawing charts), and others.
- Imports bring in specific functions: NumPy helps with math and data handling, QuantumCircuit lets you design the quantum setup, Sampler runs the circuit many times, and tools like plot_histogram create visual outputs.
- Why this first? It sets up a reliable workspace, mixing quantum tools with everyday programming helpers to make the rest of the steps possible.

After this, the notebook is ready for building the core quantum elements.

### 2. Quantum Circuit Construction

Next, the notebook creates a quantum circuit that represents the random walk. Think of the circuit as a set of instructions for quantum bits (qubits) to follow.

- Qubits are assigned roles: One acts as a "coin" to decide direction, while others track the walker's position on a line.
- Initialization: A Hadamard gate puts the coin qubit into superposition, meaning it's both heads and tails at once, creating equal chances for left or right steps.
- Walk steps: For each step in the walk, controlled operations shift the position based on the coin—moving right for one outcome, left for the other. This is repeated for a chosen number of steps, building up interference where paths can add up or cancel out.
- Measurement: At the end, measure all qubits to get the final position, collapsing the quantum possibilities into a observable result.
- Visualization: The circuit is drawn as a diagram using Matplotlib, showing gates and connections clearly.

This step turns abstract quantum ideas into a concrete model, with the diagram helping to verify everything looks right before running.

### 3. Ideal (Noiseless) Simulation

With the circuit ready, the notebook runs it in perfect conditions—no errors or noise—to see the pure quantum behavior.

- Setup: Use the Sampler from Qiskit Aer without any noise, and choose how many "shots" (trials) to run, like 10,000, for good Monte Carlo estimates.
- Execution: Run the circuit, collecting counts of each possible position outcome.
- Processing: Turn counts into probabilities by dividing by the total shots, using NumPy for calculations.
- Visualization: Plot a histogram of probabilities to show the distribution, often revealing wave-like spreads due to interference.

This phase highlights quantum advantages, such as faster exploration than classical walks, by averaging many random samples to approximate the true probabilities.

### 4. Noisy Simulation Setup

To make it more realistic, the notebook adds noise based on real quantum hardware.

- Load a noise model from an IBM device, like 'manhattan', which includes common errors: imperfect gates, measurement mistakes, and decoherence (where quantum states fade over time, like static disrupting a signal).
- Configure the Sampler to include this noise, simulating how a actual quantum computer might perform.

This setup shows the gap between ideal theory and real-world devices, where noise can weaken quantum effects.

### 5. Noisy Simulation Execution

Run the circuit again, now with the noise applied.

- Use the same number of shots for fair comparison.
- Collect and normalize the noisy counts into probabilities.
- Visualize both ideal and noisy histograms side by side, often showing how noise smooths out the sharp quantum patterns, making it look more like a classical random spread.

This step illustrates practical challenges, with visuals making it easy to spot differences.

### 6. Difference Analysis and Comparison

Finally, the notebook quantifies how noise changes the results.

- Per-position differences: For each possible walker position, subtract the noisy probability from the ideal one and take the absolute value to see mismatches.
- Key metrics:
  - Total Variation Distance (TVD): Half the sum of all absolute differences, giving a single number for overall mismatch (0 means identical, 1 means completely different).
  - Jensen-Shannon Divergence (JSD): A measure in bits of how similar the distributions are, considering their information content.
- Output: Show differences in a table or list, plus the metrics, using print statements or charts.

This analysis provides detailed insights into noise impacts, such as which positions are most affected, helping to understand hardware limitations.

## Running the Notebook

Open the notebook in Jupyter or Google Colab, and run cells one by one. Start with small changes, like fewer steps or more shots, to see effects. Outputs include diagrams, plots, and numbers for easy review.

## Potential Extensions

To build on this:
- Try walks in 2D or with more qubits.
- Run on real IBM Quantum hardware if you have access.
- Add error correction methods to reduce noise.

These can deepen exploration of quantum simulations.

## License

This project is released under.

## Acknowledgments

Created with Qiskit from IBM, an open-source toolkit for quantum computing.
