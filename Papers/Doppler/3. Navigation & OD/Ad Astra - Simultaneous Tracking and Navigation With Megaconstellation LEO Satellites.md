---
Title: "Ad Astra: Simultaneous Tracking and Navigation With Megaconstellation LEO Satellites"
Year: 2024
Authors: Zaher M. Kassas, Nadim Khairallah, Sharbel Kozhaya
Tags:
  - Doppler_OD
  - Doppler_only
  - range_rate
  - EKF
  - simultaneous_estimation
  - LEO
  - Observability
  - Orbital_dynamics
  - J2
  - Clock_drift
---
Zotero PDF Link: [Full Text PDF](zotero://select/library/items/E5I7MP8I)
Related:[[Doppler]]

### Persistent Notes
It uses **Doppler measurements in an estimation framework to recover unknown satellite position and velocity states**.

They introduce **STAN (Simultaneous Tracking and Navigation)**. A receiver on an aircraft/ground vehicle listens to signals from LEO satellites whose precise ephemerides and clock errors are not assumed to be known.

The key idea is that they simultaneously estimate the vehicle state, LEO satellite states and clock states using an **Extended Kalman Filter (EKF)**. The measurements can be pseudorange, Doppler and/or carrier phase.

The paper explicitly includes receiver/satellite clock drift, ionospheric and tropospheric delay rates, and measurement noise.

**Position appears inside the Doppler measurement equation through the LOS direction**.

$\hat{\boldsymbol\rho} = \frac{\mathbf r_r-\mathbf r_s} {\|\mathbf r_r-\mathbf r_s\|}.$

For each LEO satellite, they really are estimating **satellite 3-D position and velocity from measurements that can include Doppler**, rather than merely predicting Doppler from an already-known orbit.

They also propagate the satellite state using orbital dynamics including the dominant $J_2$ perturbation.

#### Relevance to RODINN

This is **not satellite-to-satellite relative OD**. The receiver is navigating while simultaneously estimating the orbits of the LEO satellites. Their STAN state therefore contains both the receiver/vehicle state and the satellite states.

They explicitly acknowledge **unobservability/poor estimability**. In fact, their framework assumes the vehicle initially has GNSS so that the filter gets suitable initial state estimates before GNSS becomes unavailable.

Doppler alone at one instant does not give you the full state.

Instead, the filter combines changing geometry over time + orbital dynamics + measurements + initialization.

Very relevant methodology, but receiver is an aircraft/ground vehicle rather than another satellite. Estimates LEO satellite position/velocity simultaneously with receiver state using EKF and Doppler/pseudorange/carrier phase.

Potential gap: inter-satellite Doppler, relative OD, physics-informed neural estimation.

### In-text annotations



%% Import Date: 2026-09-15T16:24:43.983+01:00 %%
