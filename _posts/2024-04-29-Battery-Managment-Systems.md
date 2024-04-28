---
layout: distill
title: Battery management systems
date: 2024-04-29 14:25:00
description: A simple introduction to battery management systems based on L. Plett's book and C26 lecture notes.  
tags: batteries lithium-ion battery-study
categories: battery-study

bibliography: 2024-04-27-Hysteresis-voltage.bib
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

### Requirement1: Battery-pack sensing

#### Voltage

Intergrated circuit are ofter used, such as LTC6803  

#### Temperature

Battery-pack sensinig: **Temperature**: A model is needed to monitor the temperature inside the battery from external temperature.  

*Thermocouple*: A thermocouple uses 2 different metals to contact and a tiny voltage generate from from the contact. The voltage can be amplified and measured. However, the measurement requires the a relative sample metal at a known temperature.  In other words, it needs a reference state. This method is good for lab but not for production BMS designs.  
*Themistor*: Resistor-temperature relationship.  

A circuit is used to monitor the resistances of thermistor. Then you can look up to the table for the thermistor-temperature relationship.  

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-29-Battery-Managment-Systems/circuit.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

#### Current  

*Current-shunt*<d-cite, key='BMS_vol2'><\d-cite>: Use a low-value($0.1m\Omega$), high-precision resistor. the $i = v_{shunt}/R_{shunt}$. The signal needs an amplifier to be detectable. 

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-29-Battery-Managment-Systems/currentshunt.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

* Pros:
  * No zero offset compared with hall-effect sensors, regradless of temperature(if the resistor do not vary with temperature).
* Cons:
  * It needs an isolated power supply to support amplifiers.  
  * Generate slight amount of hear.  

*Hall-effect sensors*<d-cite, key='BMS_vol2'><\d-cite>:  

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-29-Battery-Managment-Systems/hall.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

* Pros:
  * No isolated power supply.  
* Cons:
  * Zero-offset that is hard to calibrate.  
  * The zero offset is time and temperature dependent.  

* Protection: against overcharge, overdischarge, overcurrent, short circuits, extreme temperatures.  
* Interface: report the status
* Performance management: SOC management...
* Diagnostics: (State of health)SOH, (State of life)SOL ...

#### High-voltage contactor control

The thing is that most of battery loads are often capacitive, before it can function, a charging process will be started first. If you just use a pure contactor at the starting point the contactor may get fused.  

So a pre-contrator with a resistor is needed. Just to control the charging process not to be too fast with extreme large current.  

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-29-Battery-Managment-Systems/precontactor.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    (a)-(e) demonstrate the process to start charging a device.  <d-cite, key='BMS_vol2'><\d-cite>
</div>

#### Isolation sensing

Just take a the lead-acid battery in an car as an example. The voltage of the battery is 12V and it is directly installed on the chassis.  Though the battery has a package and a totally invisable circuit away from people. However, no one can make sure when there is an accident, the chassis do not connect to one of the electrodes of the battery.  

Consequently, there is a requirement to detect it is shunt or not with chassis. A safety current limit is 0.2mV.  

## Afternotes

*Non-Recurring Engineering(NRE)*: Non-Recurring Engineering is the cost of creating a new product and is usually fully paid before any product gets manufactured. This is in contrast with production cost, which is an ongoing cost and is generally based on the quantities produced. For example, in the camera lens industry, the NRE would be the cost of developing the lens designs and tools which will make the lens smooth; the production cost would be the cost to manufacture each camera lens.  

*Contactor* A contactor is an electrically controlled switch used for switching an electrical power circuit. A contactor is typically controlled by a circuit which has a much lower power level than the switched circuit, such as a 24-volt coil electromagnet controlling a 230-volt motor switch.  

*Amplifier(amp)*:An amplifier, electronic amplifier or (informally) amp is an electronic device that can increase the magnitude of a signal (a time-varying voltage or current). It is a two-port electronic circuit that uses electric power from a power supply to increase the amplitude (magnitude of the voltage or current) of a signal applied to its input terminals, producing a proportionally greater amplitude signal at its output.[from wikipedia:](https://en.wikipedia.org/wiki/Amplifier)  This is a kind of *active devices*(provide outpurs containing more power than their inputs), which means they need extra power supply.  

*Bus voltage* is the total voltage between power and ground(GND). It is the sum of the load voltage and the shunt voltage.  
*Load voltage* is the voltage going to the load.
*Shunt voltage* is the voltage drop across the shunt resistor that is in series with the load.

*chassis*(ʃæ̱si) A *chassis* is the framework that a vehicle is built on.



现在感觉真是越看不懂的越多，对于amp和hall element都有一个叫做zero offset的东西。 这个东西好像很深奥，然后对于不同的材料对于这个offset的modeling也不同。只能从主干入手了。旁支末节聊记于此，有心时再研究吧。  
