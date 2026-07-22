---
layout: project
title: Composite Landing Gear Design
description: Senior Design Project
technologies: [MATLAB, ANSYS Granta, ANSYS, SolidWorks]
image: assets/images/strut.png
---


For a senior design project, we were asked to create a layup for an object that does not currrently use composites. I chose to work on aluminum landing gear, used for RC aircrafts. The main purpose of this was to increase the strength-to-weight ratio and allow for the landing gear to absorb more of the impact of landing. Some of the constraints included a 4 in clearance from the ground (even with deflection) and transition of wing loading to landing gear loading. 

Ansys Granta was used to find the material best suited for a landing gear that has high strength but also low Young's Modulus to increase flexibility of the material to absorb the energy from impact. 

<p align="center">
  <img src="{{ 'assets/images/Granta.png' | relative_url }}">
  <i>Ansys Granta Material Selection</i>
</p>


4 materials were considered and combinations of these were input into a MATLAB script which used principles of composite design to output interlaminar stresses to determine the best landing gear layup. The script was based on lamination theory equations. 



## Lamination Theory Equations

### A, B, D Matrices

**A matrix:**

$$
A_{i,j} = \sum_{k=1}^{n} Q_{i,j}^{k} (h_k - h_{k-1})
$$

**B matrix:**

$$
B_{i,j} = \frac{1}{2} \sum_{k=1}^{n} Q_{i,j}^{k} (h_k^2 - h_{k-1}^2)
$$

**D matrix:**

$$
D_{i,j} = \frac{1}{3} \sum_{k=1}^{n} Q_{i,j}^{k} (h_k^3 - h_{k-1}^3)
$$

### Strain-Moment Relation

$$
\begin{bmatrix}
\varepsilon^0 \\
\kappa
\end{bmatrix}
=
\begin{bmatrix}
A & B \\
B^T & D
\end{bmatrix}
\begin{bmatrix}
N \\
M
\end{bmatrix}
$$

### Stress in Ply

$$
\{\sigma\}^{k} = [\bar{Q}]^{k} \{\varepsilon^0\} + [\bar{Q}]^{k}_z \{\kappa\}
$$




These results were then validated through using ANSYS ACP to create a composite layup based on the various materials. This was then put into ANSYS Static Structural which provided data for the stresses at different layers and also provided deflection data for the various layups. Two types of loading were used in ANSYS, one for the ground, demonstrating the static loading when the aricraft is taxiing, and dynamic loading where 3g's of acceleration occue on the landing gear strut. The laminate that had the most displacement was [0,45,0]<sub>s</sub> of [S-glass, S-glass, Kevlar]<sub>s</sub>.



<div align="center">
<table>
  <tr>
    <td align="center">
      <img src="{{'assets/images/Dynamicload.png' | relative_url}}"><br>
      <em><i>Stress on 3rd ply due to Dynamic Loading</i></em>
    </td>
    <td align="center">
      <img src="{{'/assets/images/Displacement.png' | relative_url}}" ><br>
      <em><i>Displacement due to Dynamic Loading</i></em>
    </td>
  </tr>
</table>
</div>

