# 🪐 Exoplanet Transit Depth Analysis

[![Python](https://shields.io)](https://python.org)
[![Lightkurve](https://shields.io)](https://lightkurve.org)
[![Matplotlib](https://shields.io)](https://matplotlib.org)

This repository contains a comparative analysis of exoplanetary transit depths using data from the Kepler Space Telescope. The study focuses on contrasting the photometric signatures of a gas giant (**Kepler-90h**) and a rocky planet (**Kepler-10b**).

---

## 🔬 Theoretical Background

### What is Transit Depth?
**Transit depth (\(\Delta F\) or \(\delta\))** refers to the relative drop in a host star's flux (brightness) when an exoplanet passes directly between the telescope and the stellar disk. 

Mathematically, assuming a uniform stellar disk and a circular planetary profile, the transit depth is directly proportional to the ratio of their cross-sectional areas:

\[\delta = \frac{\Delta F}{F} = \left(\frac{R_{pl}}{R_{\star}}\right)^2\]

Where:
*   \(\delta\) — Transit depth (fractional dimming of the star)
*   \(R_{pl}\) — Radius of the exoplanet
*   \(R_{\star}\) — Radius of the host star

---

## 📊 Target Comparison: Kepler-90h vs. Kepler-10b

| Parameter | Kepler-90h 🪐 | Kepler-10b 🌎 |
| :--- | :--- | :--- |
| **Type** | Gas Giant (Jupiter-analog) | Rocky Planet (Super-Earth) |
| **Radius (\(R_\oplus\))** | ~11.4 \(R_\oplus\) | ~1.4 \(R_\oplus\) |
| **Expected Signal** | Deep, sharp, and high amplitude | Shallow, low amplitude (hidden in noise) |
| **Transit Depth (\(\delta\))**| **Significant** (\(\sim 1.0\%\)) | **Microscopic** (\(\sim 0.02\%\)) |

---

## 💻 Data Processing & Visualization

The light curves were extracted, cleaned, and processed using `lightkurve` and visualized via `matplotlib`. 

### Slicing the Time Series
To observe the baseline stellar flux and isolate specific transit windows, the data was sliced using a precise time interval constraint:

```python
import matplotlib.pyplot as plt

# Slicing the light curve interval
plt.xlim(452, 457)  # Time interval in BKJD days
```

### Expected Photometric Profiles

1. **Stellar Baseline (No Transit):** High-frequency, low-amplitude chaotic oscillations representing instrumental white noise and stellar granulation (as shown in the repository screenshots).
2. **Transit Event (Gas Giant):** A sharp, deep, U-shaped or V-shaped dip that easily breaks through the photon noise floor.
3. **Transit Event (Rocky Planet):** A highly shallow, flat-bottomed dip that often requires phase-folding and binning to become statistically significant against the noise.

---

## 🎯 Key Findings & Conclusion

Based on the empirical light curve analysis, we conclude that:

> 💡 **Transit dips for gas giants are significantly deeper and sharper than those of rocky planets.** 

Because a gas giant's radius ($R_{pl}$) is roughly an order of magnitude larger than a rocky planet's, its cross-sectional area blocks vastly more starlight. This geometric reality results in distinct, high-amplitude geometric signatures, making gas giants significantly easier to detect via the transit method compared to small, rocky worlds.

---

