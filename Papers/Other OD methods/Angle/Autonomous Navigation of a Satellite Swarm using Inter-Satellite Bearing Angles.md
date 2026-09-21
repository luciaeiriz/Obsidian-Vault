---
Title: "Autonomous Navigation of a Satellite Swarm using Inter-Satellite Bearing Angles"
Year: 2025
Authors: Justin Kruger, Simone D’Amico
Tags: []
---
Zotero PDF Link: [PDF](zotero://select/library/items/FRA35I43)
Related: [[Angle ROD]]

### Persistent Notes

StarFOX, the angles-only payload on NASA's Starling mission (4 CubeSats, LEO, launched July 2023). First flight demonstration of maneuver-free angles-only convergence, multi-target/multi-observer angles-only navigation, autonomous onboard initialization for an unknown target, and simultaneous absolute+relative OD from bearing angles alone.

**Method.** The ARTMS architecture, three modules. Image processing (IMP) does multi-hypothesis target tracking. Batch orbit determination (BOD) explicitly splits the state: strongly-observable relative orbital elements go through ordinary batch least-squares, while the weakly-observable along-track/range term is handled by grid-sampling 100–300 candidate values rather than trying to estimate it directly. Sequential orbit determination (SOD) runs an adaptive UKF over the full nonlinear dynamics (not the linearized CW model the angles-only playground uses), chosen specifically because the UKF's handling of higher-order moments is what lets bearing angles alone converge without any maneuver.

Observability handling here is genuinely different from AVANTI: nonlinear dynamics plus long observation arcs plus a UKF substitute for a maneuver, and multi-observer fusion over an inter-satellite link is the other lever (the "multi-LOS" fix in Angle ROD, now with flight numbers behind it).

**Results.** Single-observer maneuver-free convergence to 1.3% of target range (1σ); multi-observer improves that to 0.6%; autonomous initialization achieved from as few as ~28 bearing measurements; simultaneous absolute+relative OD (no GPS, bearing angles only, 3 cooperating observers) took an initial 6.95 km position error down to 1.2 km over ~48 hours. One useful negative result: small in-flight maneuvers (~0.01 m/s) were too small to meaningfully improve the estimate, a real data point for "how big does the maneuver actually need to be."

**RODINN relevance.** The single most directly useful paper of the three read alongside this one. Real flight data in the nonlinear/poorly-observable/autonomous/multi-target regime the proposal is aimed at, touching Objectives 1, 2, 3 and 5. The explicit split between strongly- and weakly-observable state components, handled by different estimators, is a design pattern worth keeping in mind when scoping what a PINN actually needs to learn versus what can stay classical.

### In-text annotations



%% Import Date: 2026-09-03T15:02:16.451+01:00 %%
