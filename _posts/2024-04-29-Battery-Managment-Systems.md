---
layout: distill
title: Battery management systems
date: 2024-04-29 14:25:00
description: A simple introduction to battery management systems based on L. Plett's book and C26 lecture notes.  
tags: batteries lithium-ion battery-study
categories: battery-study

bibliography: # To be continued
toc:
  -name:

---

## An introduction to BMS

The scale of the book is mainly on how to manage battery system, involves the hardware and software parts. The software part is stressed by different algorithms to model the battery packs.  

>Definition of *Battery management(monitoring) systems(BMS)*: A permanently installed system(embeded) for measuring, storing and reporting battery parameters.  
>--IEEE Standard 1491.  

Purposes:

1. To protect the safety of operator and system components.  
2. To prolong the life of the batteries.  
3. To keep the battery functioning.  

Marginal effect: When do we need BMS？ 

Cost of failure(Expectation) and related cost higher than then cost of BMS.  

Important in such cases:

* *Hybrid-electric vehicles(HEVs)*: Never charge its batteries by a blug. The BMS combines the gasoline engine and make full use of the energy.  
* *Plug-in HEVs(PHEVs)*: It can opertate in electric only mode and prosess a larger battery pack. 
  * Charge-depletion mode: Just use electricity to operate.
  * Charge-sustaining mode: When the battery is nearly empty, it starts to work like HEVs.  
* *Extend-range electric vehicles(REVs)*: Small gasoline engine and large battery pack. Can operate just like EVs. When the battery runs out of capacity, the gasoline engine provides *extended range*.  
* *EVs*: Battery-electric vehicles.  

* Grid storage powers, telecoms off-grid power.  

## Battery-pack topology

Topology is a branch of mathematics that deals with the properties of space that are preserved under continuous deformations, such as stretching, crumpling, and bending, but not tearing or gluing.  

However, here the word topology refers to how to construct a battery pack. Taking the EVs as an example, a EV generally needs high voltage and large current density.  

High voltage can be achieved by placing the batteries in series, a *series-cell-module(SCM)*. While large current density can be achieved by placing them in parallel, a *parallel-cell-module(PCM)*. However, they all have there defects like large inner resistances which may result in low current and low voltage, respectively.  

Consequently, there is a **trade-off between series or parallel packing**.  

However, in engineering practice, we usually build a complex system in modules. We first optimize the topology in a single module and then optimize the topology in modules combinations, so on and so forth.  This methodology reduces NRE costs.  

For example, a classic *3P6S* module has 18 cells, 3 in parallel and 6 in series. The power and energy are then boteh approximately 18 times that of a single cell.  

## BMS design requirements

* Sensing and high-voltage control: $u,i,T$ monitoring.
* Protection: against overcharge, overdischarge, overcurrent, short circuits, extreme temperatures.  
* Interface: report the status
* Performance management: SOC management...
* Diagnostics: (State of health)SOH, (State of life)SOL ...

### Sensing and high-voltage control: $u,i,T$ monitoring.

**Voltage**: Intergrated circuit are ofter used, such as LTC6803  

<hr>

**Temperature**: A model is needed to monitor the temperature inside the battery from external temperature.  

*Thermocouple*: A thermocouple uses 2 different metals to contact and a tiny voltage generate from from the contact. The voltage can be amplified and measured. However, the measurement requires the a relative sample metal at a known temperature.  In other words, it needs a reference state. This method is good for lab but not for production BMS designs.  
*Themistor*: Resistor-temperature relationship.  

A circuit is used to monitor the resistances of thermistor. Then you can look up to the table for the thermistor-temperature relationship.  

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-29-Battery-Managment-Systems/circuit.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<hr>

**Current**:  

*Current-shunt*: 

*Hall-effect sensors*: 



* Protection: against overcharge, overdischarge, overcurrent, short circuits, extreme temperatures.  
* Interface: report the status
* Performance management: SOC management...
* Diagnostics: (State of health)SOH, (State of life)SOL ...

## Afternotes

*Non-Recurring Engineering(NRE)*: Non-Recurring Engineering is the cost of creating a new product and is usually fully paid before any product gets manufactured. This is in contrast with production cost, which is an ongoing cost and is generally based on the quantities produced. For example, in the camera lens industry, the NRE would be the cost of developing the lens designs and tools which will make the lens smooth; the production cost would be the cost to manufacture each camera lens.  

