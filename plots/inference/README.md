# Inference plots

Posteriors from the end-to-end *Euclid* DR1 3×2pt validation (cosmic shear,
galaxy–galaxy lensing and photometric galaxy clustering on a noiseless ΛCDM mock),
comparing the emulators against the reference Boltzmann solver inside `cloelike`.
The folder structure mirrors `emulators/`. All files are PDF.

## What each model has

For every model the emulator (CosmoPower-JAX) posterior is overlaid on the reference
Boltzmann run on the *same* mock, likelihood and priors. The reference is **CAMB** for
every model except **1bDDM**, whose emulator is trained on CLASS, so **CLASS** (at the
"ACT" precision) is the fair reference.

| File stem | Plot |
|---|---|
| `<model>-marginals.pdf` | 1-D marginals, one panel per cosmological parameter (paper-figure style). Filled blue = emulator, orange = reference, dotted black = input fiducial. |
| `<model>-corner.pdf` | Cosmology triangle. Emulator filled, reference unfilled; dashed black = fiducial. |
| `<model>-corner-full.pdf` | Full triangle of the **emulator** run with every sampled parameter (cosmology + intrinsic alignment, galaxy bias, multiplicative bias and redshift shifts), ~31–34 parameters. *Only for models with a full run.* |
| `<model>-corner-shift.pdf` | Cosmology parameters only, overlaying the cosmology-only run (filled) against the full run projected onto cosmology (green): the shift/broadening from opening up the nuisance parameters. *Only for models with a full run.* |

There is **no full-parameter CAMB run** (CAMB was run cosmology-only), so `-corner-full`
and `-corner-shift` use the emulator chains; the emulator↔CAMB comparison lives in
`-marginals` and `-corner`.

## Models

| Folder | Model | Reference | Full run? |
|---|---|---|---|
| `lcdm/hmcode/`           | `lcdm` — ΛCDM | CAMB | yes |
| `wcdm/hmcode/`           | `wcdm` — wCDM | CAMB | no |
| `w0wa/hmcode/`           | `w0wacdm` — w₀wₐCDM | CAMB | yes |
| `extended/curvature/`    | `lcdm-curvature` (ΛCDM + Ω_K), `w0wacdm-curvature` (w₀wₐCDM + Ω_K) | CAMB | yes |
| `extended/running/`      | `lcdm-running` (ΛCDM + α_s), `w0wacdm-running` (w₀wₐCDM + α_s) | CAMB | yes |
| `extended/1bddm/`        | `1bddm` — one-body decaying dark matter | CLASS | no |
| `extended/parametrised_mg/` | `mg-singlebin-bin0..4`, `mg-multibin` | — (corner only) | — |
| `extended/react/`        | `react-cosmo`, `react-extended` | — (ReACT is its own reference) | — |

**Parameterised MG** has no Boltzmann reference chain, so each is a single emulator
triangle over cosmology plus the per-bin μ, η (GR: μ = η = 1 marked). The
single-bin files free one redshift bin at a time; the multi-bin file frees all five.
The high-redshift bins are prior-dominated, as expected for a lensing-dominated 3×2pt
data vector.

**ReACT** (`react-cosmo`, `react-extended`) are the multi-model halo-model-reaction
posteriors from the paper: panel (a) the cosmological parameters, panel (b) the
model-specific parameters of f(R), nDGP, Dark Scattering and μ(k,z). The ReACT boost
emulators themselves are not distributed here (see
`../../emulators/extended/react/README.md`).

The `lcdm/halofit/`, `wcdm/halofit/` and `w0wa/halofit/` folders are intentionally
empty: the DR1 inference used the HMCode2020 emulators, so there are no Halofit chains.

Shifts between the emulator and reference posterior means stay below 0.1 σ for every
model; see the paper for the full comparison.
