---
Title: An Algorithm for Harsh Doppler Shift Estimation for Satellite Communications
Year: 2024
Authors: André B. De F. Diniz, Thomas Eriksson, Ulf Gustavsson
Tags:
  - Doppler
  - Doppler_estimation
  - LEO_to_ground
  - Orbital_determination
  - Signal_analysis
  - Doppler_ambiguity
  - LEO
---
Zotero PDF Link: [Full Text PDF](zotero://select/library/items/F63LYESQ)
Related: [[Doppler]]

### Persistent Notes
This paper is primarily about **accurately measuring/estimating the Doppler shift in a satellite communication signal**, rather than using that Doppler measurement to determine an orbit. The scenario is **LEO satellite → ground station**, motivated by communications and particularly low receiver sampling frequencies.

They construct a physical model that goes

$\text{orbital elements} \rightarrow \mathbf r_{\rm sat}(t),\mathbf v_{\rm sat}(t) \rightarrow v_r(t) \rightarrow f_D(t).$

They calculate the satellite position and velocity from its orbital elements, transform from ECI to ECEF, determine the line-of-sight direction, and then calculate
$$v_r=\mathbf v_{\rm sat}\cdot\hat{\mathbf r}$$followed by
$$\boxed{f_D = \frac{f_cv_r}{c}}$$
That part is useful because it's a concrete example of the relationship:

$\boxed{\text{relative orbital motion}\rightarrow\text{LOS velocity}\rightarrow\text{Doppler}}$

Their actual research contribution, however, is a signal-processing algorithm. They use model-based **pre-compensation** followed by estimation/refinement so that large Doppler shifts can still be accurately estimated when the receiver has a low sampling frequency.

#### Relation to RODINN
Attempts orbital parameter fitting only to improve Doppler estimation, does not mention relative satellite-to-satellite OD or PINNs.

It does focus on Doppler estimation, LOS velocity, orbital dynamics and observability / ambiguity. They say that they **are not concerned with estimating the satellite's position**; inaccurate orbital parameters are acceptable as long as they reproduce the correct Doppler curve.

Later they reiterate that the estimated orbital parameters may be different from the true parameters while still producing essentially the same Doppler history.

**That's very relevant to the question about whether Doppler contains enough information to recover position.** It demonstrates an ambiguity/observability issue: matching a Doppler curve does not necessarily uniquely determine the orbit.

### In-text annotations

 <mark class="hltr-yellow">"the Doppler shift for LEO satellites in circular orbits can be fully characterized by four orbital parameters, namely a, i, Ω and M0. Estimating them precisely in single input-single output systems, without any prior knowledge of the satellite position, may be a difficult task. The physical model is ambiguous in that different sets of orbital parameters can produce the same Doppler shifts for a given visibility window. We are not concerned with estimating the position of the satellite and, in this section, we take advantage of that to estimate the Doppler shifts even with incorrect estimates of the orbital parameters."</mark> [Page 708](zotero://open-pdf/library/items/F63LYESQ?page=708&annotation=QJFFHZMJ)




%% Import Date: 2026-09-15T14:58:13.768+01:00 %%
