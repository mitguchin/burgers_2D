# 2D Burgers'Equation (burgers_2D_main)

---

1. Problem Statement: 2D Burgers' Equation

The goal of this project is to simulate the non-linear propagation and diffusion of a velocity field in a 2D domain.

The implementation uses the Finite Difference Method(FDM) to solve the coupled  partial differential equations.


* Governing Equations

The 2D Burgers' euations describe the evolution of velocity components $u$ and $v$ in both space and time:


$x$-momentum: 

$\frac{\partial u}{\partial t} + u \frac{\partial u}{\partial x} + v \frac{\partial u}{\partial y} = \nu \left(\frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2}\right)$


$y$-momentum: 

$\frac{\partial v}{\partial t} + u \frac{\partial v}{\partial x} + v \frac{\partial v}{\partial y} = \nu \left(\frac{\partial^2 v}{\partial x^2} + \frac{\partial^2 v}{\partial y^2}\right)$


* Simulation Setup

Domain: A $2 \times 2$ squate grid with $51 times 51$ nodes.

Physical Parameters: Viscosity ($\nu$) = 0.1, Time step ($\Delta$) = 0.001


* Initial Condition(IC):

A constant background velocity of $1.0$ for both $u$ and $v$.

A high-velocity square pulse ($5.0$) located between $0.75 \le x, y \le 1.25$.


* Boundary Conditions(BC):

 Dirichlet conditions: $u=1, v=1$ at all boundaries to maintain stability.

 ---


 2. Techinical Highlights

Numerical Scheme(Discretization)
The solver utilizes an Explicit Finite Difference approach:

* Temporal Derivatives: First-order Forward Difference.

* Advection Terms: First-order Backward Difference (Upwind scheme) to maintain numerical stability during convection.

* Diffusion Terms: Second-order Central Difference for the Laplacian ($\nabla ^2$) terms.


Solver Logic

* Coupled System: The velocities $$ and $$ are updated simultaneously at each time step, accounting for their mutual interaction in the advection terms.

* Spatial Grid: A uniform mesh is generated using np.meshgrid, facilitating vectorized visualization.


---

3. Solver Strategy

A time-marching algorithm was implemented to observe the transition from initial disturbance to steady-state diffusion:


* Memory Allocation: Pre-allocation of arrays for $u$, $v$, and their $(uf, vf)$ to store 500 time steps of data.

* Iterative Loop: Nested spatial loops calculate the velocity update for every interior node $(i,j)$ based on the previous state ($u_n, v_n$).

* Boundary Enforcement: Manual re-assignment of boundary values at the end of each time step to prevent numerical drift.

---

4. Result & Visulization

The solver successfully captures the "smoothing" effect of the initial square pulse spreads and moves across the domain.

* **Initial State:**
The simulation starts with a sharp square pulse for both $u$ & $v$ components.

![Initial u]
<img width="796" height="662" alt="1" src="https://github.com/user-attachments/assets/8fe86a92-e0d3-4dd7-bfce-008bb77fccc2" />

![initial v]
<img width="785" height="660" alt="2" src="https://github.com/user-attachments/assets/9b5447c8-2c03-49b9-8958-9dc3d2e093ad" />

**Figure 1:** 
Initial sharp gradients established at the start of the simulation.

---

* **Intermediate Transition:**
As time progresses, the nonlinear convection terms move the pulse, while viscous diffusion begins to smooth the sharp edges.

![Intermediate u]
<img width="789" height="665" alt="5" src="https://github.com/user-attachments/assets/de9c5089-094d-43b0-bd51-a38e8fdfec08" />

**Figure 2:** 
Intermediate state showcasing the beginning of the smoothing effect.

---

* **Final State & Convergence:**
 The pulse eventually evolves into a smooth bell-shaped distribution, demonstrating the dissipation of energy over time.


![Final u]
<img width="782" height="668" alt="3" src="https://github.com/user-attachments/assets/08b076c9-2e64-4327-b70c-6989ef0af016" />

![Final v]
<img width="790" height="664" alt="4" src="https://github.com/user-attachments/assets/5c949a56-cdd2-4e71-ac0e-0a86a237cdd1" />

**Figure 3:**
Final predicted velocity fields for $u$ & $v$ components. 

---

* **Reference Check:**
Additional visulization confirms the consistency of the 2D flow field.

![Final v Reference]
<img width="790" height="664" alt="6" src="https://github.com/user-attachments/assets/3b3658c3-895a-4656-83fe-29e9a427debb" />


* Time Evolution: Snapshots(e.g., at $t=30$) demonstrate how the initial square pulse spreads and moves across the domain.

* Color Mapping: High-fidelity jet colormaps are used to scale velocity magnitudes, clearly showing the dissipation of kinetic energy over time.

---

5. Implemetation Details

Framework: Pure Python/NumPy for numerical computation.

* Key Libraries:*Numpy:
Used for multi-dimensional array manipulation & grid generation.

* Matplotlib/Seaborn:
Utilized for generating scientific contour plots and heatmaps.

* Hardware: Optimized for CPU-based oterative processing.

* Precision: High-resolution time-stepping ($\Delta t = 0.001$) ensures the Courant-Friedrichs-Lewy(CFL) condition is satisfied for stability.
