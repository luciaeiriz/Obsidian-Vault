---
Title: First Results of Differential Doppler Positioning with Unknown Starlink Satellite Signals
Year: 2022
Authors: Mohammad Neinavaie, Zeinab Shadram, Sharbel Kozhaya, Zaher M. Kassas
Tags:
  - Satellites
  - LEO
  - Doppler_positioning
  - differential_Doppler
  - range_rate
  - EKF
  - ground_satellite
---
Zotero PDF Link: [Full Text PDF](zotero://select/library/items/R5ZK8LFE)
Related: [[Doppler]]

### Persistent Notes
It uses real Stralink Doppler measurements for positioning, not just simulations. It estimates and tracks Doppler from unknown Starlink signals, then uses a **differential Doppler framework** to estimate the position of a rover despite kilometer-scale satellite ephemeris errors. 

Both receivers observe the same satellites. The idea is to subtract the rover and base Doppler observables so that common errors cancel, especially the satellite clock drift, which makes the measurement much cleaner.

#### Relevance to RODINN
Explains how position enters Doppler through LOS geometry.

The paper notes that subtracting the base Doppler from the rover Doppler removes common satellite clock-drift terms. This is potentially relevant later if your inter-satellite Doppler setup has common clock/frequency biases that could be cancelled through differencing or multi-link combinations.

This is still **ground/user positioning**, not relative orbit determination between two satellites.
### In-text annotations



%% Import Date: 2026-09-15T16:23:58.620+01:00 %%
