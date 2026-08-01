# Interpolation

> Sometimes the most important sample is the one that never existed.

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

**▶ Interpolation ◀**

↓

DAC

↓

Reconstruction Filter

↓

Output Stage

---

# Purpose

Interpolation estimates values that do not physically exist in memory. When playback occurs at a speed other than the original recording rate, the playback pointer frequently lands between stored samples. Since no sample exists at these intermediate positions, the playback engine must estimate what the missing value should be. Interpolation performs this estimation.

---

# Why Interpolation Exists

Suppose memory contains:

Address

0 → 10

1 → 20

2 → 30

3 → 40

Normal playback reads:

0

↓

1

↓

2

↓

3

No problem. Every address contains a stored sample.

---

# Fractional Playback

Now playback speed changes.

The pointer becomes:

0.00

↓

1.50

↓

3.00

↓

4.50

Immediately a problem appears.

Memory contains:

0

1

2

3

...

There is no sample stored at:

1.50

There never was. The playback engine must invent one.

---

# The Fundamental Question

Interpolation asks: "If a sample existed here... what would it most likely be?"
Everything that follows is simply different ways of answering that question.

---

# Nearest Neighbour

The simplest method. Choose whichever stored sample is closest.

Example

Memory

10

20

30

40

Pointer

1.60

Nearest sample

2

Output

30

No calculations. Very fast. Very inaccurate. Produces noticeable stepping.

---

# Linear Interpolation

Instead of choosing one sample, linear interpolation draws a straight line between neighbouring samples.

Example

Sample A

20

Sample B

30

Pointer

Halfway

Estimated value

25

Formula

Output

=

A + t(B − A)

where

t

is the fractional distance.

Simple.
Fast.
Much smoother than nearest neighbour.

---

# Cubic Interpolation

Linear interpolation considers only two neighbouring samples. Cubic interpolation considers several surrounding samples. Instead of a straight line, it estimates a smooth curve.

Advantages:

- Smoother waveform
- Better high-frequency behaviour
- Reduced distortion

Requires more computation.

---

# Sinc Interpolation

Sinc interpolation is often regarded as the mathematical ideal. Rather than approximating locally, it reconstructs the waveform using many neighbouring samples.

Advantages:

- Extremely accurate
- Excellent frequency response
- Very low distortion

Disadvantages:

- Computationally expensive
- Large memory access
- High processing cost

Modern software often approximates sinc interpolation using finite impulse response filters.

---

# Visual Comparison

Stored Samples

•

•

•

•

Nearest

□

□

□

Linear

╱╲

Cubic

︵︶

Sinc

Almost identical to the original continuous waveform. Each method represents a different compromise between quality and computational complexity.

---

# Vintage Samplers

Many early samplers used extremely simple interpolation methods. Some used nearest neighbour. Some used linear interpolation. Others intentionally limited interpolation quality to reduce hardware complexity. These limitations became part of their characteristic sound.

Project SP studies these behaviours because vintage character often comes from engineering constraints rather than intentional coloration.

---

# Why Vintage Sounds Different

Modern software attempts to reconstruct the waveform as accurately as possible.
Classic samplers often prioritised:

- Simplicity
- Cost
- Memory
- Processing speed

As a result, small interpolation errors became part of the instrument's sonic identity.

---

# Engineering Trade-Off

Better interpolation means:

- Higher quality
- Smoother playback
- Lower distortion

But also:

- More calculations
- More memory access
- Higher CPU load
- Greater implementation complexity

Every playback engine balances these factors differently.

---

# Engineering Questions

Several important questions remain.

- Which interpolation method should Project SP use?
- Should vintage limitations be reproduced?
- Should interpolation be selectable?
- Should playback favour authenticity or transparency?
- Which method most closely resembles the original SP-1200?

These questions will guide future implementation.

---

# Future Validation

Project SP will investigate interpolation using:

- Listening tests
- Oscilloscope measurements
- FFT analysis
- Spectral comparison
- CPU benchmarking
- Original SP-1200 comparison

---

# Project SP Design Decision

## Current Status

🟢 Playback Reconstruction Understood

## Current Concept

Project SP recognises interpolation as the mathematical bridge between stored digital samples and continuous playback. Different interpolation methods produce measurably different sonic characteristics.

## Design Rationale

Interpolation is not merely a mathematical convenience. It directly influences playback quality, frequency response and perceived character. Understanding interpolation is essential before designing the Digital-to-Analog conversion stage.

## Future Validation

Future work includes:

- Multiple interpolation implementations
- Listening comparisons
- Vintage hardware analysis
- Measurement-based verification