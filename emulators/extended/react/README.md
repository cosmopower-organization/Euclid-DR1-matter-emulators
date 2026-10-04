# Halo-model-reaction (ReACT) boost emulators

The halo-model-reaction emulators described in the paper (Hu–Sawicki f(R), nDGP,
Dark Scattering and the phenomenological scale-dependent μ(k, z) model) are **not
distributed in this repository**. They emulate only the nonlinear boost
`R(k,z) · P_pseudo / P_ΛCDM` on top of the ΛCDM baseline (HMCode2020) and are
released through the `MGemu` Python module of their respective calibration papers.

| Model | Extra parameters | Reference |
|---|---|---|
| Hu–Sawicki f(R) | log10\|f_R0\| | Euclid Collaboration (2025), *Euclid:2025yud* |
| nDGP | log10 Ω_rc | Euclid Collaboration (2023), *Euclid:2023rjj* |
| Dark Scattering | w0, wa, ξ | Tsedrik et al. (2025), *Tsedrik:2025jdv* |
| Screened μ(k, z) | w0, wa, μ0, c1, λ, q1, q2, q3 | introduced in the DR1 emulator paper |

Their redshift coverage is limited to z ≲ 2–2.5 and each model carries its own
cosmology box (Ω_m, Ω_b, H0, n_s, A_s); see the paper (Sect. "Halo model
reaction") and the references above.

This folder is kept so that the `plots/inference/extended/react/` results have a
matching entry in the emulator tree.
