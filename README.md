# Euclid DR1 matter power spectrum emulators

Neural-network emulators of the matter power spectrum for the *Euclid* Data Release 1
(DR1) analysis, released with

> Euclid Collaboration: I. Sladoljev et al., *Euclid DR1-KP-TH-1-4-B: Neural-Network
> Emulators of the Matter Power Spectrum Across Standard and Beyond-Standard
> Cosmologies*, in preparation (2026).

The suite covers ΛCDM, wCDM, w0waCDM, spatial curvature, a running spectral index,
one-body decaying dark matter and binned parameterised modified gravity, each with
several neutrino treatments. Depending on the model the emulators predict the linear
and nonlinear total-matter power spectra, the cold-dark-matter + baryon spectrum,
and the growth quantities σ8(z) and fσ8(z). All networks are
[CosmoPower-JAX](https://github.com/dpiras/cosmopower-jax) models: they are
pipeline-agnostic, differentiable, and evaluate in milliseconds. On 50 000 held-out
test samples they agree with the reference Boltzmann code at the sub-percent level
(95th percentile) over the *Euclid* k-range.

This repository contains the trained networks, their validation plots, the posteriors
of the end-to-end *Euclid* DR1 3×2pt validation, and the reference-code accuracy
comparisons of the paper.

---

## Contents

```
dr1-matter-emulators/
├── README.md
├── emulators/                      # trained networks (.npz)
│   ├── INVENTORY.md                # auto-generated table: every file, its inputs, outputs and k-grid
│   ├── lcdm/{hmcode,halofit}/      # ΛCDM
│   ├── wcdm/{hmcode,halofit}/      # wCDM
│   ├── w0wa/{hmcode,halofit}/      # w0waCDM (CPL)
│   └── extended/
│       ├── curvature/              # ΛCDM + Ωk and w0waCDM + Ωk
│       ├── running/                # ΛCDM + αs and w0waCDM + αs
│       ├── 1bddm/                  # one-body decaying dark matter
│       ├── parametrised_mg/        # binned μ(z), η(z) boosts (linear: CLASS, nonlinear: COLA)
│       └── react/                  # halo-model-reaction boosts: not in this repo, see its README
├── plots/
│   ├── validation/                 # held-out-test accuracy plots + percentile data
│   ├── accuracy-comparison/        # reference-code (CAMB/CLASS) accuracy + inference-cost figures (Appendix A)
│   └── inference/                  # Euclid DR1 3×2pt posteriors, one set per model, emulator vs CAMB/CLASS
└── notebooks/                      # usage examples
```

`hmcode/` and `halofit/` hold the same cosmological family with two different
nonlinear prescriptions (HMCode2020 with baryonic feedback, and the Takahashi
recalibration of Halofit). Every family folder in `plots/validation/` contains one
plot per emulator file with the same file stem.

---

## Quick start

```bash
pip install cosmopower-jax        # tested with cosmopower-jax 0.5.8
```

```python
import numpy as np
from cosmopower_jax.cosmopower_jax import CosmoPowerJAX

# P(k) emulators predict log10 P; probe="custom_log" makes predict() return P itself
emu = CosmoPowerJAX(probe="custom_log",
                    filepath="emulators/lcdm/hmcode/lcdm-1mass-nonlinear.npz",
                    verbose=False)
print(emu.parameters)   # ['ombh2', 'omch2', 'H0', 'ns', 'lnAs', 'z', 'mnu', 'logT_AGN']
k = np.array(emu.modes) # k-grid in Mpc^-1 (520 modes)

# one cosmology at three redshifts: every input is an array of the same length
n = 3
params = {
    "ombh2": np.full(n, 0.0224), "omch2": np.full(n, 0.120), "H0": np.full(n, 67.4),
    "ns": np.full(n, 0.965), "lnAs": np.full(n, 3.044), "mnu": np.full(n, 0.06),
    "logT_AGN": np.full(n, 7.8),
    "z": np.array([0.0, 0.5, 2.0]),
}
pk = np.atleast_2d(emu.predict(params))   # shape (3, 520), P_nl(k, z) in Mpc^3

# scalar emulators (σ8/fσ8, DDM growth/global) predict the values directly;
# the DDM distances file stores log10 values and is loaded with probe="custom_log" like P(k)
s8 = CosmoPowerJAX(probe="custom",
                   filepath="emulators/lcdm/halofit/halofit-lcdm-1mass-combined-s8-fs8.npz",
                   verbose=False)
params.pop("logT_AGN")                    # not an input of the Halofit-family files
sigma8, fsigma8 = np.atleast_2d(s8.predict(params)).T
```

Inputs are passed as a dictionary keyed by the names in `emu.parameters` (the order
does not matter); each value is a 1-D array, so a whole batch of cosmologies or
redshifts is evaluated in one call. Redshift is an ordinary input, not a fixed grid.
For a single sample `predict` returns a 1-D array, hence the `np.atleast_2d`.

**Inputs outside the training box are silently extrapolated.** CosmoPower-JAX raises
no error and returns no NaN. Keeping the parameters inside the ranges listed below
is the user's responsibility.

---

## The emulator suite

| Family | Folder | ν variants | Nonlinear prescription | Reference code | Products | Family-specific inputs |
|---|---|---|---|---|---|---|
| ΛCDM | `lcdm/hmcode` | 0mass, 1mass, 2degen, 3degen | HMCode2020 | CAMB | P_lin, P_nl, P_cb,lin, P_cb,nl, σ8/fσ8 | `mnu`, `logT_AGN` |
| ΛCDM | `lcdm/halofit` | 0mass, 1mass, 2mass, 3mass | Halofit (Takahashi) | CAMB | same | `mnu` |
| wCDM | `wcdm/hmcode` | 0mass, 1mass, 2degen, 3degen | HMCode2020 | CAMB | same | `w`, `mnu`, `logT_AGN` |
| wCDM | `wcdm/halofit` | 0mass, 1mass, 2mass, 3mass | Halofit (Takahashi) | CAMB | same | `w`, `mnu` |
| w0waCDM | `w0wa/hmcode` | 0mass, 1mass, 2degen, 3degen | HMCode2020 | CAMB | same | `w0`, `wa`, `mnu`, `logT_AGN` |
| w0waCDM | `w0wa/halofit` | 0mass, 1mass, 2mass, 3mass | Halofit (Takahashi) | CAMB | same | `w0`, `wa`, `mnu` |
| Curvature, ΛCDM and w0waCDM | `extended/curvature` | 0mass, 1mass, 3degen | HMCode2020 | CAMB | same | `omk` (+ `w0`, `wa`), `mnu`, `logT_AGN` |
| Running index, ΛCDM and w0waCDM | `extended/running` | 0mass, 1mass, 3degen | HMCode2020 | CAMB | same | `alpha_s` (+ `w0`, `wa`), `mnu`, `logT_AGN` |
| One-body decaying DM | `extended/1bddm` | 3 degenerate, Σmν = 0.06 eV fixed | none emulated; boost formula applied at run time | CLASS | P_lin, P_cb,lin, σ8/fσ8, H/D_A/D_L, σ8/Ω_m/r_drag | `f_dcdm`, `Gamma_times_f` |
| Parameterised MG, binned μ(z), η(z) | `extended/parametrised_mg` | fixed (not an input) | COLA boost | CLASS (linear), COLA (nonlinear) | linear and nonlinear boosts P_MG/P_ΛCDM | `mu`, `eta` or `mu1..5`, `eta1..5` |
| Halo-model reaction: f(R), nDGP, Dark Scattering, μ(k,z) | `extended/react` | — | R × HMCode2020 | ReACT | nonlinear boost | **not distributed here**, see [emulators/extended/react/README.md](emulators/extended/react/README.md) |

A per-file listing with the exact input names, output type and k-grid of every one
of the 197 files is in [emulators/INVENTORY.md](emulators/INVENTORY.md).

### Neutrino variants

Massive neutrinos are a variant axis applied across families. The tag in the file
name selects how N_eff = 3.044 is split between massless and massive species:

| Tag | Setup | `mnu` input |
|---|---|---|
| `0mass` (no tag at all in `*/hmcode/`, e.g. `lcdm-linear.npz`) | 3.044 massless, no massive species | no |
| `1mass` | 1 massive eigenstate carrying Σmν, 2.044 massless | yes |
| `2degen` / `2mass` | 2 degenerate massive eigenstates, 1.044 massless (not described in the paper) | yes |
| `3degen` / `3mass` | 3 degenerate massive eigenstates, 0.044 massless | yes |

`Nmass` in the Halofit files and `Ndegen` in the HMCode2020 files mean the same
thing. `mnu` is always the total mass sum Σmν in eV.

### Nonlinear prescriptions

* **HMCode2020** (`hmcode/`, `curvature/`, `running/`): augmented halo model with
  baryonic feedback. The AGN heating temperature `logT_AGN` = log10(T_AGN / K) is
  an ordinary input of the nonlinear emulators.
* **Halofit** (`halofit/`): Takahashi et al. (2012) recalibration, gravity only, no
  feedback parameter; massive neutrinos via the CAMB implementation with the
  Bird et al. (2012) corrections.
* **One-body DDM**: the nonlinear spectrum is not emulated. It is reconstructed at
  evaluation time as the ΛCDM nonlinear prediction (from the ΛCDM HMCode2020 or
  Halofit emulators) rescaled by the decay-induced boost of Hubert et al. (2021),
  built from the ratio of the 1bDDM and ΛCDM linear emulators. See Sect. "Fitting-formula
  boost for decaying dark matter" of the paper.
* **Parameterised MG**: linear boosts from a modified CLASS, nonlinear boosts
  measured from COLA simulations (512³ particles in a (512 h⁻¹ Mpc)³ box) that
  share initial conditions with a ΛCDM run. The boost multiplies a ΛCDM P(k)
  from the ΛCDM emulators.

---

## File naming

```
[halofit-][curvature-|nrun-]<family>-<ν tag>-<product>.npz
```

| Piece | Values |
|---|---|
| prescription prefix | `halofit-` for the Halofit files; no prefix means HMCode2020 |
| extension prefix | `curvature-` (Ωk), `nrun-` (αs) |
| family | `lcdm`, `wcdm`, `w0wa` |
| ν tag | `0mass`, `1mass`, `2degen`, `3degen`, `2mass`, `3mass`; omitted for massless in `*/hmcode/` |
| product | see below |

| Product suffix | Quantity | `probe` for loading | Extra input |
|---|---|---|---|
| `-linear` | P_lin(k, z), total matter | `custom_log` | — |
| `-nonlinear` | P_nl(k, z), total matter | `custom_log` | `logT_AGN` (HMCode2020 files only) |
| `-cb-linear` | P_cb,lin(k, z), CDM + baryons | `custom_log` | — |
| `-cb-nonlinear` | P_cb,nl(k, z) | `custom_log` | `logT_AGN` (HMCode2020 files only) |
| `-s8-fs8`, `-combined-s8-fs8` | [σ8(z), fσ8(z)] | `custom` | `logT_AGN` in the HMCode2020-family files (physically irrelevant for σ8; any in-range value works, `cloelib` passes 7.6) |

Special families:

| File | Quantity | `probe` |
|---|---|---|
| `ddm-1body-combined-linear`, `-cb-linear` | P_lin, P_cb,lin | `custom_log` |
| `ddm-1body-combined-growth` | [σ8(z), fσ8(z)] | `custom` |
| `ddm-1body-combined-distances` | [H(z) in Mpc⁻¹, D_A(z) in Mpc, D_L(z) in Mpc] — stored as log10, so load with `custom_log` | `custom_log` |
| `ddm-1body-combined-global` | [σ8(z=0), Ω_m, r_drag] — no `z` input | `custom` |
| `mg-boost-linear-bin0` … `bin4` | linear boost, μ and η modified in one redshift bin | `custom_log` |
| `mg-boost-linear-multibin` | linear boost, `mu1..mu5`, `eta1..eta5` all free | `custom_log` |
| `mg-boost-nonlinear-bin0` … `bin4` | nonlinear boost, μ only (η does not enter the nonlinear boost) | `custom_log` |
| `mg-boost-nonlinear-multibin` | nonlinear boost, `mu1..mu5` | `custom_log` |

The MG redshift bins are, in order of increasing redshift (`bin0` … `bin4` ↔ bins 1 … 5):
0 ≤ z < 0.43, 0.43 ≤ z < 0.91, 0.91 ≤ z < 1.47, 1.47 ≤ z < 2.15, 2.15 ≤ z < 3.0.

Two files keep a historical misspelling because `cloelib` requests them from
Zenodo by exactly these names: `wcdm/hmcode/wcdm-1mass-nolinear.npz` and
`wcdm/hmcode/wcdm-1mass-cb-nolinear.npz` (they are the nonlinear emulators).

---

## Inputs

Names as stored in the files (`emu.parameters`):

| Key | Meaning | Used by |
|---|---|---|
| `ombh2` | ω_b = Ω_b h² | all CAMB families |
| `omch2` | ω_c = Ω_c h² | all CAMB families |
| `H0` | H0 in km s⁻¹ Mpc⁻¹ | all CAMB families |
| `ns` | scalar spectral index | all CAMB families |
| `lnAs` | ln(10¹⁰ A_s), pivot 0.05 Mpc⁻¹ | all CAMB families |
| `z` | redshift | every emulator except `ddm-1body-combined-global` |
| `mnu` | Σmν in eV | massive-neutrino variants |
| `logT_AGN` | log10(T_AGN / K), HMCode2020 feedback | HMCode2020 nonlinear and σ8/fσ8 files |
| `w` | constant dark-energy equation of state | wCDM |
| `w0`, `wa` | CPL equation of state w(a) = w0 + wa (1 − a) | w0waCDM and its curvature / running extensions |
| `omk` | Ω_k | curvature |
| `alpha_s` | running dn_s / dln k | running |
| `omega_b`, `omega_cdm_tot`, `h`, `n_s`, `ln10^{10}A_s` | ω_b, **total** (stable + decaying) ω_cdm, h, n_s, ln(10¹⁰ A_s) | 1bDDM (CLASS) |
| `f_dcdm` | decaying fraction of the dark matter | 1bDDM |
| `Gamma_times_f` | Γ_dcdm · f_dcdm in Gyr⁻¹ | 1bDDM |
| `Omega_m`, `Omega_b`, `h`, `ns`, `lnAs` | Ω_m, Ω_b, h, n_s, ln(10¹⁰ A_s) | parameterised MG |
| `mu`, `eta` / `mu1..mu5`, `eta1..eta5` | modification of the Poisson equation and gravitational slip (GR: μ = η = 1) | parameterised MG |

### Training ranges

The CAMB families (ΛCDM, wCDM, w0waCDM, curvature, running) are trained on the
union of a *standard* set (≈ 100 000 near-ΛCDM samples) and an *extended* set
(≈ 250 000 samples), both Latin hypercubes; the emulators are valid over the
extended box:

| Parameter | Standard set | Extended set |
|---|---|---|
| ω_b | [0.015, 0.035] | [0.001, 0.100] |
| ω_c | [0.05, 0.20] | [0.05, 0.90] |
| H0 [km s⁻¹ Mpc⁻¹] | [60, 80] | [20, 100] |
| n_s | [0.90, 1.05] | [0.60, 1.30] |
| ln(10¹⁰ A_s) | [2.5, 3.5] | [1.61, 5.00] |
| log10 T_AGN | [7.8, 8.2] | [7.30, 8.50] |
| z | [0, 5] | [0, 5] |
| w (wCDM) | [−1.0, −0.5] | [−3.0, 0.0] |
| w0 (CPL) | [−1.0, −0.5] | [−3.0, −0.33] |
| wa (CPL) | [−0.5, 0.5] | [−3.0, 3.0] |
| Σmν [eV] | [0.0, 0.1] | [0.0, 1.0] |
| α_s | [−0.1, 0.1] | [−0.3, 0.3] |
| Ω_k | [−0.1, 0.1] | [−0.3, 0.3] |

One-body DDM (CLASS, z ∈ [0, 3]): f_dcdm ∈ [0, 1], Γ_dcdm f_dcdm ∈ [0, 0.0316] Gyr⁻¹
(the calibration domain of the Hubert et al. 2021 fitting formula); the cosmological
box follows Table 2 of that paper.

Parameterised MG (COLA boosts):

| Parameter | Single-bin | Multi-bin |
|---|---|---|
| Ω_m | [0.25, 0.35] | [0.25, 0.40] |
| Ω_b | [0.040, 0.055] | [0.040, 0.055] |
| h | [0.65, 0.73] | [0.65, 0.75] |
| n_s | [0.95, 1.00] | [0.80, 1.20] |
| ln(10¹⁰ A_s) | [2.996, 3.091] | [2.944, 3.219] |
| μ, η (per bin) | [0.9, 1.1] | [0.9, 1.1] |
| z | [0.01, 3] | [0, 3] |

The training-sample mean and standard deviation of every input are stored in each
file (`param_train_mean`, `param_train_std`).

---

## Outputs, units and grids

* k is in Mpc⁻¹ and P(k) in Mpc³ (CAMB `hubble_units=False`, `k_hunit=False`); no
  factors of h anywhere.
* The CAMB families share one grid of 520 k-modes from 1.0 × 10⁻⁵ to 49.2 Mpc⁻¹
  (log-spaced, denser at high k), stored in the `modes` key of each file. The
  curvature emulators use a reduced grid of 471 modes starting at 5.3 × 10⁻⁴ Mpc⁻¹,
  because non-zero curvature changes the lowest available k.
* 1bDDM: same 520-mode grid, z ∈ [0, 3].
* Parameterised MG boosts: single-bin linear 800 modes on [10⁻⁴, 10], multi-bin
  linear 512 modes on [10⁻⁴, 10], nonlinear 1024 modes on [0.016, 12.6]
  (the COLA measurement grid).
* Scalar emulators return the listed quantities in the order given above; the
  DDM distances are H(z) in Mpc⁻¹ and D_A(z), D_L(z) in Mpc (CLASS units).

### File format

Each `.npz` holds a single pickled dictionary (`np.load(f, allow_pickle=True)["arr_0"].item()`)
in the CosmoPower format: `weights_`, `biases_`, `alphas_`, `betas_` (network),
`param_train_mean`, `param_train_std`, `feature_train_mean`, `feature_train_std`
(normalisation), `parameters`, `n_parameters`, `modes`, `n_modes`, `n_hidden`,
`n_layers`, `architecture`. Every network is a dense MLP with four hidden layers of
512 neurons and the trainable CosmoPower activation.

---

## Validation

`plots/validation/` mirrors the emulator tree. For each emulator there is a PDF/PNG
of the relative error on the held-out test set and a `percentiles/*.npz` file with
the 68 / 95 / 99 / 99.9 percentile curves; two text tables summarise all families.
See [plots/validation/README.md](plots/validation/README.md) for the format and for
the few emulators without plots.

The paper validates every family against the code that generated its training data
(CAMB, CLASS, COLA, or ReACT + HMCode2020) and, as the decisive test, runs a full
cosmological inference on a simulated *Euclid* DR1 3×2pt data vector with the
emulators replacing CAMB/CLASS inside `cloelike`. Shifts in the marginalised
posterior means stay below 0.1 σ. Those posteriors are in
[plots/inference/](plots/inference/) (one set per model, emulator vs CAMB/CLASS), and
the reference-code accuracy and inference-cost figures of Appendix A are in
[plots/accuracy-comparison/](plots/accuracy-comparison/).

---

## Use in the Euclid likelihood

The emulators are exposed in `cloelib` through the `Perturbations` protocol
(`cloelib.cosmology.cosmopower_jax_cosmology`), which downloads the files by name
from the Zenodo record and returns P_mm(k, z), P_cb(k, z), σ8(z) and fσ8(z) to
`cloelike`. They can equally be plugged into any other framework that accepts an
external P(k, z) provider (CosmoSIS, CCL, …).

---


## Citation

If you use these emulators please cite the paper above together with
CosmoPower (Spurio Mancini et al. 2022) and CosmoPower-JAX (Piras & Spurio Mancini
2023).

Maintainer: Ivan Sladoljev.
