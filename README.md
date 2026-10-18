---
marp: true
theme: default
math: mathjax
footer: Reservoir Simulation | Amedeka Emperor | amedekaemperor@gmail.com
paginate: true
---

# Petroleum Reservoir Simulation with MATLAB/GNU Octave

Mr. Amedeka Emperor
Research Scientist
[Email](amedekaemperor@gmail.com) | [LinkedIn](https://www.linkedin.com/in/amedeka-emperor-7978b9196/)
<!-- Petro Skill Virtual Learning -->

![bg right height:5in](img/img1.png)

---
## Introduction
* Reservoir simulation is a computer-based engineering technique used to predict how fluids—such as oil, natural gas, and water—flow through underground porous rock formations.
* The main goal of reservoir simulation is to guide management of a subsurface reservoir through future forecasting and prediction, thereby avoiding wasting resources.
* Developing reservoir simulation models combines the disciplines of physics, mathematics, chemistry, reservoir engineering, and computer programming.

---
## Software
* MATLAB Reservoir Simulation Toolbox ([MRST](https://www.sintef.no/projectweb/mrst/download/)) is a free, open-source software platform developed primarily by SINTEF Digital for modeling and simulating fluid flow, transport, and mechanics in porous media.
![bg right height:4in](img/mrst.png)

---
## Software
* The mrst-core is a minimal, stable foundation that provides essential data structures and basic utilities:
    * `Gridding`: routines for defining, processing, and manipulating grids
    * `Solvers`: mathematical and standard procedural solvers (e.g., standard incompressible flow solvers).
    * `Basic Visualization`: 2D/3D plotting and grid mapping.

---
## Software
* MRST includes over 65 specialized add-on modules that users can activate as needed depending on their workflow:
    * `Automatic Differentiation`: modules like ad-core, ad-props, and ad-blackoil enable simulation engines.
    * `Physical Models`: modules for Enhanced Oil Recovery (ad-eor), compositionals, geochemistry, geomechanics (ad-mechanics), and geothermal simulation.
    * `Workflows & Industry:` modules like deckformat to read and parse industry-standard ECLIPSE input simulation decks.
    * `Specialized Applications`: such as co2lab for  modeling of geological CO₂ storage

---
![bg center height:6in](img/mrst2.webp)

---
## Software
* You must use one of the following two numerical computing environments to host and run MRST scripts:
    * `MATLAB (Recommended)`: this is the native environment MRST is designed for.
    * `GNU Octave (Free Alternative)`: most core features of MRST are fully compatible with GNU Octave (version 5.2.0 or newer). 
* Download MRST here: [MRST](https://www.sintef.no/projectweb/mrst/download/)
* In this course, we will using GNU Octave as its a great open-source and free substitute.
* You can download GNU Octave here (windows/linux): [Octave](https://octave.org/download) or here (macos): [Octave](https://octave-app.org).


---
## Basic Theory for Single Phase Flow
* The flow in subsurface reservoirs differs from flows in channels and basins as it takes place inside a porous medium consisting of complex networks of interconnected pores.
![bg right height:4in](img/darcy.png)

---
## Basic Theory for Single Phase Flow
* The fluid properties are sufficiently described by the `viscosity` $\mu$ and `density` $\rho$.
* The porous medium properties are more complex, but the essentials are summed up by the `porosity` $\phi$ and `permeability` $k$.
* `Porosity` is the fractional volume of the interconnected pore space to the total volume. 
* `Permeability` is a description of how easy, or fast, a fluid flows through a porous medium after factoring out the fluid properties. That is, a medium through which the fluid flows more easily has a higher permeability.

---
## Basic Theory for Single Phase Flow
* The first phenomenological description of permeability comes from Henry Darcy. He was working on the water system of Dijon, and considered the flow of water through filter sand.
* Darcy noted the relationship:
$$
\frac{Q}{A}\propto-\frac{(P_o-P_i)}{\mu l}
$$
![bg right height:6in](img/darcy2.png)

---
## Basic Theory for Single Phase Flow

$$
\begin{align}
\frac{Q}{A}&\propto-\frac{(P_o-P_i)}{\mu l}\\
\frac{Q}{A}&\propto-\frac{(p_o+\rho g h_o-(p_i+\rho g h_i))}{\mu l}\\
\frac{Q}{A}&\propto-\frac{(p_o-p_i+\rho g(h_o-h_i))}{\mu l}\\
q&=\frac{Q}{A}=-\frac{k}{\mu}\frac{(\Delta p+\rho g\Delta h)}{l}\\
\end{align}
$$
![bg right height:6in](img/darcy2.png)

---
## Basic Theory for Single Phase Flow
* Assume a volume element $V$ with surface $A$, and let $\vec n$ be the unit normal on the surface pointing out of the volume element.
* The mass flow over the full boundary $A$ is
$$
\int_{A}\rho\vec q\cdot \vec n dA
$$

![bg right height:4in](img/mass.png)


---
## Basic Theory for Single Phase Flow
* The mass of fluid inside the volume element is
$$
\int_{V}\phi\rho dV
$$
![bg right height:4in](img/mass.png)
