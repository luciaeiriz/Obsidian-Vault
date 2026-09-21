---
Title: Doppler Shift Estimation for Satellite Communications using Linear Estimators
Year: 2024
Authors: André B. De F. Diniz, Thomas Eriksson, Ulf Gustavsson
Tags:
  - Doppler_estimation
  - LEO
  - Linear_estimator
  - Pilot_signal
  - LOS_velocity
  - Frequency_estimation
  - CRLB
  - Communications
---
Zotero PDF Link: [Full Text PDF](zotero://select/library/items/R6TBX95H)
Related: [[Doppler]]

### Persistent Notes
Explains how Doppler is actually estimated from a radio signal, but not an OD paper. It is very focused on signal processing 

On page 2 they write the Doppler-shifted received signal as

$y[n] = e^{j\epsilon} e^{j\Omega_d(n-(L-1)/2)} x[n]+w[n],$

where $\Omega_d$ is the normalized Doppler shift, $\epsilon$ is an unknown phase offset, $x[n]$ is the known transmitted pilot signal and $w[n]$ is noise.

They then connect the actual Doppler frequency to satellite motion through

​$f_d = \frac{v f_c cos\alpha}{c}$

#### Relevance to RODINN
This paper shows one way that observation can actually be extracted from the raw received signal.
**page 2 / Section II is the useful part**
### In-text annotations



%% Import Date: 2026-09-03T12:55:59.711+01:00 %%
