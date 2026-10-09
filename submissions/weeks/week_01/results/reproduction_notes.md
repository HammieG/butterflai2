# ButterflAI 2.0 Tasks 1–9

Source commit: 0129aea104aec57f5534f9b8472db66f98e54bc7

Catalog: https://github.com/SwRI-IDEA-Lab/butterflai2/blob/0129aea104aec57f5534f9b8472db66f98e54bc7/data/composite_sunspot_groups_daily_measurements_10_23.csv

Task definitions: https://github.com/SwRI-IDEA-Lab/butterflai2/blob/0129aea104aec57f5534f9b8472db66f98e54bc7/weeks/week_01/01_counting_process.ipynb

Submitted notebook: ../01_counting_process.ipynb. Place it inside a clone of the source repository to rerun. Its standard setup cell loads the frozen legacy model. All 1,000 realizations per Poisson comparison were executed. The original source notebook used 20.

Seed: 42; EMD: 43; homogeneous Poisson: 44; 365-day null: 45; 91-day null: 46.

Tasks 1–2 use latitude at peak area, as specified in the legacy recap. Tasks 3–9 use each group’s first observation. Selection: cycle labels 12–23 and lifetime peak corrected area strictly greater than 30 MSH. Alignment is the supplied hemispheric reference epoch subtracted from decimal year, without time normalization.

Each Fano uses only complete windows, sample variance ddof=1, and number-of-window weighting across hemispheric cycles. Simulation ranges are pointwise Monte Carlo ranges conditional on the fitted rate envelope. The course’s 24 observed spans define the nulls. The homogeneous benchmark uses 24 units of the mean observed span and the pooled mean rate, exactly as specified in the notebook.

Checks: 22,122 unique selected IDs; 24 hemispheric cycles; 22,098 inter-arrival times; sorted event times; all selection predicates satisfied; optimized window counts match numpy.histogram on selected cycles and widths; F=1 lies within the constant-rate Monte Carlo ranges at all 17 widths. Notebook schema validated.

Limits: first observation can lag true emergence; daily tied timestamps prevent interpretation of sub-day gaps; exposure is assumed complete; model scores are descriptive Week 1 scores rather than held-out validation. The finite NLL omits 110 impossible events, and the full NLL is infinite. Task 2 EMD follows the course’s Gaussian sampling rule without applying the hard gate.
