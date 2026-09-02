---
layout: project
title: Car Design Optimization
description: CFD on car design minimizing drag
technologies: [Fusion, ANSYS CFD]
image: assets/images/newcarvel.png
---


<h2>Motivation</h2>
With growing concerns around climate change and resource sustainability, improving the efficiency of electric vehicles is critical to making them a viable replacement for internal combustion engines. While battery technology continues to advance, aerodynamic design plays a major role in extending vehicle range by reducing energy losses due to drag.

This project focused on designing an electric vehicle body that minimizes aerodynamic drag. By reducing flow separation and turbulence, the goal was to improve overall efficiency and contribute to more sustainable transportation solutions.


<h2>Model</h2>
To evaluate and improve the vehicle design, I used computational fluid dynamics (CFD) to analyze airflow around the car body. The flow was modeled using the Reynolds-Averaged Navier–Stokes (RANS) equations, which describe conservation of mass and momentum in fluid flow. Simulations were performed in ANSYS Fluent using a pressure-based solver for incompressible flow.

Key modeling assumptions included steady-state flow, constant air properties, and negligible compressibility effects at a velocity of 27 m/s. Turbulence was captured using the k-omega GEKO model, which is well-suited for resolving boundary layers and flow separation near the rear of the vehicle.

The simulation domain included realistic boundary conditions such as a moving ground to mimic road conditions, a no-slip condition on the car surface, and symmetry to reduce computational cost. Mesh refinement, including boundary layer resolution, was used to ensure convergence and accuracy of results.

Below was the base car's velocity, and the car had a drag coefficient of 0.30.


<p class="centered-image-block">
  <img src="{{ 'assets/images/velocitycar.png' | relative_url }}">
  <i>Original Car Velocity Contours</i>
</p>


<h2>New Car and New Results</h2>
The redesigned car featured a sharper nose and an extended body length of approximately 4.3 m. The front profile was adjusted to have a more gradual incline from the nose to the highest point of the vehicle, reducing the likelihood of early flow separation. Similarly, the rear geometry was modified with a smoother, more gradual decline to minimize separation in the wake region, where it is most significant.

The tire placement remained fixed to meet the required constraints, and the vehicle height was set to 1.36 m, just above the minimum requirement of 1.35 m. The sharper nose design was inspired by high-performance sports cars, which use low inclines and reduced frontal height to decrease aerodynamic drag.

<p class="centered-image-block">
  <img src="{{ 'assets/images/newcar.png' | relative_url }}">
  <i>New Car CAD</i>
</p>

The resulting design showed a clear improvement in aerodynamic performance. Velocity contour analysis indicated smoother flow over the body with a maximum velocity of 37.9 m/s, and the drag coefficient decreased to approximately 0.25, representing a significant reduction compared to the baseline design.

<p class="centered-image-block">
  <img src="{{ 'assets/images/newcarvel.png' | relative_url }}">
  <i>New Car Velocity Contours</i>
</p>

<p class="centered-image-block">
  <img src="{{ 'assets/images/residual.png' | relative_url }}">
  <i>Drag Coefficient Residuals</i>
</p>


<h2>Limitations</h2>
Several simplifications in the model mean the results likely underestimate real-world drag. Turbulence intensity was lower than typical road conditions, which may have reduced the predicted size of the wake region. Surface roughness and some viscous effects were also neglected, further lowering drag estimates.

Additionally, the analysis focused only on drag and did not account for lift, which was relatively high in some designs and could negatively impact vehicle stability in practice. The model also assumed steady, symmetric flow and did not capture transient or asymmetric effects that occur in real driving conditions.

Finally, while the optimized design improved aerodynamic efficiency, it introduced practical challenges such as reduced interior space and limited trunk accessibility, highlighting the tradeoff between performance and usability.