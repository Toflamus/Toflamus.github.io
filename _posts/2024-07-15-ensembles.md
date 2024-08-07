---
layout: distill
title: Ensembles
date: 2024-07-15 9:00:00
description: Summary of the Micro-canonical, canonical, Isobaric-isothermal, grand-canonical ensembles.   
tags: md statistical_mechanics longposts
categories: md statistical_mechanics

bibliography: 2024-07-14-umbrellasampling.bib

toc:
  - name: Summary table
  - subsections:
    - name: Table 1 Micro-canonical
    - name: Table 2 Canonical
    - name: Table 3 Isobaric-isothermal
    - name: Table 4 Grand-canonical
  - name: Derivations of partiion functions and other properties
  - subsections: 
    - name: Canonical ensemble 
    - name: Isobaric-isothermol ensemble
    - name: Grand-canonical ensemble
  - name: Appendix
---

## Summary table

### Table 1 Micro-canonical

| Ensembles | Micro-canonical |
| :----------- | :------------: |
| **Comment**      |    This is just like to give a constrain on on Canonical ensenmble on the hyperplane of $\mathcal{H}(\mathbf{p}^N, \mathbf{r}^N) = E$    |
|**Const parameters**| $N,V,E$ |
| **Partition function**     |    $$\Omega_{E,V,N} = \frac{1}{h^{3N}N!}\int  d\mathbf p^N d\mathbf r^N \delta(\mathcal{H}(\mathbf{p}^N, \mathbf{r}^N)-E)$$    |
|**Partition function in configurational space**|  |
|**Probability to find a state**|  $1/\Omega$   |
| **Probability to find a configuration**$$\mathcal N$$       |       |
|**Free energy relationship**| |

### Table 2 Canonical

