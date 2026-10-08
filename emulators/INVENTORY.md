# Emulator inventory

Auto-generated from the `.npz` files (keys `parameters`, `n_modes`, `modes`) by `extra/make_inventory.py`. One row per file. 
Inputs are the dictionary keys expected by `CosmoPowerJAX.predict`; `k` ranges are as stored in `modes` (Mpc⁻¹ for all families except the parameterised-MG boosts, which are in h/Mpc). 
Total: 197 files.
P(k) emulators return P in Mpc³ when loaded with `probe="custom_log"`; scalar emulators (σ8, fσ8, DDM growth and global) are loaded with `probe="custom"`; the DDM distances file stores log10 values and is loaded with `probe="custom_log"` (returns H in Mpc⁻¹, D_A and D_L in Mpc).

## `emulators/lcdm/hmcode/` — ΛCDM — HMCode2020

20 files. k in Mpc⁻¹.

| File | Inputs | Output | n_out | k_min | k_max |
|---|---|---|---|---|---|
| `lcdm-1mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-1mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-1mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-1mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-1mass-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `lcdm-2degen-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-2degen-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-2degen-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-2degen-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-2degen-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `lcdm-3degen-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-3degen-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-3degen-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-3degen-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-3degen-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `lcdm-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-linear.npz` | ombh2, omch2, H0, ns, lnAs, z | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `lcdm-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |

## `emulators/lcdm/halofit/` — ΛCDM — Halofit

20 files. k in Mpc⁻¹.

| File | Inputs | Output | n_out | k_min | k_max |
|---|---|---|---|---|---|
| `halofit-lcdm-0mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-0mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-0mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z | σ8(z), fσ8(z) | 2 | – | – |
| `halofit-lcdm-0mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, z | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-0mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-1mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-1mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-1mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | σ8(z), fσ8(z) | 2 | – | – |
| `halofit-lcdm-1mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-1mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-2mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-2mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-2mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | σ8(z), fσ8(z) | 2 | – | – |
| `halofit-lcdm-2mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-2mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-3mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-3mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-3mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | σ8(z), fσ8(z) | 2 | – | – |
| `halofit-lcdm-3mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-lcdm-3mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, mnu | P_nl(k,z) | 520 | 1e-05 | 49.2 |

## `emulators/wcdm/hmcode/` — wCDM — HMCode2020

20 files. k in Mpc⁻¹.

| File | Inputs | Output | n_out | k_min | k_max |
|---|---|---|---|---|---|
| `wcdm-1mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-1mass-cb-nolinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-1mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-1mass-nolinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-1mass-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `wcdm-2degen-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-2degen-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-2degen-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-2degen-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-2degen-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `wcdm-3degen-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-3degen-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-3degen-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-3degen-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-3degen-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `wcdm-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `wcdm-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w, z, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |

## `emulators/wcdm/halofit/` — wCDM — Halofit

20 files. k in Mpc⁻¹.

| File | Inputs | Output | n_out | k_min | k_max |
|---|---|---|---|---|---|
| `halofit-wcdm-0mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-0mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-0mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w, z | σ8(z), fσ8(z) | 2 | – | – |
| `halofit-wcdm-0mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-0mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-1mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-1mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-1mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | σ8(z), fσ8(z) | 2 | – | – |
| `halofit-wcdm-1mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-1mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-2mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-2mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-2mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | σ8(z), fσ8(z) | 2 | – | – |
| `halofit-wcdm-2mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-2mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-3mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-3mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-3mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | σ8(z), fσ8(z) | 2 | – | – |
| `halofit-wcdm-3mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-wcdm-3mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w, z, mnu | P_nl(k,z) | 520 | 1e-05 | 49.2 |

## `emulators/w0wa/hmcode/` — w0waCDM — HMCode2020

20 files. k in Mpc⁻¹.

| File | Inputs | Output | n_out | k_min | k_max |
|---|---|---|---|---|---|
| `w0wa-1mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-1mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-1mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-1mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-1mass-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `w0wa-2degen-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-2degen-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-2degen-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-2degen-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-2degen-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `w0wa-3degen-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-3degen-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-3degen-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-3degen-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-3degen-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `w0wa-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `w0wa-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |

## `emulators/w0wa/halofit/` — w0waCDM — Halofit

20 files. k in Mpc⁻¹.

