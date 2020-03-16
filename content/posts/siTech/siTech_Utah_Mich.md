---
title: "Silicon-based Neurotechnology III - Utah Array and Michigan Style probes"
date: 2020-03-14T18:19:37+01:00
draft: false
categories: ["uni", "microsystem"]
tags: ["summary", "neuroscience", "silicon"]
---
# Utah Array and Michigan Style probes
The Utah Array and Michigan Style probes are Microelectrode arrays (MEAs) and used for Brain Computer Interfaces (BCI). They are produced using vastly different techniques and thus, differ in their advantages and restrictions. Let's start with the Utah Array.

Utah Array uses an out-of-plane 3-D probe produced on a single wafer. It has 100 needles and each needle has one recording site at its tip. Each electrode has a lead wire bonded to its base. It is the first and only MEA ever allowed in humans, and has been successfully used to enable people with paralysis to pinpoint something on a screen or move a robotic arm.

![](/posts/siTech/img/utah-in-vivo.jpg "Woman with Utah Array Implant controlling robotic arm")

This has been a remarkable feat for the scientists behind the Utah Array and a more important one for people with paralysis. Let's now look at how that chip is produced.

A silicon wafer is used as the substrate (a). The back is diced (b) and a glass layer is added to the back and then annealed so that it fills the holes of the dicing before (c). Then we add a rear side metalization for each needle so that each needle is also individually addressable (d). This is done by depositing a Aluminum pad at the end of each needle. This pad is then annealed, which leads to thermomigration which forms $Al-Si$ eutectic doplets inside the substrate. Then, we dice the front to get the pillar shape which are later going to be the needles (e). We then apply the wet etching, which means the material is dipped into the etching fluid in such a way, that the top is etched more than the bottom, thus leaving needle shapes (f). This process reduces the volume of the needles by about 30%. Then, a resist coating is applied to cover everything and the top is removed via UV exposure. This makes only the tip of the needles stick out of the coating. A metalization layer is added to make the tips (and nothing else) more sensible to electronic stimuli (g). The resist coating is then removed/dissolved in acetone and lifted off the material. Then, the carrier wafer is mounted and separate the chips. This means, the chips are diced apart on the wafer (h). Then, everything is passivated with a parylene C deposition (i). Another photoresist is applied which does not cover the tips. Then, the parylene deposition at the tips is removed via a oxygen plasma etching (j). Finally, the photoresist is removed and the final chip/wafer form is obtained (k).

![](/posts/siTech/img/utah-production.jpg "Production steps of Utah Array")

The standard Utah Array has been developed further to be convoluted or slanted to fit it into different shapes. The basic idea, 100 needles with each one recording site stays the same however. This is not true for the so-called Next Gen Utah Electrode Array (UAE). These have less needles, only 1/9 of them, but each needle has 9 recording site. It has the same number of total recording sites, but the resolution is improved and, more importantly, the bioavailability. Less needles also mean less tissue damage.

Michigan Style Probes in contrast to the Utag Array are in-plane chips, ie. constructed in 2-D. It means the former is limited in length by the wafer while the latter is limited in height. There is no Michigan Style probe currently allowed in humans, but there is a lot of animal testing (maybe too much and for sure too cruel). Michigan style probes are characterized by long needles and multiple recording sites on the needle. The production process very simplified with Boron Diffusion is:
1. Apply a masking and dope the substrate with Boron Diffusion. This results in a p++ material.
2. Deposit the lower dielectrics, then pattern, then deposit upper dielectrics.
3. Open the contact vias where needed and deposit and liftoff at sites. Then, bond the pads where the contact vias where opened.
4. Etch the field dielectrics and wet etch the non-doped silicon with EDP (an etch fluid, which is highly selective for Boron doped silicon).

![](/posts/siTech/img/michigan_production.jpg "Production steps of an Michigan Probe with Boron Diffusion Array")

As one would expect scientists did not stop there. Why would they? There have been multiple variations of the Utah Probe. One of the more simple ones is to include electrodes on the front as well as on the back. There are two variations of this, either the backside is etched through the substrate so that the electrode is applied to the front side but faces the back side. This severely limits the number of electrodes though, as all connections have to run on the front side. On the other hand, using real dual-sided probes (with no hole) makes the device thicker, takes more processing steps but increases the number of recording sites. For such probes glass has to be used as a substrate. It has the positive side effect of being biocompatible and light sensitive.
In a more curious development, scientists used thins on the side of the needles to record from undamaged tissue. They also tried to add a shaft (making it sort of 3-D) to stiffen the probe and make the rest smaller.
To increase the bioavailability further, scientists came up with a lattice like structure leaving holes in the needle where tissue could grow through.
Slender probes are another approach to make probes more biocompatible. It is inserted with a shuttle which is removed after insertion. This causes less damage, especially to the recording site, but is also more brittle (and broken devices inside the brain are no good!). 
More interesting is the integration of CMOS technology which allows for more electrodes and minimal distance between electrodes and neurons. Increasing the  electrode count also increases the switch matrix complexity or the adapter size. A switch matrix enables the selective activation of electrodes, making it possible to switch the recorded site if the tissue around the current recording site were to die. Newer CMOS probes have 1600 recording sites with a shaft width of 100 μm.

![](/posts/siTech/img/high-channel.jpg "High Channel probe needs big Adapter")

Stacking multiple Michigan Style Probes results in a single 3-D probe. Contrary to Utah Electrode Arrays there is almost no limit to the electrodes on the probes which makes interfacing these devices a real issues. The probe in the image above has four needles and already needs a huge connector. An idea has been to "outsource" the interfacing with longer ribbon cables. The main ideas for 3-D probes are straight forward, make a platform and either fix the probes via latches of solder/electroplate them to it. In both we need to guarantee a correct alignment between the platform and the probes. This is often achieved with ping/bumps and holes/cavities. To achieve this we basically apply a reversed masking layer to one side. Another approach is to use folding style probes shown in the picture below. The probes can be pushed upwards and the cable on the side downwards, now that is origami!

![](/posts/siTech/img/folding-probe.jpg "Folding/Origami")

To measure temperature and mechanical stress temperature and bending sensitive sensors have been placed at the tip and start of the needle, respectively.
Finally, mechanical probes include some kind of motor to move the probe slowly inside the tissue to decrease the tissue damage. These devices are highly complex and look rather scary when implanted into rodents.

![](/posts/siTech/img/mice-mechanical-probe.jpg "Mice with Mechanical Probe")

#### Disclaimer:
This is just a summary of what I learned and I will try to be as accurate as possible.
But there are probably mistakes in the text!




