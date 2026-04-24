# 2D Burgers'Equation (burgers_2D_main)

---

1. Problem Statement: 2D Burgers' Equation

The goal of this project is to simulate the non-linear propagation and diffusion of a velocity field in a 2D domain.

The implementation uses the Finite Difference Method(FDM) to solve the coupled  partial differential equations.


* Governing Equations

The 2D Burgers' euations describe the evolution of velocity components $u$ and $v$ in both space and time:


$x$-momentum: $\frac{\partial u}{\partial t} + u \frac{\partial u}{\partial x} + v \frac{\partial u}{\partial y} = \nu \left(\frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2}\right)$

$y$-momentum: $\frac{\partial v}{\partial t} + u \frac{\partial v}{\partial x} + v \frac{\partial v}{\partial y} = \nu \left(\frac{\partial^2 v}{\partial x^2} + \frac{\partial^2 v}{\partial y^2}\right)$
