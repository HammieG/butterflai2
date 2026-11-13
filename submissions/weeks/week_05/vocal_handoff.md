# Week 5 handoff — neural fields

I prepared a submission copy of the official Week 5 notebook with Tasks 44–55 implemented. The notebook keeps the program’s fixed ruler (`s` from −6 to +11 years, `|latitude|` from 0° to 60°, and the 201 × 241 mesh), uses the same leave-one-cycle-out protocol, and restricts conditioning to each wing’s own area-record amplitude and hemisphere.

## Prediction record

These predictions were written after the initial Colab run, so they are recorded retrospectively rather than presented as pre-scoring predictions.

1. **In-sample score.** I predict the neural model will lower the training loss. I expect it to fit the observed wings better because it has more flexibility.
2. **Held-out score.** I predict the held-out score will improve only a little. The model may fit the training wings well but struggle with new wings.
3. **Best conditioning method.** I predict concatenation will perform best. It gives the network amplitude and hemisphere information in a simple way.
4. **Stopping on the scored wing.** I predict stopping on the scored wing will make the score look better. I expect this improvement to be optimistic because it uses information from the test wing.
5. **Where the models differ.** I predict the largest differences will appear during the early rising phase and near the low-latitude late phase. These are the parts where a flexible model can change the belt’s shape most.
6. **Timing shift.** I predict stronger wings will peak earlier after the 15-degree crossing. I think this will appear as a negative timing slope, although the clock may explain part of it.
7. **Meaning of the timing result.** If the network finds the same timing pattern without being given one, I would see that as evidence that the pattern is present in the data. If it does not find it, I would treat the pattern as uncertain rather than assume the model failed.
8. **Belt center at s = 0.** I predict the network’s center will be closer to 15° than the champion’s center near 13°. This would suggest the network is less affected by the champion’s fitted latitude parameter.
9. **Next experiment.** I would test the signed timing shift on more held-out cycles. I predict the negative slope will remain, but become smaller or more uncertain with stricter testing.

## Validation status

- Notebook JSON is valid.
- All code cells pass Python syntax parsing.
- The notebook was run in Google Colab on the CPU `taste` profile. All cells completed after the plotting and dtype fixes; Colab reported “All changes saved.”
- This is a provisional run on four north wings and two folds, not the full T4 profile. The FiLM variant was numerically unstable in this taste run, so its very large score should not be treated as a reliable scientific conclusion.

No instructor files or organization repositories were modified.
