---
layout: project
title: Papa's Planeria - Glider Design
description: Aerodynamics Design Project
technologies: [Aircraft Design, Aerodynamics, SolidWorks, Hand Fabrication]
image: assets/images/glider.png
---

<h2>Introduction</h2>
The motivation for this project was to design a glider capable of collecting atmospheric data on Tarrytown, a fictional planet with distinct atmospheric conditions, ahead of a future human mission. Before scaling up to a Tarrytown-ready design, the glider first had to be built and tested on Earth to validate sizing and performance. The design goal was to maximize flight time over a 15 meter distance. Our approach was to select a wingspan and aspect ratio suited to Earth's atmospheric conditions, using a rectangular wing with no dihedral or taper for ease of manufacturing, paired with a conventional tail to counteract the wing's lift moment. We selected the S9037 airfoil with 9% camber for its strong low-Reynolds-number performance, which suited our target of maximizing flight duration.

<h2>Earth Glider Design</h2>

**Airfoil Selection**

The S9037 airfoil with 9% camber was chosen for its slight camber, which increases lift generation, its strong performance at low Reynolds numbers, and its ability to generate meaningful lift even at negative angles of attack.

<p class="centered-image-block">
  <img src="{{ 'assets/images/s9037-airfoil-polars.png' | relative_url }}">
  <i>S9037 Airfoil Shape and Cl/Cd Performance Curves</i>
</p>

**Wing and Tail Sizing**

An aspect ratio of 7 was selected, on the higher end of the typical 4.5–7.5 range for gliders, since higher aspect ratios reduce induced drag. With an 80 cm wingspan (set by available material), this gave a chord length of 11.43 cm. The vertical stabilizer was sized using a tail volume coefficient method:

$$
v_v = \frac{S_v\, l_v}{S\, b}
$$

Using $l_v = 30$ cm and a tail volume ratio $v_v = 0.035$ (within the typical 0.02–0.05 range), the required vertical stabilizer surface area was found to be $S_v = 85.33\ \text{cm}^2$. A trapezoidal shape was chosen for the vertical stabilizer to reduce stagnation pressure at the leading edge and encourage upward airflow. The horizontal stabilizer was sized as 15% of the wing surface area (within the recommended ⅛–⅙ range), giving $137.145\ \text{cm}^2$, realized as a 9.14 cm × 15 cm rectangle.

<p class="centered-image-block">
  <img src="{{ 'assets/images/glider-sizing-sketch.png' | relative_url }}">
  <i>Hand Calculations and Dimensioned Sketch of the Earth Glider</i>
</p>

**Fabrication**

The fuselage used roughly 40 cm of spruce wood, with ⅛" balsa wood (~350 cm² total, oversized to account for cutting losses) for the stringers, ribs, and tail. Only the top half of each airfoil profile was laser cut to reduce mass, and approximately ⅓ of the provided clay was packed into the nose to shift the center of gravity forward toward the quarter-chord point. Tissue paper (~1200 cm²) was applied to smooth the airfoil surfaces, and the assembly was completed with super glue.

<p class="centered-image-block">
  <img src="{{ 'assets/images/assembled-glider-photo.png' | relative_url }}">
  <i>Assembled Earth Glider</i>
</p>

<h2>Earth Glider Performance</h2>

Using the airfoil's maximum lift coefficient ($C_{L,max} = 1.3$) and setting lift equal to weight at standard sea level, the flight velocity and key non-dimensional parameters were calculated:

$$
L = \frac{1}{2} C_L \rho V^2 S
$$

$$
V = \sqrt{\frac{L}{\frac{1}{2}\rho S C_L}} = 6.864\ \text{m/s}
$$

$$
M = \frac{V}{343} = 0.02
$$

$$
C_{D_i} = \frac{C_L^2}{\pi\, AR} = 0.077
$$

$$
F_{D_i} = \frac{1}{2} C_{D_i}\, \rho\, A\, V^2 = 0.203\ \text{N}
$$

$$
Re = \frac{\rho V L}{\mu} = 55{,}554
$$

The resulting velocity was consistent with observed flight behavior during launch testing.

<h2>Tarrytown Glider Design</h2>

To size the Tarrytown glider, we assumed no skin drag and matched the earth glider's Mach and Reynolds numbers to Tarrytown's atmospheric conditions: gravity $\tfrac{1}{10}$ of Earth's, viscosity 1.5× lower, density 150× lower, and a speed of sound of 120 m/s.

$$
M = 0.02 \;\Rightarrow\; V_{TT} = 2.4\ \text{m/s}
$$

$$
Re = 55{,}554 = \frac{\rho_{TT} V_{TT} L_{TT}}{\mu_{TT}} \;\Rightarrow\; L_{TT} = 32.69\ \text{m (chord)}
$$

Matching these dimensionless parameters gave a scale factor of about 286× relative to the Earth glider. This produced a Tarrytown wingspan of 228.9 m (preserving the same aspect ratio of 7), a rectangular horizontal stabilizer of 26.14 m × 42.9 m, and a vertical stabilizer surface area of $2.44\ \text{m}^2$.

Estimating mass from the scale factor (~90 kg, increased to a 120 kg design tolerance) and setting lift equal to weight under Tarrytown gravity:

$$
L = \frac{1}{2} C_L \rho_{TT} V_{TT}^2 S \;\Rightarrow\; C_L = 0.668
$$

$$
C_{D_i} = \frac{C_L^2}{\pi\, AR} = 0.02
$$

<h2>Discussion</h2>

**Flight Time Analysis**

Using basic kinematics, the Earth glider — launched from a height of 1.6 m — was found to take 2.185 s to cover the required horizontal distance of 15 m:

$$
x = V_{0x}t, \qquad t = \frac{d}{V_{0x}} = \frac{15}{6.864} = 2.185\ \text{s}
$$

$$
y - h = -\frac{1}{2}g t^2 \;\Rightarrow\; y = 1.6 - \frac{1}{2}(9.81)(2.185)^2 = -21.824\ \text{m}
$$

This showed that, due to our own physical height limitations at launch, the Earth glider would strike the ground before reaching the full 15 m distance. On Tarrytown, without this height constraint, the glider could launch from a greater height of 19.160 m, giving it 6.25 s of flight time to cover the same distance:

$$
t = \frac{d}{V_{0x}} = \frac{15}{2.4} = 6.25\ \text{s}, \qquad h = \frac{1}{2}g_{TT}t^2 = \frac{1}{2}\left(\frac{9.81}{10}\right)(6.25)^2 = 19.160\ \text{m}
$$

**Validity and Future Improvements**

We consider the Earth glider a reasonable approximation for the Tarrytown design, since both are matched on Reynolds and Mach number despite Earth's launch-height limitations. Going forward, we identified several improvements: reducing mass through cutouts in the tail (and correspondingly less nose clay), using the full airfoil profile rather than just the top surface to generate more lift and simplify tissue paper wrapping, and revising the stringer notch geometry to avoid cutting off the trailing edge. We are still weighing whether to reduce or increase overall mass, since our test flight showed the glider was light but not very stable in wind. We also mistakenly bonded the vertical stabilizer in the wrong orientation during assembly, an error to correct in the next iteration.
