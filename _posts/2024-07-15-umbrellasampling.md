---
layout: distill
title: From umbrella sampling to MBAR
date: 2024-07-15 9:00:00
description: This post mainly focuses on the histogram method for free energy calculation on reaction coordinate (order parameter) by MD. Starting from biased sampling to umbrella sampling till the advanced multistate data processing method(Multistate Bennett Acceptance ratio, MBAR).  
tags: advanced-transforms algorithms longposts
categories: algorithms

bibliography: 2024-07-14-umbrellasampling.bib

toc:
  - name: General overview
  - name: 
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

## Notations of Statistic Mechanics



The TI method is easy to understand
