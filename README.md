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

