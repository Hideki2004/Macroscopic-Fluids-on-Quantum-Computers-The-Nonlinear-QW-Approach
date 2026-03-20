# Macroscopic Fluids on Quantum Computers: The Nonlinear QW Approach

## 📌 Abstract
The **long-term vision** of this research is to simulate classical macroscopic fluid dynamics (e.g., Navier-Stokes equations) on Fault-Tolerant Quantum Computers (FTQC). While classical Computational Fluid Dynamics (CFD) faces severe memory bottlenecks at high resolutions, quantum computing offers a promising paradigm shift due to its exponentially large state space. However, establishing a scalable quantum framework for macroscopic fluid equations is challenging due to the inherent unitarity and linearity of quantum mechanics.

The **specific scope of this Unitary Fund project** is to propose and validate a novel theoretical framework that seamlessly introduces **irreversibility (viscosity)** and **nonlinearity (advection)** into Quantum Walks (QW). By prioritizing spatial efficiency via a 1-ancilla architecture, we aim to provide a foundational algorithm for classical fluid simulations on future quantum hardware.

## 🔬 Theoretical Framework: The "1-Ancilla" Architecture
We overcome the fundamental limitations of standard QWs through a highly resource-efficient 1-ancilla model.

### 1. Viscosity via Open Quantum Dynamics
To replicate the energy dissipation characteristic of viscous fluids, we model the system as an Open Quantum System. 
By entangling the primary walker qubits with a single ancilla qubit representing a thermal bath, and subsequently performing a trace-out operation, we introduce controlled decoherence. This phase relaxation selectively dampens the off-diagonal elements of the density matrix, smoothly transitioning the ballistic quantum walk into a diffusive (viscous) regime without losing probability mass.

### 2. Nonlinearity via Density-Dependent Phase Shift
To capture the nonlinear advection term $(v \cdot \nabla)v$, we draw mathematical inspiration from the optical Kerr effect. 
We introduce a nonlinear operator $\hat{N}(\rho)$ that applies a localized phase rotation directly proportional to the probability density $d(x,t)$:

$$\hat{N}(\rho) = \sum_{x} \exp(i g \cdot d(x,t)) |x\rangle\langle x| \otimes \hat{I}_c$$

Through the Madelung transform relation ($v \propto \nabla S$), this self-induced phase gradient acts as a dynamic velocity field, enabling the quantum fluid to exhibit macroscopic self-advection.

### 3. The Master Equation
The complete discrete-time evolution $\rho(t) \rightarrow \rho(t+\Delta t)$ is elegantly expressed as a sequence of completely positive trace-preserving (CPTP) maps and unitary operators:

$$\rho(t+\Delta t) = \mathcal{S}_{shift}\Big(\mathcal{E}_{visc}\big(\mathcal{C}_{coin}(\mathcal{N}_{nonlinear}(\rho(t)))\big)\Big)$$

## 🎯 Project Roadmap & Unitary Fund Milestones
The foundational theoretical mapping is established. The primary goal of this project is to bridge this theory with verifiable numerical simulations and open-source software:

- **Month 1: Reference Implementation**
  Develop a flexible matrix-based numerical simulator in Python/Qiskit to execute the proposed non-unitary, nonlinear QW circuits.
- **Month 2: 2D Fluid Dynamics Validation**
  Simulate canonical fluid scenarios (e.g., flow around a cylindrical obstacle) to verify the emergence of macroscopic wake formations and scattering.
- **Month 3: Theoretical Exploration & Open Science**
  Investigate the mathematical connection between the proposed QW model and the Lattice Boltzmann Method (LBM) framework. The theoretical findings, challenges encountered, and full simulation results will be documented and published as an interactive Jupyter Notebook whitepaper.
