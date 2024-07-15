---
layout: distill
title: Concepts of Statistical Mechanics in molecular simulation
date: 2024-07-14 8:00:00
description: A quick recap of the brief framework, concepts and notations in statistical mechanics for molecular simulation, (MD,MC).  
tags: md statistical_mechanics longposts
categories: md statistical_mechanics

bibliography: 2024-07-14-umbrellasampling.bib

toc:
  - name: Assumptions and concepts
  - subsections:
    - name: Eigenstates and Number of Eigenstates
    - name: Inverse temperature, zeroth law,and entropy
  - name: Constant T systems, Boltzmann distribution, partition function
  - subsections: 
    - name: From const T to Boltzmann distribution
    - name: Energy relations and partition function
    - name: Statistical Average
  - name: Configurational integral and probability density
---

## Assumptions and concepts

### Eigenstates and Number of Eigenstates

>Computer simulations are based on that classical mechanics can be used to describe the motions of atoms and molecules.  

The quantum mechanical notations are used for convenience.  

The ***Hamiltonian*** of the system $\mathcal{H}$ follows the equations of:  

$$\mathcal{H} |i \rangle  = E_i|i\rangle$$

Where $|i \rangle$ is a state.  

The ***number of eigenstates*** with energy $E$, volume $V$, and $N$ particals are denoted as $\mathcal{\Omega} = \mathcal{\Omega}(E,V,N)$  

### Inverse temperature, zeroth law,and entropy

When doing derivations, the $0^{th} \ law\ of\ thermodynamics$ works well.  

>Generally, we needs to assume an equilibrium with a large environment o r another system. This allow us to do Taylor expension at $E,V \sim 0$. The ***weakly interacting subsystems*** assumption is also required as we always want to decouple the energy of target system and environment while they are in thermoequilibrium, which means $E = E_1+E_2$ and $\mathcal{\Omega} = \mathcal{\Omega}_1(E_1)\times \mathcal{\Omega}_2(E_2)$  

If we assume the target system 1 is closed. Only energy can be changed between 1 and 2. What is the most likely distribution of the distribution of energy between 1 and 2. This allows to derive some mathmatical formula for the $0^{th}$ law of thermodynamics.

Starting from:

$$ln\mathcal{\Omega}(E_1, E-E_1) = ln\mathcal{\Omega}_1(E_1) + ln\mathcal{\Omega}_2(E-E_1)$$

At most likelyhood, the derivative of the total number of states should be 0.  

$$\left( \frac{\partial ln\mathcal{\Omega}(E_1,E-E_1)}{\partial E_1} \right)_{N,V,E}$$

$$\left(\frac{\partial ln\mathcal{\Omega}_1(E_1)}{\partial E_1}\right)_{N_1,V_1} = \left(\frac{\partial ln\mathcal{\Omega}_2(E_2)}{\partial E_2}\right)_{N_2,V_2}$$

This is a property that only relative the same system itself.  

$$\mathcal{Def}: \beta(E,V,N) = \left(\frac{\partial ln\mathcal{\Omega}(E)}{\partial E}\right)_{N,V} $$

From the $0^{th}$ law of thermodynamics, we know that the $\beta$ must has something to do with the convential temperature $T$.  teach

From the thermodynamic relation that:

$$\left(\frac{\partial S}{\partial E}\right)_{N,V} = 1/T$$

We wish that there is some relationship between $S$ and $ln\Omega$  

Now let's introduce the equation connecting the ***micro*** and ***macro*** states.  

> $S = k_B ln\Omega$  

This means that $\beta$ can  be defined as the ***Inverse temperature***.  

$$\beta = 1/k_BT$$  

## Constant T systems, Boltzmann distribution, partition function

### From const T to Boltzmann distribution

What would happen when a small ***closed*** system **1** is in equilibrium with a large heat bath **2** (environment)?  

We can actually imagine that in a specific temperature, the system can have different probability to be in different energy state. There is an energy distribution.  

Because the system has a fixed total energy and weakly interacting, the probability of finding system **1** with energy $E_i$, equals the probability of system **2** to be found at energy $E-E_i$.  

What's more, as the fundamental postulate of Statistical Mechanics goes:  
>An isolated system in an equilibrium macrostate has equal probability of being in any of the microstates corresponding to that macrostate.  

The probability is proportional to the number of the eigenstate of energy $E_i$  

$$P_i = P_{i,1}(E_i) = P_{i,2}(E-E_i)= \frac{\Omega_2(E-E_i)}{\sum_j \Omega_2(E-E_j)}$$  

