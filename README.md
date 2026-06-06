# CFD Analysis of an Axial-Flow Cooling Fan

> Computational Fluid Dynamics (CFD) and Fluid-Structure Interaction (FSI) analysis of a
> computer cooling axial-flow fan. Solved in ANSYS Fluent using the standard $k-\epsilon$
> turbulence model with a pressure-based steady solver.

[![ANSYS Fluent](https://img.shields.io/badge/ANSYS%20Fluent-CFD-FFB71B?logo=ansys&logoColor=black)]()
[![CFD](https://img.shields.io/badge/Method-k--%CE%B5%20turbulence-blue)]()
[![Report PDF](https://img.shields.io/badge/Report-PDF-red?logo=adobe-acrobat-reader&logoColor=white)]()

---

## 1. Project Overview

This repository contains the full individual project: a quantitative CFD and FSI simulation
of a computer cooling axial-flow fan. The work covers:

- Geometry preparation in ANSYS DesignModeler and SpaceClaim
- Unstructured tetrahedral mesh with quality metrics
- Steady-state pressure-based solver with the standard $k-\epsilon$ turbulence model
- Rotating reference frame for the rotor-stator interaction
- FSI coupling of fluid pressure loads onto the blade structure
- Validation against wind-tunnel experimental data within $\pm 3\%$

---

## 2. Report (PDF)

The complete individual project report is available as a PDF:

| Document | File |
|---|---|
| Individual Project : CFD & FSI of an Axial-Flow Fan | [`reports/Individual-Project.pdf`](reports/Individual-Project.pdf) |

A plain-text extract is also included in
[`reports/Individual-Project_text.txt`](reports/Individual-Project_text.txt).

The original submitted copy is also preserved at the repository root as
`Computational_Fluid_Dynamics_Analysis_of_Flow_Through_a_Computer_Cooling_Axial_Flow_Fan._55 (3).pdf`.

---

## 3. Methodology

### 3.1 Governing Equations
The incompressible Reynolds-Averaged Navier-Stokes (RANS) equations with the standard
$k-\epsilon$ closure are solved:

$$\frac{\partial}{\partial x_i}(\rho u_i u_j) = -\frac{\partial p}{\partial x_j} + \frac{\partial}{\partial x_i}\left[\left(\mu + \mu_t\right)\left(\frac{\partial u_j}{\partial x_i} + \frac{\partial u_i}{\partial x_j}\right)\right] + \rho g_i$$

with turbulent viscosity $\mu_t = \rho C_\mu k^2 / \epsilon$ and transport equations for
$k$ and $\epsilon$:

$$\frac{\partial(\rho k u_i)}{\partial x_i} = \frac{\partial}{\partial x_i}\left[\left(\mu + \frac{\mu_t}{\sigma_k}\right)\frac{\partial k}{\partial x_i}\right] + G_k - \rho \epsilon$$

$$\frac{\partial(\rho \epsilon u_i)}{\partial x_i} = \frac{\partial}{\partial x_i}\left[\left(\mu + \frac{\mu_t}{\sigma_\epsilon}\right)\frac{\partial \epsilon}{\partial x_i}\right] + C_{1\epsilon}\frac{\epsilon}{k}G_k - C_{2\epsilon}\rho\frac{\epsilon^2}{k}$$

with $C_{1\epsilon} = 1.44$, $C_{2\epsilon} = 1.92$, $C_\mu = 0.09$, $\sigma_k = 1.0$, $\sigma_\epsilon = 1.3$.

### 3.2 Mesh
| Quantity | Value |
|---|---|
| Total elements | 7,805 |
| Total nodes | 4,085 |
| Element type | Tetrahedral (unstructured) |
| Maximum skewness | $< 0.1$ |
| Minimum orthogonal quality | $> 0.95$ |
| Tip clearance | $\le 1.5\,\text{mm}$ ( $< 0.1D$ ) |

### 3.3 Boundary Conditions
| Boundary | Type | Value |
|---|---|---|
| Inlet | Velocity inlet | $V = 5\,\text{m/s}$ |
| Outlet | Pressure outlet | $p_g = 0\,\text{Pa}$ |
| Hub / casing | No-slip wall | Standard wall functions |
| Rotating zone | Moving reference frame | $\omega = 2{,}600\,\text{rpm}$ |

### 3.4 Solver Settings
- Solver: pressure-based, steady
- Pressure-velocity coupling: SIMPLE
- Spatial discretisation: second-order upwind
- Convergence: residuals $< 10^{-5}$ for all transport equations

---

## 4. Key Results

| Metric | Value |
|---|---|
| Optimal blade installation angle | $30^\circ$ |
| Pressure rise | $\Delta p = 78\,\text{Pa}$ |
| Mass flow rate | $\dot{m} = 0.082\,\text{kg/s}$ |
| Efficiency gain over baseline | $+2.1\%$ |
| Validation vs experiment | within $\pm 3\%$ |

---

## 5. Figure Gallery

<table>
<tr><td align="center"><img src="images/figure-01.png" width="240" alt="figure-01.png"/><br/><sub>figure-01.png</sub></td><td align="center"><img src="images/figure-02.png" width="240" alt="figure-02.png"/><br/><sub>figure-02.png</sub></td><td align="center"><img src="images/figure-03.png" width="240" alt="figure-03.png"/><br/><sub>figure-03.png</sub></td><td align="center"><img src="images/figure-04.png" width="240" alt="figure-04.png"/><br/><sub>figure-04.png</sub></td></tr>
<tr><td align="center"><img src="images/figure-05.png" width="240" alt="figure-05.png"/><br/><sub>figure-05.png</sub></td><td align="center"><img src="images/figure-06.png" width="240" alt="figure-06.png"/><br/><sub>figure-06.png</sub></td><td align="center"><img src="images/figure-07.png" width="240" alt="figure-07.png"/><br/><sub>figure-07.png</sub></td><td align="center"><img src="images/figure-08.png" width="240" alt="figure-08.png"/><br/><sub>figure-08.png</sub></td></tr>
<tr><td align="center"><img src="images/figure-09.png" width="240" alt="figure-09.png"/><br/><sub>figure-09.png</sub></td><td align="center"><img src="images/figure-10.png" width="240" alt="figure-10.png"/><br/><sub>figure-10.png</sub></td><td align="center"><img src="images/figure-11.png" width="240" alt="figure-11.png"/><br/><sub>figure-11.png</sub></td><td align="center"><img src="images/figure-12.png" width="240" alt="figure-12.png"/><br/><sub>figure-12.png</sub></td></tr>
<tr><td align="center"><img src="images/figure-13.png" width="240" alt="figure-13.png"/><br/><sub>figure-13.png</sub></td><td align="center"><img src="images/figure-14.png" width="240" alt="figure-14.png"/><br/><sub>figure-14.png</sub></td><td align="center"><img src="images/figure-15.png" width="240" alt="figure-15.png"/><br/><sub>figure-15.png</sub></td><td align="center"><img src="images/figure-16.png" width="240" alt="figure-16.png"/><br/><sub>figure-16.png</sub></td></tr>
<tr><td align="center"><img src="images/figure-17.png" width="240" alt="figure-17.png"/><br/><sub>figure-17.png</sub></td><td align="center"><img src="images/figure-18.png" width="240" alt="figure-18.png"/><br/><sub>figure-18.png</sub></td><td align="center"><img src="images/figure-19.png" width="240" alt="figure-19.png"/><br/><sub>figure-19.png</sub></td><td align="center"><img src="images/figure-20.png" width="240" alt="figure-20.png"/><br/><sub>figure-20.png</sub></td></tr>
<tr><td align="center"><img src="images/figure-21.png" width="240" alt="figure-21.png"/><br/><sub>figure-21.png</sub></td><td align="center"><img src="images/figure-22.png" width="240" alt="figure-22.png"/><br/><sub>figure-22.png</sub></td><td align="center"><img src="images/figure-23.png" width="240" alt="figure-23.png"/><br/><sub>figure-23.png</sub></td><td align="center"><img src="images/figure-24.png" width="240" alt="figure-24.png"/><br/><sub>figure-24.png</sub></td></tr>
<tr><td align="center"><img src="images/figure-25.png" width="240" alt="figure-25.png"/><br/><sub>figure-25.png</sub></td><td align="center"><img src="images/figure-26.png" width="240" alt="figure-26.png"/><br/><sub>figure-26.png</sub></td><td align="center"><img src="images/figure-27.png" width="240" alt="figure-27.png"/><br/><sub>figure-27.png</sub></td><td align="center"><img src="images/figure-28.png" width="240" alt="figure-28.png"/><br/><sub>figure-28.png</sub></td></tr>
<tr><td align="center"><img src="images/figure-29.png" width="240" alt="figure-29.png"/><br/><sub>figure-29.png</sub></td><td align="center"><img src="images/figure-30.png" width="240" alt="figure-30.png"/><br/><sub>figure-30.png</sub></td><td align="center"><img src="images/figure-31.png" width="240" alt="figure-31.png"/><br/><sub>figure-31.png</sub></td></tr>
</table>

---

## 6. How to Run

The repository does not include the ANSYS Workbench project files (`.wbpj`, `.agdb`, `.cas.h5`)
because they are several gigabytes in size. To reproduce this work:

1. Reconstruct the fan geometry in **ANSYS DesignModeler** or import a CAD model into
   **ANSYS SpaceClaim** (the same geometry as the original report).
2. Generate the mesh in **ANSYS Meshing** with the parameters from Section 3.2.
3. Open **ANSYS Fluent**, set the boundary conditions from Section 3.3, choose the standard
   $k-\epsilon$ model with the rotating reference frame, and run the SIMPLE-coupled solver
   to the residuals specified in Section 3.4.
4. For the FSI step, export the pressure field from Fluent as a load and apply it in
   **ANSYS Mechanical** to compute the blade stress / strain.

The PDF report in `reports/Individual-Project.pdf` contains every step, screenshot, and the
final contour plots.

---

## 7. Topics

`cfd` `ansys-fluent` `fsi` `axial-fan` `fluid-dynamics` `finite-element-analysis`
`aerospace-engineering` `matlab` `turbulence-modelling` `pressure-based-solver`
`computational-fluid-dynamics` `engineering-simulation`
