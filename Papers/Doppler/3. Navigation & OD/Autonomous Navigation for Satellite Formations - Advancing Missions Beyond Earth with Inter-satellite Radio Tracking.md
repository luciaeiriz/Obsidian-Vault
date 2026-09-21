---
Title: "Autonomous Navigation for Satellite Formations: Advancing Missions Beyond Earth with Inter-satellite Radio Tracking"
Year: 2024
Authors: E. Turan
Tags:
  - Doppler
  - Relative_OD
  - SST
  - Inter_satellite
  - range_rate
  - Autonomous_navigation
  - Observability
  - EKF
---
Zotero PDF Link: [PDF](zotero://select/library/items/JSWU6VSH)
Related: [[Doppler]]

### Persistent Notes
**Very relevant**. It specifically talks about satellite-to-satellite tracking (SST) for autonomous OD. This thesis explicitly considers **range, range-rate/Doppler, and angle measurements** for estimating spacecraft states.

This thesis explicitly describes the crosslink navigation this way: : round-trip light time gives distance, while Doppler gives relative velocity; these measurements are then processed by navigation algorithms to determine relative or absolute spacecraft positions and velocities.

It does range rate only SST orbit determination and compares it against angle-only and range-only OD.

The thesis finds that **orbital dynamics and observation geometry are what make the state observable over time**. Differences in the spacecraft dynamics improve observability and reduce state-estimation uncertainty; inclination, orbital shape and orbital size can all matter.

So one Doppler measurement doesn't magically give you position. Instead:

$\Delta f(t) \rightarrow \dot{\rho}(t)$

combined with

$\text{dynamical model} + \text{many measurements over time}$

allows an estimator to constrain

$\mathbf x(t)= \begin{bmatrix} \mathbf r_1 & \mathbf v_1 & \mathbf r_2 & \mathbf v_2 \end{bmatrix}^{T}.$


#### Relevance to RODINN
It basically does everything I was looking at except PINNs. Turan explicitly says the SST-OD literature still has unresolved questions involving **measurement errors, observation geometry, which of range/range-rate/angle is best, network topology, tracking windows and onboard estimation filters** 

### In-text annotations

 <mark class="hltr-yellow">"Doppler tracking between satellites provides a pivotal means for determining the relative velocity between two spacecraft"</mark> [Page 52](zotero://open-pdf/library/items/JSWU6VSH?page=52&annotation=DNULQML7)


 <mark class="hltr-yellow">"The Doppler shifted received frequency, f_r is:"</mark> [Page 52](zotero://open-pdf/library/items/JSWU6VSH?page=52&annotation=WVDXIXWR)
$f_R = f_T(1 - \frac{\dot \rho}{c})$

 <mark class="hltr-yellow">"The instantaneous Doppler shift is then:"</mark> [Page 52](zotero://open-pdf/library/items/JSWU6VSH?page=52&annotation=RD4665TB)
$\Delta f = f_R -f_T = -f_T \frac{\dot \rho}{c}$

 <mark class="hltr-yellow">"In the two-way operation"</mark> [Page 52](zotero://open-pdf/library/items/JSWU6VSH?page=52&annotation=9WU7ZADX)
$\Delta f \approx -2f_T \frac{\dot \rho}{c}$


%% Import Date: 2026-09-15T15:09:29.627+01:00 %%
