---
Title: "Relative Orbit Determination for Unconnected Spacecraft Within a Constellation"
Year: 2021
Authors: Tong Qin, Dong Qiao, Malcolm Macdonald
Tags: []
---
Zotero PDF Link: [Full Text](zotero://select/library/items/D3EWD48K)
Related: [[Angle ROD]]

### Persistent Notes

> [!warning] Not actually angles-only
> This paper uses scalar inter-satellite range measurements ($\rho = |\vec r_B - T \vec r_A|$, a crosslink ranging observable), not bearing angles from a camera. Different sensor, different literature entirely — it cites Psiaki, Hill & Born, GPS crosslink autonomous navigation, none of which overlaps with the Woffinden–Geller lineage the other two papers filed under Angle ROD come from. Worth checking why it landed in this pile: could be intentional for the transferable idea below, or just a filing mismatch.

**What it does.** For a constellation where not every satellite pair has a direct range crosslink, it derives an indirect relative OD method using spherical trigonometry, so a spacecraft can get its relative orbit orientation with respect to a non-neighbor by chaining through one or more intermediate, directly-linked spacecraft. Validated on a 6-satellite ring with only nearest-neighbor links. One genuinely interesting side result: a coplanar pair of orbits, which is a special-case unobservable geometry for the direct range method, becomes observable again once routed through a third, non-coplanar intermediate spacecraft — chaining doesn't just extend reach, it can recover an outright unobservable geometry.

**RODINN relevance.** Tangential given the sensor mismatch, but the structural idea, routing through an intermediate link to recover something otherwise unobservable, is the same trick as the multi-observer fix in the angles-only literature, just applied to range instead of bearing. Possibly worth a footnote under Objective 2/3, not as angles-only evidence.

### In-text annotations



%% Import Date: 2026-09-03T15:02:16.483+01:00 %%
