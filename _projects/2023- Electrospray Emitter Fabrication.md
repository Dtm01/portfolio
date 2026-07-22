---
layout: project
title: Alumina Ceramic Electrospray Emitter Substrate Fabrication
description: Research
technologies: [Ansys Granta, SolidWorks, Resin Printing, SEM]
image: assets/images/emittersem.jpeg
---


ASTRA Lab at Cornell University works on various space propulsion systems. My research project within the lab was to create a more effecient process for fabricating electrospray emitters made of alumina ceramic. This process included resin-printing substrates of the emitter, sanding this substrate at micron-level grit, adding a cone-shaped tip using nanofabrication techniques, and then filling the substrate with an alumina ceramic slurry. The next step included debinding by burning the resin mold and sintering the emitter. This technique is consistent with slurry-based additive manufacturing and its heat treatment. 

<p align="center">
  <img src="{{ 'assets/images/process.png' | relative_url }}" width="600">
  <i>Process of Electrospray Emitter Fabrication</i>
</p>

Resin-printing the substrate took the longest amount of time within the process and led to delays in fabrication and therefore testing of the emitters. Some other issues included the resin not burning fully in the debinding phase. If it did not burn fully, it could not go into the sintering furnace, or it could meld into the emitter, which was not optimal. If the substrate was burned off, but was still on the surface of the emitter, it could not be taken off since the emitter was not sintered and did not have the structural integrity to take any amount of force required to take the piece of the mold off. By far, the largest flaw of resim printing was that there was a warped center hole in the substrate. This center hole was the center used for the nanofabrication lab and a nano-scale cone could not be formed on top with a fairly deformed center. 




<p align="center">
  <img src="{{ 'assets/images/deform.png' | relative_url }}"  width="200">
  <i>Warped Resin Substrate</i>
</p>


To create more consistent and reliable substrates, ANSYS Granta was used to find materials that had the most similar properties to the emitter tip mold, IP-Q. When the tip was fabricated, the entire substrate was put into PGMEA and IPA, so the material chosen had to be resistant to those chemicals. It also had to have the closest debinding temperature to IP-Q. With these parameters, the best material was found to be HDPE. Insstead of printing with HDPE and leading to the same warping issues, using a a high-powered laser beam to cut the center hole was a better fit. The CAD below is what the original resin-printed version would have looked like, and the HDPE below shows a more centered and precise hole. 


<div align="center">
<table>
  <tr>
    <td align="center">
      <img src="{{'assets/images/picture.png' | relative_url}}" width="200"><br>
      <em><i>CAD of Substrate</i></em>
    </td>
    <td align="center">
      <img src="{{'assets/images/hole.png' | relative_url}}" width="100"><br>
      <em><i>HDPE Substrate</i></em>
    </td>
  </tr>
</table>
</div>


Future steps of this project includes doing thermogravimetric analysis (TGA) on the HDPE to determine precise temperatures at which thermal debind occurs to change furnace settings. After this, an emitter will be fabricated and it will be tested under an Scanning Electron Microscope (SEM) to validate that this model is a solution to the tip fabrication issue, or if further modification to the manufacturing process need to be made. 
