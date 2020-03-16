---
title: "Silicon-based Neurotechnology IV - Chemotrodes"
date: 2020-03-15T18:19:37+01:00
draft: false
categories: ["uni", "microsystem"]
tags: ["summary", "neuroscience", "silicon"]
---
# Chemotrodes
This is going to be short but I hope interesting none the less. Unlike in the probes before chemotrodes do not measure the activation of cells directly but instead use a proxy neurotransmitter. Neurotransmitters are chemicals which enable the transmit of a signal across chemical synapse, such as neuromuscular junctions, ie. from one neuron (nerve cell) to a "target" neuron. But importantly, neurotransmitters can also inhibit neuron activation. These neurotransmitters are stored in the cell body and freed/diffused when stimulated. The diffusion in the brain liquid is highly local in the synaptic cleft.

![](/posts/siTech/img/neurotransmitter.png "Neurotransmitters in Action")

Chemotrodes enable the measurement of the neurotransmitters concentration, but crucially, also the manipulation of cell activation via the enjection of exogenous neurotransmitters. This can be done in the Central nervous system (CNS) or Peripheral nervous system (PNS), see introduction. There are two similar ways to do this. Either with a push-pull cannula. Such a probe has an input and a physically separated output and pumps a solution to the target brain region. The probe usually includes a biosensors at the inlet/outlet port to monitor the neurochemical concentration.

![](/posts/siTech/img/push-pull.jpg "Push-Pull Cannula (lef), Dialysis Probe (right)")

In Microdialysis probes have no separate outlet and inlet ports, but a membrane which lets the incoming fluid and the brain fluid dissolve. In an equilibrium, the concentration is the same in the brain as well as in the probe. Methods to detect the neurotransmitter concentration exploit the fact that neurochemicals are also electroactive. For correctness, a probe should always measure at two positions, close to the injection side and a control electrode positioned further away. Sometimes it can be easier to measure a proxy, for example a toxic by-product, instead of the neurotransmitter itself.

When using biosensors many things have to be considered. The sensitivity and selectivity are crucially important, but lifetime, spatial resolution, response time and biocompatibility all need to be weigh carefully. There are two main ways biosensors work, they either detect a charge between two different points as in Amperometric enzyme biosensor. These usually have a working electrode (WE) a reference electrode (RE) and a counter electrode (CE). The output is the difference in electrical charge between the WE and CE. The RE can be neglected if the potential drop in the solution is mall. But it is also possible to immobilize an enzyme on an electrode, ie. the enzyme attached to an insoluble material. This usually happens via a covalent binding (sharing of electrons), an entrapment (enzyme trapped in 3-D polymer matrix) and cross-linking (links one polymer chain to another).

To insert the biosensors into a probe either KOH or DRIE etching is used to form a recess.
![](/posts/siTech/img/koh.png "KOH vs DRIE recess")

 

#### Disclaimer:
This is just a summary of what I learned and I will try to be as accurate as possible.
But there are probably mistakes in the text!






