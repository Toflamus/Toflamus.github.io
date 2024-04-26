---
layout: post
title: Build a equivalent circuit of batteries from scratch
date: 2024-04-26 14:25:00
description: First blog! 
tags: batteries
categories: battery-study
---

This is just some quick notes and there should be a better version in the future.  
Some notes and insights from <a href="https://www.amazon.co.uk/Battery-Management-Systems-Modeling-Engineering/dp/1630810231">L.Plett's book</a>  
Also from the lecture notes of C26, used without permission but I did cite something. 

## Open circuit voltage(OCV)

The first thing one thinks to build a equivalent circuit is to ADD a *voltage source* to the circuit. From high school physics, the *open circuit voltage* is supposed to be the voltage at infinite large load, which means the current density is approximately zero. I previously thinks that the OCV may related to current density, diffusion, kinetics. However, I misunderstood the concept of OCV it is not working. Ideally there is no current, consequently no diffusion and kinetics problems. It should be more stable then I had thought.  

Nonetheless, it is by no means stationary. From Nernst equation:

$$\Delta G = -zFE$$
$$E = E^\circ - \frac{RT}{zF}ln(Q_r)$$

with the ongoing of reaction the activity is also changed. OK, one may argue that in a <s> rockin' roll  </s> the *rocking chair battery(RCB)* the solvent may not change concentration just like their famous relative *Lithium-ion batteries*. However, I still thinks SEI formation, surface reshaping, and other side effects may drive the OCV away when using the battery. So here we introduce an important concept called *State of Charge(SOC)*. This should actually mean the charge status, like SOC = 100% means fully charged. Just like the worrying battery percentage thing in your cellphone. OK, I have to admit this really confused me for several days when I first get to know the concept, because nobody told me the UNIT of SOC(unit of 1). I find people directly use the voltage in a capacitor to be the SOC and this works because ideal capacitors have a linear relationship between voltage and remaining charges.  

<hr>

## Small talks

> At winter, the electric car can be driven for less distance not only because the inner resitance of bateries become larger, but also because there is 7% larger air resistance at 5 C compared with 25 C.
> —My kindly lecturer of C26  
