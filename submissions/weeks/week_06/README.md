# Week 6 — Does emergence have memory?

Submission copy for HammieG. Tasks 56–67 implement a strictly past history bank, analytic history integral, bounded offspring coefficients, fold-specific scoring and caches, direction-of-time diagnostics, sequential simulation, paired ablations, residual maps, and the deliberate self-inclusion leakage experiment.

The four student predictions are recorded in the notebook before execution, with assistant assistance explicitly described. The accompanying handoff distinguishes the student's predictions from computational interpretation prepared for review.

The main notebook now contains the full T4 GPU run: 18 development wings, held-out cycles 14, 19 and 21 (six scored wings), width 48, seed 42, and both neural arms. Validation cycle 13 selected 270 epochs for the no-history neural arm and 330 for the history arm. This is the course's full runtime profile, not a complete nine-fold study. Development conclusions remain provisional; cycles 16, 20, and 22 stay withheld. The earlier CPU run is retained in Git history.

The student's corrected CPU reflections are in `student_reflections.md` and the final notebook. Their timing and assistance are described explicitly; the full-run computational interpretation is assistant analysis for review.

See `validation_notes.md` for numerical checks, feedback, approximation details, and execution status. The observation window is s in [-6, 11] years, latitude in [0, 60] degrees, with the course's frozen 201 × 241 quadrature mesh. The history integral is analytic.
