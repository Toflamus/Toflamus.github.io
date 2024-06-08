---
layout: distill
title: Build an equivalent circuit of batteries from scratch
date: 2024-04-26 14:25:00
description: First blog! 
tags: batteries longposts 
categories: battery-study

bibliography: 2024-04-26-equivalent-circuit-of-batteries.bib

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).
toc:
  - name: Open circuit voltage(OCV) and State of Charge(SOC) dependence
    # if a section has subsections, you can add them as follows:
    # subsections:
    #   - name: Example Child Subsection 1
    #   - name: Example Child Subsection 2

---


This blog is a summary of the problems and concerns one may encounter when consider the battery system. Detailed but not essential formulas are not included. This blog is just a general description.  

## Open circuit voltage(OCV) and State of Charge(SOC) dependence <d-cite key="BMS_vol1"></d-cite>  

The first thing one thinks to build a equivalent circuit is to ADD a *voltage source* to the circuit. From high school physics, the *open circuit voltage* is supposed to be the voltage at infinite large load, which means the current density is approximately zero. I previously thinks that the OCV may related to current density, diffusion, kinetics. However, I misunderstood the concept of OCV it is not working. Ideally there is no current, consequently no diffusion and kinetics problems. It should be more stable then I had thought.  

Nonetheless, it is by no means stationary. From Nernst equation:  

$$\Delta G = -zFE$$
$$E = E^\circ - \frac{RT}{zF}ln(Q_r)$$

with the ongoing of reaction the activity is also changed. OK, one may argue that in a <s> rockin' roll  </s> the *rocking chair battery(RCB)* the solvent concentration may not change, just like their famous relative of RCB: *Lithium-ion batteries(LIBs)*. However, I still thinks SEI formation, surface reshaping, and other side effects may drive the OCV away when using the battery. So here we introduce an important concept called *State of Charge(SOC)*. This should actually mean the charge status, like SOC = 100% means fully charged. Just like the worrying battery percentage thing in your cellphone. OK, I have to admit this really confused me for several days when I first get to know the concept, because nobody told me the UNIT of SOC(unit of 1). I find people directly use the voltage in a capacitor to be the SOC and this works because ideal capacitors have a linear relationship between voltage and remaining charges.  

So now we have a circuit with a SOV dependent OCV.  

By the way, one may come up with the question: **How to test the SOC and OCV relationships?**. Naturally, we may think of a simple method that we charge/discharge the battery to different SOC and wait it to reach equilibrium. This technique is called *Galvanostatic internmittent titration test(GITT)*. The method involves a small charge/discharge and then a long rest period to allow the cell to equilibrate. Then the voltages at the end of the periods are taken as the OCV. <d-cite key="C26_2"></d-cite>  

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-26-equivalent-circuit-of-batteries/GITT.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Here is an typical graphic example of GITT<d-cite key="LIBOCVmodel"></d-cite>  
</div>

Now we can model the SOC(denoted by $z(t)$) with continuous and discrete form by differential and difference equations. Assuming that discharge current is positive.  

* Continuous form:
  * $\dot z(t) = -\eta(t)i(t)/Q$
  * $z(t) =z(0) -\frac{1}{Q} \int_0^t \eta(\tau)i(\tau)$
* Discrete form:
  * $z[k+1] = z[k] - \frac{\Delta t}{Q}\eta[k]i[k]$

Some other concepts and their definitions:  

- *total charge capacity(total capacity) $Q$*: total charge removed from SOC = 100% to SOC = 0%
- *discharge capacity*: total charge removed from SOC = 100% to some cut off voltage where SOC > 0%.
- *depth of discharge(DOD)*: $DOD = 1 - SOC$

OK now I am gonna say that what has been built above is straight forward but a lot too simple.There are a lot of things to be taken into account. *Randles circuit*, *Warburg impedence*   

## 




<hr>

## Small talks

> At winter, the electric car can be driven for less distance not only because the inner resitance of bateries become larger, but also because there is 7% larger air resistance at 5 C compared with 25 C.
> —My kindly lecturer of C26  
