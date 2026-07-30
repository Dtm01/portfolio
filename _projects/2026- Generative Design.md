---
layout: project
title: Generative Design
description: Generative Design of a Gear
technologies: [Fusion360, Generative Design, ANSYS]
image: 
---


Generative design was used to decrease weight on an additively manufactured gear piece. Since powder-bed fusion and directed energy deposition are the possibel choices, there are more options for the gear than the traditional machining options. There is also less material waste since both technologies will only use the amount of material specified rather than having the waste of subtravtive manufacturing. 

The baseline gear had a 140 mm diameter with 12 teeth and a 10 mm shaft bore. To simulate real operating conditions, a 1000 N normal force was applied to a single tooth, representing worst-case loading during engagement. The inner bore was fixed as the only connection point to the system. Rather than simplifying the model using symmetry, I created independent load cases for all 12 teeth to ensure the gear could withstand loading in any orientation.



<div class="centered-image-block">
  <table>
    <tr>
      <td>
        <img src="{{ 'assets/images/oggear.png' | relative_url }}" width="200"><br>
        <em><i>Original Gear Geometry</i></em>
      </td>
      <td>
        <img src="{{ 'assets/images/loadgeom.png' | relative_url }}" width="200"><br>
        <em><i>Load Case</i></em>
      </td>
    </tr>
  </table>
</div>

To enable meaningful optimization, I defined preserve and obstacle regions within the design space. The gear teeth and shaft interface were preserved to maintain proper meshing and integration, while surrounding regions were constrained to prevent unwanted deformation. The remaining volume between the inner hub and outer ring was left open for material redistribution, allowing the algorithm to generate efficient internal load paths. A minimum factor of safety of 1.2 was enforced.

[Place Image 3: Preserve and obstacle geometry setup]

<p class="centered-image-block">
  <img src="{{ 'assets/images/genconstraint.png' | relative_url }}"  width="400">
  <i>Preserve and Obstacle Geometry</i>
</p>

Using Fusion 360’s generative design tools, I explored multiple configurations across materials and additive manufacturing methods. While several viable solutions were produced, the final design was optimized for AlSi10Mg using Powder Bed Fusion (PBF), offering the best balance between weight reduction and structural performance.

The optimized gear achieved:

~45% mass reduction compared to the original geometry
Factor of safety ≈ 1.7 under 1000 N loading
Maximum stress ≈ 139 MPa, below material yield (~240 MPa)



<p class="centered-image-block">
  <img src="{{ 'assets/images/finalgear.png' | relative_url }}"  width="400">
  <i>Final Optimized Gear Design</i>
</p>

To validate the design, I conducted finite element analysis in both Fusion 360 and ANSYS.

[Place Image 5: Stress analysis comparison (Fusion vs ANSYS)]


<div class="centered-image-block">
  <table>
    <tr>
      <td>
        <img src="{{ 'assets/images/fusiongear.png' | relative_url }}" width="200"><br>
        <em><i>Stress Analysis in Fusion</i></em>
      </td>
      <td>
        <img src="{{ 'assets/images/ansysgear.png' | relative_url }}" width="200"><br>
        <em><i>Stress Analysis in ANSYS</i></em>
      </td>
    </tr>
  </table>
</div>


Both simulations showed consistent stress distribution patterns, with peak stresses occurring in the internal load-bearing members rather than the gear teeth. This confirms that preserving the tooth geometry prevented stress concentration at the contact surfaces, while the optimized internal structure efficiently transferred loads to the shaft. Differences in absolute stress values between the two tools highlighted variations in modeling assumptions, but overall trends aligned, supporting the design’s reliability.