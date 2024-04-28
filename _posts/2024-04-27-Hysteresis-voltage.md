---
layout: distill
title: Hysteresis voltage modeling
date: 2024-04-27 14:25:00
description: Simple introduce hysteresis voltage and its phenomenological modeling
tags: batteries lithium-ion battery-study
categories: battery-study

bibliography: 2024-04-27-Hysteresis-voltage.bib
toc:
  - name: Hysteresis voltage
  - name: Main loop and minor loop
  - name: Hysteresis modeling
  - name: Enhanced self-correcting (ESC) model
  - subsections:
       - name: Single resistor-and-capacitor pair
       - name: ESC model and its *state equation*
---

## Hysteresis voltage

Definition: OCV-SOC curves for charging and discharging Li-ion batteries do not overlap. The difference between the curves is defined as *Hysteresis voltage*.  

The modeling can be physics-based or phenomenon-based.  

I find the modeling of hysteresis is a deep field because the hysteresis phenomenon can happen in various disciplines. There is even a book about hysteresis modeling<d-cite key="hysteresismodelingmath"></d-cite>. There are plenty of different models to model a hysteresis, such as Prandtl-Ishlinskii hysteresis model<d-cite key="4739202"></d-cite>(This is a topic in control engineering). However, they are not covered in this blog post. I just put them here for further reference. The main framework is still from L. Plett's book.<d-cite key="BMS_vol1"></d-cite>  

## Main loop and minor loop

This part is mainly from the Guillaume Larrat's thesis. <d-cite key = "Lihysteresismodeling">

The charging and discharging OCV curves that were displayed in the figure below allows to create a voltage hysteresis loop for a SOC varying from 0% to 100% which includes the whole range of possible values for the SOC.  

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-27-Hysteresis-voltage/OCV_curve.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

It is composed of the two **major** OCV curves: a charge from 0% to 100% SOC and a full discharge from 100% to 0%. The corresponding voltage hysteresis loop is then called a major loop. However, if the cell is partially charged or discharged from a state different than 0% or 100%, the OCV will not follow the two curves displayed earlier. If a cell is at a 60% SOC and is then discharged to 40% and then charged back to 60%, this will create a minor loop as shown in Figure below:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-27-Hysteresis-voltage/major_minor_loop.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Assupmtion: The loop of a real-time charge/discharge process only locates insides the major loop. Apparently, the changing rate in a minor loop is different from the major loop.  

## Hysteresis modeling

Let's just build a simple model:  
Assumptions:  

* Linear: The changing rate of hysteresis voltage only depends the difference between maxium OCV and current OCV.  
* Past path invariant: The hyseresis does not depend on how to get to the state but just and past state themselves. Actually, this is not true.  

$$h(z(t)) = OCV_{charge}(z(t))-OCV_{discharge}(z(t))$$
$$\frac{dh(z,t)}{dz} = \gamma sgn(\dot z)(M(z,\dot z)- h(z,t))$$

$\gamma$ is just a coefficient for linear approximation.  
$M(z,\dot z)$: A function that gives the maximum polarization due to the hysteresis as a function of SOC and rate of charge.  
$M(z,\dot z)- h(z,t)$:  Indicates that the rate of change of the hysteresis voltage is proportional to the distance of the current hysteresis value from the main hysteresis loop. In other words, the driving force decides the rate of change.  
$z(t)$ defines the changing direction of the hysteresis. For charging process, $\dot z > 0$, which means hysteresis tends to be larger, this means the $$OCV_{charge}(z(t))$ tends to be closer to the maximum OCV.  

Because our previous equivalent circuit model depends on the time, we use the chain rule to make the differencial equation a function of time.  

$$\frac{dh(z,t)}{dz} \frac{dz}{dt} = \gamma sgn(\dot z)(M(z,\dot z)- h(z,t)) \frac{dz}{dt}$$

$$\frac{dz}{dt} = -\eta(t)i(t)/Q$$
$\dot z sgn(\dot z) = |z|$

$$\frac{dh(z,t)}{dz} \frac{dz}{dt} = \gamma (M(z,\dot z)- h(z,t)) *|\frac{\eta(t)i(t)}{Q}|$$

To make life easier **assume $I(t)$ & $M(z,\dot z)$ are constant during sampling period**. So if one want to get the fully profile, multiple linear approximation can be made to tackle this problem.  

Solve the ODE and make it discrete, and do some rearrangements:

$$h[s+1] = exp(-|\frac{\eta[s]I\Delta t\gamma}{Q}|)h[s] + M(z,\dot z)(1-exp(-|\frac{\eta[s]I\Delta t\gamma}{Q}|))$$

Note: $M(z,\dot z) $ varies with current orientation, the simplest way to make it a const is by $M(z,\dot z) = -M sgn(i(t))$

Now the equation becomes:  

$$h[s+1] = exp(-|\frac{\eta[s]I\Delta t\gamma}{Q}|)h[s] - Msgn(i(t))(1-exp(-|\frac{\eta[s]I\Delta t\gamma}{Q}|))$$

$A_H[s] = exp(-|\frac{\eta[s]I\Delta t\gamma}{Q}|)$

$$h[s+1] = A_H h[s] - Msgn(i(t))(1-A_H)$$
## Enhanced self-correcting (ESC) model

