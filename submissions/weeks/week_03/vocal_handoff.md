# Week 3 tutor handoff

This handoff records the actual tutor discussion and my answers in this chat. It is a summary rather than a verbatim transcript.

## What I expected

I expected stronger cycles to have wider residual scatter around the belt centerline. I also thought the scatter might narrow as activity approached the equator. I separated residual spread from raw latitude spread: raw spread includes the latitude range traced by the moving wing, while residual spread is closer to the belt's width. A rise in residual spread with cycle strength would be more consistent with a physically broader emergence zone than a rise in raw spread alone.

For validation, I argued that leaving out an entire cycle while learning the shared drift shape only from the other cycles is a conditional shape test, even though the held-out cycle's own events estimate its time origin. I would not call that an operational forecast: estimating the origin from the complete held-out wing uses information that would not be available when forecasting its onset or timing.

Before Task 29, I ranked extending the time window as the largest score change, coarsening the quadrature grid as intermediate, and extending latitude to 90° as smallest. I expected the nearly empty time tail to dilute the per-year loss and the far-latitude Gaussian tail to add little mass. I thought a coarse mesh might miss intensity between nodes and make NLL look artificially lower.

## What the notebook showed

The fixed reference ruler is `s = [-6, 11]` years and `|latitude| = [0°, 60°]` on a `201 × 241` mesh. Task 29 kept the fitted predictions fixed and changed the scoring ruler:

- Reference mesh: `−14.9022` NLL per hemicycle-year.
- Latitude extended to 90°: `−7.9820`, a change of `+6.9202`.
- Time extended to +15 years: `−9.3787`, a change of `+5.5235`.
- Coarse `101 × 31` mesh: `−14.9378`, a change of `−0.0356`.

My ranking was wrong: the latitude extension moved the score most, then the time extension; coarsening barely moved it. The model's softplus emission has a nonzero floor even when the latent field is near zero, so the extra polar area and late years add predicted background intensity. Also, keeping node counts fixed while stretching either domain changes the grid spacing. The latitude and time rows therefore combine boundary changes with resolution changes; they do not isolate the tail effect by itself. The small coarse-grid shift is in the expected NLL direction, but its magnitude is much smaller than I expected.

Task 30 measured a positive association in the 18 development hemicycles: the log–log slope was `+0.390` for residual spread and `+0.340` for raw spread. This supports my expectation that residual scatter grows with activity, but it does not show that amplitude causes the width change. Event count is only a proxy for activity, and spread also depends on how it is defined and on the drifting centerline.

For Task 31, both flexible width rules improved the in-sample likelihood, but neither improved the held-out area-record score relative to constant width. The amplitude-dependent rule increased paired held-out NLL by `+0.509` on average (better on 4 of 18 hemicycles); the latitude-dependent rule increased it by `+0.918` (better on 0 of 18). The fold fits now start from fixed values rather than the all-development-data fit. My revised interpretation is: a residual-width signal exists, but these flexible rules may overfit or transfer poorly. Nine development cycles are too few to make a universal claim about the physical width law.

In Task 28, the area-record amplitude prediction had an average paired cost of `+1.879` NLL per hemicycle-year versus fitting amplitude from the held-out events, with cycle-level SE `0.292` across nine development cycles. This comparison holds the shared shape out by cycle, but each held-out hemicycle still supplies its own time shift. It tests conditional shape transfer, not future-cycle timing or onset prediction.

## Conclusions and limits to carry forward

- The latent belt is inferred from emergence events; the catalog does not directly measure the magnetic field.
- The softplus threshold leaves nonzero background emission below threshold, which matters for integrations over large empty regions.
- Keep the reference mesh and domain fixed for model comparisons. Quote the mesh, domain, and time window with any NLL score.
- Compare models on the same held-out hemicycles and show paired differences. Since north and south belong to the same cycle, cycle-level uncertainty is more appropriate than treating all 18 hemicycles as independent.
- Cycles 16, 20, and 22 remain untouched. The leave-one-cycle-out results in this notebook are from the nine development cycles, not a final evaluation on those reserved cycles.
- Do not describe these scores as forecasts of a cycle's onset, timing, or amplitude. The time origin is estimated retrospectively from events in the held-out wing.

For next week, carry forward the distinction between a held-out shape test and an operational forecast, the effect of the softplus background floor, the fixed reference mesh, and the need to judge width rules by paired held-out results rather than their in-sample fit.
