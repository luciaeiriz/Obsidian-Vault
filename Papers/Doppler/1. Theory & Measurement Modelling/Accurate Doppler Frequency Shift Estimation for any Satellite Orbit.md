---
Title: Accurate Doppler Frequency Shift Estimation for any Satellite Orbit
Year: 2007
Authors: Shervin Amiri, Mohammad Mehdipour
Tags:
  - Doppler_modelling
  - range_rate
  - LOS_velocity
  - Orbital_dynamics
  - Elliptical_orbit
  - Ground_receiver
  - Doppler_rate
---
Zotero PDF Link: [Full Text PDF](zotero://select/library/items/XM4P3RUQ)
Related: [[Doppler]]

### Persistent Notes
This paper solves the inverse problems, with a known orbit and a known ground station it calculates the relative motion and from it the Doppler shift 

It explicitly states that calculating Doppler requires the relative velocity between the satellite and ground terminal, and that this relative motion comes from their positions.

The satellite orbit is described by the six classical orbital elements, and they account for perturbations associated with Earth's non-spherical gravity using the Gauss planetary equations.

Section IV, **“Doppler Equations,”** is probably the most relevant section.

#### Relevance to RODINN

Despite the title saying **“Doppler Frequency Shift Estimation,”** they don't actually estimate an orbit from a measured Doppler.

They already know the satellite orbital parameters and ground-station.

The conclusion explicitly describes the method as a **Doppler prediction scheme** that takes the satellite orbital parameters and ground-terminal position as inputs.

So there is **no EKF, least-squares OD, state recovery, relative orbit estimation, or Doppler inversion** here.

### In-text annotations



%% Import Date: 2026-09-15T16:25:02.243+01:00 %%