Now we needs to mention a great assumption in derivation:  

> When the system **2** is infinitely large. It is so large that the $E_i$ seems to be 0 compare to $E-E_i$. So we can always expand $f(E_i) = ln\Omega_2(E-E_i)$ at $E_i \sim 0$

$$ln\Omega_2(E-E_i) =ln\Omega_2(E) - E_i\frac{\partial ln\Omega_2(E)}{\partial E} + \mathcal{O}(1/E)$$  

Which is:

$$ln\Omega_2(E-E_i) =ln\Omega_2(E) - E_i/k_BT + \mathcal{O}(1/E)$$  

When $E \rarr +\infty$:

$$P_i \propto \exp(-E_i/k_BT) $$  

After normalization, the equation becomes ***Boltzmann distribution***: 

$$P_i = \frac{\exp(-E_i/k_BT)}{\sum_j \exp(-E_j/k_BT)} $$  

### Energy relations and partition function

Now let's get the formula for average energy:  
$$ \langle E \rangle = \sum_iE_iP_i $$
$$ = \sum_i\frac{E_i\exp(-E_i/k_BT)}{\sum_j \exp(-E_j/k_BT)}$$  
$$ = -\frac{\partial ln\sum_i\exp(-E_i/k_BT)}{\partial 1/k_BT}$$  

Now we can define the ***Partition function*** of *canonical ensembles*:  
$$\mathcal{Def}: Q(N,V,T) = \sum_i\exp(-E_i/k_BT)$$

$$ \langle E \rangle= -\frac{\partial lnQ}{\partial 1/k_BT}$$

***Helmholtz free energy*** relates to energy with:  

$$E = \frac{\partial F/T}{\partial 1/T}$$  

>$$F = -k_BT \ln Q = -k_BT \ln \sum_i\exp(-E_i/k_BT)$$  

This is an extremely important equation for Helmholtz free energy and we will use this a lot when calculating free energies.  

### Statistical Average

With probability and partition function in hand, let's derive the macroscopic average of an observable $A$.

The average of an observable $A$ in eigenstate $i$ is:  
$$\langle A \rangle_i= \langle i|A| i \rangle$$
This average is the average of the wave function.  

At temperature T, the average of an obserable should be the average of the average of every state. This average is the average to all the states.  

$$\langle A \rangle= \sum_i\frac{\langle i|A| i \rangle\exp(-E_i/k_BT)}{\sum_j \exp(-E_j/k_BT)}$$  

This function means that if we want to get a macrostate average of a funcition. We can firstly solve the eigenstates of the Schrodinger equation:  

$$\mathcal{H} \psi = E \psi$$

Then, we can solve the average of $\langle i|A| i \rangle$. Finally, after doing this for every $E_i$ and solved every eigenstate, we can determine the final macro average.  

However, this process is never workable, as we will have so many quantum states if we have a real macro-system.  

Fortunately, this function can be further transformed with:
$$exp(-E_i \beta) = \langle i|exp(-\mathcal{H}\beta)|i\rangle$$

Taking this equation into consideration:  

$$\langle A \rangle= \sum_i\frac{\langle i|A| i \rangle \langle i|exp(-\mathcal{H}\beta)|i\rangle}{\sum_j \exp(-E_j/k_BT)}$$

Because the orthogonality or eigenfunctions $ | i \rangle \langle i| = \mathbb I$

$$\langle A \rangle= \sum_i\frac{\langle i|exp(-\mathcal{H}\beta)A|i\rangle}{\sum_j \langle j|exp(-\mathcal{H}\beta)|j\rangle}$$

$$= \frac{Tr(exp(-\mathcal{H}\beta)A)}{Tr(exp(-\mathcal{H}\beta))}$$

Where the $Tr$ denotes the trace of the matrix 

$$[exp(-\mathcal{H\beta})A]_{ij} = \langle i|exp(-\mathcal{H}\beta)A|j\rangle$$  

Because $\mathcal{H} = \mathcal{K} + \mathcal{U}$, in which $\mathcal{K}$ is a function of momentum eigenfunction and $\mathcal{U}$ is a function of coordinate eigenfunction, what we really want to do is to simplify the equation by variable separation:  

$$exp(-\mathcal{H}\beta) =  exp(-\mathcal{K}\beta)exp(-\mathcal{U}\beta)\ \ \ (Wrong)$$  

However, we cannot promise $\mathcal{H} = \mathcal{K} + \mathcal{U}$ is diagonal. There is actually a commutator in the equation.  

