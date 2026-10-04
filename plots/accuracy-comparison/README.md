# Accuracy-comparison plots

Reference-code accuracy and inference-cost figures from Appendix A of the paper. These are
*not* emulator-vs-reference residuals (those live in `../validation/`); they quantify how much
the reference Boltzmann codes themselves move when their internal accuracy settings are pushed,
and the cost of running inference with each.

| File | What it shows |
|---|---|
| `accuracy_comparison.pdf` | Relative change of the matter power spectrum P(k) when the Boltzmann-code accuracy is raised. Left: CAMB accuracy boost (2,2,2) and (3,3,3) vs the standard (1,1,1). Right: CLASS precision (high-acc `pk_ref` and "ACT") vs CLASS base. Shaded band = ±0.1 %; dotted line = the top of the emulator k-range. |
| `cmb_tt_accuracy_camb.pdf` | Relative change of the CMB TT spectrum C_ℓ^TT for the CAMB accuracy boosts (2,2,2)/(3,3,3) vs (1,1,1), split at ℓ = 4000. |
| `cmb_tt_accuracy_class.pdf` | Same for the CLASS precision settings (high-acc, "ACT") vs the CLASS default, split at ℓ = 4000. |
| `leonardo_inference.pdf` | Cosmological-parameter recovery vs Boltzmann-code accuracy: posteriors on the five ΛCDM parameters from a simulated *Euclid* DR1 3×2pt inference with the standard/medium/high CAMB settings and two CLASS configurations (all unfilled) plus the emulator (filled). Legend entries quote the sampling cost in CPU-h (cores × wall time) on the Leonardo DCGP cluster. |

Together these show that raising the Boltzmann-code accuracy moves P(k) and C_ℓ by well under the
emulator error, so the standard settings used for the training data are adequate, while the emulator
recovers the same cosmology at a ~10²–10³ lower cost.
