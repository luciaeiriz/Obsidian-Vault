---
Title: A Double-Difference Doppler Shift-Based Positioning Framework With Ephemeris Error Correction of LEO Satellites
Year: 2024
Authors: Md. Ali Hasan, M. Humayun Kabir, Md. Shafiqul Islam, Sangmin Han, Wonjae Shin
tags:
  - Doppler
  - Doppler_positioning
  - Ground_receiver
  - LOS_velocity
  - range_rate
  - WLS
  - methodology
  - background
  - LEO
---
Zotero PDF Link: [Full Text PDF](zotero://select/library/items/9S325GZ6)
Related: [[Doppler]]

### Persistent Notes

The paper uses **Doppler shifts from LEO satellites to estimate the position and velocity of a moving user terminal on Earth**. The setup is therefore **satellite → ground receiver**, rather than **satellite → satellite relative orbit determination**. Their main contribution is a double-difference Doppler method called **3DPose**, designed to reduce clock-synchronisation and satellite-ephemeris errors.

The part that is relevant is their Doppler measurement model. They explicitly state that Doppler depends on the **relative velocity projected onto the line of sight**, and convert the measured Doppler shift into pseudorange rate/range rate.

More importantly, they then write the range-rate measurement as essentially

$$\dot{\rho} = (\mathbf v_{\rm sat}-\mathbf v_{\rm UT}) \cdot \frac{\mathbf x_{\rm sat}-\mathbf x_{\rm UT}} {\|\mathbf x_{\rm sat}-\mathbf x_{\rm UT}\|} +\text{errors}.$$

**This equation is extremely relevant.** It's the mathematical version of: Doppler doesn't directly measure position, but the measurement depends on position through the LOS unit vector.

They then linearise this nonlinear measurement equation around an initial estimate and solve for corrections to the **unknown position and velocity**:

$$\Delta\mathbf x_{pv} = [\Delta\mathbf x_{\rm UT},\Delta\mathbf v_{\rm UT}],$$

using least squares/weighted least squares. The iterative WLS procedure repeatedly updates the estimated position and velocity until the correction becomes sufficiently small.

Important sections: Section II (System Model) and the beginning of Section III

#### Relation to RODINN

It **does not do relative satellite-to-satellite OD**. Their unknown object is a moving terrestrial user terminal; the LEO satellite positions and velocities are supplied from TLE/SGP4 estimates. In fact, inaccurate knowledge of those satellite states is one of the problems the paper is trying to correct.

It also does **not use a PINN**. Their estimator is an iterative LS/WLS method based on linearising the Doppler measurement model.

### In-text annotations



%% Import Date: 2026-09-03T12:55:59.734+01:00 %%
