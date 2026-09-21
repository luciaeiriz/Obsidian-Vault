---
tags: [project-overview, RODINN]
---
# RODINN — Project Overview

> [!warning] Confidential — internal only
> This note is synthesized (not copied) from the ESA OSIP proposal document, which is marked "Internal Distribution Only" and copyright University of Strathclyde. Keep this note itself private — don't paste it externally, into a public repo, or into anything that leaves the vault, without checking with Prof Macdonald first.

## Research question

Can self-learning physics-informed neural networks (PINNs) be developed and deployed on small satellites to perform accurate, robust, and autonomous non-linear relative orbit determination (ROD), overcoming the limitations of conventional estimators and purely data-driven methods?

## The gap

Existing ROD approaches force a trade-off: EKF/UKF/IEKF-style filters are cheap but linearize around a reference trajectory, so they degrade under strongly nonlinear regimes (angles-only, range-only) and diverge without strong priors or frequent updates. Particle filters handle nonlinearity better but scale badly with state dimension. Batch least-squares/smoothing gives high accuracy but needs memory and long data arcs, ruling it out for real-time autonomy. On top of that, passive angles-only sensing has fundamental observability limits (e.g. RAAN stays unobservable under J2 alone), and on-board SWaP (size/weight/power) budgets rule out the more accurate but expensive methods. No existing approach embeds full nonlinear dynamics into a learning-based estimator to get accuracy, robustness, *and* on-board feasibility together — and PINNs haven't yet been applied to cooperative/relative OD specifically (only single-spacecraft OD so far).

## The approach — five objectives

1. **PINN ROD estimator** — design a PINN that embeds orbital dynamics + measurement physics directly into the learning process, aiming for something both physically consistent and cheap enough to run on-board.
2. **Accuracy under nonlinearity** — show the PINN approach handles strong nonlinearity and poor observability (passive, limited sensors) better than the accuracy/feasibility trade-off current methods are stuck with.
3. **Self-learning / on-orbit adaptation** — extend the estimator so it keeps adapting on-orbit to sensor drift and unmodelled perturbations, within physics constraints, reducing dependence on ground-based retraining.
4. **Pathway to spiking networks (Pi-SNNs)** — explore converting/co-designing the PINN as an event-driven Physics-Informed Spiking Neural Network, for low-power execution on FPGA/neuromorphic hardware — this is the second-lab (NSSP) contribution.
5. **Quantify feasibility for on-board deployment** — build a simulation environment, benchmark against classical baselines (EKF/UKF/particle/batch least-squares), and validate on Strathclyde's VESPRE testbed (a virtual constellation emulator, up to 1000 satellites at flight-representative compute).

## Programme structure (36 months)

- WP1 — Project management, reporting, dissemination (spans the whole project; explicitly includes AI-ethics and export-control checks)
- WP2 — Requirements, KPIs, verification & validation planning
- WP3 — High-fidelity ROD simulation environment + classical baseline estimators
- WP4 — PINN design & prototyping (Objectives 1–2)
- WP5 — Self-learning / on-orbit adaptation (Objective 3)
- WP6 — Pathway to Pi-SNNs / event-driven execution (Objective 4)

## Context

- **Sponsor:** ESA OSIP Open Discovery Ideas Channel — co-sponsored research (ESA + University of Strathclyde). The outline proposal already passed review and advanced to full-proposal stage.
- **Labs:** Applied Space Technology Laboratory (ApSTL) and the Neuromorphic Sensor Signal Processing Lab (NSSP), Centre for Signal & Image Processing, University of Strathclyde.
- **Supervision:** two supervisors, one per lab (astrodynamics/ROD side and neuromorphic/spiking side) — an ESA co-supervisor is also anticipated.
- **Testbed:** VESPRE — Strathclyde's virtual constellation emulation environment.
- **Possible ESA on-site stay** (~3 months) later in the project, subject to security checks and agreement with ESA.
- **Open science intent:** the proposal commits to releasing code/datasets/benchmarks openly "where permissible" via GitHub, Zenodo, arXiv, etc. — i.e. parts of this *are* meant to go public eventually, just not by default and not without review. This is why the RODINN GitHub repo defaults to private for now.

## Current reading focus

> Update this whenever the focus shifts — the triage process in the note-taking skill points here rather than hard-coding a topic.

