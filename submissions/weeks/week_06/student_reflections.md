# Student reflections after the CPU run

The student wrote these responses in chat after reviewing the assistant's draft and the CPU results. Spelling and punctuation were corrected. Two technical phrases were clarified: a small score gain does not *prove memory*, and the leakage came from a small *change to the history rule*, rather than a small model. These responses precede the full GPU results and should not be represented as reflections on that later run.

1. A small positive improvement doesn't prove memory, as it could come from normal variation in the fitting process. If it is below the uncertainty floor, I can't separate it from that variation.

2. Groups that are similar in latitude could have a shared underlying cause, or one could cause another.

3. I think that the cheating gain was the one that most surprised me. I had predicted 20 nats, but there was around 77.82 nats of apparent improvement, which showed how a small change to the history rule could have a big apparent improvement. My equal-pair-count prediction turned out to be correct, but the CPU results didn't support my predicted improvement.

## Tutor clarification

For response 2, missing longitude prevents us from checking whether the groups occupy the same compact solar region; latitude similarity alone cannot distinguish a shared cause from triggering. The student has identified the two possible explanations, but has not yet independently explained that missing-coordinate argument. Correlation alone does not establish that one event caused another.
