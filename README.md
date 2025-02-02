Quantum Factorization using Shor's Algorithm

Overview

This project implements Shor's Algorithm using the Quantum Rings Simulator to factorize large semiprime numbers. Shor’s Algorithm exploits quantum parallelism to efficiently find the prime factors of a given number N by determining the periodicity of modular exponentiation.

Algorithm Steps

Choose a Random Base (a): Pick a number  such that .

Check GCD: If gcd(a, N) ≠ 1, then gcd gives a factor immediately.

Quantum Phase Estimation:

Apply Hadamard gates to create superposition.

Use modular exponentiation to find the period r.

Apply the Inverse Quantum Fourier Transform (IQFT) to extract r.

Classical Computation:

If r is even, compute gcd(a^{r/2} - 1, N) and gcd(a^{r/2} + 1, N).

If these are valid factors, return them; otherwise, retry with another a.

Prerequisites

Python 3.x

Quantum Rings API access

Required Python Libraries:

pip install numpy matplotlib QuantumRingsLib

Setup & Execution

Register with Quantum Rings and obtain an API token.

Modify provider settings in the script:

provider = QuantumRingsProvider(token="YOUR_TOKEN_HERE", name="YOUR_EMAIL")

Run the script:

python shors_algorithm.py

Example Execution (N = 143):

Factors of 143: 11, 13

Challenges Faced

Choosing the correct base (a): Some values of a do not yield useful periods, requiring multiple trials.

Quantum Circuit Depth: Factoring larger numbers (e.g., 143) increases the number of gates significantly, making execution costly.

Noisy Results: Quantum measurement noise can affect period estimation, requiring multiple executions.

Learnings & Insights

Optimization of Modular Exponentiation can significantly reduce gate complexity.

Choosing good values of a increases success probability.

Quantum simulators provide a great way to test quantum algorithms without real quantum hardware limitations.


Future Work

Extend the implementation to handle larger numbers (e.g., 561 or 391).

Explore hybrid quantum-classical optimizations to improve efficiency.

Test execution on real quantum hardware instead of a simulator.

Acknowledgments

Quantum Rings for providing the simulator.

Peter Shor for pioneering quantum factorization.