As of September 2026: Doppler shift and how it can be used to determine the state of a satellite and its relative orbit (RO), read against the five objectives above. A paper counts as relevant if it either (a) uses Doppler measurements to estimate position/velocity/relative state of a satellite or receiver (Objectives 1–2), (b) says something about accuracy, observability, or nonlinearity in that estimation (Objective 2), (c) touches on-orbit adaptation or on-board/low-power deployment of an estimator (Objectives 3–4), or (d) is a validation/benchmarking approach relevant to Objective 5. Papers that are purely about extracting the Doppler *measurement* from a raw communications signal (receiver/PHY-layer signal processing) are background only, not core reading, since RODINN takes Doppler as an already-available observation.

## Reading map

Fill in as papers are read — which objective(s) each paper actually informs, not just its topic.

- **Baselines (EKF/UKF/particle/batch least-squares) for OD:** —
- **Nonlinear / observability-focused OD:** —
- **Angles-only ROD:** —
- **Doppler-based OD/navigation:** [[Doppler characterization for LEO satellites]] (read, assessed) — closed-form ground-to-satellite Doppler curve fit, single link only. [[Carrier synchronization under Doppler shift of the nongeostationary satellite communication systems]] (read, assessed) — receiver/carrier-recovery design for LEO Doppler, not OD, but confirms Doppler and its drift rate are large for LEO links. [[Navigation using carrier Doppler shift from a LEO constellation TRANSIT on steroids]] (read, assessed) — full ground-receiver navigation state (position/velocity/clock) from simultaneous Doppler across 8+ LEO satellites, batch least-squares, GDOP analysis. Still ground-receiver, not inter-satellite, but the most complete Doppler-to-state estimation example so far. [[In-Orbit Space Situational Awareness Using Doppler Frequency Shift]] (read, assessed) — **the first paper found that's genuinely inter-satellite Doppler**: one satellite's beacon received by another, used to estimate relative orbit geometry and collision miss-distance via batch least-squares. Directly answers the Y1 week 1 open question that such work exists, though it's a two-parameter fit for one close-approach event, not a continuous learned relative-state estimator. [[A Double-Difference Doppler Shift-Based Positioning Framework With Ephemeris Error Correction of LEO Satellites]] (read, assessed) — ground receiver self-positioning from LEO signals of opportunity, using double-difference Doppler plus an explicit correction for satellite ephemeris (TLE/SGP4) error; not inter-satellite RO, but a good reference for differencing techniques and treating ephemeris error as a correctable term rather than ground truth. All five are background/vocabulary, not methods to build on directly, all classical (not learning-based) and none solve continuous relative OD, but Al-Hourani 2024 is still the closest prior-art match found and worth flagging to supervisors. (Vilar & Austin 1991, on-board oscillator correction hardware for highly elliptical orbits, was read and assessed as least relevant of this group, then removed from the vault by Lucia on that basis.)
- **Doppler shift measurement/estimation (receiver signal processing, not OD):** [[Doppler Shift Estimation for Satellite Communications using Linear Estimators]] and its extension [[An Algorithm for Harsh Doppler Shift Estimation for Satellite Communications]] (both read, assessed) — accurately extracting the Doppler value itself from a noisy pilot signal, reaching the Cramér-Rao bound; the second handles low sampling-rate receivers via model-based pre-compensation. [[An Efficient Blind Doppler Shift Estimation and Compensation Method for LEO Satellite Communications]] (read, assessed) — real-time, ephemeris-free Doppler tracking via a spectral estimator plus a two-state (value/rate) filter, FPGA-validated. [[Novel Algorithm for Tracking LEO Satellites Using Doppler Frequency Shift Technique]] (abstract only, no PDF in Zotero) — predicted-vs-measured Doppler used in a closed loop for ground-station antenna pointing. All four are background only under the current focus: useful vocabulary and measurement-noise context, but they measure Doppler rather than using it to estimate state, so none feed Objectives 1–5 directly.
- **PINNs in astrodynamics:** —
- **Spiking / neuromorphic / event-driven methods:** —

## Open questions log

- Can we calculate the Doppler shift of a satellite from the receiving satellite? (from Lab book, Y1 week 1) — partially answered: yes, see [[In-Orbit Space Situational Awareness Using Doppler Frequency Shift]] for a published inter-satellite Doppler example, though it's a classical batch fit for collision miss-distance, not a continuous relative-state estimator. Still open whether/how to extend this toward what RODINN needs.
