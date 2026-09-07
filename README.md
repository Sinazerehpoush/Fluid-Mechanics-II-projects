# Aerodynamic Analysis of NACA 2418 Airfoil

![ANSYS Fluent](https://img.shields.io/badge/CFD-ANSYS%20Fluent%202024%20R1-ea1d24.svg)
![Validation](https://img.shields.io/badge/Benchmark-NACA%20Report%20824-0052cc.svg)
![Type](https://img.shields.io/badge/Course-Fluid%20Mechanics%20II-brightgreen.svg)

A computational fluid dynamics (CFD) investigation evaluating the aerodynamic characteristics, flow physics, and boundary layer separation over a **NACA 2418** cambered airfoil. The numerical framework evaluates both laminar and turbulent regimes across different angles of attack and validates numerical force coefficients against experimental wind tunnel benchmarks.

---

## Technical Highlights

* **Grid Independence & Verification:** Evaluated spatial convergence using coarse (9.9k cells), medium (42k cells), and fine (228k cells) structured/boundary-layer meshes to minimize numerical diffusion[cite: 2].
* **Empirical Validation:** Benchmarked force coefficients against standard experimental data from **NACA Technical Report No. 824** ($Re = 2.9 \times 10^6, \, \alpha = 0^\circ$), yielding a drag coefficient discrepancy of just **2.7%**[cite: 2].
* **Reynolds Number Sensitivity:** Analyzed aerodynamic performance degradation under laminar flow ($Re = 8 \times 10^4$) versus fully turbulent flow ($Re = 2.9 \times 10^6$) caused by premature boundary layer detachment[cite: 2].
* **Flow Physics Diagnostics:** Quantified chordwise pressure distributions ($C_p$), static/dynamic pressure gradients, wall vorticity, and streamline separation at $\alpha = 0^\circ$ and $\alpha = 8^\circ$[cite: 2].

---

## Operating Parameters & Configurations

| Parameter | Laminar Case | Turbulent Case (Baseline) | High-Lift Case |
| :--- | :---: | :---: | :---: |
| **Airfoil Section** | NACA 2418[cite: 2] | NACA 2418[cite: 2] | NACA 2418[cite: 2] |
| **Angle of Attack ($\alpha$)** | $0^\circ$[cite: 2] | $0^\circ$[cite: 2] | $8^\circ$[cite: 2] |
| **Reynolds Number ($Re$)** | $8 \times 10^4$[cite: 2] | $2.9 \times 10^6$[cite: 2] | $2.9 \times 10^6$[cite: 2] |
| **Adopted Mesh** | Medium (42,000 Elements)[cite: 2] | Medium (42,000 Elements)[cite: 2] | Medium (42,000 Elements)[cite: 2] |

---

## Key Results & Validation

### 1. Grid Convergence Study ($\alpha = 0^\circ, \, Re = 2.9 \times 10^6$)
| Mesh Resolution | Nodes | Elements | $C_l$ | $C_d$ | Outcome / Selection[cite: 2] |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Coarse**[cite: 2] | 10,118[cite: 2] | 9,900[cite: 2] | 0.2020[cite: 2] | $1.06 \times 10^{-2}$[cite: 2] | High numerical error; unviable[cite: 2] |
| **Medium (Selected)**[cite: 2] | 42,420[cite: 2] | 42,000[cite: 2] | 0.1880[cite: 2] | $1.07 \times 10^{-2}$[cite: 2] | Optimal balance of accuracy and compute time[cite: 2] |
| **Fine**[cite: 2] | 229,012[cite: 2] | 228,000[cite: 2] | 0.1859[cite: 2] | $1.08 \times 10^{-2}$[cite: 2] | Marginal precision gain with excessive CPU load[cite: 2] |

### 2. Validation Against NACA Technical Report No. 824
| Parameter | Simulation (Medium Mesh) | Benchmark (NACA Report 824) | Discrepancy |
| :--- | :---: | :---: | :---: |
| **Drag Coefficient ($C_d$)** | $1.07 \times 10^{-2}$[cite: 2] | $1.10 \times 10^{-2}$[cite: 2] | **2.7%**[cite: 2] |
| **Lift Coefficient ($C_l$)** | 0.1880[cite: 2] | 0.1000[cite: 2] | Documented in verification study[cite: 2] |

### 3. Flight Regime & Angle of Attack Comparison
* **Laminar vs. Turbulent ($\alpha = 0^\circ$):** Lower boundary layer momentum in the laminar regime ($Re = 8 \times 10^4$) triggers earlier flow detachment, doubling drag ($C_d = 0.0219$) and cutting lift ($C_l = 0.1118$) compared to the turbulent baseline ($C_l = 0.1880$, $C_d = 0.0107$)[cite: 2].
* **Effect of Pitch ($\alpha = 0^\circ \rightarrow 8^\circ$):** Lift increases nearly fivefold to $C_l = 0.9349$ due to strong suction-side pressure reduction[cite: 2]. The drag coefficient rises to $C_d = 0.0227$ with elevated trailing-edge vorticity and incipient boundary-layer separation[cite: 2].

---

## Visualizations & Contours

| Flow Characteristic | $\alpha = 0^\circ$ | $\alpha = 8^\circ$ |
| :---: | :---: | :---: |
| **Static Pressure**[cite: 2] | Symmetric, balanced profile[cite: 2] | Large upper surface suction peak[cite: 2] |
| **Dynamic Pressure**[cite: 2] | Smooth stagnation & attached recovery[cite: 2] | High forward acceleration; aft drop[cite: 2] |
| **Velocity & Streamlines**[cite: 2] | Uniform, fully attached pathlines[cite: 2] | Trailing-edge divergence & recirculation risk[cite: 2] |
| **Vorticity**[cite: 2] | Confined boundary layer vorticity[cite: 2] | Elevated rotational shear along upper wall[cite: 2] |

---

## Repository Structure

```text
.
├── report/
│   ├── report.tex                 # Cleaned LaTeX source code
│   └── mechanical_fluid_2.pdf     # Full technical PDF report
├── figures/                       # Mesh snapshots, Cp plots, and Fluent contours
│   ├── Picture1.png - Picture2.png   # Computational domain & boundary layer mesh
│   ├── Picture3.png - Picture6.png   # Convergence history curves (Cl, Cd)
│   ├── Picture7.png                  # NACA Report 824 experimental polar
│   ├── Picture8.png - Picture9.png   # Laminar vs. turbulent velocity contours
│   ├── Picture10.png - Picture17.png # Pressure, velocity, and vorticity contours
│   └── Picture18.png - Picture21.png # Streamline traces and Cp distributions
└── README.md
