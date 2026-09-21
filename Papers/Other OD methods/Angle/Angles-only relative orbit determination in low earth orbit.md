---
Title: "Angles-only relative orbit determination in low earth orbit"
Year: 2018
Authors: Jean-Sébastien Ardaens, Gabriella Gaias
Tags: []
---
Zotero PDF Link: [PDF](zotero://select/library/items/SNAVCLSQ)
Related: [[Angle ROD]].

### Persistent Notes

Overview of the ground-based Angle ROD.

**Method.** Post-facto batch least-squares, state = inertial relative position/velocity plus the chaser's drag coefficient (to absorb differential drag). Measurement = right-ascension/declination pairs extracted from star-tracker images via a two-stage target detection pipeline: DBSCAN clustering plus a second-order Bezier fit to recognize a moving target's trajectory kinematically, then a brightness-based detector once the target gets close enough to outshine background stars. Observability is handled the "classical" way, leaning on the rendezvous maneuvers themselves; at very far range (30–45 km, low-maneuver arcs) the least-squares fit only converges at all if constrained by a TLE-derived a priori covariance.

**Results.** Accuracy improves continuously as range decreases, meter-level by <1 km separation, with the along-track/range-like component always the weakest (hundreds of meters to km error at far range even when lateral accuracy is at the meter level). Independently validated against German TIRA radar tracking at >40 km. Worth keeping: the paper explicitly notes the least-squares covariance is "often found to be too optimistic" relative to true error, the same overconfidence pattern the angles-only playground's EKF demo turned up, now with flight-data backing rather than just a toy simulation.

**RODINN relevance.** Strongest real-world grounding for Objective 2 (nonlinear, poorly-observable regime, strong differential drag and J2 in play) and a good source of realistic noise/perturbation magnitudes to sanity-check simulations against.

### In-text annotations



%% Import Date: 2026-09-03T14:54:56.989+01:00 %%
