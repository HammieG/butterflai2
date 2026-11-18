# Week 6 validation and provenance

The main artifact is now the full T4 GPU run, downloaded from the saved Drive notebook and validated. It has 81 code cells and 14 figures; execution reached the final cell without error outputs. Drive's export omitted numeric Jupyter execution counters, so those remain unset rather than reconstructed. Successful cell metadata, dependent results, visible completion and preserved outputs document execution. Two markdown cells were appended after execution: full-run review and corrected student reflections. Colab's per-cell user name and account identifier were removed from metadata before publication.

## Inputs and authorship

The notebook is based on the official Week 6 template. The student supplied the four numbered predictions in chat before this implementation was executed. Assistant examples informed those predictions; the numerical guesses were suggested by the assistant and adopted by the student. With permission, spelling and the descriptions of close pairs and self-inclusion were corrected. Code implementation and computational interpretation were assisted by Codex.

## Independent numerical checks

Passed checks on notebook schema and every code cell's Python syntax; direct evaluation of history kernels; exclusion of self and simultaneous events under strict history; the equatorial half-mass boundary; analytic history integrals versus adaptive integration; coefficient transforms and inactive-channel zeros; invalid count matching; forward/backward pair-count equality; and simulator stability rejection.

Forty zero-history simulations of a constant base with an expected count of 20.4 had mean count 20.725, within the prespecified four-standard-error tolerance. Event times were strictly increasing and latitudes stayed in [0, 60] degrees.

## Simulation approximation

The sequential simulator linearly interpolates the base intensity between the frozen grid's time slices. This makes the maximum endpoint marginal rate a valid bound for each time interval. Latitude sampling uses an inverse CDF on the latitude grid. All previous parents are retained; there is no finite-history cutoff. The likelihood uses the supplied base functions and analytic history compensator, not this simulation approximation. Generation diagnostics must therefore be interpreted with the stated discretization.

## Feedback carried forward

The official Classical_contributions notebook credits HammieG's amplitude-dependent timing idea, identifies a missing parameter in an earlier two-sided-shape fit, explains the positive-delay sign restriction, and emphasizes recording the student's own predictions before scoring. The Week 6 template carries the corrected signed-shift champion. Its parameter declaration is 10 shared parameters; reduced-profile fitted counts must be assessed against that profile's actual training-wing count, rather than the full-profile count of 29.

No issues were found in the fork or mentioning HammieG in the official repository on the current check. Discord was not checked.

## Scope

The full executed artifact has 102 original-plus-prediction cells; the final review and student reflections bring the submission to 104 cells. All code cells pass Python AST parsing and the notebook passes nbformat schema validation. Numerical and scientific figures are inspected for the paired scoreboard and held-out generation. Published content is checked against the local file using Git's blob hash after upload.

The supplied `Model.n_params` counts amplitudes using all `FIT_WINGS`: on taste this is 10 shared champion shape parameters, four amplitudes, and one global scale, totaling 15. Each held-out fold actually trains on three wings, so its fitted base has 14 parameters; the printed model-family count is one larger. Adding the history channels increases the printed count by the active channel count. This reporting convention is distinct from the earlier Week 4 missing-shape-parameter failure. The supplied fit explicitly updates and stores its training amplitudes.

Working files are in submissions/weeks/week_06. Instructor-provided files, earlier submissions, and the organization repository were not edited.
