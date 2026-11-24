# Integrated Exoplanet Habitability Index (IHI) Model

Python model developed as part of my Master's Thesis (TFM) in Astrophysics. This project evaluates the habitability potential of exoplanets by combining **Galactic Habitability (H_g)** and **Stellar/Planetary Habitability (H_e)** into a single **Integrated Habitability Index (IHI)**.

## Scientific Overview

Traditional habitability metrics often focus exclusively on the circumstellar Habitable Zone (HZ). This script expands that approach by weighting both the local planetary environment and the broader galactic context:

1. **Galactic Habitability (H_g):**
   * **Stellar Metallicity ([Fe/H]):** Gaussian probability distribution centered at mu = 0.1 (sigma = 0.3) favoring terrestrial planet formation.
   * **Galactocentric Distance (R_gal):** Models survival probabilities against sterilizing astrophysical events, specifically Supernovae and Gamma-Ray Bursts (GRB).
   * **Stellar Separation (d_sep):** Evaluates dynamical stability and reduced close-encounter risks (B).

2. **Stellar & Planetary Habitability (H_e):**
   * **Circumstellar Habitable Zone:** Computes inner and outer HZ boundaries using the parametric formulation from **Kopparapu et al. (2013)** based on stellar luminosity (L_star) and effective temperature (T_eff).
   * **Relative HZ Position & Equilibrium Temperature (RHZ):** Evaluates orbital distance (d_p) relative to the HZ midpoint, weighted by a thermal factor (T_eq optimal range: 253 K - 303 K).
   * **Orbital & Environmental Stability:** Incorporates orbital eccentricity (O = 1 - e), atmospheric retention (A), and stellar activity/stability (E).

3. **Integrated Habitability Index (IHI):**
   * Weighted combination of both sub-indices (IHI = X_g H_g + X_e H_e, set to equal weighting X_g = X_e = 0.5 by default).

## Analyzed Sample

The script evaluates **Earth** as a baseline alongside **8 exoplanets** orbiting M and K dwarf stars:
* `Kepler-296 Af` & `Kepler-296 Ae`
* `TOI-1452 Ab`
* `K2-288 Bb`
* `GJ 667 Cc`
* `Kepler-1651 Ab`
* `Kepler-1649 Ab` & `Kepler-1649 Ac`

## Outputs

Running the script generates:
1. **Console Summary Table:** Full breakdown of input parameters, intermediate scores, and final H_g, H_e, and IHI values.
2. **Comparative Visualizations:**
   * A scatter plot comparing H_g vs. H_e color-coded by the Integrated Habitability Index (IHI).
   * A grouped bar chart breaking down the scores across all analyzed planets.

## Requirements & Usage

### Dependencies
* Python 3.8+
* `numpy`
* `matplotlib`
* `pandas`

### Running the Code
```bash
git clone https://github.com
cd TU_REPOSITORIO
pip install numpy matplotlib pandas
python habitability_model.py
```
