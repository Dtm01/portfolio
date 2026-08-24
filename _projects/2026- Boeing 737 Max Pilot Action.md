---
layout: project
title: Boeing 737 Max 9 Pilot Action Simulation
description: Pilot Action Simulation
technologies: [MATLAB]
image: asstes/images/lionair.jpg
---

<h2>Background</h2>
For this project, I studied the Lion Air Flight 610 crash involving the Boeing 737 MAX and its Maneuvering Characteristics Augmentation System (MCAS). Shortly after takeoff, a faulty angle-of-attack sensor sent falsely high readings to the flight control system, triggering MCAS to repeatedly command nose-down stabilizer trim despite the aircraft not actually being in a stall. The pilots fought the automatic trim inputs for roughly thirteen minutes before the aircraft crashed into the Java Sea, killing all 189 people on board. The goal of this project was to model the longitudinal dynamics behind the accident and determine what exactly happened, and whether it was recoverable.

<h2>Mathematical Model</h2>

#### Longitudinal Equations of Motion

$$
m\frac{dV}{dt} = -\frac{1}{2}\rho S V^2 C_x + F - mg_0 \sin\gamma
$$

$$
-mV\frac{d\gamma}{dt} = -\frac{1}{2}\rho S V^2 C_z + mg_0 \cos\gamma
$$

$$
B\frac{dq}{dt} = \frac{1}{2}\rho S l V^2 C_m
$$

$$
\frac{d\alpha}{dt} + \frac{d\gamma}{dt} = q
$$

$$
\frac{dh}{dt} = V\gamma
$$

#### Aerodynamic Force and Moment Coefficients

$$
C_z = C_{z_\alpha}\alpha + C_{z_{\delta m}}\delta_m
$$

$$
C_x = C_{x_0} + kC_z^2
$$

$$
C_m = C_{m_0} + C_{m_\alpha}\alpha + C_{m_{\delta m}}\delta_m
$$

#### Thrust Model

$$
F = \frac{\rho}{\rho_{SL}} S F_0 \delta_x
$$

#### Coefficients With MCAS (Empennage Deflection $\delta_e$)

$$
C_z = C_{z_\alpha}\alpha + C_{z_{\delta m}}\delta_m + C_{z_{\delta_e}}\delta_e
$$

$$
C_m = C_{m_0} + C_{m_\alpha}\alpha + C_{m_{\delta m}}\delta_m + C_{m_{\delta_e}}\delta_e
$$

<h2>MCAS Coefficient Derivation</h2>
MCAS adjusts pitch by deflecting the horizontal stabilizer (empennage), which changes the empennage's angle of attack $\alpha_e$ and its lift coefficient $C_{z_e}$. The empennage and wing lift coefficients relate to the aircraft's overall lift coefficient through:

$$
S_w C_{z_w} + S_e C_{z_e} = S C_z \qquad \text{(1)}
$$

and the aircraft's zero-lift moment coefficient is impacted by $C_{z_e}$ through:

$$
S_w C_{z_w} l_{wg} + S_e C_{z_e} l_{eg} = -S l\, C_{m_0} \qquad \text{(2)}
$$

The empennage lift coefficient is modeled as $C_{z_e} = C_{z_{e_\alpha}}\alpha_e$, where the lift-curve slope comes from thin airfoil theory:

$$
C_{z_{e_\alpha}} = \frac{2\pi}{1 + \dfrac{2}{AR_e}}
$$

Using an empennage aspect ratio of $AR_e = 4.3$ gives $C_{z_{e_\alpha}} \approx 4.29$. The empennage angle of attack is modeled as:

$$
\alpha_e = -\varepsilon + \alpha + \delta_{e_0} + \delta_e
$$

At zero angle of attack, $\alpha_e = -\varepsilon + \delta_{e_0} + \delta_e$, so any MCAS-driven change can be written:

$$
C_{z_e} = C_{z_{e,0}} + C_{z_{e_\alpha}}\delta_e
$$

Substituting into the moment balance at zero angle of attack:

