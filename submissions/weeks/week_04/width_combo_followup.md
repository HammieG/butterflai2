# Week 4 follow-up: do the two belt-width effects combine?

## Question

The Week 4 notebook asks whether amplitude-dependent and latitude-dependent width effects add, or overlap. This follow-up compares the saved `width-combo` run with the saved baseline and the two single-effect ablations, using the same held-out area-record NLL and protocol fingerprint (`5e55384fbc54`).

## Results

Positive “gain” below means a lower (better) held-out NLL than the baseline.

| Width model | Mean held-out NLL (nats / hemicycle-year) | Mean gain vs baseline | SE of paired gain | Hemicycles improved |
|---|---:|---:|---:|---:|
| Baseline: constant width | −25.4451 | — | — | — |
| Amplitude-dependent | −26.1399 | +0.6949 | 0.2874 | 15 / 18 |
| Latitude-dependent | −25.5805 | +0.1355 | 0.0677 | 14 / 18 |
| Combined amplitude + latitude | −26.1004 | +0.6553 | 0.2905 | 13 / 18 |

The gain standard errors in the table use the nine development cycles as the independent units, averaging each cycle's north and south differences first. If the two effects added exactly, the combined gain would be about `0.6949 + 0.1355 = 0.8303` nats per hemicycle-year. The observed combined gain is `0.6553`, a descriptive shortfall of `0.1750` (SE `0.0672`, across those nine cycle means).

The direct paired comparison is also useful: relative to amplitude-only, the combined model's mean held-out NLL is `0.0396` nats per hemicycle-year worse (cycle-paired SE `0.0142`); the combined model has the lower NLL in 4 of 18 hemicycles and in 2 of 9 cycle-averaged comparisons. This is a development-fold comparison, not an independent final test, and the class leaderboard explicitly treats rankings selected on these nine cycles as provisional.

## Interpretation

On these nine development cycles, the combined width rule has a slightly worse mean held-out NLL than the amplitude-only rule (`0.0396` nats per hemicycle-year; paired SE `0.0142`). The latitude-width improvement is small by comparison, and adding that term to the amplitude rule does not produce the sum of the two separate gains. In the full-development fit, the combined model's latitude slope is slightly negative (`−0.0053`), while the latitude-only fit estimates a positive slope (`+0.1128`). This is consistent with the two terms partly describing the same variation in this model family, but it does not establish that the physical effects are identical. There are only nine development cycles, the variants are compared on the same folds used to choose among models, and the final class ranking remains provisional. Cycles 16, 20, and 22 remain sealed and were not used here.

## Provenance and reproducibility

This summary was computed from the saved JSON result caches created by the Week 4 notebook:

- `data/derived/scoreboard1/baseline.json`
- `data/derived/scoreboard1/width-amplitude.json`
- `data/derived/scoreboard1/width-latitude.json`
- `data/derived/scoreboard1/width-combo.json`

For each model, the mean held-out score is the mean of the 18 `nll/yr (area record)` rows. Paired gain is baseline NLL minus variant NLL, matched by hemicycle; means and standard errors average north and south within each of the nine development cycles before computing uncertainty. The direct combo-versus-amplitude difference uses the same cycle-paired calculation. The interaction diagnostic is computed cycle-wise as `gain(combo) − gain(amplitude) − gain(latitude)`. All four cache files carry the same frozen-protocol fingerprint, `5e55384fbc54`.

This is a supplemental analysis of saved notebook outputs. It does not alter the instructor notebook, the already-submitted report, or the tutor-session handoff; that handoff remains a record of what was discussed. The Week 4 notebook explicitly asks whether the width effects add or overlap and identifies `width=combo` as the comparison for answering it.

## Possible next experiment

For a later model comparison, keep amplitude-dependent width as the reference and test one latitude modulation that returns exactly to that reference when its coefficient is zero, for example `w = w_amp(A) * exp(gamma * h(|mu|))` with `h` centered and scaled in advance. Predeclare the regularization strength or choose it without using the final withheld cycles, then compare paired held-out likelihood and the existing diagnostics. That would test whether latitude adds predictive information after amplitude is represented; the present result alone does not justify changing the physical interpretation or the course model.
