---
layout: distill
title: Concerns on MD 
date: 2024-06-21 0:00:00
description: This is a memo of the concerns when I studying MD simulations.    
tags: memo shortposts md
categories: memo md
bibliography: 2024-06-13-raman.bib
toc:
  - name: Concerns on MD
---

## Concerns on MD

### Equipartition of energy

How can MD algorithms do not violate the principle of equipartition of energy and some convervation laws?  

A classical example is the Berendsen heat bath thermostat. It just simply scales the velocity to keep it at constant. This violates M-B distribution and results in [Flying ice cube](https://en.wikipedia.org/wiki/Flying_ice_cube). A latter developed Bussi-Donadio-Parrinello thermostat is said to be able to avoid the problem.  

There are also some [Energy drift](https://en.wikipedia.org/wiki/Energy_drift) problems that may result in Shadow Hamiltonian.  


