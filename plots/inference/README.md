# Inference plots

Posteriors from the end-to-end *Euclid* DR1 3×2pt validation (cosmic shear,
galaxy–galaxy lensing and photometric galaxy clustering on a noiseless ΛCDM mock),
comparing the emulators against the reference Boltzmann solver inside `cloelike`.
All files are PDF.

## What each model has

For every model the emulator (CosmoPower-JAX) posterior is overlaid on the reference
Boltzmann run on the *same* mock, likelihood and priors. The reference is **CAMB** for
every model except **1bDDM**, whose emulator is trained on CLASS, so **CLASS** (at the
"ACT" precision) is the fair reference.

| File stem | Plot |
|---|---|
| `<model>-marginals.pdf` | 1-D marginals, one panel per cosmological parameter (paper-figure style). Filled blue = emulator, orange = reference, dotted black = input fiducial. |
| `<model>-corner.pdf` | Cosmology triangle. Emulator filled, reference unfilled; dashed black = fiducial. |
| `<model>-corner-full.pdf` | Full triangle of the **emulator** run with every sampled parameter (cosmology + intrinsic alignment, galaxy bias, multiplicative bias and redshift shifts), 31–33 parameters. |
| `<model>-corner-shift.pdf` | Cosmology parameters only, overlaying the cosmology-only run (filled) against the full run projected onto cosmology (red, dotted): the shift/broadening from opening up the nuisance parameters. |
| `w0wacdm-corner-full-camb-vs-emu.pdf` | The one full-parameter run that was repeated with CAMB: all 33 w₀wₐCDM parameters, emulator (filled) against CAMB (unfilled). |

Full-parameter runs exist for `lcdm`, `w0wacdm`, both curvature and both running models;
`wcdm` and `1bddm` have the cosmology-only `-marginals` and `-corner` plots. CAMB was run
cosmology-only everywhere except for the w₀wₐCDM full run above, so the other `-corner-full`
and `-corner-shift` plots show emulator chains and the emulator↔CAMB comparison lives in
`-marginals` and `-corner`.

## Models

| Folder | Model | Reference |
|---|---|---|
| `lcdm/hmcode/`           | `lcdm` — ΛCDM | CAMB |
| `wcdm/hmcode/`           | `wcdm` — wCDM | CAMB |
| `w0wa/hmcode/`           | `w0wacdm` — w₀wₐCDM | CAMB |
| `extended/curvature/`    | `lcdm-curvature` (ΛCDM + Ω_K), `w0wacdm-curvature` (w₀wₐCDM + Ω_K) | CAMB |
| `extended/running/`      | `lcdm-running` (ΛCDM + α_s), `w0wacdm-running` (w₀wₐCDM + α_s) | CAMB |
| `extended/1bddm/`        | `1bddm` — one-body decaying dark matter | CLASS |
| `extended/parametrised_mg/` | `mg-corner-mu-eta`, `mg-corner-sigma`, `mg-singlebin-bin{0..4}-corner`, `mg-multibin-corner` | — (emulator only) |
| `extended/react/`        | `react-cosmo`, `react-extended`, `react-{fr,ndgp,ds,mu}-corner` | — (ReACT is its own reference) |

**Parameterised MG** has no Boltzmann reference chain; these are the paper's
modified-gravity corners, overlaying the joint multi-bin posterior (orange) with the
five independent single-bin posteriors (blue) over cosmology and the per-bin
gravitational-slip parameters, GR (μ = η = Σ = 1) dashed. `mg-corner-mu-eta` shows the
per-bin μ_i, η_i; `mg-corner-sigma` the lensing combination Σ_i = μ_i(1 + η_i)/2. The
high-redshift bins are prior-dominated, as expected for a lensing-dominated 3×2pt data
vector. The remaining six files are the individual emulator triangles behind those
overlays: `mg-singlebin-bin{0..4}-corner` is the run with μ and η free in one redshift bin
(bin0 is the lowest, 0 ≤ z < 0.43) and GR elsewhere, over the five cosmological
parameters plus that bin's μ, η; `mg-multibin-corner` is the joint run with all ten
μ₁…μ₅, η₁…η₅ free. Dashed lines mark the fiducial (GR) values.

**ReACT** are the halo-model-reaction posteriors from the paper. `react-cosmo` and
`react-extended` are the two marginal panels — panel (a) the cosmological parameters,
panel (b) the model-specific parameters of f(R), nDGP, Dark Scattering and μ(k,z) —
and `react-{fr,ndgp,ds,mu}-corner` are the full triangle per model (cosmology plus that
model's extra parameters). The ReACT boost emulators themselves are not distributed
here (see `../../emulators/extended/react/README.md`).

Shifts between the emulator and reference posterior means stay below 0.1 σ for every
model; see the paper for the full comparison.
