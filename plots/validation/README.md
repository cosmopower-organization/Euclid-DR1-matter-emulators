# Validation plots

Accuracy of every released emulator on its held-out test set, organised exactly
like `emulators/` (same folder, same file stem). For each emulator
`<name>.npz` you will find:

* `<name>.pdf` / `<name>.png` — the plot.
  * **P(k) and boost emulators**: relative difference |X_emu − X_ref| / X_ref in per
    cent as a function of k, shaded at the 68th, 95th and 99th percentile of the
    test set.
  * **Scalar emulators** (σ8/fσ8, DDM growth, distances and global quantities):
    bar chart of the 68 / 95 / 99 / 99.9 percentiles of the relative error per
    output quantity.
* `percentiles/<name>-percentiles.npz` — the numbers behind the plot:
  * `modes` — the k-grid (or output index for scalar emulators),
  * `percentiles` — array of shape (4, n_modes): rows are the 68, 95, 99 and 99.9
    percentiles of the relative error in per cent,
  * `n_test` — number of test samples used,
  * `names` — output names for scalar emulators (`None` for P(k) emulators),
  * `emulator`, `params_file`, `feats_file` — provenance strings (local paths of
    the machine the validation was run on; informational only).

Two summary tables aggregate everything:

* `summary-99percent-kbands.txt` — for the P(k) and boost emulators, the median of
  the 99th-percentile curve in three k bands (k < 0.01, 0.01 ≤ k < 1, 1 ≤ k ≤ 50
  Mpc⁻¹), plus the maxima of the 68 % and 99 % curves and the test-set size.
* `summary-scalar-emulators.txt` — for the scalar emulators, the 68 / 95 / 99 /
  99.9 percentiles per output.

Note that the paper's master table quotes a different statistic (median of the
95th-percentile curve in k < 0.1, 0.1–1 and ≥ 1 Mpc⁻¹).

## What is missing, and why

* `lcdm/hmcode`, `wcdm/hmcode`: no σ8/fσ8 plots except `wcdm-2mass-s8-fs8` — the
  test sets for those scalar emulators were not available when the validation
  was run. (`w0wa/hmcode` now has them, see below.)
* `w0wa/hmcode`: `w0wa-2mass-s8-fs8` has no plot. Its retraining on the extended
  box did not converge, so that emulator alone was left at its previous version,
  for which no test set was available. The other three σ8/fσ8 variants are new.
* `extended/react`: the halo-model-reaction emulators are not distributed here
  (see `emulators/extended/react/README.md`); their validation is in the
  respective MGemu papers.

## Extended-ranges revalidation

139 of the released emulators were retrained on the extended box (w0 up to +1,
ω_c up to 0.90) and revalidated; their plots, percentile files and summary rows
here are the new ones. This closed two of the gaps listed above: the 16 ΛCDM
Halofit P(k) emulators and 3 of the 4 `w0wa/hmcode` σ8/fσ8 emulators are
validated here for the first time.

The curves were computed by `Emulators/codes/plotting/testing-expanding-ranges.py`
and re-packed into this layout by `extra/validation-plots/refresh-validation-extended-ranges.py`;
`params_file` / `feats_file` in those percentile files name that script rather
than a test-set path. The error definition and the 68/95/99/99.9 levels are
unchanged, so these rows stay directly comparable with the ones that were not
recomputed.

Not retrained, and therefore unchanged here: `lcdm/hmcode`, `wcdm/hmcode`,
`extended/1bddm`, `extended/parametrised_mg`.
