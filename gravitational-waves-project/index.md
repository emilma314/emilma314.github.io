---
layout: page
title: Gravitational Waves Project
---

# Gravitational Waves: Physics and Observation

## What Are Gravitational Waves?

Gravitational waves (GWs) are ripples in spacetime produced by accelerating masses, analogous to how accelerating electric charges produce electromagnetic waves. They were first predicted by **Albert Einstein** in 1916 as part of General Relativity.
![Simulation of a Gravitational Wave](assets/images/ligo_interferometer.jpg)


### Historical Notes
- First indirect evidence: Hulse and Taylor binary pulsar (1974)
- First direct detection: **GW150914** by LIGO (2015). In the GW150914 event, two black holes with masses of approximately 36 and 29 solar masses spiraled toward each other and merged to form a single black hole of about 62 solar masses. The remaining mass, roughly 3 solar masses, was converted directly into energy and emitted as gravitational waves, according to Einstein’s relation $E=mc^2$. 

### How LIGO Detects Gravitational Waves

![Diagram of the LIGO interferometer](assets/images/ligo_interferometer.jpg)

The Laser Interferometer Gravitational-Wave Observatory (LIGO) detects
gravitational waves using a Michelson interferometer with two
perpendicular arms, each 4 km long.

A passing gravitational wave stretches spacetime in one direction while
compressing it in the perpendicular direction. As a result, the relative
lengths of LIGO’s two arms change by a tiny amount.

Laser light is split and sent down both arms, reflected by mirrors, and
recombined. When the arm lengths change, the returning light waves shift
out of phase, producing an interference pattern that is measured as
**strain**:

\(
h(t) = \frac{\Delta L(t)}{L}
\)

For astrophysical sources, the measured strain is extremely small,
typically on the order of \(10^{-21}\).


# Project: Analyzing GW150914 Data

In the following sections, I analyze publicly available LIGO strain data
from the first detected gravitational-wave event, GW150914, and recreate
the key steps used to identify the signal from detector noise.

---

## 1. Raw Strain Time Series

The raw strain shows the detector output over time. Noise dominates the signal, so preprocessing is necessary.

![Raw Strain](assets/plots/strain_time.png)  <!-- your saved figure -->

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

![Roughly Whitened](assets/plots/rough_white.png)  
![GWpy Whitened](assets/plots/GWpy_white.png)

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

![Analytic Model Frequency](assets/plots/simple_analytic_model.png)  
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

