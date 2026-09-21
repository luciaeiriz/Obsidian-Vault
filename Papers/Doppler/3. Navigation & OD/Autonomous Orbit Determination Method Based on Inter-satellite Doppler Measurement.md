---
Title: Autonomous Orbit Determination Method Based on Inter-satellite Doppler Measurement
Year: 2016
Authors: Kui Lin, Wende Huang, Zhuli Hu, Jianwei Yang, Fanghong Huang
Tags:
  - EKF
  - Doppler
  - Inter_satellite
  - range_rate
  - Autonomous_navigation
  - Observability
  - MEO
  - GEO
---
Zotero PDF Link: [PDF](zotero://select/library/items/P7Q44VPG)
Related: [[Doppler]]

### Persistent Notes
The authors explicitly ask whether **inter-satellite Doppler measurements can be used for autonomous orbit determination**. They simulate satellite-to-satellite Doppler observations and feed those measurements into an **Extended Kalman Filter (EKF)** to estimate an orbit

They begin from the fact that relative radial motion between transmitter and receiver produces a Doppler shift. For two satellites, they count Doppler cycles over an interval $\Delta T$, giving

$f_d=\frac{N}{\Delta T}.$

They then convert that frequency information into the **rate of change of inter-satellite distance**:

$v=\frac{\rho_2-\rho_1}{\Delta T}.$

Then §3.2 makes the measurement model explicit. The receiver obtains the range-change rate between the transmitting and receiving satellites from the Doppler count.

For equal nominal transmitter/receiver frequencies, they simplify this to

$V=-\frac{c}{f}\frac{N}{\Delta t}+e,$

where $e$ represents measurement error.

And crucially,

$\boxed{ V_k=\frac{\rho(X_k)-\rho(X_{k-1})}{\Delta t_k}+e_k }$

where $\rho(X)$ is the geometric distance between the two satellites.

That equation makes the connection extremely clear:

$\boxed{ \text{Doppler} \rightarrow \dot{\rho} \approx \frac{\rho_k-\rho_{k-1}}{\Delta t} }$

They actually estimate the orbit:
$\boxed{ X= \begin{bmatrix} x&y&z&\dot x&\dot y&\dot z \end{bmatrix}^{T} }$
so they're estimating **3D position and 3D velocity**, not merely radial velocity.

So Doppler is not independently giving the state vector. It is providing observations that constrain a dynamically propagated estimate.

One distinction:
This isn't quite the pure **two-satellite relative OD problem**.For their OD simulation, they select **six visible reference satellites** and establish observations between those known/reference satellites and the satellite whose orbit is being estimated.

They find that satellites whose relative positions remain approximately unchanged produce almost zero Doppler, making them unsuitable for this method. They therefore use satellites on different orbital tracks/layers, while also accounting for periods where Earth blocks the inter-satellite link.

They explicitly conclude that visibility constraints and careful selection of reference satellites are necessary to ensure sufficient observation data.

This reinforces what Turan (2024) was telling us: Doppler OD performance is strongly geometry-dependent.

It is not simply a question of how accurately you measure frequency.
### In-text annotations



%% Import Date: 2026-09-15T14:39:37.352+01:00 %%
