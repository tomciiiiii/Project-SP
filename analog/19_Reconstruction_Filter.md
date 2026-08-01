# Reconstruction Filter

> Nature does not produce staircases.

---

## Signal Path

Input Interface

↓

Input Protection

↓

Gain Stage

↓

Anti-Alias Filter

↓

Sample and Hold

↓

ADC Introduction

↓

SAR ADC

↓

Quantization

↓

Dither

↓

Sampling Rate

↓

Clock

↓

Jitter

↓

Digital Audio Memory

↓

Sample Playback

↓

Pitch Shifting

↓

Interpolation

↓

Digital-to-Analog Converter (DAC)

↓

**▶ Reconstruction Filter ◀**

↓

Output Stage

---

# Purpose

The Digital-to-Analog Converter reconstructs analog voltage from digital samples. However, the DAC output is not yet a smooth analog waveform. Instead, it consists of discrete voltage steps. The purpose of the Reconstruction Filter is to smooth these steps and remove unwanted high-frequency components introduced by the sampling process. The result is a continuous analog waveform suitable for the output stage.

---

# Why Reconstruction is Necessary

The DAC converts each digital value into a voltage. Each voltage remains constant until the next sample arrives. Instead of a smooth waveform, the output becomes:

____
    |
    |____
         |
         |____

Although this accurately represents the stored samples, it does not yet resemble a natural analog signal.

---

# The Staircase Waveform

Digital samples are discrete. The DAC therefore produces discrete voltage levels. The waveform contains sudden transitions between adjacent samples. These rapid transitions introduce unwanted high-frequency energy.

---

# Imaging

Unlike aliasing, which appears during sampling, playback introduces image frequencies. These images are mathematical copies of the reconstructed spectrum centred around multiples of the sampling frequency. Although not part of the original audio, they naturally appear whenever discrete samples are converted back into analog voltage. The reconstruction filter removes these unwanted images.

---

# Low-Pass Filtering

The reconstruction filter is almost always a low-pass filter.

Its objectives are:

- Preserve the audible signal
- Remove DAC images
- Smooth voltage transitions
- Produce a continuous waveform

The cutoff frequency depends on the system sampling rate.

---

# Relationship with Sampling Rate

Higher sampling rates move image frequencies further away from the audible band. This allows gentler reconstruction filters. Lower sampling rates require steeper filtering. This is one reason why vintage samplers often required carefully designed analog output filters.

---

# Reconstruction is Not Guessing

Interpolation estimates missing digital values before the DAC. Reconstruction filtering performs a different task. It operates entirely in the analog domain. Its purpose is not to create new samples, but to remove unwanted high-frequency components created by discrete playback.

---

# Anti-Alias vs Reconstruction Filter

Although both are low-pass filters, their purposes are fundamentally different.

Anti-Alias Filter

↓

Before the ADC

↓

Prevents aliasing during recording.

Reconstruction Filter

↓

After the DAC

↓

Removes imaging during playback.

Together they form the analog boundaries of the complete digital signal chain.

---

# Filter Characteristics

Several filter characteristics may be used.

Examples include:

- Butterworth
- Bessel
- Chebyshev
- Active Low-Pass Filters

Each offers different compromises between:

- Frequency response
- Phase response
- Transient behaviour
- Complexity

---

# Vintage Samplers

The analog output filter contributed significantly to the overall sound of many classic samplers. Component tolerances, operational amplifiers, filter topology and cutoff frequency all influenced the final analogue output. Project SP studies these effects as part of the complete playback chain.

---

# Engineering Questions

Several important questions remain.

- Which filter topology best matches the original SP-1200?
- Which cutoff frequency should be selected?
- How should phase response be considered?
- Should component tolerances be modelled?
- Which op-amp should drive the filter?

These questions will guide future hardware implementation.

---

# Future Validation

Project SP will investigate:

- Frequency response
- Step response
- FFT measurements
- Oscilloscope analysis
- Listening tests
- Original SP-1200 comparison

---

# Project SP Design Decision

## Current Status

🟢 Analog Reconstruction Understood

## Current Concept

Project SP treats the reconstruction filter as the final stage responsible for restoring a natural analog waveform after digital playback. Rather than merely smoothing the DAC output, this filter represents the final analogue voice of the instrument.

## Design Rationale

The reconstruction filter completes the digital-to-analog conversion process by removing unwanted playback images while preserving the desired audio signal.

## Future Validation

Future work includes:

- Filter implementation
- Analog measurements
- Listening comparisons
- Vintage hardware analysis
- Final output verification