$$exp\{-[\mathcal{K}+\mathcal{U}+ \mathcal{O}([\mathcal{K},\mathcal{U}])]\beta\} =  exp(-\mathcal{K}\beta)exp(-\mathcal{U}\beta)$$

According to the textbook<d-cite key="undMD"></d-cite>, the diagonality only exist when $\hbar \rarr 0$<d-footnote>This means the world is totally continuous. I do not know how to prove the relationship between the diagnoality and contiunity condition. </d-footnote>

Anyway, if we really satisfied the condition, we'd have:  

$$Tr exp(\mathcal{-\beta H}) = \sum_{r,k} \langle r|e^{-\beta \mathcal{U}}|r\rangle \langle r|k\rangle\langle k|e^{-\beta \mathcal{K}}|k\rangle \langle k|r\rangle$$

Note:  

$$\langle r|e^{-\beta \mathcal{U}}|r\rangle = exp[-\beta \mathcal{U}(\mathbf r^{ N})]$$  

$$\langle k|e^{-\beta \mathcal{K}}|k\rangle = exp[-\beta \sum_{i=1}^{N}p_i^2/(2m_i)]$$  

$$p_i = \hbar k_i$$  

$$\langle r|k\rangle\langle k|r\rangle = 1/V^N$$  

Where $V$ is the volume of the system and the $N$ is the number of the particles. Thus the Partition function for classical system can be:  

$$Q_{classical} = Trexp(-\beta \mathcal{H}) \approx \frac{1}{h^{dN} N!} \int d\mathbf p^N d\mathbf r^N exp\left\{ -\beta  \left[ \sum_{i=1}^{N}p_i^2/(2m_i)+\mathcal{U}(\mathbf r^{ N})\right] \right\}$$

The term $N!$ appears because of the all same particles in this system. This related to the famous [Gibbs paradox](https://en.wikipedia.org/wiki/Gibbs_paradox). Now the average becomes:  

$$\langle A \rangle = \frac{\int d\mathbf p^N d\mathbf r^N A(\mathbf p^N ,\mathbf r^N)exp\left\{ -\beta  \left[ \sum_{i=1}^{N}p_i^2/(2m_i)+\mathcal{U}(\mathbf r^{ N})\right] \right\}}{\int d\mathbf p^N d\mathbf r^N exp\left\{ -\beta  \left[ \sum_{i=1}^{N}p_i^2/(2m_i)+\mathcal{U}(\mathbf r^{ N})\right] \right\}}$$

## Configurational integral and probability density

As we assumed before the integration over the potential does not depend on momentum. Thus we can now integrate momentum analytically. This may have different forms for different systems. However, we assume that the 3-d momentum is symmetric and every atom is the same.  

$$\int d\mathbf p^N exp\left[ -\beta \sum_i\frac{\mathbf{p}_i^N}{2m}\right] = \left[\int dp^N exp\left[ -\beta \sum_i\frac{p^N}{2m}\right]\right]^{3N} = \left(\frac{2\pi m}{\beta}\right)^{\frac{3N}{2}}$$

Assuming:  

$$\Lambda = \sqrt{\frac{h^2\beta}{2\pi m}}$$

The partition function becomes:  

$$Q = \frac{1}{\Lambda^{3N} N!} \int  d\mathbf r^N exp   \left[-\beta \mathcal{U}(\mathbf r^{ N})\right]$$

Now we can define the ***configurational integral*** as:  
$$\mathcal{Def}: Z(N,V,T) = \int  d\mathbf r^N exp   \left[-\beta \mathcal{U}(\mathbf r^{ N})\right]$$  

Now we can also define the proability of finding a system in a particular configuration $\mathbf{r}^N$ is:  

$$\mathcal{N}(\mathbf{r}^N) = \frac{1}{Z(N,V,T)}  \int  d\mathbf{r'}^N \delta(\mathbf{r}^N-\mathbf{r'}^N)exp   \left[-\beta \mathcal{U}(\mathbf{r'}^{ N})\right]$$  

$$= \frac{1}{Z(N,V,T)} exp\left[-\beta \mathcal{U}(\mathbf{r}^{ N})\right] \int  d\mathbf{r'}^N \delta(\mathbf{r}^N-\mathbf{r'}^N)$$  

If the ensemble average of a quality $A(\mathbf r^N)$ only depends on the cooridnates, then:  

$$\langle A \rangle = \frac{1}{Z(N,V,T)}  \int  d\mathbf r^N A(\mathbf r^N)exp   \left[-\beta \mathcal{U}(\mathbf r^{ N})\right]$$  