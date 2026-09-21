---
Title: "Hera Inter-Satellite link Doppler characterization for Didymos Gravity Science experiments"
Year: 2022
Authors: Edoardo Gramigna, Jeppe Græsdal Johansen, Riccardo Lasagni Manghi, José Magalhães, Marco Zannoni, Paolo Tortora, Etienne Le Bras, Andrea Togni
Tags: [Space_vehicles, Doppler_shift, Doppler, Conferences, CubeSat, Didymos, Gravity, Harmonic_analysis, Hera, Inter-Satellite_Link, Metrology, Numerical_simulation, Planetary_orbits, Radio_Science, small_bodies, smallsat]
---
Zotero PDF Link: [Full Text PDF](zotero://select/library/items/FEVPLCV6)
Related: [[Doppler]]

### Persistent Notes
This paper is almost exactly the physical measurement scenario we want: **one spacecraft measuring Doppler from another spacecraft through an inter-satellite radio link**, and then using those measurements in an **orbit determination process**.

The abstract explicitly describes the observable as the Doppler shift caused by the **relative line-of-sight velocity between two spacecraft**.

They define the fractional frequency as

$\boxed{ y= \frac{f_{\mathrm{Doppler}}}{f} = -\frac{\dot{\rho}}{c} }$

where $\dot{\rho}$ is the **two-way range-rate** and $c$ is the speed of light.

This is directly connected to the low-velocity Doppler equation:

$\frac{\Delta f}{f_0}\approx-\frac{v_r}{c}.$

Here,

$v_r \leftrightarrow \dot{\rho}.$

So you can already connect the theory you've been studying to an actual inter-satellite measurement:

$\boxed{ \text{relative spacecraft motion} \rightarrow \dot{\rho} \rightarrow \text{Doppler frequency shift} \rightarrow \text{OD observable} }$

The radio system tracks the **phase of the received carrier** using a phase-locked loop (PLL).

The Doppler observable is calculated from the change in phase over a count interval:

$\boxed{ f_{\mathrm{Doppler}} = \frac{ \phi(t+T_c/2)-\phi(t-T_c/2) }{ 2\pi T_c } }$

with $T_c=60\,\mathrm{s}$ in their experiment.

Conceptually:

$\text{received radio wave} \rightarrow \text{track carrier phase} \rightarrow \Delta\phi \rightarrow \Delta f \rightarrow \dot{\rho}.$

That answers an important practical question for your project: **what does a spacecraft actually measure when we say it "measures Doppler"?**

It is measuring/tracking the radio carrier's phase/frequency, from which range-rate is inferred.

They actually feed the simulated measurements into an **OD process** using JPL's MONTE software.

They compare three scenarios:

A:Hera only
B:Hera + ISL range
C:Hera + ISL range + Doppler.

And the result is quite striking: the paper says that **most of the additional information from the ISL comes from Doppler rather than range**. Adding ISL Doppler enables much better estimation of Didymos's gravity field and significantly improves estimation of Dimorphos's mass.

The plots on page 6 make this particularly clear: as ISL Doppler measurements are added and the observing duty cycle increases, the uncertainties in the gravity parameters decrease substantially.

#### Relevance to RODINN
This is a **core paper**. 

The paper also gives us a useful target for later: their navigation-mode estimated range-rate accuracy is **30 mm/s**, while the dedicated radio-science mode has a much tighter requirement of **50 μm/s at 60 s integration time**.

### In-text annotations



%% Import Date: 2026-09-15T14:38:21.681+01:00 %%
