---
layout: page
title: Gravitational Waves Project
---

# Gravitational Waves: Physics and Observation

Emil Ma, Mentor: Norm Prokup.

## What Are Gravitational Waves?

Gravitational waves (GWs) are ripples in spacetime produced by accelerating masses, analogous to how accelerating electric charges produce electromagnetic waves. They were first predicted by **Albert Einstein** in 1916 as part of General Relativity.
![Simulation of a Gravitational Wave](assets/images/ligo_interferometer.jpg)


### Historical Notes
- First indirect evidence: Hulse and Taylor binary pulsar (1974)
- First direct detection: **GW150914** by LIGO (2015). In the GW150914 event, two black holes with masses of approximately 36 and 29 solar masses spiraled toward each other and merged to form a single black hole of about 62 solar masses. The remaining mass, roughly 3 solar masses, was converted directly into energy and emitted as gravitational waves, according to Einstein’s relation for energy.  

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
**strain**: how much the detector’s arm lengths change due to a passing gravitational wave.

It is defined as the change in length of the arms, 
ΔL(t), divided by the original arm length, 
L.

For astrophysical sources, the measured strain is extremely small,
typically on the order of 10^-21.


# Project: Analyzing GW150914 Data

In the following sections, I analyze publicly available LIGO strain data
from the first detected gravitational-wave event, GW150914, and recreate
the key steps used to identify the signal from detector noise.

---

## 1. Raw Strain Time Series

This plot shows the LIGO strain h(t) over time in a 32-second window centered on the GW150914 event.

![Raw Strain](assets/plots/strain_time.png)  <!-- your saved figure -->

**Explanation:**  
- x-axis: time (s) around the merger  
- y-axis: strain (dimensionless)  

The strain measures how much the length of LIGO’s arms changes relative to their original length. In the raw data, the signal is buried in noise from the environment and the detector itself. Though there are several spikes, the gravitational wave cannot be clearly seen at this stage.

---

## 2. Amplitude Spectral Density (ASD)

The amplitude spectral density shows how much noise the detector has at each frequency.

![ASD Full Range](assets/plots/asd_full.png)  
![ASD Zoomed](assets/plots/asd_zoom.png)

**Explanation:**  

Different frequencies are affected by different noise sources. Low frequencies are dominated by seismic motion, while very high frequencies are limited by the laser light itself. LIGO is most sensitive between about 100 and 300 Hz, which is also where binary black hole mergers emit most strongly.

---

## 3. Whitening the Data

Whitening adjusts the data so that noise has roughly the same strength at all frequencies.

![Roughly Whitened](assets/plots/rough_white.png)  
![GWpy Whitened](assets/plots/GWpy_white.png)

**Explanation:**  

After whitening, the background noise looks more uniform, and short-lived signals stand out more clearly in time. The GWpy method produces a cleaner result than a simple manual approach.

---

## 4. Q-Transform

The Q-transform displays how the signal’s energy changes with both time and frequency.

![Q-Transform](assets/plots/qtransform.png)

**Explanation:**  
- x-axis: time (s)  
- y-axis: frequency (Hz)  
- Color: normalized energy  

A clear “chirp” pattern appears, where the frequency increases rapidly over time. This behavior is exactly what is expected when two massive objects spiral together and merge.

---

## 5. Bandpass Filtering

A bandpass filter keeps only a selected range of frequencies and removes the rest.

![Bandpass 32s Window](assets/plots/bandpass_32s.png)  
![Bandpass Zoom 0.3s](assets/plots/bandpass_zoom.png)

**Explanation:**  

By keeping frequencies between about 30 and 400 Hz, most of the noise is removed while the gravitational-wave signal remains. The zoomed-in plot clearly shows the short burst of the merger.

---

## 6. Analytic Model vs. Data

An analytic model predicts how the gravitational-wave frequency should change over time for a merging binary system.

![Analytic Model Frequency](assets/plots/simple_analytic_model.png)  
![Q-Transform Scatter Projection](assets/plots/qtransform_scatter.png)

**Explanation:**  

The model predicts an increasing frequency as the two black holes approach each other. This trend matches the frequency track extracted from the data using the Q-transform.

---

## 7. Fitting an Oscillation Function

We fit an analytic waveform directly to the processed strain data.

![Function Not Fitted](assets/plots/osc_not_fitted.png)  
![Function Fitted](assets/plots/osc_fitted.png)

**Explanation:**  

The fitted curve closely follows the oscillations and amplitude increase seen in the data near the merger. This indicates that the model captures the key features of the signal.

---

## 8. Conclusion

Starting from noisy interferometer data, this analysis reproduces the key steps used by LIGO to identify GW150914. Through filtering, time-frequency analysis, and modeling, a clear gravitational-wave signal from a binary black hole merger emerges.

Big thanks again to Norm for guiding through this independent study!

### Notes / References
- MITxT 8.S50.1xComputational Data Science in Physics I
- LIGO Open Science Center: [https://losc.ligo.org](https://losc.ligo.org)  
- Analytical approximation references: Blanchet et al., PRL 1995 [link](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.74.3515)

