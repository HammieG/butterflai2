# Week 6 handoff — memory in sunspot emergence

## Contribution and prediction provenance

The student discussed the four predictions with the assistant, then wrote and authorized the responses below before executing Week 6. Numerical guesses of 2 and 20 nats were first suggested by the assistant and adopted by the student. The assistant implemented the code and prepared the numerical checks. This file does not claim independent student implementation or mastery inferred from assistant-written analysis.

1. I think that the counts will be equal because a close pair stays the same distance apart when we reverse time. Counting pairs cannot tell us whether an event triggered another event.
2. My prediction is that history will tell the classical model a lot more information than the neural model, as the neural model can describe some patterns missed by the classical model.
3. My guess would be around 2 nats per hemicycle-year, although I am not really sure whether it will be detectable based on the seed-spread anchor provided in the notebook. The comparison will use the larger of the paired standard error and the supplied seed-spread anchor.
4. My guess would be 20 nats per hemicycle-year. Counting an event as its own history gives an artificial boost to its predicted rate without increasing the integrated cost, so I expect a larger apparent improvement.

## Tutor snapshot

HANDOFF

learns by: plain-language examples followed by an explanation in the student's own words

domain: point processes | level: not fully calibrated | milestone: not assessed | anchor: conditional intensity

- history: introduced; the student predicts that past events will add more information to the classical model.
- triggering kernel, self-exciting process, Hawkes process, Cox process, branching ratio: not independently deployed in the student's responses.
- time reversibility: concept explained through the student's unchanged-distance argument, but the term itself has not been independently deployed.
- conditional intensity: next learning target; distinguish a rate given a wing's own past from a rate depending only on latitude and time.

domain: statistical inference | level: not fully calibrated | milestone: not assessed | anchor: resolution floor

- nested model, degeneracy, data leakage: discussed through examples; no independent vocabulary assessment completed.
- The student explicitly distinguishes an uncertain numerical prediction from a detectable result in prediction 3.
- Next step: explain why a positive gain below the resolution floor is not a detection.

domain: solar cycle physics | level: not assessed | milestone: not assessed | anchor: active nest

- active nest and solar rotation period: require a future explanation in the student's own words.
- Longitude remains deferred; first observation may lag true emergence, and identical recorded timestamps limit short-timescale inference.

domain: machine learning | level: not fully calibrated | milestone: not assessed | anchor: feature engineering

- feature engineering: not independently deployed.
- The student expects a flexible neural base to absorb some structure missed by the classical base.

## Remaining student reflection

After reviewing the computed results, the student should explain which predictions held, what changed their reasoning, how timestamp ties affect the short channels, which missing measurement would most help, and what the evidence can actually support. Those responses have not been invented on the student's behalf.

## Executed results — assistant analysis for student review

Colab completed all 81 code cells without error outputs on the CPU taste profile: four northern wings, folds 18 and 19, seed 42, and 55 epochs for each neural arm chosen on validation cycle 13. Outputs and figures are preserved in the submitted notebook.

- Prediction 1 was confirmed: pair counts agreed exactly at all 60 cutoffs. This identity cannot establish or rule out triggering.
- Predictions 2 and 3 were not supported by this reduced run: the champion's history gain was 0.0002 ± 0.0001 nats per hemicycle-year, and the neural gain was 0.2877 ± 0.2015. Both fell below the supplied 1.0019 seed-spread anchor. Their raw order is not a detected difference.
- Prediction 4 had the right sign and mechanism but underestimated the magnitude: self-inclusion gained 77.8209 nats per hemicycle-year. The mean fitted scale 0.8246 did not approach the deliberately high leak cap of 50.
- The mean time-asymmetry statistic was −0.2963 against a memoryless-null mean −0.2776 and SD 0.7315, with neither real wing outside the two-SD band. The null calibration used 16 draws and the triggering calibration two simulated wings.
- The generated 18N history wing had 1,090 events versus 1,138 observed; its latitude centroid was 15.323° versus 15.182°, and median gap 1.849 versus 1.772 days. With fitted classical history coefficients nearly zero, this generation is close to the base model.

The conclusion is no detection of added history or a time arrow at this run's resolution, not proof that solar emergence has no memory. The supplied seed anchor is not a fresh taste-profile seed study. Missing longitude, first-observation timing lag, timestamp ties, and solar visibility remain interpretation limits. See the notebook's final execution-review cell for the complete discussion, including template count-label qualifications.
