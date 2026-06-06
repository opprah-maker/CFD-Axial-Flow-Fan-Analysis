# CFD Analysis of a Computer Cooling Axial-Flow Fan: NACA 0012 Validation, 3D Simulation, and FSI

> **Comprehensive CFD and FSI Analysis** — Module: Mechanical Engineering Modelling & Simulation
> Module Leader: Jhon Paul Roque MRAeS

This repository contains the full CFD and FSI analysis of a 60mm computer cooling axial-flow fan with 6 NACA 0012 profile blades. The work covers three phases: NACA 0012 airfoil validation against experimental wind-tunnel data, 3D numerical simulation of the complete fan assembly, and coupled fluid-structure interaction (FSI) analysis.

[![ANSYS Fluent](https://img.shields.io/badge/ANSYS%20Fluent-CFD-FFB71B?logo=ansys&logoColor=black)]()
[![ANSYS Mechanical](https://img.shields.io/badge/ANSYS%20Mechanical-FFB71B?logo=ansys&logoColor=black)]()
[![CFD](https://img.shields.io/badge/Method-k--%CF%89%20SST-blue)]()
[![Report PDF](https://img.shields.io/badge/Report-PDF-red?logo=adobe-acrobat-reader&logoColor=white)]()

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Report (PDF)](#2-report-pdf)
3. [Fan Geometry & Operating Conditions](#3-fan-geometry--operating-conditions)
4. [Methodology](#4-methodology)
 - [4.1 Phase 1: NACA 0012 Validation](#41-phase-1-naca-0012-validation)
 - [4.2 Phase 2: 3D Fan Simulation](#42-phase-2-3d-fan-simulation)
 - [4.3 Phase 3: FSI Coupling](#43-phase-3-fsi-coupling)
5. [Key Results](#5-key-results)
6. [Figure Reference & Captions](#6-figure-reference--captions)
7. [How to Reproduce](#7-how-to-reproduce)
8. [3D Gaussian Splat Visualisations](#8-3d-gaussian-splat-visualisations)
9. [Topics](#9-topics)

---

## 1. Project Overview

The exponential growth in computational power and miniaturisation of electronic components has created unprecedented thermal management challenges in modern computing systems. Conventional cooling solutions prove inadequate due to increasing power densities and heat generation rates. This study applies advanced CFD and FEA methodologies to design and validate a computer cooling axial-flow fan.

**Software**: ANSYS Workbench 2023 R1 (DesignModeler, Meshing, Fluent, Mechanical, System Coupling)

---

## 2. Report (PDF)

The complete report is available as a PDF:

| Document | File |
|---|---|
| Numerical Modelling: CFD & FSI of an Axial-Flow Fan | [`reports/6-Numerical-Modelling.pdf`](reports/6-Numerical-Modelling.pdf) |

The original submitted copy is preserved at the repository root as `6-Numerical Modelling.docx`.

---

## 3. Fan Geometry & Operating Conditions

| Parameter | Value |
|---|---|
| Impeller diameter | 60 mm |
| Number of blades | 6 |
| Blade profile | NACA 0012 |
| Housing internal diameter | 64 mm |
| Rotational speed | 1,500 RPM |
| Target volumetric flow rate | 6 x 10⁻³m³/s |
| Target pressure head | 10 Pa |
| Blade material | ABS plastic (yield strength 40 MPa) |

---

## 4. Methodology

### 4.1 Phase 1: NACA 0012 Validation

The standard k-omega SST turbulence model is validated against experimental wind-tunnel data for the NACA 0012 airfoil across a range of angles of attack. The lift coefficient predictions agree with experiment within **3.2% accuracy** up to 14° angle of attack, confirming the CFD methodology reliability.

### 4.2 Phase 2: 3D Fan Simulation

Steady-state simulation of the complete fan assembly using ANSYS Fluent with the k-omega SST turbulence model. The rotating reference frame captures the rotor-stator interaction.

**Mesh:**
- Unstructured tetrahedral mesh
- Quality metrics: skewness < 0.1, orthogonal quality > 0.95

**Boundary Conditions:**
| Boundary | Type | Value |
|---|---|---|
| Inlet | Velocity inlet | V = 5m/s |
| Outlet | Pressure outlet | pg = 0Pa |
| Hub / casing | No-slip wall | Standard wall functions |
| Rotating zone | Moving reference frame | omega = 1,500rpm |

### 4.3 Phase 3: FSI Coupling

ANSYS System Coupling links the Fluent pressure field to the Mechanical structural solver. The blade stress and deflection are computed under the aerodynamic load.

**Structural Results:**
| Metric | Value |
|---|---|
| Maximum von Mises stress | 15.2 MPa (at blade root) |
| Safety factor against ABS yield (40 MPa) | 2.6 |
| Maximum blade tip deflection | 0.032 mm (< 0.3\% of chord) |

---

## 5. Key Results

| Metric | Value |
|---|---|
| Optimal blade installation angle | 30° |
| Volumetric flow rate achieved | 6.34 x 10⁻³m³/s (105.7% of target) |
| Pressure rise achieved | 10.8 Pa (108% of target) |
| NACA 0012 lift coefficient validation | within 3.2% of experiment |
| Maximum von Mises stress (FSI) | 15.2 MPa |
| Safety factor | 2.6 |
| Validation vs experiment | within +/- 3\% |

---

## 6. Figure Reference & Captions

All 16 figures are extracted from the original report and renamed sequentially.

| Fig. | Preview | Description |
|---|---|---|
| 1 | <a href="images/figure-01.png"><img src="images/figure-01.png" width="120" alt="Figure 1"></a> | Velocity streamlines from ANSYS Fluent — 3D streamline visualisation showing flow through the fan assembly, colour-coded by velocity magnitude (0–9 m/s), showing tip vortices and wake structure |
| 2 | <a href="images/figure-02.png"><img src="images/figure-02.png" width="120" alt="Figure 2"></a> | Pressure contours on blade surfaces — blade surface pressure distribution from ANSYS CFD-Post, pressure scale blue (−400 Pa) to red (+600 Pa) relative to ambient, spanwise and chordwise variation |
| 3 | <a href="images/figure-03.png"><img src="images/figure-03.png" width="120" alt="Figure 3"></a> | NACA 0012 airfoil mesh — 2D computational mesh around the validation airfoil with boundary layer resolution |
| 4 | <a href="images/figure-04.png"><img src="images/figure-04.png" width="120" alt="Figure 4"></a> | NACA 0012 lift coefficient vs. angle of attack — CFD vs. experimental wind-tunnel data, showing agreement within 3.2% up to 14° AoA |
| 5 | <a href="images/figure-05.png"><img src="images/figure-05.png" width="120" alt="Figure 5"></a> | Fan geometry in ANSYS DesignModeler — 3D model of the 60mm impeller with 6 NACA 0012 blades and cylindrical housing |
| 6 | <a href="images/figure-06.png"><img src="images/figure-06.png" width="120" alt="Figure 6"></a> | Computational domain — fluid volume around the fan with inlet, outlet, and housing walls |
| 7 | <a href="images/figure-07.png"><img src="images/figure-07.png" width="120" alt="Figure 7"></a> | Tetrahedral mesh — global view of the unstructured mesh with inflation layers on blade surfaces |
| 8 | <a href="images/figure-08.png"><img src="images/figure-08.png" width="120" alt="Figure 8"></a> | Mesh quality metrics — skewness and orthogonal quality histograms |
| 9 | <a href="images/figure-09.png"><img src="images/figure-09.png" width="120" alt="Figure 9"></a> | Velocity magnitude contour at mid-span — showing the throughflow velocity distribution and tip leakage |
| 10 | <a href="images/figure-10.png"><img src="images/figure-10.png" width="120" alt="Figure 10"></a> | Static pressure contour — pressure field around the fan assembly |
| 11 | <a href="images/figure-11.png"><img src="images/figure-11.png" width="120" alt="Figure 11"></a> | Turbulent kinetic energy contour — k distribution showing regions of high turbulence near blade tips and housing |
| 12 | <a href="images/figure-12.png"><img src="images/figure-12.png" width="120" alt="Figure 12"></a> | Wall shear stress on blade — viscous stress distribution on blade surfaces |
| 13 | <a href="images/figure-13.png"><img src="images/figure-13.png" width="120" alt="Figure 13"></a> | FSI: von Mises stress on blade — structural stress field from coupled FSI, maximum 15.2 MPa at blade root |
| 14 | <a href="images/figure-14.png"><img src="images/figure-14.png" width="120" alt="Figure 14"></a> | FSI: total deformation — blade deflection under aerodynamic load, maximum 0.032 mm at tip |
| 15 | <a href="images/figure-15.png"><img src="images/figure-15.png" width="120" alt="Figure 15"></a> | Convergence history — residuals for continuity, momentum, k, and omega all below 10⁻⁵ |
| 16 | <a href="images/figure-16.png"><img src="images/figure-16.png" width="120" alt="Figure 16"></a> | Performance curve — flow rate vs. pressure rise at the optimal 30° installation angle |

---

## 7. How to Reproduce

The repository does not include the ANSYS Workbench project files (`.wbpj`, `.agdb`, `.cas.h5`)
because they are several gigabytes in size. To reproduce this work:

1. **Phase 1 — NACA 0012 Validation**:
 - Import the NACA 0012 airfoil coordinates into ANSYS DesignModeler.
 - Generate a 2D mesh with y⁺ ~= 1 boundary layer resolution.
 - Set up ANSYS Fluent with the k-omega SST model and run a sweep of angles of attack from -10° to 20°.
 - Compare CL vs. alpha with experimental data.

2. **Phase 2 — 3D Fan Simulation**:
 - Reconstruct the fan geometry in ANSYS DesignModeler (60mm impeller, 6 NACA 0012 blades).
 - Generate the tetrahedral mesh with inflation layers.
 - Set up the rotating reference frame at 1,500 RPM.
 - Run the steady-state solver with SIMPLE coupling and second-order upwind discretisation.

3. **Phase 3 — FSI Coupling**:
 - Export the Fluent pressure field as a load.
 - Apply the load in ANSYS Mechanical with ABS plastic material properties (E = 2.0GPa, nu = 0.35).
 - Use ANSYS System Coupling for two-way FSI if transient effects are of interest.

The PDF report in `reports/6-Numerical-Modelling.pdf` contains every step, screenshot, and the final contour plots.

---

## 8. 3D Gaussian Splat Visualisations

Two figures from this project were also reconstructed as interactive 3D Gaussian splat previews using TripoSR (stabilityai/TripoSR, CPU inference) plus a custom mesh-to-splat converter. The splats contain about 100 000 surface samples each, with marching-cubes resolution 192. Drag to orbit, scroll to zoom.

### 8.1 Fan rotor assembly (from figure 2)

[![Open interactive 3D Gaussian splat of images/figure-02.png](https://raw.githubusercontent.com/opprah-maker/CFD-Axial-Flow-Fan-Analysis/main/images/figure-02.png)](https://opprah-maker.github.io/splat/?s=fan_02 '3D Gaussian Splat viewer')

[**View in 3D (drag to orbit, scroll to zoom) &#x2192;**](https://opprah-maker.github.io/splat/?s=fan_02) hosted on the portfolio site

### 8.2 Fan blade wireframe (from figure 1)

[![Open interactive 3D Gaussian splat of images/figure-01.png](https://raw.githubusercontent.com/opprah-maker/CFD-Axial-Flow-Fan-Analysis/main/images/figure-01.png)](https://opprah-maker.github.io/splat/?s=fan_01 '3D Gaussian Splat viewer')

[**View in 3D (drag to orbit, scroll to zoom) &#x2192;**](https://opprah-maker.github.io/splat/?s=fan_01) hosted on the portfolio site

### 8.3 Generation notes

- Model: TripoSR (stabilityai/TripoSR), CPU inference, about 20-30 s per image
- Marching cubes: scikit-image (CUDA-only `torchmcubes` was patched out)
- Surface sampling: trimesh, 100 000 points, face-normal quaternion encoding
- Splat format: antimatter15/splat, 32 bytes per splat
- Hardware: GTX 1050, 2 GB VRAM, no CUDA toolkit, CPU mode

The full 3D splat gallery is at <https://opprah-maker.github.io/#3d>.

---

## 9. Topics

`cfd` `ansys-fluent` `fsi` `ansys-mechanical` `axial-fan` `naca-0012` `fluid-dynamics` `aerospace-engineering` `matlab` `k-omega-sst` `pressure-based-solver` `computational-fluid-dynamics` `engineering-simulation` `thermal-management`
