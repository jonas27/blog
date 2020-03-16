---
title: "Silicon-based Neurotechnology II - Processing Tech Deep Dive"
date: 2020-03-14T12:19:37+01:00
draft: false
categories: ["uni", "microsystem"]
tags: ["summary", "neuroscience", "silicon"]
---
# Processing Techniques Deep Dive
This part is going to be a little nerdy, so if you don't want to read much technical blabla, click here to skip to the next part. With that out of the way, let's dig deep.

The base materials used for neurotechnoogy are mostly the same as in standard electronics, mainly silicon, polysilicon, polymers and dialectrics. Out of the earth materials are not pure, so in order to use them for as wafers they often need purification and with todays technology, we can get close to 100% purity. The base material for computer chips is called the "substrate" and usually produced in wafers with a diameter of *<300mm* for CMOS and *4“, 6“, 8“*  for MEMS in neuroscience. These wafers are cut from single crystal ingots derived with the Czochralski process. Often, the same materials are used as in common electronics to achieve the same goal: tiny, highly customizable chips (ie. micrometers matter!). But there some materials used in neuroscience which are not commonly used elsewhere and I will come back to those in a little while. For the moment let's keep it simple. Below is an image of different wafer sizes and chips printed on them. 
<!-- sdf -->
![](/posts/siTech/img/wafer.jpg "Wafers used as substrate.")

It's important to understand that the substrate is (usually) out of one semi-conductive material. The interesting things, electronic circuits, are added during production. There are additive as well as substractive production steps. Some of the additive Steps are:
* Thin film deposition: The substrate is covered with a small film, eg. a mirror has a small metal coating/film on the backside of the class which makes it reflective. We differentiate between physical deposition and chemical depoistion. The former uses mechanical, electromechanical or thermodynamic means to produce a thin film of solid and a prime example of it is frost. In the latter, a fluid precursor undergoes a chemical change at a solid surface, leaving a solid layer.  Thin film coating is achieved with oxidation (eg. Silicon dioxide $SiO_2$), sputter deposition (relies on plasma or nitrogen/oxygen to knock of a few atmos of the substrate and is usefull when materials would evaporate at different rates). Various other techniques exist, but these are the two most important. 
* Spin coating: The coating material is put into the middle of the substrate. Then, the substrate is rotated and the coating material distributes itself evenly via centrifugal forces. 

These techniques mostly add additional layers to the substrate. In order to get the desired structure it is often important to remove unwated parts. This is usually where the patterning comes into play. In patterning a mask is applied to the material to exposes only certain areas and selectively remove unwanted parts. This procedure is also called pattern transfer and shown below.
![patterning](/posts/siTech/img/patterning.jpg  "Simple Patterning." )
Photolithography is used to make the same material react differenlty, mostly to make some parts soluble, the unwated parts, while the rest remains. Removing the soluble material is called etching and can either be done with gas/plasma or with fluids:
<!-- <img src="/posts/siTech/img/patterning.jpg" alt="drawing" style="width:200px;"/> -->
* Dry Etching: Primarily used for submicron precision. It is often plasma assisted (Plasma is a fourth state and can be obtained by energizing gas and is characterized by free Ions or electrons) and then called Reactive Ion Etching (RIE). In dry etching the etch profile is independent on crystallinity and wafer orientation and achieves high homogenity. The process is highly automatable and does not reduce much material. But, for the reaction mostly toxic gases are used, which need correct handling.
* Wet Etching: Used for larger geometries, above 3 microns. It is based on chemical interaction with acids, bases, solvents. Wet etching is simple and cheap while offering a high etch rate and selectivity. It is possible to achieve isotropic or anisotropic caveties. But on the downside, the etch profile is dependent on crystallinity and wafer orientation and to keep a constant etch rate, the etching material needs to be replaced. Additionally, the toxic etch fluids need correct handling. 
For both etching techniques, the etch rate is defined by the substrate, the etching material and the enviroinment. Further, etching can either happen ansiotropic, so mainly in one direction, or isotropic in all directions, dependent of the crystaline structure of the material.

There are some other production procedures worth noting. One is passivation and spicifically thin film oxidation. Passivation refers to procedures which makes the outer material more resilient to outside damage. Thin film oxidation procedure is performed in furnaces at around 800 -- 1200 °C with add oxygen. The top layer of the silicon substrate reacts with the oxygen to form a silicon dioxide layer used for passivation. The chemical reaction is $Si + O_2 \rightarrow SiO_2$. 

Doping is another one. In doping, boron, arsenic, phosphorus, and gallium are used to introduce impurities into the substrate to modulate/regulate its electrical, optical and structural properties.

Metalization and Thermomigration are two procedures closely related. Metalization is just the superficial coating of the material with metal to increase the electrical properties. Thermomigration is the process of transferring the coating inside the substrate. For example, aluminum trails can be produce $p+$ doped trails in the substrate (see below).
![metalization](/posts/siTech/img/metalization.png  "Metalization and Thermomigration" )

Grinding is a strictly substractive technique and mainly used post production to decrease the wafer thickness. Often, the production procedure requires a certain wafer thickness, but post production the wafer can be grinded on the back side to make the final chip even small.

Deep Reactive Ion Etching (DRIE) is a combination of RIE and the Bosch process. Etching and passivation are repeated to achieve a deep cavity. The picture below makes this a lot clearer. 
![patterning](/posts/siTech/img/drie.png  "Deep Reactive Ion Etching" )

Flip Chip bonding is a technique of connecting two different devices, often a cable with a probe. Scientist were able to shrink probes down to milimeters, but the adapters used to interface these devices were huge. With flip chip bonding we can directly connect the to contact pads with each other. The process is straight forward. One device is turned upside-down and the other device is put ontop, see image below. Then we use electroplating to unite the two. Usually, bumps and holes are used for prior alignment.

![patterning](/posts/siTech/img/flip-chip.png  "Flip Chip Bonding" )

Finally, the thermal expension coefficient and mechanical stress is something always to keep in mind when designing chips. A chip is only as flixible as the most rigit layer. Bending can happen exogenous, so through mechanical forces from outside, or endogenously through thermal expension. Two different layers, can expand or shrink at different rates thus bending or breaking the probe. This is especially bad in brain, as banding can cause irreperable tissue damage.

And that's it for this post. Next up are the Utah Array and Michigan Style probes, stay tuned!

#### Disclaimer:
This is just a summary of what I learned and I will try to be as accurate as possible. 
But there are probably mistakes in the text!




