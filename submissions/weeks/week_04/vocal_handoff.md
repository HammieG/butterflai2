HANDOFF
turns: 2
learns by: example-in-context
domain: point processes | level: 1 | milestone: none | anchor: marginal intensity
marginal intensity | claim: no | prior: none | end: unused | "no quote"
other deployed: amplitude-dependent onset delay
other open: none
domain: statistical inference | level: 1 | milestone: none | anchor: ablation
ablation | claim: no | prior: none | end: unused | "no quote"
leaderboard | claim: no | prior: none | end: unused | "no quote"
generalization | claim: no | prior: none | end: unused | "no quote"
overfitting | claim: no | prior: none | end: unused | "no quote"
metric gaming | claim: no | prior: none | end: unused | "no quote"
model selection | claim: no | prior: none | end: unused | "no quote"
other deployed: none
other open: none
domain: solar cycle physics | level: 1 | milestone: none | anchor: hemispheric asymmetry
hemispheric asymmetry | claim: no | prior: none | end: unused | "no quote"
other deployed: none
other open: none

This is a concise snapshot of the Week 4 work chat, not a verbatim tutor-session transcript. The student proposed an amplitude-dependent onset delay. The notebook tests it as a nonnegative delay parameter, tau * log(1 + amplitude / 20,000), applied through a gate whose tau=0 value is pointwise identical to the baseline. The assistant supplied the working directional prior because the student did not state one: stronger cycles would be delayed, but the effect would be small after the standard t0 alignment.

The gate ablation was effectively tied with baseline and was reverted from the final model. The 13 one-knob variants were run. Width proportional to amplitude was selected: it improved held-out NLL by 0.6949 +/- 0.2874 nats per hemicycle-year against baseline, with a lower score on 15 of 18 hemicycles. The final report uses the fixed 201 x 241 mesh over |latitude|=[0,60] degrees and s=[-6,11] years; cycles 16, 20, and 22 remained withheld.

The Week 03 handoff had already measured a +1.879 nats/hemicycle-year gain from fitting held-out amplitude on that wing's own events. That was carried forward as the Week 04 prior for the largest protocol leak. Week 04 measured +0.2761 +/- 0.0845 for that leak, +0.0399 +/- 0.0464 for the all-data clock, and -5.0038 +/- 1.3691 for a held-out per-wing rise parameter. The last is a conditional bound and performed worse here.

The chosen model generated cycle 23 with a mean count error of 4.0%; its latitude centroid and spread were close to observed values. These are held-out shape-transfer results, not operational forecasts of cycle timing.

For next week, carry forward the fixed scoring ruler, the distinction between predictions and conditional bounds, and the fact that the amplitude-dependent onset delay was tried and tied. The transcript does not contain a student-authored explanation of the leaderboard or marginal intensity; those terms remain open.
