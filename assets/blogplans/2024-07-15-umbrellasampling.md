---
layout: distill
title: Free energy, from histogram method and bias sampling to MBAR
date: 2024-07-15 10:00:00
description: This post mainly focuses on the histogram method for free energy calculation on reaction coordinate (order parameter) by MD. Starting from biased sampling to umbrella sampling till the advanced multistate data processing method(Multistate Bennett Acceptance ratio, MBAR).  
tags: advanced-transforms algorithms longposts
categories: algorithms

bibliography: 2024-07-14-umbrellasampling.bib

toc:
  - name: General overview
  - name: Introduction of histogram method, from overlapping-distribution method to free energy perturbation(FEP) expression
  - subsections: 
    - name: The core of histogram method
  - name: 
  - name: 
---

## General overview

This is an overview and recap from the book of Frenkel and Daan.<d-cite key="undMD"></d-cite>

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets\img\2024-07-14-umbrellasampling\Free_energy_computation.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

This figure demostrates 2 main ways of computation of free energy. The first one is thermodynamic integration(TI), the second one is the Histogram method.  

The TI method is easy to understand, people who did *Physical Chemistry* are good at establish an imaginary reversible route from state $1$ to state $2$. Since the free energy is a state property, it can be easily calculate by integration from one state to another state. However, in the textbook<d-cite key="undMD"></d-cite> the TI method only concerns Canonical ensemble and another newly published paper<d-cite key="jinnouchi_machine_2024"></d-cite> is attached for grand canonical ensemble.  

Here, we mainly focus on the Histogram method and bias sampling, while *Wang-Landau* style algorithm and *Density of state* approximation<d-cite key="wang-landau00"></d-cite> are not covered. Meanwhile, Bennett Acceptance Ratio method, the basis of MBAR, are excluded from this blog, because the derivation takes me 4 pages of paper.  

## Introduction of histogram method, from overlapping-distribution method to free energy perturbation(FEP) expression

For convenience, only canonical ensemble, ($N,V,T$) systems, are discussed here. $F$ denotes Helmholtz free energy.  

### The core of histogram method

>First thing frist, people only cares about the free energy difference.  
>$$\Delta F = -\frac{1}{\beta}\ln(Q_1/Q_0)$$  

Every thing we do is to estimate $Q_1/Q_0$

***Notices***:  

* If we want to compare the free energy difference, the 2 systems should have the same setting, such as the same atom types and number, but not necessarily the potential operator $\mathcal{U}(\mathbf{r}^ N)$. As a result, in a infinite long sampling, that can have identical configurations that overlap each other. This is where histogram is from.<d-footnote>You will understand what I am saying after reading the Overlapping distribution method part</d-footnote>. However, one may think that the free energy can be compared among totally different systems as long as they have the same reference,such as water and carbon with standard $H$ and $S$ reference. However, we can consider a reversible transition process which transfer the 2 systems to a imaginary system with same settings<d-footnote>You may prefer to transfer a system to another,more specifically, transfering a type of atom to another, adding atoms, expanding the volumes. There must be some reversible pathway to do this</d-footnote>.  This process can be calculate with thermo-integration(TI) method. So the key problem is the partition function ratio of 2 systems of same or overlapping [configurational space](https://en.wikipedia.org/wiki/Configuration_space_(physics)).  
* The distribution of configuration, normally<d-footnote>If we do not consider the commutor $\mathcal{O}[\mathcal{K}, \mathcal{U}]$</d-footnote>, is not influenced by temperature, as temperature only represent the momentum, while $\mathcal{U}(\mathbf{r}^N)$ is a function of the coordinate $\mathbf{r}^N$.  

### Overlapping distribution method

Starting from the core of histogram method:  

$$\Delta F = -\frac{1}{\beta}\ln(Q_1/Q_0)$$  

Using the configurational partition expression to replace $Q$:  

$$\Delta F = -\frac{1}{\beta}\ln\left(\frac{\int d \chi exp[-\beta \mathcal{U_1}(\chi)]}{\int d \chi exp[-\beta \mathcal{U_0}(\chi)]}\right)$$  

Suppose we have 2 systems with same configurational space, by which I mean the atom types, atom number, volume of the system are the same and the atom coordinate in these 2 system are able to have the same value<d-footnote>They may not necessarily have the same force field or potential operator</d-footnote>. If we have a infinite long sampling with a really good algorithm that can sample every state with correct probability. Then the configurational space are fully searched with accuracy. As a result, the 2 system must have some configuration that are the same but have different probability of visiting  this configuration.  

In other words, for every configuration visited during this sampling of system $1$ we can compute the potential energy of system $0$ for the same configuration $\mathbf{s}^N$. The potential energy difference of the same configuratio in 2 systems are: $\Delta\mathcal{U}(\mathbf{s}^N) = \mathcal{U_1}(\mathbf{s})^N-\mathcal{U_0}(\mathbf{s})^N$. We use this information to construct a histogram that measures the probability density by $p_1(\Delta\mathcal{U})$:  

$$p_1(\Delta\mathcal{U}) = \frac{\int d\chi}{}$$