Sincronizar Obsidian
Picture for ApSTL
Proposal ESA?
understand the Doppler ambiguity


## order to follow

1. **Freeze current model as “Baseline Problem”.** Keep circular, same altitude, known A, two-body, continuous sampling, no noise. You now know the code works. Save this version and do not keep modifying it. Your first result is: _the true solution can be recovered, but the Doppler-only problem has other solutions too.
2. **Investigate the non-uniqueness next.** This is now the most important question. Before worrying about noise, J2J_2, eccentricity, etc., you need to understand why different B orbits can produce the same Doppler. Work out the reflection symmetry mathematically, run many initial guesses, and identify how many distinct solution families exist. This is an **observability/identifiability problem**, not an optimiser problem. Al-Hourani's simplified co-shell model already shows how strongly the Doppler profile is tied to relative inclination and phase, so it remains your main reference here.
3. **Then study initialisation.** Once you know what the valid solution branches look like, ask: _given an initial guess, which solution does the optimiser converge to?_ Use increasingly bad starting guesses, random/multistart guesses, and eventually physically motivated guesses. This should be its own experiment, because initialisation does not change the measurement physics. Psiaki explicitly tested convergence from large initial errors using nonlinear least squares, which makes that paper especially relevant at this stage. Shi et al. similarly found that Doppler positioning can fail when the initial position is too far from the truth, so initialization sensitivity is a legitimate research question rather than merely a coding detail.
4. **Then study the information content of the Doppler history.** Keep the model noise-free and vary only things that affect observability: observation arc, relative inclination, RAAN/phase geometry, and separation. This answers questions such as “How long do I need to observe?” and “Which geometries are weak or impossible?” Lin is useful here because they explicitly note that same-plane/similar relative motion can produce nearly zero useful Doppler and that geometry/visibility determines whether adequate observations are available. Turan should become one of your main references at this stage because its focus is much more explicitly on observability and inter-satellite tracking.
5. **Only after the ideal problem is understood, make the measurements imperfect.** Add Doppler noise first. Then change cadence. Then introduce gaps/LOS constraints. Then frequency/clock bias. Do one at a time. At this stage, you are asking about **robustness**, not basic identifiability.
6. **Then relax the orbital assumptions.** I would do this gradually:
    
    $[i,\Omega,u] \rightarrow [a,i,\Omega,u] \rightarrow [a,e,i,\Omega,\omega,\nu] \rightarrow [\mathbf r,\mathbf v].$
    
    First allow different altitudes, then eccentricity, then general six-degree-of-freedom states. Only after that add J2J_2, drag, model mismatch, etc. Al-Hourani explicitly notes that its circular Keplerian simplification is intended for short arcs and that more complete propagators are needed for higher-fidelity propagation.
    
7. **Then relax the “A is perfectly known” assumption.** Progress from known A → noisy A → prior covariance on A → joint A/B estimation. This is significantly harder, so there is no benefit in introducing it before you understand the single-unknown-orbit case.
8. **Only then move to the PINN.** By that point you will have a classical benchmark and, crucially, you will know _where the information is actually missing_. A PINN cannot remove a fundamental reflection ambiguity if the measurements themselves do not distinguish the two solutions. What it can potentially improve is robustness to noise, sparse data, initialization, model mismatch, etc.




Al-Hourani remains your reference for the simple two-satellite circular Doppler geometry. Lin becomes relevant when you study **relative geometry, visibility and filtering**; it uses dynamic OD with an EKF and explicitly discusses weak same-plane Doppler geometry. Psiaki and Shi become relevant when you study **nonlinear least squares, initialization and convergence**. Psiaki also goes much further into Doppler observability/GDOP. Turan becomes particularly important for **observability, inter-satellite range/range-rate and filter initialization**; it even discusses using an initial least-squares solution before a Kalman-type filter when initial states are poor.

I would make one small literature matrix in your notes with columns like **paper | measurement | number of satellites/links | estimated state | initialization | dynamics | observability study | noise/bias | estimator**. Then every time you reach one of the stages above, look horizontally across that table and ask, “Who has already studied this part?”





