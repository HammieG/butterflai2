# Week 6 — Does emergence have memory?

Submission copy for HammieG. Tasks 56–67 implement a strictly past history bank, analytic history integral, bounded offspring coefficients, fold-specific scoring and caches, direction-of-time diagnostics, sequential simulation, paired ablations, residual maps, and the deliberate self-inclusion leakage experiment.

The four student predictions are recorded in the notebook before execution, with assistant assistance explicitly described. The accompanying handoff distinguishes the student's predictions from computational interpretation prepared for review.

Execution uses the course's CPU `taste` profile: four northern wings (13N, 14N, 18N, 19N), two held-out fold cycles (18, 19), width 16, and both neural arms. All reported results on this profile are provisional. Cycles 16, 20, and 22 stay withheld.

See `validation_notes.md` for numerical checks, feedback, approximation details, and execution status. The observation window is s in [-6, 11] years, latitude in [0, 60] degrees, with the course's frozen 201 × 241 quadrature mesh. The history integral is analytic.
