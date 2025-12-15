# Wildfire Spread Modeling: A Coupled Reaction-Diffusion-Convection System
This repository contains the numerical solution and analysis for a complex, coupled Reaction-Diffusion-Convection system used to model the spread of a wildfire. The project demonstrates a quantitative approach to modeling a challenging, non-linear physical phenomenon and leverages advanced numerical methods and optimized computing techniques.

---
## Scenario 1: a centered hill with an ignition point on its southwest aspect.
![Boundary/scenario conditions showing topography and a wind map](../ICHill.png)
![Initial $u$ (temperature) and $\beta$ (fuel)](../HillBegin.png)
![A simple fire model over a centered hill with a steady ENE wind for $t_{span} = [0, 8]](simpleFire_hill.gif)
---
## Scenario 2: A drainage with an ignition point in the base of the valley.
![Boundary/scenario conditions showing topography and a wind map](../ICValley.png)
![Initial $u$ (temperature) and $\beta$ (fuel)](../ValleyBegin.png)
![A simple fire model over a centered drainage with a steady ENE wind for $t_{span} = [0, 8]$](simpleFire_Valley.gif)

---

## 1. Project Overview and Core Mathematical Physics
The central objective was to accurately model the fundamental physics governing fire spread based on topography, wind, and fuel. This required discretizing and solving a coupled system of Partial Differential Equations (PDEs) that track heat temperature ($u$) and fuel depletion ($\beta$) over space and time.

* **Complex System Modeling:** The work showcases a deep understanding of **numerical analysis** principles and the stability requirements for solving a highly coupled, **non-linear PDE system**. The ability to correctly formulate the mathematical model (RDC) is a core competency for advanced **scientific computing** and **computer research** roles.
* **Foundation for Modern ML/AI:** By building and solving this high-fidelity, physics-based model, the project generates a rich, time-series dataset that can serve as **ground truth** for training purely **data-driven ML models**. Furthermore, the underlying mathematical structure is the perfect basis for future exploration into techniques like **Physics-Informed Neural Networks**, a key area in modern AI.

---

## 2. Key Results and Engineering Excellence
### Robust Numerical Solution
The primary achievement is the stable and efficient solution of the RDC system as an Initial Value Problem (IVP) using the high-level integrators in `scipy.integrate.solve_ivp`.

* **Methodology and Code Quality:** The implementation utilizes the **Python scientific stack** (`numpy`, `scipy`) to create a modular, reproducible solution within the Jupyter Notebook environment. This repository also adheres to **software engineering** best practices for scientific computing.
* **High-Performance Optimization:** Crucially, the system's core Jacobian matrix was engineered to be represented and processed using **sparse matrices** (`scipy.sparse`). This  optimization significantly reduces the memory footprint and computation time compared to dense matrix approaches, a necessity for scaling to larger spatial grids and a key skill in **data engineering** for high-volume simulation data.

### Demonstration of Realistic Fire Behavior
The simulation successfully modeled realistic, non-linear fire propagation, validating the physical accuracy of the mathematical formulation:

* **Topographical Impact:** The fire spread rate was observed to accelerate uphill and slow/stop against negative slopes, demonstrating the correct physical coupling with the predefined terrain.
* **Convection and Fuel:** The model captured wind-driven **convection forces** dominating the direction of spread, resulting in fire being pushed downwind. It also tracked **fuel depletion** (\beta), correctly showing that the fire front ceases propagation once local fuel is consumed.

---

## 3. Simulation Analysis and Insights
The ability to generate and interpret high-dimensional simulation output is essential for translating complex models into actionable information.

* **Data Interpretation and Visualization:** The project involved **processing and visualizing 3D simulation data** (2D space + time), demonstrating the capability to handle and communicate complex results effectively. This includes generating time-series animations of the fire front and fuel maps.
* **Scenario Analysis:** By modifying initial conditions (e.g., wind speed, spark location, terrain profiles), the model facilitates **scenario analysis**. This provides the necessary framework to derive actionable conclusions about how different environmental variables affect fire behavior, a critical skill for **data analytics** and decision support.

---

## Areas for Extension (Future Work)
The core model provides a strong foundation. Future work focuses on increasing physical fidelity, integrating real-world datasets, and improving computational performance.

1. **Physics: Increase Physical Realism**
* **Goal:** Enhance the model's accuracy by incorporating a more truthful ignition requirement.
* **Key Task:** Add **Fuel Moisture Content ($\psi$)** as a third, dynamic PDE variable to the coupled system.


2. **Application: Ground Truth Integration**
* **Goal:** Transition the model from theoretical scenarios to real-world predictive capability.
* **Key Task:** Import and integrate **Digital Elevation Model (DEM)** (terrain) and **Land Cover** (fuel type) data from a specific real-world location, demonstrating full **data pipeline planning**.


3. **Performance: GPU Acceleration**
* **Goal:** Drastically reduce simulation time to allow for larger grids, longer time scales, and real-time scenario testing.
* **Key Task:** Port the Right-Hand-Side (RHS) function of the differential equation solver to a **GPU-accelerated framework** (e.g., PyTorch or CuPy) to parallelize matrix operations, further demonstrating **computational efficiency** expertise.