| File | Inputs | Output | n_out | k_min | k_max |
|---|---|---|---|---|---|
| `halofit-w0wa-0mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-0mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-0mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z | σ8(z), fσ8(z) | 2 | – | – |
| `halofit-w0wa-0mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-0mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-1mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-1mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-1mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | σ8(z), fσ8(z) | 2 | – | – |
| `halofit-w0wa-1mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-1mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-2mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-2mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-2mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | σ8(z), fσ8(z) | 2 | – | – |
| `halofit-w0wa-2mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-2mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-3mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-3mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-3mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | σ8(z), fσ8(z) | 2 | – | – |
| `halofit-w0wa-3mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `halofit-w0wa-3mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, w0, wa, z, mnu | P_nl(k,z) | 520 | 1e-05 | 49.2 |

## `emulators/extended/curvature/` — Curvature Ωk (ΛCDM and w0waCDM) — HMCode2020

30 files. k in Mpc⁻¹.

| File | Inputs | Output | n_out | k_min | k_max |
|---|---|---|---|---|---|
| `curvature-lcdm-0mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk | P_cb,lin(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-lcdm-0mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, logT_AGN | P_cb,nl(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-lcdm-0mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `curvature-lcdm-0mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk | P_lin(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-lcdm-0mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, logT_AGN | P_nl(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-lcdm-1mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, mnu | P_cb,lin(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-lcdm-1mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, mnu, logT_AGN | P_cb,nl(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-lcdm-1mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `curvature-lcdm-1mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, mnu | P_lin(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-lcdm-1mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, mnu, logT_AGN | P_nl(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-lcdm-3degen-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, mnu | P_cb,lin(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-lcdm-3degen-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, mnu, logT_AGN | P_cb,nl(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-lcdm-3degen-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `curvature-lcdm-3degen-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, mnu | P_lin(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-lcdm-3degen-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, mnu, logT_AGN | P_nl(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-w0wa-0mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa | P_cb,lin(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-w0wa-0mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa, logT_AGN | P_cb,nl(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-w0wa-0mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `curvature-w0wa-0mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa | P_lin(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-w0wa-0mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa, logT_AGN | P_nl(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-w0wa-1mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa, mnu | P_cb,lin(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-w0wa-1mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa, mnu, logT_AGN | P_cb,nl(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-w0wa-1mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `curvature-w0wa-1mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa, mnu | P_lin(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-w0wa-1mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa, mnu, logT_AGN | P_nl(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-w0wa-3degen-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa, mnu | P_cb,lin(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-w0wa-3degen-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa, mnu, logT_AGN | P_cb,nl(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-w0wa-3degen-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `curvature-w0wa-3degen-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa, mnu | P_lin(k,z) | 471 | 0.000531 | 49.2 |
| `curvature-w0wa-3degen-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, omk, w0, wa, mnu, logT_AGN | P_nl(k,z) | 471 | 0.000531 | 49.2 |

## `emulators/extended/running/` — Running spectral index αs (ΛCDM and w0waCDM) — HMCode2020

30 files. k in Mpc⁻¹.

| File | Inputs | Output | n_out | k_min | k_max |
|---|---|---|---|---|---|
| `nrun-lcdm-0mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-lcdm-0mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-lcdm-0mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `nrun-lcdm-0mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-lcdm-0mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-lcdm-1mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-lcdm-1mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, mnu, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-lcdm-1mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `nrun-lcdm-1mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-lcdm-1mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, mnu, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-lcdm-3degen-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-lcdm-3degen-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, mnu, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-lcdm-3degen-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `nrun-lcdm-3degen-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-lcdm-3degen-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, mnu, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-w0wa-0mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-w0wa-0mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-w0wa-0mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `nrun-w0wa-0mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-w0wa-0mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-w0wa-1mass-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-w0wa-1mass-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa, mnu, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-w0wa-1mass-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `nrun-w0wa-1mass-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-w0wa-1mass-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa, mnu, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-w0wa-3degen-cb-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa, mnu | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-w0wa-3degen-cb-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa, mnu, logT_AGN | P_cb,nl(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-w0wa-3degen-combined-s8-fs8.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa, mnu, logT_AGN | σ8(z), fσ8(z) | 2 | – | – |
| `nrun-w0wa-3degen-linear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa, mnu | P_lin(k,z) | 520 | 1e-05 | 49.2 |
| `nrun-w0wa-3degen-nonlinear.npz` | ombh2, omch2, H0, ns, lnAs, z, alpha_s, w0, wa, mnu, logT_AGN | P_nl(k,z) | 520 | 1e-05 | 49.2 |

## `emulators/extended/1bddm/` — One-body decaying dark matter, free neutrino mass sum `m_ncdm` — CLASS

5 files. k in Mpc⁻¹.

| File | Inputs | Output | n_out | k_min | k_max |
|---|---|---|---|---|---|
| `ddm-1body-neutrino-cb-linear.npz` | omega_b, omega_cdm_tot, h, n_s, ln10^{10}A_s, z, f_dcdm, Gamma_times_f, m_ncdm | P_cb,lin(k,z) | 520 | 1e-05 | 49.2 |
| `ddm-1body-neutrino-distances.npz` | omega_b, omega_cdm_tot, h, n_s, ln10^{10}A_s, z, f_dcdm, Gamma_times_f, m_ncdm | H(z) [Mpc⁻¹], D_A(z), D_L(z) [Mpc] (log10 stored → `custom_log`) | 3 | – | – |
| `ddm-1body-neutrino-global.npz` | omega_b, omega_cdm_tot, h, n_s, ln10^{10}A_s, f_dcdm, Gamma_times_f, m_ncdm | σ8, Ω_m, r_drag | 3 | – | – |
| `ddm-1body-neutrino-growth.npz` | omega_b, omega_cdm_tot, h, n_s, ln10^{10}A_s, z, f_dcdm, Gamma_times_f, m_ncdm | σ8(z), fσ8(z) | 2 | – | – |
| `ddm-1body-neutrino-linear.npz` | omega_b, omega_cdm_tot, h, n_s, ln10^{10}A_s, z, f_dcdm, Gamma_times_f, m_ncdm | P_lin(k,z) | 520 | 1e-05 | 49.2 |

## `emulators/extended/parametrised_mg/` — Parameterised modified gravity μ(z), η(z) — CLASS linear / COLA nonlinear boosts (grids in h/Mpc)

12 files. k in h/Mpc.

| File | Inputs | Output | n_out | k_min | k_max |
|---|---|---|---|---|---|
| `mg-boost-linear-bin0.npz` | Omega_m, Omega_b, h, ns, lnAs, mu, eta, z | linear boost B_lin(k,z) = P_MG/P_ΛCDM | 800 | 0.0001 | 10 |
| `mg-boost-linear-bin1.npz` | Omega_m, Omega_b, h, ns, lnAs, mu, eta, z | linear boost B_lin(k,z) = P_MG/P_ΛCDM | 800 | 0.0001 | 10 |
| `mg-boost-linear-bin2.npz` | Omega_m, Omega_b, h, ns, lnAs, mu, eta, z | linear boost B_lin(k,z) = P_MG/P_ΛCDM | 800 | 0.0001 | 10 |
| `mg-boost-linear-bin3.npz` | Omega_m, Omega_b, h, ns, lnAs, mu, eta, z | linear boost B_lin(k,z) = P_MG/P_ΛCDM | 800 | 0.0001 | 10 |
| `mg-boost-linear-bin4.npz` | Omega_m, Omega_b, h, ns, lnAs, mu, eta, z | linear boost B_lin(k,z) = P_MG/P_ΛCDM | 800 | 0.0001 | 10 |
| `mg-boost-linear-multibin.npz` | Omega_m, Omega_b, h, ns, lnAs, mu1, mu2, mu3, mu4, mu5, eta1, eta2, eta3, eta4, eta5, z | linear boost B_lin(k,z) = P_MG/P_ΛCDM | 512 | 0.0001 | 10 |
| `mg-boost-nonlinear-bin0.npz` | Omega_m, Omega_b, h, ns, lnAs, mu, z | nonlinear boost B_nl(k,z) = P_MG/P_ΛCDM | 1024 | 0.0157 | 12.6 |
| `mg-boost-nonlinear-bin1.npz` | Omega_m, Omega_b, h, ns, lnAs, mu, z | nonlinear boost B_nl(k,z) = P_MG/P_ΛCDM | 1024 | 0.0157 | 12.6 |
| `mg-boost-nonlinear-bin2.npz` | Omega_m, Omega_b, h, ns, lnAs, mu, z | nonlinear boost B_nl(k,z) = P_MG/P_ΛCDM | 1024 | 0.0157 | 12.6 |
| `mg-boost-nonlinear-bin3.npz` | Omega_m, Omega_b, h, ns, lnAs, mu, z | nonlinear boost B_nl(k,z) = P_MG/P_ΛCDM | 1024 | 0.0157 | 12.6 |
| `mg-boost-nonlinear-bin4.npz` | Omega_m, Omega_b, h, ns, lnAs, mu, z | nonlinear boost B_nl(k,z) = P_MG/P_ΛCDM | 1024 | 0.0157 | 12.6 |
| `mg-boost-nonlinear-multibin.npz` | Omega_m, Omega_b, h, ns, lnAs, mu1, mu2, mu3, mu4, mu5, z | nonlinear boost B_nl(k,z) = P_MG/P_ΛCDM | 1024 | 0.0157 | 12.6 |

