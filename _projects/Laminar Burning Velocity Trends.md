---
layout: project
title: Laminar Burning Velocity Trends
description: Velocity Trends due to Pressure
technologies: [LaTeX, Cantera, Python]
image: assets/images/blueflame.png
---

<h2>Motivation</h2>
Understanding how pressure affects flame propagation is critical for designing rocket propulsion systems and high-pressure combustors. Flame speed directly influences how quickly and completely combustion occurs in the chamber, which in turn affects chamber pressure and thrust generation. As an engineer, this also influences design choices for the combustion chamber. This study compares methane (an alkane) and ethylene (an alkene) to determine how fuel chemistry alters pressure sensitivity, providing insight into fuel selection for pressure-sensitive combustion applications.

<h2>Model</h2>
Cantera's free flame solver was used to model a one-dimensional, adiabatic, premixed flame at stoichiometric conditions (φ = 1.0) over a pressure range of 0.1–20 atm. Key modeling choices and assumptions included:
<p class="centered-image-block">
  <img src="{{ 'assets/images/combchart.png' | relative_url }}"  width="500">
</p>




<h2>Results</h2>

Flame speed decreases with increasing pressure, following an approximate power law. Although higher pressure raises collision frequency and slightly increases flame temperature due to suppressed dissociation, one might expect flame speed to rise. Instead, terminating reactions overtake chain-branching at elevated pressures, consuming reactive radicals and slowing flame propagation. This kinetic effect outweighs any temperature-driven gain, leading to a net decrease in flame speed.
When comparing fuels at the same pressure, higher flame temperature generally means higher flame speed. This explains why ethylene (an alkene) burns faster than methane (an alkane). Here, fuel chemistry drives the difference, whereas pressure effects are governed by the shift toward terminating reactions.






<div class="centered-image-block">
  <table>
    <tr>
      <td>
        <img src="{{ 'assets/images/tempvpress.png' | relative_url }}" width="200"><br>
        <em><i>a. Adiabatic Flame Temperature</i></em>
      </td>
      <td>
        <img src="{{ 'assets/images/velpress.png' | relative_url }}" width="200"><br>
        <em><i> b. Flame Speed</i></em>
      </td>
    </tr>
    <tr>
      <td colspan="2" style="text-align: center;">
        <em><i>Free Flame Characteristics vs. Pressure</i></em>
      </td>
    </tr>
  </table>
</div>

<h2>Limitations</h2>


The most significant limitation is the restricted pressure range over which the model is validated. GRI-Mech 3.0 and similar mechanisms are primarily validated against experimental data within 1–10 atm. Predictions below 1 atm or above 10 atm may exhibit inconsistencies due to:
High pressure (>10 atm): Reliability of reaction rates, transport properties, and thermodynamic data becomes increasingly uncertain
Low pressure (<1 atm): Limited validation data reduces model accuracy
One-dimensional assumption: Cannot capture viscous effects, turbulence, or multi-dimensional flow phenomena
Real flame behavior: Turbulent flames exhibit speeds orders of magnitude higher than laminar flames due to enhanced mixing — entirely absent from this framework
These constraints limit direct application to practical combustion devices (gas turbines, internal combustion engines, rockets) where pressures often exceed 10 atm and turbulent flow dominates.




