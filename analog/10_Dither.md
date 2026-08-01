# Dither

> Sometimes adding a tiny amount of noise reveals more truth than perfect silence.

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

**▶ Dither ◀**

↓

Sampling Rate

↓

Clock

↓

Jitter

↓

Digital Processing

↓

Memory

↓

DAC

↓

Output Stage

---

# Purpose

Dither is the intentional addition of a very small amount of random noise before quantization.

Although this initially appears counterintuitive, dithering improves the statistical behaviour of quantization by preventing quantization error from becoming correlated with the input signal.

Instead of producing deterministic distortion, the remaining error behaves like random noise.

The result is often perceived as more natural, especially at very low signal levels.

---

# Why Dither Exists

Quantization always introduces error. Without dither, this error is directly related to the signal itself. Instead of sounding like random noise, quantization error may become audible as distortion.

Dither randomizes this process.

Rather than eliminating quantization error, it removes its predictability.

---

# The Fundamental Idea

Without Dither

Signal

↓

Quantization

↓

Signal-correlated Error

↓

Distortion

With Dither

Signal

↓

Small Random Noise

↓

Quantization

↓

Random Error

↓

Noise

The total error still exists.

Its character changes completely.

---

# Why Noise Can Improve Quality

This seems paradoxical. Adding noise would normally be expected to reduce quality. However, the human ear often finds low-level random noise less objectionable than deterministic distortion. Random noise masks itself. Distortion creates new harmonic components that did not previously exist.

Our hearing is generally much more sensitive to these artificial harmonics.

---

# Quantization Without Dither

Imagine a slowly changing signal. Every sample is rounded to the nearest digital level. Because the rounding always follows the same mathematical rule, the error repeats.

The repeating error becomes distortion.

---

# Quantization With Dither

Now imagine adding an extremely small random voltage before conversion. Sometimes the value rounds upward. Sometimes downward. Over many samples, the average value becomes much closer to the original analog signal. The distortion disappears. Only a very small amount of random noise remains.

---

# Probability Distribution

Not all dither is identical.

Different probability distributions produce different statistical behaviour.

Common examples include:

- Rectangular PDF
- Triangular PDF (TPDF)
- Gaussian PDF

Among these, TPDF dither is widely used because it completely removes first-order quantization distortion without introducing significant bias.

---

# Noise Floor

Dither slightly raises the overall noise floor. This increase is intentional. The additional noise is usually extremely small compared with the benefit of eliminating correlated distortion. The engineering challenge is therefore balancing:

- Increased noise

against

- Reduced distortion

---

# Dither and Human Hearing

The human auditory system is remarkably sensitive to low-level distortion. Small amounts of harmonic distortion often remain audible below the level where random noise becomes objectionable. For this reason, replacing distortion with noise can produce a more transparent listening experience.

---

# Dither is Not Error Correction

Dither does not increase ADC resolution. It does not create new information. It does not recover lost bits. Instead, it changes the statistical behaviour of quantization error. The information remains limited by converter resolution.

---

# Dither in Audio Production

Dither is commonly applied when reducing word length.

Examples include:

24-bit

↓

16-bit

Mastering engineers almost always apply dither before exporting lower-resolution audio.

Without dither, truncation introduces measurable distortion.

---

# Dither and Vintage Samplers

Many classic samplers operated without sophisticated dithering techniques.

Their characteristic sound often results from the interaction of:

- Limited resolution
- Quantization
- Analog circuitry
- Converter architecture
- Sampling rate

Project SP therefore investigates dither as an optional experimental feature rather than assuming it was always present in vintage hardware.

---

# Engineering Questions

Several important questions remain.

- Should Project SP reproduce the original behaviour exactly?
- Should optional dither be available?
- Which probability distribution should be used?
- Should dither be switchable?
- Should playback and recording use identical behaviour?

These questions will be investigated experimentally.

---

# Future Validation

Project SP will evaluate dither using:

- Listening tests
- FFT analysis
- Low-level sine wave measurements
- Noise spectrum measurements
- Comparison with undithered conversion
- Comparison with vintage sampler recordings

---

# Project SP Design Decision

## Current Status

🟢 Concept Understood

## Current Concept

Project SP treats dither as an engineering tool rather than a sound effect.

Its purpose is not to increase resolution, but to improve the perceptual behaviour of quantization.

## Design Rationale

Understanding dither is essential for understanding why modern digital audio frequently sounds cleaner than simple low-resolution conversion.

Project SP will investigate whether optional dither contributes positively to an SP-inspired workflow.

## Future Validation

Future work includes:

- Statistical analysis
- Listening comparisons
- FFT measurements
- Quantization error analysis
- Comparison with the original SP-1200 behaviour