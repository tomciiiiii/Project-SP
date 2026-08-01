# Quantization

> The analog world is continuous. The digital world is made of steps.

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

**▶ Quantization ◀**

↓

Dither

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

Quantization is the process of assigning a continuously varying analog voltage to one of a finite number of digital values.

Unlike the analog world, where infinitely many voltage levels exist, a digital system can only represent a limited number of discrete values.

Every sampled voltage must therefore be rounded to the nearest available digital level.

This unavoidable approximation is called quantization.

---

# Why Quantization Exists

An analog signal can theoretically assume an infinite number of voltage values.

For example:

1.000001 V

1.000002 V

1.000003 V

...

A digital converter cannot represent infinitely many values. Instead, it divides the input range into a fixed number of equally spaced levels. Every measured voltage is assigned to the closest available level.

---

# Continuous vs Discrete

Analog World

∞ possible voltages

↓

Quantization

↓

Digital World

2ⁿ possible values

The conversion from infinity to a finite set is irreversible.

---

# Quantization Levels

The number of available digital levels depends on converter resolution.

Examples:

8-bit

256 levels

10-bit

1024 levels

12-bit

4096 levels

16-bit

65536 levels

The general equation is:

Number of Levels = 2ⁿ

where

n = ADC resolution in bits.

---

# Quantization Step

Each digital level represents a small voltage interval. This interval is called the Least Significant Bit (LSB).

The quantization step is

ΔV

=

Input Range

────────────

2ⁿ

Example

Input Range

5 V

Resolution

12 bits

Levels

4096

Therefore

ΔV

=

5

─────

4096

≈

1.22 mV

Every digital code therefore represents approximately 1.22 millivolts.

---

# Quantization Process

Suppose the converter can only represent:

0 V

1 V

2 V

3 V

An input voltage of

2.43 V

cannot be represented exactly.

Instead, it is rounded to the nearest available level. The small difference between the true voltage and the represented voltage is called quantization error.

---

# Quantization Error

Quantization error is simply

Actual Voltage

−

Represented Voltage

The maximum theoretical error is

± ½ LSB

because every value is rounded to the nearest level.

This error is unavoidable.

No ideal ADC can eliminate it.

---

# Staircase Approximation

An analog signal changes continuously.

After quantization, the signal becomes a staircase.

Analog

~~~~~~~~~~~~~

Digital

____

|

|____

|

|____

|

|____

The higher the resolution, the smaller the steps become.

---

# Resolution vs Accuracy

Higher resolution provides more digital levels.

However:

Higher resolution does not automatically mean higher accuracy.

Actual accuracy also depends on:

- Offset error
- Gain error
- INL
- DNL
- Noise
- Reference voltage accuracy

Resolution and accuracy are related, but not identical concepts.

---

# Dynamic Range

Increasing resolution increases the theoretical dynamic range.

An ideal converter has

Dynamic Range

≈

6.02N + 1.76 dB

Examples

8-bit

≈ 50 dB

12-bit

≈ 74 dB

16-bit

≈ 98 dB

This equation represents the theoretical limit of an ideal converter.

---

# Why Quantization Sounds Like Noise

Quantization introduces a small error for every sample. Because this error changes from sample to sample, it behaves similarly to noise. However, quantization noise is not always random. Without additional processing it can become correlated with the signal itself.

This produces distortion.

---

# Relationship with Dither

Dither intentionally adds a very small amount of random noise before quantization. Although this appears counterintuitive, it decorrelates quantization error from the original signal. The result is often perceived as more natural and less distorted.

A dedicated Project SP document discusses this process in detail.

---

# Quantization in Vintage Samplers

Classic samplers were often limited to relatively low resolutions.

Rather than treating this limitation as a flaw, many instruments became famous because of the sonic character produced by their quantization process.

Project SP studies quantization as one of several contributors to vintage digital sound.

Resolution alone does not define the complete character.

---

# Engineering Questions

Several important questions remain.

- Should Project SP emulate ideal quantization?
- Should quantization include measured non-linearities?
- Should quantization noise remain deterministic?
- Should optional dither be available?
- How closely should the original SP-1200 behaviour be reproduced?

These questions will be answered experimentally.

---

# Future Validation

Project SP will investigate quantization through:

- Mathematical analysis
- Simulation
- Oscilloscope measurements
- FFT analysis
- Listening tests
- Comparison with the original SP-1200

---

# Project SP Design Decision

## Current Status

🟢 Fundamental Principle Understood

## Current Concept

Project SP treats quantization as an essential part of analog-to-digital conversion rather than a simple mathematical rounding operation.

Its behaviour will be analysed theoretically and validated experimentally.

## Design Rationale

Understanding quantization is necessary before studying dither, dynamic range and vintage digital colouration.

## Future Validation

Future work includes:

- Quantization error measurements
- FFT analysis
- Dynamic range verification
- Listening comparisons
- Original SP-1200 comparison