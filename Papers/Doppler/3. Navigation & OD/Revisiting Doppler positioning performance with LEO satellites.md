---
Title: Revisiting Doppler positioning performance with LEO satellites
Year: 2023
Authors: Chuang Shi, Yulu Zhang, Zhen Li
Tags:
  - Observability
  - Geometry
  - Doppler_positioning
  - range_rate
  - LEO
  - Orbit_error
  - Clock_drift
---
Zotero PDF Link: [PDF](zotero://select/library/items/9J4FJCPG)
Related: [[Doppler]]

### Persistent Notes
This paper goes beyond simply showing that Doppler positioning works. It also studies, what **limits Doppler positioning accuracy**.  

It is still **receiver positioning**, not inter-satellite relative OD, but methodologically it is highly relevant.

They use seven satellites to solve the seven unknowns (3d position, 3d velocity and receiver lock drift).

They introduce **DDOP — Doppler Dilution of Precision**, which is very relevant because it is essentially an observability/geometry metric for Doppler positioning. 

#### Relevance to RODINN
The most useful parts for PhD are not the positioning results themselves, but the fact that it quantifies how Doppler estimation performance depends on: geometry, orbit accuracy, atmosphere, velocity accuracy, clock errors, initialization.

Error sensitivity is very relevant, can be useful for deciding what should eventually go into a realistic simulation. 
### In-text annotations



%% Import Date: 2026-09-16T11:14:53.822+01:00 %%
