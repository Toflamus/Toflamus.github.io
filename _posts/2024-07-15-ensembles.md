---
layout: distill
title: Ensembles
date: 2024-07-15 9:00:00
description: Summary of the Micro-canonical, canonical, Isobaric-isothermal, grand-canonical ensembles.   
tags: md statistical_mechanics
categories: md statistical_mechanics

bibliography: 2024-07-14-umbrellasampling.bib

toc:
  - name: Summary table
  - name: 
  - name: 
  - name: 
---

## Summary table

| Ensembles | Micro-canonical | Canonical | Isobaric-isothermal | Grand-canonical |  
| :----------- | :------------: | :------------: | :------------: |  :------------: |  
| **Comment**      |    This is just like to give a constrain on on Canonical ensenmble on the hyperplane of $\mathcal{H}(\mathbf{p}^N, \mathbf{r}^N) = E$    | Partition function |   |  
|**Const parameters**| $N,V,E$ | $N, V, T$| $N, P, T$|$\mu, V, T$|
| **Partition function **     |    $$\Omega_{E,V,N} = \frac{1}{h^{3N}N!}\int  d\mathbf p^N d\mathbf r^N \delta(\mathcal{H}(\mathbf{p}^N, \mathbf{r}^N)-E)$$    | $$Q_{N,V,T} =\frac{1}{h^{dN} N!} \int d\mathbf p^N d\mathbf r^N exp\left[ -\beta  \mathcal{H}(\mathbf{p}^N, \mathbf{r}^N) \right]$$ |   |  
| **Probability** $$\mathcal N$$       |    center 3    |       right 3 |  lol |  geg |
|**Free energy relationship**| | $$\beta F = -\ln Q(N,V,T)$$ | $$\beta G = -\ln Q(N,P,T)$$| Grand potential $\Phi$ $$\beta \Phi = \beta(F-N\mu) = \ln \Xi$$|  

## Derivations of partiion functions

The derivations are all based on the fact that a system is in ***weak interaction*** with another large environment. So we can use the taylor expansion of $\ln \Omega(N,V,T)$ to derive the partition function. As I wrote in the previous blog:  

The derivation can be devided into 2 steps.  

* On equilibrium with some bath
* Do Taylor expansion on $E_i = 0$

### Canonical ensemble  

This on is classic:  

***Firstly: On equilibrium with heat bath***


