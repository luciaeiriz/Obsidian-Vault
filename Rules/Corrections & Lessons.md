---
tags: [meta, RODINN]
---
# Corrections & Lessons

A running log of mistakes caught and corrected, so they don't repeat. Newest first.

Format per entry: date, what happened, what was wrong, the correction or the general lesson.

## Log

- **2026-09-08** — Reviewing the step5 arc-length sweep script before Lucia had run it herself, reran it myself and got a residual spike (0.073°, well above the 0.01° sensor floor) plus a position-error spike at the 90-minute row. Wrote this up as a second, distinct failure mode (a bad local minimum) and flagged it as needing a rerun. Lucia's actual run showed no such thing — 90 min converged cleanly, in line with the rest of the trend, residual at the noise floor like every other row. The spike was an artifact of running her script in a different environment (numpy/scipy version drift — the same risk already flagged in the step4 noise-sweep review), not a real feature of the experiment. Correction: when an interpretation is based on a rerun I did myself rather than Lucia's own output, say so plainly and hold the finding as provisional until her numbers confirm it — don't write up my own rerun's anomaly as a confirmed result about the experiment.
- **2026-09-07** — Asked to draft the "Hide the truth" lab book step, wrote a multi-paragraph explanation with physical intuition, derivations, and cross-references (knowledge-base style). Corrected: the lab book is a log of what Lucia is doing, not a place for me to re-teach the theory — entries there should be terse (a few sentences: what the step does, why), not essays. Save the longer explanatory register for chat or for the Knowledge folder, only when actually asked for it.
- **2026-09-03** — Asked to derive relative velocity between two satellites "starting simple," jumped straight to whether/how well it's recoverable from Doppler (an observability/estimation question) instead of first just deriving the relative velocity vector itself from the two orbits. Correction: when asked to derive a quantity, do that first as pure kinematics/dynamics before bringing in what a specific sensor could recover of it — those are separate questions, and the derivation should stand on its own before the estimation layer gets added on top.
