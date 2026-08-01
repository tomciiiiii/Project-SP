# Digital-to-Analog Converter (DAC)

> Every number deserves to become a voltage again.

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

**▶ Digital-to-Analog Converter (DAC) ◀**

↓

Reconstruction Filter

↓

Output Stage

---

# Purpose

The Digital-to-Analog Converter (DAC) performs the opposite operation of the Analog-to-Digital Converter. Rather than measuring an analog voltage and producing a binary number, the DAC receives binary numbers and generates the corresponding analog voltage. This conversion marks the beginning of the playback path.

---

# From Numbers Back to Voltage

Digital Memory

↓

2048

↓

2056

↓

2081

↓

2120

↓

DAC

↓

Analog Voltage

The stored numbers once again become electrical signals.

---

# The Reverse of the ADC

ADC

Voltage

↓

Binary Number

DAC

Binary Number

↓

Voltage

Together these two devices form the bridge between the analog and digital worlds.

---

# Every Sample Becomes a Voltage

Each stored digital sample corresponds to one output voltage.

Example

Binary

↓

000000000000

↓

0 V

Binary

↓

100000000000

↓

Mid-scale Voltage

Binary

↓

111111111111

↓

Maximum Output Voltage

The exact voltage depends on the converter reference voltage.

---

# Continuous Playback

The DAC receives a continuous stream of samples.

Example

2048

↓

2056

↓

2081

↓

2120

↓

2114

↓

2097

Each value produces one output voltage.

Together these voltages approximate the original waveform.

---

# Why the DAC Output Looks Wrong

The DAC does not immediately produce a smooth waveform. Instead, each sample is held until the next sample arrives. The result is a staircase waveform.

Ideal Samples

↓

____

    |

    |____

         |

         |____

This is expected. The waveform has not yet been reconstructed.

---

# Conversion Methods

Several DAC architectures exist.

Examples include:

- R-2R Ladder
- Current Steering DAC
- Sigma-Delta DAC
- PWM-based DAC
- Resistor Network DAC

Each architecture balances:

- Accuracy
- Speed
- Complexity
- Cost

---

# Resolution

Like ADCs, DACs also have resolution.

Examples

8-bit

256 output levels

12-bit

4096 output levels

16-bit

65536 output levels

Higher resolution produces smaller voltage steps.

---

# Accuracy

DAC performance depends on more than resolution.

Important specifications include:

- Offset Error
- Gain Error
- INL
- DNL
- Noise
- Reference Stability

An ideal DAC reproduces every digital value as the correct analog voltage.

---

# Vintage Samplers

Classic samplers often used converter technologies very different from modern audio interfaces. The behaviour of the DAC contributed significantly to the overall sonic character. Project SP studies the DAC not merely as a playback component, but as one of the defining elements of vintage digital sound.

---

# Engineering Questions

Several important questions remain.

- Which DAC architecture best represents the original SP-1200?
- Should converter imperfections be reproduced?
- How accurately should voltage levels be matched?
- Which reference voltage should be used?
- How should the analog output be filtered?

These questions will guide future implementation.

---

# Future Validation

Project SP will investigate:

- DAC linearity
- Voltage measurements
- FFT analysis
- Step response
- Listening tests
- Comparison with the original SP-1200

---

# Project SP Design Decision

## Current Status

🟢 Digital-to-Analog Conversion Understood

## Current Concept

Project SP treats the DAC as an active contributor to the instrument's sonic character. Playback quality depends not only on stored samples but also on how accurately they are reconstructed into analog voltages.

## Design Rationale

Understanding DAC operation completes the digital conversion cycle and prepares the signal for analog reconstruction.

## Future Validation

Future work includes:

- DAC implementation
- Linearity measurements
- Step response analysis
- Vintage hardware comparison