*Enhanced* means the model also includes hysteresis effects.  
*Self-correcting* means the model converges to the $OCV+hysteresis$ when $i = 0$  

From the discussion on equivalant circuit models, now with new information with hysteresis effects. The OCV with half cell equivalent circuit can be viewed as follows:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-27-Hysteresis-voltage/circuit1.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    half-cell with OCV and hysteresis
</div>

When the time scale difference bewteen Warburg impedance and other circuit elements are so large, that the Warburg impedance get out on to the main branch.  

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-27-Hysteresis-voltage/circuit2.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    approximation of half-cell with OCV and hysteresis.
</div>

As we have discussed in another blog the linear part of Warburg impedance can be approximated by a series of parallel resistor-and-capacitor pairs.  

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-27-Hysteresis-voltage/circuit3.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Let's denote the charge transfer resistance and double layer capacity as $R_{0}$ and $C_{0}$

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024-04-27-Hysteresis-voltage/circuit4.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### Single resistor-and-capacitor pair

Let's use the current to analyze resistor-and-capacitor pair.  

For a single pair,  use the voltage change of a single resistor-and-capacitor pair as a birdge:

$$u_k = \frac{Q_k}{C_k} = \frac{1}{C_k}\int_0^t I-i_k dt$$
$$u_k = R_k i_k$$
where $i_k$ is the current goes through $R_k$ and I is main branch current.  

After take a derivative and rearrangement:  

$$i_k(t) + \frac{i(t)}{C_kR_k} = \frac{I(t)}{C_kR_k}$$

Solve the ODE using Cauchy's method.  

$$i_k(t) = Ae^{-\frac{t}{C_kR_k}} + i_c(t)$$

When in reality, the I(t) can be AC current such as in the case of (EIS). So it can be extended to a fourier series. This means the solution of the ODE is also a fourier series, denoted $i_c(t) = I'(t)$.  

Now let's think about the discret form.  
$$i_k[s] = Ae^{-\frac{s\Delta t}{C_kR_k}} + i_c[s]$$
$$i_k[s+1] = Ae^{-\frac{(s+1)\Delta t}{C_kR_k}} + i_c[s+1]$$
Then:

$$i_k[s+1] = F_k * i_k[s] + i_c[s+1] - F_k i_c[s]$$
$$F_k = e^{-\frac{\Delta t}{C_kR_k}}$$

To make life easier **assume I(t) is a constant during sample period**. So if one want to get the fully profile, multiple linear approximation can be made to tackle this problem.  

$$i_c[s] = i_c[s+1] = I$$

The original solution becomes:  
$$i_k[s+1] = F_k * i_k[s] + (1- F_k)I$$

Convert this equation to a matrix form:  

$$\vec i_r[s+1] = \mathbb A_{RC} * \vec i_r[s] + b_{RC} I$$
$$\mathbb A_{RC} = diag(F_k)$$
$$[\vec b_{RC}]_i = 1-F_i$$

### ESC model and its *state equation*

Combine everything above together, we get the *state equation* of ESC model
\[
    \begin{bmatrix}
    z[s+1]\\
    \vec i_r[s+1]\\
    h[s+1]\\
    \end{bmatrix}
    =
    \begin{bmatrix}
    1 & 0 & 0\\
    0 & \mathbb A_{RC} & 0 \\
    0 & 0 & A_H\\
    \end{bmatrix}
    \begin{bmatrix}
    z[s]\\
    \vec i_r[s]\\
    h[s]\\
    \end{bmatrix}
    + 
    \begin{bmatrix}
    -\frac{\eta [s] \Delta t}{Q} & 0\\
    \vec b_{RC} & 0\\
    0 & A_H-1
    \end{bmatrix}
    \begin{bmatrix}
    I & sgn(I)\\
    \end{bmatrix}
\]  

## Afterwords

### SOC method to analysis the circuit

When considering the voltage of each resistor-and-capacitor pair,the ODE for a single resistor-and-capacitor pair is:

$$\dot u_i = -\frac{1}{R_i C_i} u_i + \frac{1}{C_i} I$$

The ODEs for resistor-and-capacitor pairs can be expressed as:

\[
    \begin{bmatrix}
    \dot u_0\\
    \dot u_1\\
    \vdots\\
    \dot u_n\\
    \end{bmatrix}
    =
    \begin{bmatrix}
    -\frac{1}{C_0R_0} & 0 & \cdots & 0 \\
    0 & -\frac{1}{C_1R_1}  & \cdots & 0 \\
    \vdots & 0 & \cdots & 0 \\
    0 & \cdots & 0 & -\frac{1}{C_nR_n}\\
    \end{bmatrix}
    \begin{bmatrix}
    u_0\\
    u_1\\
    \vdots\\
    u_n\\
    \end{bmatrix}
    + 
    \begin{bmatrix}
    \frac{1}{C_0}\\
    \frac{1}{C_1}\\
    \vdots\\
    \frac{1}{C_n}\\
    \end{bmatrix}
    I
\]  
This is the method with voltage to describe the SOC but however I need to use current instead of voltage to analyze the circuit here. 

I did not heard about this topic too much before when I concentrated at ElectroChemistry. The hysteresis effect is important for Battery Management Systems.  
