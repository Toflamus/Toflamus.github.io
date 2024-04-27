---
layout: distill
title: Hysteresis voltage modeling
date: 2024-04-27 14:25:00
description: Introduce hysteresis voltage and its modeling
tags: batteries lithium-ion battery-study
categories: battery-study

bibliography: 2024-04-27-Hysteresis-voltage.bib
toc:
  - name: Hysteresis voltage

---

## Hysteresis voltage

Definition: OCV-SOC curves for charging and discharging Li-ion batteries do not overlap. The difference between the curves is defined as *Hysteresis voltage*.  

The modeling can be physics-based or phenomenon-based.  

I find the modeling of hysteresis is a deep field because the hysteresis phenomenon can happen in various disciplines. There is even a book about hysteresis modeling<d-cite key="hysteresismodelingmath"></d-cite>. There are plenty of different models to model a hysteresis, such as Prandtl-Ishlinskii hysteresis model<d-cite key="4739202"></d-cite>. However, they are not covered in this blog post. I just put them here for further reference. The main framework is still from L. Plett's book.<d-cite key="BMS_vol1"></d-cite>  

## Main circle and minor circle

This part is mainly from the Guillaume Larrat's thesis. <d-cite key = "Lihysteresismodeling">

The charging and discharging OCV curves that were displayed in the figure below allows to create a voltage hysteresis loop for a SOC varying from 0% to 100% which includes the whole range of possible values for the SOC.  

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-27-Hysteresis-voltage/OCV_curve.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

It is composed of the two **major** OCV curves: a charge from 0% to 100% SOC and a full discharge from 100% to 0%. The corresponding voltage hysteresis loop is then called a major loop. However, if the cell is partially charged or discharged from a state different than 0% or 100%, the OCV will not follow the two curves displayed earlier. If a cell is at a 60% SOC and is then discharged to 40% and then charged back to 60%, this will create a minor loop as shown in Figure below:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-27-Hysteresis-voltage/major_minor_loop.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Assupmtion: The loop of a real-time charge/discharge process only locates insides the major loop. Apparently, the changing rate in a minor loop is different from the major loop.  


## The model

Let's just build a simple model:  
Assumptions:  

* Linear: The changing rate of hysteresis voltage only depends the difference between maxium OCV and current OCV.  
* Past invariant: The hyseresis does not depend on the using history but just state. Actually, this is not true.  

$$\frac{dh(z,t)}{dz} = \gamma sgn(\dot z)(M(z,\dot z)- h(z,t))$$

$M(z,\dot z)$: A function that gives the maximum polarization due to the 

## Afterwords

I did not heard about this topic too much before when I concentrated at ElectroChemistry. The hysteresis effect is important for Battery Management Systems.  
