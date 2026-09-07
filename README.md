# Aerodynamic Analysis of NACA 2418 Airfoil

![ANSYS Fluent](https://img.shields.io/badge/CFD-ANSYS%20Fluent%202024%20R1-ea1d24.svg)
![Validation](https://img.shields.io/badge/Benchmark-NACA%20Report%20824-0052cc.svg)
![Course](https://img.shields.io/badge/Course-Fluid%20Mechanics%20II-brightgreen.svg)

A 2D computational fluid dynamics (CFD) investigation evaluating the aerodynamic behavior, boundary-layer development, and force characteristics of the **NACA 2418** cambered airfoil. The study examines both laminar and turbulent regimes across multiple angles of attack, performs a spatial grid independence analysis, and benchmarks numerical results against experimental wind tunnel data.

> 📄 **[Read Full PDF Report](report/mechanical_fluid_2_project.pdf)**

---

## Technical Highlights

* **Spatial Convergence Verification:** Evaluated coarse (9.9k cells), medium (42k cells), and fine (228k cells) mesh resolutions to minimize numerical discretization errors.
* **Empirical Validation:** Benchmarked computed coefficients against experimental wind tunnel data from **NACA Technical Report No. 824** ($Re = 2.9 \times 10^6, \ \alpha = 0^\circ$), yielding a drag coefficient discrepancy of **2.7%**.
* **Flow Regime Sensitivity:** Analyzed aerodynamic performance degradation transitioning from turbulent ($Re = 2.9 \times 10^6$) to laminar flow ($Re = 8 \times 10^4$) caused by early boundary-layer separation.
* **Flow Diagnostics:** Examined chordwise pressure distributions ($C_p$), static/dynamic pressure fields, velocity profiles, wall vorticity, and streamline separation at $\alpha = 0^\circ$ and $\alpha = 8^\circ$.

---

## Operating Parameters & Test Matrix

| Parameter | Laminar Baseline | Turbulent Baseline | High-Lift Case |
| :--- | :---: | :---: | :---: |
| **Airfoil Geometry** | NACA 2418 | NACA 2418 | NACA 2418 |
| **Angle of Attack ($\alpha$)** | $0^\circ$ | $0^\circ$ | $8^\circ$ |
| **Reynolds Number ($Re$)** | $8 \times 10^4$ | $2.9 \times 10^6$ | $2.9 \times 10^6$ |
| **Selected Mesh** | Medium (42,000 Elements) | Medium (42,000 Elements) | Medium (42,000 Elements) |

---

## Key Results & Validation

### 1. Grid Independence Study ($\alpha = 0^\circ, \ Re = 2.9 \times 10^6$)

| Mesh Density | Nodes | Elements | $C_l$ | $C_d$ | Trade-off / Decision |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Coarse** | 10,118 | 9,900 | 0.2020 | $1.06 \times 10^{-2}$ | Significant deviation; insufficient accuracy |
| **Medium (Selected)** | 42,420 | 42,000 | 0.1880 | $1.07 \times 10^{-2}$ | Optimal trade-off between computational cost and accuracy |
| **Fine** | 229,012 | 228,000 | 0.1859 | $1.08 \times 10^{-2}$ | Marginal gain in precision with high CPU overhead |

### 2. Experimental Validation (NACA Report No. 824)

| Parameter | CFD (Medium Mesh) | Experimental (NACA Report 824) | Discrepancy |
| :--- | :---: | :---: | :---: |
| **Drag Coefficient ($C_d$)** | $1.07 \times 10^{-2}$ | $1.10 \times 10^{-2}$ | **2.7% error** |
| **Lift Coefficient ($C_l$)** | 0.1880 | 0.1000 | $\Delta C_l = 0.088$ (Near-zero base) |

### 3. Flow Regime & Angle of Attack Sensitivity

* **Turbulent to Laminar Transition ($\alpha = 0^\circ$):** At low Reynolds number ($Re = 8 \times 10^4$), reduced laminar boundary-layer momentum leads to premature flow detachment. This doubles total drag ($C_d = 0.0219$) and drops lift ($C_l = 0.1118$) compared to turbulent flow ($C_l = 0.1880, \ C_d = 0.0107$).
* **Effect of Increasing Incidence ($\alpha = 0^\circ \rightarrow 8^\circ$):** Lift increases significantly to $C_l = 0.9349$ due to stronger leading-edge upper surface suction. Drag increases to $C_d = 0.0227$ accompanied by rising upper-surface vorticity and trailing-edge flow divergence.

---

## Flow Field Comparisons

| Diagnostic Variable | $\alpha = 0^\circ$ | $\alpha = 8^\circ$ |
| :--- | :--- | :--- |
| **Static Pressure** | Nearly symmetric distribution; minimal net force | Prominent upper-surface suction peak driving lift |
| **Dynamic Pressure** | Smooth, attached flow over both surfaces | Severe acceleration near leading edge; aft pressure loss |
| **Velocity Fields** | Uniform velocity gradients across the boundary layer | Upper-surface velocity acceleration and aft deceleration |
| **Vorticity** | Low, confined vorticity along the profile | Elevated shear layer vorticity indicating shear layer growth |
| **Streamlines** | Smoothly attached trajectories across the entire chord | Streamline divergence in the aft half of the airfoil |

---

## Repository Structure

```text
.
├── report/
│   ├── fluid_2.tex                    # Formatted LaTeX source file
│   └── mechanical_fluid_2_project.pdf # Compiled technical PDF report
├── figures/                           # High-resolution simulation figures
│   ├── Picture1.png - Picture2.png    # Domain and near-wall mesh setup
│   ├── Picture3.png - Picture6.png    # Residual and force convergence histories
│   ├── Picture7.png                   # NACA Report 824 reference polar
│   ├── Picture8.png - Picture9.png    # Laminar vs. turbulent velocity contours
│   ├── Picture10.png - Picture17.png  # Pressure, velocity, and vorticity contours
│   ├── Picture18.png - Picture19.png  # Streamlines and pathlines
│   └── Picture20.png - Picture21.png  # Chordwise Cp distributions
└── README.md
```

---

## Author

* **Sina Zerehposh**
* Department of Mechanical Engineering, Sharif University of Technology
* Course: Fluid Mechanics II (Instructor: Dr. Kamran)

