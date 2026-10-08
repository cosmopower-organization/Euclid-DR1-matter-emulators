# Notebooks

Worked examples for the emulator suite. Notebooks `01` to `03` use the files directly and need only
`cosmopower-jax`, `numpy` and `matplotlib`; notebook `04` additionally needs `cloelib` and `camb`.
All of them are stored with their outputs, so they can be read without running anything.

| Notebook | Contents |
|---|---|
| [01_quickstart_standalone.ipynb](01_quickstart_standalone.ipynb) | What is in an emulator file and how to load it; linear and nonlinear $P(k,z)$; $P_{\rm mm}$ vs $P_{\rm cb}$; $\sigma_8(z)$, $f\sigma_8(z)$ and the growth factor; evaluating on your own $k$ grid; batch evaluation and timing; derivatives with JAX; checking the training box. |
| [02_model_families.ipynb](02_model_families.ipynb) | Neutrino variants; wCDM and w0waCDM; HMCode2020 vs Halofit and baryonic feedback; spatial curvature; running spectral index; a consistency check of all families at their common ΛCDM point. |
| [03_beyond_lcdm_ddm_and_mg.ipynb](03_beyond_lcdm_ddm_and_mg.ipynb) | One-body decaying dark matter (free neutrino mass sum): linear suppression, ΛCDM limit vs the CAMB suite, background and growth emulators, nonlinear reconstruction with the Hubert et al. boost. Parameterised gravity: single- and multi-bin boosts, the $z_{\rm top}$ rule, $h$/Mpc grids, applying a boost to a ΛCDM spectrum. |
| [04_cloelib_interface.ipynb](04_cloelib_interface.ipynb) | The same emulators through the `cloelib` `Perturbations` protocol: ΛCDM vs CAMB, $P_{\rm cb}$, nonlinear spectra with `log10TAGN`, dark energy, neutrino variants, growth quantities, timing against CAMB. |

## Running them

```bash
pip install cosmopower-jax matplotlib jupyterlab     # cosmopower-jax pulls in jax and numpy
cd notebooks
jupyter lab
```

The notebooks locate the emulators through the relative path `../emulators`, so start Jupyter from this folder
(or from the repository root; both are handled). The stored outputs were produced with `cosmopower-jax` 0.5.8
and `jax` 0.4.38 on a CPU; timings will differ on other machines.

Notebook `04` points `cloelib` at the files of this repository (first cell) instead of letting it download them
from GitHub, and translates the pre-release file names that `cloelib` may still request. It reflects the `cloelib`
API of October 2026 (ΛCDM, wCDM, w0waCDM with HMCode2020 and Halofit, curvature and running); decaying dark
matter and parameterised gravity are shown with the bare files in notebook `03`.