| Ensembles  | Canonical |
| :-----------  | :------------: |
| **Comment**      | Partition function 
|**Const parameters**| $N, V, T$|
| **Partition function**    | $$Q_{N,V,T} =\frac{1}{h^{dN} N!} \int d\mathbf p^N d\mathbf r^N exp\left[ -\beta  \mathcal{H}(\mathbf{p}^N, \mathbf{r}^N) \right]$$ |
|**Partition function in configurational space**| $\Lambda = \sqrt{\frac{h^2\beta}{2\pi m}}$ $$Q = \frac{1}{\Lambda^{3N} N!} \int  d\mathbf r^N exp   \left[-\beta \mathcal{U}(\mathbf r^{ N})\right]$$|
|**Probability to find a state** |$$P_1(E_i, V_1, T) \propto exp(-\beta E_i)$$$$P_i = \frac{\exp(-E_i/k_BT)}{\sum_j \exp(-E_j/k_BT)} $$  |
| **Probability to find a configuration**$$\mathcal N$$   | $$\mathcal{N}(\mathbf{r}^N) = \frac{1}{Z(N,V,T)}  \int  d\mathbf{r'}^N \delta(\mathbf{r}^N-\mathbf{r'}^N)exp   \left[-\beta \mathcal{U}(\mathbf{r'}^{ N})\right]$$  $$\mathcal{N}(\mathbf{r}^N) \propto  exp\left[-\beta \mathcal{U}(\mathbf{r}^{ N})\right] $$ |
|**Free energy relationship**| $$\beta F = -\ln Q(N,V,T)$$ |

### Table 3 Isobaric-isothermal

| Ensembles  | Isobaric-isothermal |
| :------------: | :------------: |  
| **Comment** |   |
|**Const parameters**| $N, P, T$|
| **Partition function**    |  $$Q_{N,P,T} =\frac{P}{h^{dN} N!} \int  dV' exp   \left(-\beta PV'\right)\int d\mathbf p^N d\mathbf r^N exp\left[ -\beta  \mathcal{H}(\mathbf{p}^N, \mathbf{r}^N) \right]$$ |
|**Partition function in configurational space**| $$Q(N,P,T) = \frac{P}{\Lambda^{3N} N!} \int  dV' exp   \left(-\beta PV'\right)\int  d\mathbf r^N exp   \left[-\beta \mathcal{U}(\mathbf r^{ N})\right]$$|
|**Probability to find a state** |  $$P_1(E_i,V_j)  \frac{exp(-\beta E_i-V_jP\beta)}{\sum_k\int dV' exp(-\beta E_k-V'P\beta)}$$ $$P_1(E_i, V_j, T) \propto exp(-\beta E_i-V_jP\beta)$$  |
| **Probability to find a configuration**$$\mathcal N$$   |  $$\mathcal{N}(\mathbf{r}^N,V) = \frac{1}{Z(N,P,T)}  \int_{V'}dV'\delta(V-V')\int_{\mathbf{r'}}  d\mathbf{r'}^N \delta(\mathbf{r}^N-\mathbf{r'}^N)exp\left[-\beta \mathcal{U}(\mathbf{r'}^{ N})-V'P\beta\right]$$ $$\mathcal{N}(\mathbf{r}^N,V) \propto  exp\left[-\beta \mathcal{U}(\mathbf{r}^{ N})-VP\beta\right] $$  |
|**Free energy relationship** | $$\beta G = -\ln Q(N,P,T)$$|

### Table 4 Grand-canonical

| Ensembles  | Grand-canonical |  
| :------------: |  :------------: |  
| **Comment**  | It is called Grand-canonical because from the formula of the partition function, the grand-canonical seems like the summation of many canonical ensemble.  |
|**Const parameters**|$\mu, V, T$|
| **Partition function**    |    |
|**Partition function in configurational space**|$$\Xi(\mu,V,T) = \sum_{N' = 0}^{+\infty}\frac{exp   \left(N'\mu\beta\right)}{\Lambda^{3N'} N'!}  \int  d\mathbf r^{N'} exp   \left[-\beta \mathcal{U}(\mathbf r^{N'})\right]$$ $$= \sum_{N' = 0}^{+\infty}exp   \left(N'\mu\beta\right)e^{-\beta F(N',V,T)}$$|
|**Probability to find a state** | $$P_1(E_i,N_j)  = \frac{exp(-\beta E_i+N_j\mu\beta)}{\sum_k\sum_{n = 0}^{N} exp(-\beta E_k+n\mu\beta)}$$ $$P_1(E_i, N_j, T) \propto exp(-\beta E_i+N_j\mu\beta)$$|
| **Probability to find a configuration**$$\mathcal N$$   |  $$\mathcal{N}(\mathbf{r}^N,N) =   \sum_{N'} \frac{1}{Z(N',\mu,T)}\delta(N-N')\int_{\mathbf{r'}}  d\mathbf{r'}^{N'} \delta(\mathbf{r}^{N'}-\mathbf{r'}^{N'})exp\left[-\beta \mathcal{U}(\mathbf{r'}^{N'})+N'\mu\beta\right]$$ $$\mathcal{N}(\mathbf{r}^N,N) \propto  exp\left[-\beta \mathcal{U}(\mathbf{r}^{ N})+N\mu\beta\right]$$   |
|**Free energy relationship** | Grand potential $\Phi$ $$\beta \Phi = \beta(F-N\mu) = \ln \Xi$$|  

## Derivations of partiion functions and other properties

The derivations are all based on the fact that a system is in ***weak interaction*** with another large environment. So we can use the taylor expansion of $\ln \Omega(N,V,T)$ to derive the partition function.:  

The derivation of partition function can be devided into 5 steps.  

* Be on equilibrium with some bath
* Do Taylor expansion on of $\ln \Omega(N,V,T)$ $E_i = 0$
* Use symmetry and the properties of identical particles
* Analytically express momentum integral
* Express partition function by configurational integral

The last three steps are basically the same and tedious. The last three steps can be found in the [previous blog](https://toflamus.github.io/blog/2024/smconcepts/#statistical-average)  

The derivation of density of a configuration is usually be done by using Dirac $\delta$ function.  

$$\mathcal{N}(\mathbf{r}^N) = \frac{1}{Z} \int  d\mathbf{r'}^N \delta(\mathbf{r}^N-\mathbf{r'}^N)exp   \left[-\beta \mathcal{U}(\mathbf{r'}^{ N})\right]$$  

### Canonical ensemble  

This one is classic:  

***Firstly***, on equilibrium with a **heat** bath.  

For constant $N, V, T$, the system is a closed system, only exchanging energy with environment by heat. Assuming that the heat bath is system $2$ and the target system is system $1$.  

When the system **2** is infinitely large. It is so large that the $E_i$ seems to be 0 compare to $E-E_i$. So we can always expand $f(E_i) = \ln\Omega_2(E-E_i)$ at $E_i \sim 0$, where $i$ stants for the $i^{th}$ state.  

***Secondly***, do Taylor expansion and take a limit on $E\rarr +\infty$:  

$$\ln\Omega_2(E-E_i, V_2, T,N_2) =\ln\Omega_2(E, V_2,T,N_2) - E_i\frac{\partial \ln\Omega_2(E)}{\partial E} + \mathcal{O}(1/E)$$

Because the $V$, $T$ and $N$ do not change, they will not be writen in the equation anymore.  

$$\ln\Omega_2(E-E_i) \approx \ln\Omega_2(E) - E_i\frac{\partial \ln\Omega_2(E)}{\partial E} $$

$$P_1(E_i) = P_2(E-E_i) \propto \frac{\Omega_2(E-E_i)}{\Omega_2(E)} = exp(-\beta E_i)$$

$$P_1(E_i, V_1, T) \propto exp(-\beta E_i)$$

The probebility to find system $1$ with an energy $E_i$ is the Boltzmann distribution:  

$$P_i = \frac{\exp(-E_i/k_BT)}{\sum_j \exp(-E_j/k_BT)} $$  

Now after the next three steps, the partition function in configurational space can be expressed as:  

$$Q(N,V,T) = \frac{1}{\Lambda^{3N} N!} \int  d\mathbf r^N exp   \left[-\beta \mathcal{U}(\mathbf r^{ N})\right]$$

As I mentioned before, the density of finding a state can be easily done by $\delta$ function.
$$\mathcal{N}(\mathbf{r}^N) = \frac{1}{Z(N,V,T)}  \int  d\mathbf{r'}^N \delta(\mathbf{r}^N-\mathbf{r'}^N)exp   \left[-\beta \mathcal{U}(\mathbf{r'}^{ N})\right]$$  

$$= \frac{1}{Z(N,V,T)} exp\left[-\beta \mathcal{U}(\mathbf{r}^{ N})\right] \int  d\mathbf{r'}^N \delta(\mathbf{r}^N-\mathbf{r'}^N)$$  

$$\mathcal{N}(\mathbf{r}^N) \propto  exp\left[-\beta \mathcal{U}(\mathbf{r}^{ N})\right] $$

### Isobaric-isothermol ensemble

***Firstly***, on equilibrium with a **heat** and **pressure** bath.  

For constant $N, P, T$, the system is a closed system, only exchanging energy with environment by heat. Assuming that the heat bath is system $2$ and the target system is system $1$.  

When the system **2** is infinitely large. It is so large that the $E_i$ seems to be 0 compare to $E-E_i$. What's more, the same is $V_j$ to $V-V_j$So we can always expand $f(E_i, V_j) = \ln\Omega_2(E-E_i, V-V_j)$ at $E_i, V_j \sim 0$, where $i$ stants for the $i^{th}$ when the volume of system $1$ is $V_j$.  

***Secondly***, do Taylor expansion for $\ln\Omega_2(E-E_i, V-V_j, T,N_2)$ at $E,V$and take a limit on total energy and volume $E,V\rarr +\infty$. Because the $T$ and $N$ do not change, they will not be writen in the equation anymore.  

$$\ln\Omega_2(E-E_i,V-V_j) \approx \ln\Omega_2(E,V) - E_i\left(\frac{\partial \ln\Omega_2(E,V)}{\partial E}\right)_{N,V} - V_i\left(\frac{\partial \ln\Omega_2(E,V)}{\partial V}\right)_{N,E}$$

because of thermodynamics:  

$$\left(\frac{\partial S}{\partial V}\right)_{N,E} =\frac{P}{T}$$

$$\ln\Omega_2(E-E_i,V-V_j) \approx \ln\Omega_2(E,V) - E_i\beta - V_jP\beta$$

$$P_1(E_i,V_j) = P_2(E-E_i,V-V_j) = \frac{\Omega_2(E-E_i,V-V_j)}{\sum_k\int dV' \Omega_2(E-E_k,V')}$$

$$P_1(E_i, V_j, T) \propto exp(-\beta E_i-V_jP\beta)$$

Now after the next three steps, the partition function in configurational space can be expressed as:  

$$Q(N,P,T) = \frac{P}{\Lambda^{3N} N!} \int  dV' exp   \left(-\beta PV'\right)\int  d\mathbf r^N exp   \left[-\beta \mathcal{U}(\mathbf r^{ N})\right]$$

As I mentioned before, the density of finding a state can be easily done by $\delta$ function.
$$\mathcal{N}(\mathbf{r}^N,V) = \frac{1}{Z(N,P,T)}  \int_{V'}dV'\delta(V-V')\int_{\mathbf{r'}}  d\mathbf{r'}^N \delta(\mathbf{r}^N-\mathbf{r'}^N)exp\left[-\beta \mathcal{U}(\mathbf{r'}^{ N})-V'P\beta\right]$$  

$$= \frac{1}{Z(N,V,T)} exp\left[-\beta \mathcal{U}(\mathbf{r}^{ N})-VP\beta\right]  \int  d\mathbf{r'}^N \delta(\mathbf{r}^N-\mathbf{r'}^N)$$  

$$\mathcal{N}(\mathbf{r}^N,V) \propto  exp\left[-\beta \mathcal{U}(\mathbf{r}^{ N})-VP\beta\right]$$  

### Grand-canonical ensemble

***Firstly***, on equilibrium with a **heat**, **particle** bath.  

For constant $\mu, P, T$, the system is an **open** system, this system not only exchange energy with the envrionment but also exchanges mass. Assuming that the heat, particle bath is system $2$ and the target system is system $1$.  

When the system **2** is infinitely large. It is so large that the $E_i,N_j$ seems to be 0 compare to $E-E_i,N-N_j$. So we can always expand $f(E_i, N_j) = \ln\Omega_2(E-E_i, N_j)$ at $E_i, N_j \sim 0$, where $i$ stants for the $i^{th}$ when the number of particles of system $1$ is $N_j$.  

***Secondly***, do Taylor expansion for $\ln\Omega_2(E-E_i, V_2, T,N-N_j)$ at $E,N$and take a limit on total energy and volume $E,N\rarr +\infty$. Because the $T$ and $V$ do not change, they will not be writen in the equation anymore.  

$$\ln\Omega_2(E-E_i,N-N_j) \approx \ln\Omega_2(E,N) - E_i\left(\frac{\partial \ln\Omega_2(E,N)}{\partial E}\right)_{N,V} - N_i\left(\frac{\partial \ln\Omega_2(E,N)}{\partial N}\right)_{E,V}$$

because of thermodynamics:  

$$\left(\frac{\partial S}{\partial N}\right)_{V,E} =-\frac{\mu}{T}$$

$$\ln\Omega_2(E-E_i,N-N_j) \approx \ln\Omega_2(E,N) - E_i\beta + N_j\mu\beta$$

$$P_1(E_i,N_j) = P_2(E-E_i,N-N_j) = \frac{\Omega_2(E-E_i,N-N_j,V_2)}{\sum_k\sum_{n = 0}^{N} \Omega_2(E-E_k,N-n,V_2)}$$

It may be a little bit confusing to do a summation like $\sum_{n = 0}^{N}$, because this violate the fact that $N_1$ is small. However, just like the infinite integral in the volume case, the probability would be infinite small then. Thus, it is allowed(Maybe?).  

$$P_1(E_i, N_j, T) \propto exp(-\beta E_i+N_j\mu\beta)$$

Now after the next three steps, the partition function $\Xi$ in configurational space can be expressed as:  

$$\Xi(\mu,V,T) = \sum_{N' = 0}^{+\infty}\frac{exp   \left(N'\mu\beta\right)}{\Lambda^{3N'} N'!}  \int  d\mathbf r^{N'} exp   \left[-\beta \mathcal{U}(\mathbf r^{N'})\right]$$
$$= \sum_{N' = 0}^{+\infty}exp   \left(N'\mu\beta\right)e^{-\beta F(N',V,T)}$$
As I mentioned before, the density of finding a state can be easily done by $\delta$ function.
$$\mathcal{N}(\mathbf{r}^N,N) =   \sum_{N'} \frac{1}{Z(N',\mu,T)}\delta(N-N')\int_{\mathbf{r'}}  d\mathbf{r'}^{N'} \delta(\mathbf{r}^{N'}-\mathbf{r'}^{N'})exp\left[-\beta \mathcal{U}(\mathbf{r'}^{N'})+N'\mu\beta\right]$$  

$$= \frac{1}{Z(N,\mu,T)} exp\left[-\beta \mathcal{U}(\mathbf{r}^{ N})+N\mu\beta\right]  \int  d\mathbf{r'}^N \delta(\mathbf{r}^N-\mathbf{r'}^N)$$  

$$\mathcal{N}(\mathbf{r}^N,N) \propto  exp\left[-\beta \mathcal{U}(\mathbf{r}^{ N})+N\mu\beta\right]$$  

## Appendix

| Ensembles | Micro-canonical | Canonical | Isobaric-isothermal | Grand-canonical |  
| :----------- | :------------: | :------------: | :------------: |  :------------: |  
| **Comment**      |    This is just like to give a constrain on on Canonical ensenmble on the hyperplane of $\mathcal{H}(\mathbf{p}^N, \mathbf{r}^N) = E$    | Partition function |   | It is called Grand-canonical because from the formula of the partition function, the grand-canonical seems like the summation of many canonical ensemble.  
|**Const parameters**| $N,V,E$ | $N, V, T$| $N, P, T$|$\mu, V, T$|
| **Partition function**     |    $$\Omega_{E,V,N} = \frac{1}{h^{3N}N!}\int  d\mathbf p^N d\mathbf r^N \delta(\mathcal{H}(\mathbf{p}^N, \mathbf{r}^N)-E)$$    | $$Q_{N,V,T} =\frac{1}{h^{dN} N!} \int d\mathbf p^N d\mathbf r^N exp\left[ -\beta  \mathcal{H}(\mathbf{p}^N, \mathbf{r}^N) \right]$$ |  $$Q_{N,P,T} =\frac{P}{h^{dN} N!} \int  dV' exp   \left(-\beta PV'\right)\int d\mathbf p^N d\mathbf r^N exp\left[ -\beta  \mathcal{H}(\mathbf{p}^N, \mathbf{r}^N) \right]$$ |  |
|**Partition function in configurational space**|  | $\Lambda = \sqrt{\frac{h^2\beta}{2\pi m}}$ $$Q = \frac{1}{\Lambda^{3N} N!} \int  d\mathbf r^N exp   \left[-\beta \mathcal{U}(\mathbf r^{ N})\right]$$|$$Q(N,P,T) = \frac{P}{\Lambda^{3N} N!} \int  dV' exp   \left(-\beta PV'\right)\int  d\mathbf r^N exp   \left[-\beta \mathcal{U}(\mathbf r^{ N})\right]$$|$$\Xi(\mu,V,T) = \sum_{N' = 0}^{+\infty}\frac{exp   \left(N'\mu\beta\right)}{\Lambda^{3N'} N'!}  \int  d\mathbf r^{N'} exp   \left[-\beta \mathcal{U}(\mathbf r^{N'})\right]$$ $$= \sum_{N' = 0}^{+\infty}exp   \left(N'\mu\beta\right)e^{-\beta F(N',V,T)}$$|
|**Probability to find a state**|  $1/\Omega$   |$$P_1(E_i, V_1, T) \propto exp(-\beta E_i)$$$$P_i = \frac{\exp(-E_i/k_BT)}{\sum_j \exp(-E_j/k_BT)} $$  |   $$P_1(E_i,V_j)  \frac{exp(-\beta E_i-V_jP\beta)}{\sum_k\int dV' exp(-\beta E_k-V'P\beta)}$$ $$P_1(E_i, V_j, T) \propto exp(-\beta E_i-V_jP\beta)$$  | $$P_1(E_i,N_j)  = \frac{exp(-\beta E_i+N_j\mu\beta)}{\sum_k\sum_{n = 0}^{N} exp(-\beta E_k+n\mu\beta)}$$ $$P_1(E_i, N_j, T) \propto exp(-\beta E_i+N_j\mu\beta)$$|
| **Probability to find a configuration**$$\mathcal N$$       |       | $$\mathcal{N}(\mathbf{r}^N) = \frac{1}{Z(N,V,T)}  \int  d\mathbf{r'}^N \delta(\mathbf{r}^N-\mathbf{r'}^N)exp   \left[-\beta \mathcal{U}(\mathbf{r'}^{ N})\right]$$  $$\mathcal{N}(\mathbf{r}^N) \propto  exp\left[-\beta \mathcal{U}(\mathbf{r}^{ N})\right] $$ |  $$\mathcal{N}(\mathbf{r}^N,V) = \frac{1}{Z(N,P,T)}  \int_{V'}dV'\delta(V-V')\int_{\mathbf{r'}}  d\mathbf{r'}^N \delta(\mathbf{r}^N-\mathbf{r'}^N)exp\left[-\beta \mathcal{U}(\mathbf{r'}^{ N})-V'P\beta\right]$$ $$\mathcal{N}(\mathbf{r}^N,V) \propto  exp\left[-\beta \mathcal{U}(\mathbf{r}^{ N})-VP\beta\right] $$  |  $$\mathcal{N}(\mathbf{r}^N,N) =   \sum_{N'} \frac{1}{Z(N',\mu,T)}\delta(N-N')\int_{\mathbf{r'}}  d\mathbf{r'}^{N'} \delta(\mathbf{r}^{N'}-\mathbf{r'}^{N'})exp\left[-\beta \mathcal{U}(\mathbf{r'}^{N'})+N'\mu\beta\right]$$ $$\mathcal{N}(\mathbf{r}^N,N) \propto  exp\left[-\beta \mathcal{U}(\mathbf{r}^{ N})+N\mu\beta\right]$$   |
|**Free energy relationship**| | $$\beta F = -\ln Q(N,V,T)$$ | $$\beta G = -\ln Q(N,P,T)$$| Grand potential $\Phi$ $$\beta \Phi = \beta(F-N\mu) = \ln \Xi$$|  

