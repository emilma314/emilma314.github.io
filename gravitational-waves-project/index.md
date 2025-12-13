---
layout: page
title: Gravitational Waves Project
---

# Gravitational Waves: Physics and Observation

## What Are Gravitational Waves?

Gravitational waves (GWs) are ripples in spacetime produced by accelerating masses, analogous to how accelerating electric charges produce electromagnetic waves. They were first predicted by **Albert Einstein** in 1916 as part of General Relativity.

### Historical Notes
- First indirect evidence: Hulse and Taylor binary pulsar (1974)
- First direct detection: **GW150914** by LIGO (2015)
- GW astronomy opens a new window to observe black hole and neutron star mergers.

### Illustrations
*(Insert relevant images here, e.g., spacetime ripple diagram, LIGO interferometer schematic)*

---

# Project: Analyzing GW150914 Data

In this project, we analyze LIGO’s H1 detector data for the GW150914 event. The goal is to visualize strain, characterize the signal, and compare with simple analytic models.

---

## 1. Raw Strain Time Series

The raw strain shows the detector output over time. Noise dominates the signal, so preprocessing is necessary.

![Raw Strain](assets/plots/raw_strain.png)  <!-- your saved figure -->

**Explanation:**  
- x-axis: time (s) around the merger  
- y-axis: strain (dimensionless)  
- Note the spike corresponding to the gravitational-wave event.

---

## 2. Amplitude Spectral Density (ASD)

ASD shows the frequency content of the strain data.

![ASD Full Range](assets/plots/asd_full.png)  
![ASD Zoomed](assets/plots/asd_zoom.png)

**Explanation:**  
- Frequencies <100 Hz dominated by seismic noise  
- LIGO is most sensitive ~100–300 Hz  
- Zoomed view highlights the GW signal’s frequency range.

---

## 3. Whitening the Data

Whitening removes frequency-dependent noise.

![Roughly Whitened](assets/plots/whitened_rough.png)  
![GWpy Whitened](assets/plots/whitened_gwpy.png)

**Explanation:**  
- Flattened spectrum makes the signal more visible  
- Facilitates further processing like bandpass filtering

---

## 4. Q-Transform

The Q-transform shows time-frequency energy of the signal.

![Q-Transform](assets/plots/qtransform.png)

**Explanation:**  
- x-axis: time (s)  
- y-axis: frequency (Hz)  
- Color: normalized energy  
- Shows the "chirp" pattern of increasing frequency as the binary merges

---

## 5. Bandpass Filtering

Bandpass isolates the frequency range of interest.

![Bandpass 32s Window](assets/plots/bandpass_32s.png)  
![Bandpass Zoom 0.3s](assets/plots/bandpass_zoom.png)

**Explanation:**  
- Filters out low-frequency seismic noise and high-frequency artifacts  
- Short-window zoom shows the GW spike clearly

---

## 6. Analytic Model vs. Data

We can approximate the GW frequency evolution with a simple model.

![Analytic Model Frequency](assets/plots/analytic_model.png)  
![Q-Transform Scatter Projection](assets/plots/qtransform_scatter.png)

**Explanation:**  
- Analytic model uses chirp mass and Newtonian/GR approximation  
- Scatter projection of Q-transform highlights observed signal vs model

---

## 7. Fitting an Oscillation Function

We fit a function to the whitened, bandpassed strain.

![Function Not Fitted](assets/plots/osc_not_fitted.png)  
![Function Fitted](assets/plots/osc_fitted.png)

**Explanation:**  
- Red line: best-fit analytic function  
- Matches the peak strain and frequency evolution of the event

---

### Notes / References

- LIGO Open Science Center: [https://losc.ligo.org](https://losc.ligo.org)  
- Analytical approximation references: Blanchet et al., PRL 1995 [link](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.74.3515)

