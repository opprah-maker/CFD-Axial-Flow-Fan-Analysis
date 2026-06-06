# CFD Analysis of an Axial-Flow Cooling Fan — Individual Project

> Computational Fluid Dynamics (CFD) and Fluid-Structure Interaction (FSI) analysis of a
> computer cooling axial-flow fan. Solved in ANSYS Fluent using the standard $k-\epsilon$
> turbulence model with a pressure-based steady solver.

[![ANSYS Fluent](https://img.shields.io/badge/ANSYS%20Fluent-CFD-FFB71B?logo=ansys&logoColor=black)]()
[![CFD](https://img.shields.io/badge/Method-k--%CE%B5%20turbulence-blue)]()
[![Report PDF](https://img.shields.io/badge/Report-PDF-red?logo=adobe-acrobat-reader&logoColor=white)]()
[![Individual Project](https://img.shields.io/badge/University-Individual%20Project-orange)]()

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Report (PDF)](#2-report-pdf)
3. [Methodology](#3-methodology)
   - [3.1 Governing Equations](#31-governing-equations)
   - [3.2 Mesh](#32-mesh)
   - [3.3 Boundary Conditions](#33-boundary-conditions)
   - [3.4 Solver Settings](#34-solver-settings)
4. [Key Results](#4-key-results)
5. [Figure Reference & Captions](#5-figure-reference--captions)
6. [How to Reproduce](#6-how-to-reproduce)
7. [Topics](#7-topics)

---

## 1. Project Overview

This repository contains the **full individual project dissertation**: a quantitative CFD and FSI simulation
of a computer cooling axial-flow fan. The work covers:

- Geometry preparation in ANSYS DesignModeler and SpaceClaim
- Unstructured tetrahedral mesh with quality metrics
- Steady-state pressure-based solver with the standard $k-\epsilon$ turbulence model
- Rotating reference frame for the rotor-stator interaction
- FSI coupling of fluid pressure loads onto the blade structure
- Validation against wind-tunnel experimental data within $\pm 3\%$

**Key outcome**: Optimal blade installation angle of $30^\circ$, yielding $+2.1\%$ efficiency
gain over baseline with pressure rise $\Delta p = 78\,\text{Pa}$ and mass flow
$\dot{m} = 0.082\,\text{kg/s}$.

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

## 5. Figure Reference & Captions

All 31 figures are extracted from the original dissertation and renamed sequentially.
Each figure is linked to its file in the `images/` directory.

| Fig. | File | Description |
|---|---|---|
| 1 | [`figure-01.png`](images/figure-01.png) | Fan geometry overview in ANSYS DesignModeler — full assembly with hub, blades, and shroud |
| 2 | [`figure-02.png`](images/figure-02.png) | Blade profile cross-section showing aerofoil shape and installation angle reference |
| 3 | [`figure-03.png`](images/figure-03.png) | Computational domain extents — inlet, outlet, and periodic boundaries |
| 4 | [`figure-04.png`](images/figure-04.png) | Unstructured tetrahedral mesh — global view of the fluid volume |
| 5 | [`figure-05.png`](images/figure-05.png) | Mesh quality histogram — skewness distribution (max $< 0.1$) |
| 6 | [`figure-06.png`](images/figure-06.png) | Mesh quality histogram — orthogonal quality distribution (min $> 0.95$) |
| 7 | [`figure-07.png`](images/figure-07.png) | Boundary layer mesh detail near blade leading edge |
| 8 | [`figure-08.png`](images/figure-08.png) | Tip clearance region mesh refinement |
| 9 | [`figure-09.png`](images/figure-09.png) | Static pressure contour on blade suction side at optimal angle ($30^\circ$) |
| 10 | [`figure-10.png`](images/figure-10.png) | Static pressure contour on blade pressure side |
| 11 | [`figure-11.png`](images/figure-11.png) | Total pressure contour — rotor-stator interaction region |
| 12 | [`figure-12.png`](images/figure-12.png) | Velocity magnitude contour — throughflow and tip leakage |
| 13 | [`figure-13.png`](images/figure-13.png) | Velocity vector plot — hub-to-shroud flow redistribution |
| 14 | [`figure-14.png`](images/figure-14.png) | Turbulent kinetic energy ($k$) contour |
| 15 | [`figure-15.png`](images/figure-15.png) | Turbulent dissipation rate ($\epsilon$) contour |
| 16 | [`figure-16.png`](images/figure-16.png) | Wall shear stress distribution on blade surface |
| 17 | [`figure-17.png`](images/figure-17.png) | Pressure coefficient ($C_p$) distribution along blade span |
| 18 | [`figure-18.png`](images/figure-18.png) | Blade loading comparison: baseline vs optimised angle |
| 19 | [`figure-19.png`](images/figure-19.png) | Efficiency vs installation angle curve — peak at $30^\circ$ |
| 20 | [`figure-20.png`](images/figure-20.png) | Pressure rise vs installation angle |
| 21 | [`figure-21.png`](images/figure-21.png) | Mass flow rate vs installation angle |
| 22 | [`figure-22.png`](images/figure-22.png) | FSI: von Mises stress contour on blade structure |
| 23 | [`figure-23.png`](images/figure-23.png) | FSI: total deformation contour on blade |
| 24 | [`figure-24.png`](images/figure-24.png) | FSI: stress distribution at blade root (critical region) |
| 25 | [`figure-25.png`](images/figure-25.png) | Validation: CFD vs wind-tunnel pressure data at mid-span |
| 26 | [`figure-26.png`](images/figure-26.png) | Validation: CFD vs wind-tunnel velocity profile at exit |
| 27 | [`figure-27.png`](images/figure-27.png) | Residual convergence history — all equations $< 10^{-5}$ |
| 28 | [`figure-28.png`](images/figure-28.png) | Monitor point convergence — pressure and mass flow |
| 29 | [`figure-29.png`](images/figure-29.png) | Mesh independence study — three mesh densities |
| 30 | [`figure-30.png`](images/figure-30.png) | Tip leakage vortex structure (Q-criterion iso-surface) |
| 31 | [`figure-31.png`](images/figure-31.png) | Summary infographic — key metrics and optimal configuration |

---

## 6. How to Reproduce

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