$$
S_w C_{z_w} + S_e C_{z_e} + S_e C_{z_{e_\alpha}}\delta_e = S C_z + S\,\Delta C_z
$$

Using Equation (1) to cancel the leftmost terms and the $SC_z$ term leaves:

$$
S_e C_{z_{e_\alpha}}\delta_e = S\,\Delta C_z
$$

Rearranging gives the MCAS contribution to the lift coefficient:

$$
C_{z_{\delta_e}} = \Delta C_{z_{\delta_e}} = \frac{S_e}{S} C_{z_{e_\alpha}}
$$

Using estimated 737 MAX reference and empennage areas, this yields $C_{z_{\delta_e}} \approx 1.08$.

Following the same process for Equation (2):

$$
S_w C_{z_w} l_{wg} + S_e C_{z_e} l_{eg} + S_e l_{eg} C_{z_{e_\alpha}}\delta_e = -S l\, C_{m_0} - S l\, \Delta C_m
$$

which reduces to:

$$
S_e l_{eg} C_{z_{e_\alpha}}\delta_e = -S l\, \Delta C_m
$$

Rearranging gives the MCAS contribution to the moment coefficient:

$$
C_{m_{\delta_e}} = \Delta C_{m_{\delta_e}} = \frac{-S_e\, l_{eg}}{S\,l}\, C_{z_{e_\alpha}}
$$

Using the estimated surface areas along with reference lengths $l_{eg} = 15\text{ m}$ and $l = 4.24\text{ m}$, this yields $C_{m_{\delta_e}} \approx -3.82$.

<h2>Analysis</h2>

**Pre-MCAS Pseudo-Equilibrium**

The pilots maintained control until reaching an altitude of roughly 600 m, at which point MCAS activated and the aircraft was lost. Using known pre-MCAS flight conditions ($h = 600$ m, $V = 130$ m/s, $\gamma = 10°$), the pseudo-equilibrium equations gave a trim state of $\alpha = 5.43°$, $\delta_m = -5.09°$, and $\delta_x = 68.4\%$ throttle.

**MCAS-Only Simulation**

Starting from this trim condition, the longitudinal dynamics were simulated in MATLAB using `ode45` for a maximum MCAS stabilizer input of $\delta_e = 2.5°$. Left uncorrected, the aircraft pitches down almost immediately and enters a near-complete nosedive within seconds.

<p class="centered-image-block">
  <img src="{{ 'assets/images/onegraph.png' | relative_url }}">
  <i>Longitudinal Response to MCAS (Pitch vs. Time)</i>
</p>

**Pilot Recovery Simulation**

A second simulation modeled pilot intervention: MCAS activates at $t = 0$, and after a 5-second reaction time the pilot turns off MCAS and applies a corrective elevator deflection of $-3.53°$ to restore equilibrium. This introduced a phugoid-like oscillation, where the aircraft trades altitude for airspeed and back again, driven by the mismatch between the MCAS-disturbed state and steady trim.

<p class="centered-image-block">
  <img src="{{ 'assets/images/twograph.png' | relative_url }}">
  <i>Altitude, Angle of Attack, and Pitch Response with Pilot Takeover at t = 5s</i>
</p>

<h2>Results</h2>
The pilot-recovery case showed a significant reduction in the amplitude of altitude, angle of attack, and pitch angle compared to the MCAS-only case, even though a single corrective input wasn't enough to fully damp the resulting phugoid motion. This suggests that with one or more additional, smaller corrective inputs, the aircraft could have been returned to a new steady state.

<h2>Conclusion</h2>
The crash was driven by a sustained pitch-down moment from repeated MCAS-induced stabilizer deflections, triggered by a single faulty angle-of-attack sensor. The MCAS-only model shows an unattended nosedive was essentially inevitable, while the pilot-recovery model shows the outcome was survivable had the crew known to disable MCAS and apply a timely counteracting elevator input. The primary limitation of this model is that it applies a single maximum-deflection MCAS event, whereas the actual flight involved repeated, smaller trim commands that pilots had to continuously counteract throughout the flight.
