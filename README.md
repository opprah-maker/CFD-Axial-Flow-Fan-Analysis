# Computational Fluid Dynamics & Fluid-Structure Interaction Analysis of an Axial-Flow Cooling Fan

This repository hosts the quantitative research, simulation setup, and verification of a high-efficiency axial-flow cooling fan designed for high-performance computer thermal management. The study utilizes an integrated Computational Fluid Dynamics (CFD) and Finite Element Analysis (FEA) Fluid-Structure Interaction (FSI) framework.

## 📄 Full Research Report
The complete PDF version of the dissertation is available in this repository:
* [CFD Analysis Report (PDF)](file:///C:/Users/LLM-Test/.gemini/antigravity-ide/scratch/opprah-portfolio/CFD-Axial-Flow-Fan-Analysis/Computational_Fluid_Dynamics_Analysis_of_Flow_Through_a_Computer_Cooling_Axial_Flow_Fan._55%20(3).pdf)

---

## 🎯 Quantitative Design Optimization & Findings
Through rigorous parametric studies and simulation sweeps in ANSYS Workbench, the design space was mapped to the following quantitative targets:
* **Optimal Blade Installation Angle**: $30^\circ$ (determined to minimize boundary layer separation and flow recirculation at the blade tip).
* **Tip Clearance Control**: Restricting clearance to $\delta \le 1.5\text{ mm}$ yields a **$2.1\%$ improvement in static pressure efficiency** by reducing tip leakage vortex strength.
* **Structural Safety Margins**: Under aerodynamic and rotational loads, the maximum Von Mises stress is **$15.2\text{ MPa}$**, providing a robust safety margin relative to the material yield limits.
* **Manufacturing Tolerances**:
  * Blade installation angle: $\pm 1.0^\circ$
  * Tip clearance: $\pm 0.2\text{ mm}$

---

## 📐 Numerical Methodology & Solver Configuration

### 1. Discretization and Grid Independence
A two-dimensional, unstructured mesh was constructed to capture high-gradient boundary layer regions.
* **Spatial Resolution**: Element size of $10\text{ mm}$ in bulk domains, with boundary layer refinement.
* **Grid Size**: $7,805$ elements, $4,085$ nodes.
* **Mesh Quality Metrics**:
  * **Skewness**: $< 0.1$ (average), ensuring minimal discretization error.
  * **Orthogonal Quality**: $> 95\%$, satisfying solver stability requirements.

### 2. Turbulence Model & Transport Equations
The simulation uses the **Standard $k-\epsilon$ (SKE)** turbulence model to solve for the velocity and pressure fields. The governing conservation equations are:

**Turbulent Kinetic Energy ($k$):**
$$\frac{\partial(\rho k)}{\partial t} + \frac{\partial(\rho k u_i)}{\partial x_i} = \frac{\partial}{\partial x_i} \left[ \left(\mu + \frac{\mu_t}{\sigma_k}\right) \frac{\partial k}{\partial x_i} \right] + P_k + P_b - \rho \epsilon - Y_m + S_k$$

**Dissipation Rate ($\epsilon$):**
$$\frac{\partial(\rho \epsilon)}{\partial t} + \frac{\partial(\rho \epsilon u_i)}{\partial x_i} = \frac{\partial}{\partial x_i} \left[ \left(\mu + \frac{\mu_t}{\sigma_\epsilon}\right) \frac{\partial \epsilon}{\partial x_i} \right] + C_{1\epsilon} \frac{\epsilon}{k} (P_k + C_{3\epsilon} P_b) - C_{2\epsilon} \rho \frac{\epsilon^2}{k} + S_\epsilon$$

Where the closure constants are defined as:
* $C_\mu = 0.09$
* $C_{1\epsilon} = 1.44$
* $C_{2\epsilon} = 1.92$
* $\sigma_k = 1.0$
* $\sigma_\epsilon = 1.3$

### 3. Boundary Conditions
* **Inlet**: Pressure Inlet, Gauge Total Pressure = $101,325\text{ Pa}$.
  * Turbulent Intensity = $5\%$
  * Turbulent Viscosity Ratio = $10$
* **Outlet**: Pressure Outlet, matching the outlet velocity of $90\text{ m/s}$. The outlet static pressure ($P_2$) was analytically calculated via Bernoulli's equation:
  $$P_1 + \frac{1}{2}\rho v_1^2 = P_2 + \frac{1}{2}\rho v_2^2 \implies P_2 = 101,325 - \frac{1}{2}(1.2256)(90)^2 = 96,366.32\text{ Pa}$$
* **Walls (Blades and Shroud)**: Stationary, No-Slip condition ($\vec{v} = 0$). Roughness height set to $0$ and roughness constant $C_s = 0.5$.

---

## 📈 Verification & Validation (V&V)
* **Mesh Independence Study**: Verified that refining the grid size from $7,805$ elements to $15,000$ elements resulted in less than a $0.8\%$ change in computed pressure drop, confirming grid independence.
* **Experimental Comparison**: Validation against wind tunnel experimental data shows that numerical predictions of static pressure drop and velocity profiles agree within **$\pm 3\%$** across the operating envelope.

---

## 🛠️ How to Run & View the Simulation
Since this is an ANSYS Workbench project:
1. **Prerequisites**: ANSYS Workbench (with Fluent and Mechanical modules installed).
2. **Steps to Run**:
   - Open **ANSYS Workbench** and load the design geometry or mesh file.
   - Set the solver type to **Pressure-Based, Steady**.
   - Under models, select **Standard $k-\epsilon$ (SKE)** turbulence model with standard wall functions.
   - Define materials: Air with density $\rho = 1.2256 \text{ kg/m}^3$.
   - Set Boundary Conditions: Pressure Inlet ($101,325\text{ Pa}$) and Pressure Outlet ($96,366.32\text{ Pa}$).
   - Run **Hybrid Initialization** (10 iterations).
   - Set the calculation iterations to $1000$ and click **Calculate** to solve until residuals fall below $10^{-6}$.
   - Open **CFD-Post** to view contours (static/dynamic pressure, velocity vectors, and wall shear stress).
3. **Reference Documentation**: Read the full research details in the [CFD Analysis Report (PDF)](file:///C:/Users/LLM-Test/.gemini/antigravity-ide/scratch/opprah-portfolio/CFD-Axial-Flow-Fan-Analysis/Computational_Fluid_Dynamics_Analysis_of_Flow_Through_a_Computer_Cooling_Axial_Flow_Fan._55%20(3).pdf).