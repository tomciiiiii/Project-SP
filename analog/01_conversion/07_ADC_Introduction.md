# Analog-to-Digital Converter (ADC)

> Transforming continuous voltages into discrete numbers.

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

**▶ Analog-to-Digital Converter ◀**

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

The Analog-to-Digital Converter (ADC) is responsible for transforming a continuous analog voltage into a discrete digital value. It represents the boundary between the analog and digital domains. Everything before the ADC exists as continuously varying electrical signals. Everything after the ADC exists as numerical data. The quality of this conversion directly influences the accuracy, dynamic range and overall behaviour of the digital system.

---

# Why an ADC is Necessary

Computers, DSPs and microcontrollers cannot directly understand voltage. They only process numbers. The ADC acts as a translator between:

Continuous voltage

↓

Binary numbers

Without an ADC, digital signal processing would not be possible.

---

# What Does an ADC Actually Measure?

An ADC does not measure sound.

It does not measure frequency.

It does not measure music.

It measures only one thing:

Voltage.

Each conversion represents the instantaneous voltage present at the ADC input during the sampling instant.

Everything else—including frequency, waveform and timbre—is reconstructed later from thousands of these individual measurements.

---

# The Analog World

Analog signals are continuous.

They can theoretically assume an infinite number of voltage values.

Example:

1.000001 V

1.000002 V

1.000003 V

...

There is no smallest analog voltage.

---

# The Digital World

A digital converter can represent only a finite number of levels.

For example:

8-bit

256 levels

12-bit

4096 levels

16-bit

65536 levels

Each measured voltage must therefore be assigned to the nearest available digital level.

---

# Two Fundamental Operations

Every ADC performs two essential operations.

## Sampling

Determining when the voltage will be measured. Handled by the Sample and Hold stage.

---

## Quantization

Determining which digital value best represents the measured voltage. This process introduces quantization error.

---

# ADC Families

Many different ADC architectures exist.

Examples include:

- Flash ADC
- SAR ADC
- Sigma-Delta ADC
- Dual-Slope ADC
- Pipeline ADC

Each architecture offers different trade-offs between:

- Speed
- Resolution
- Complexity
- Power consumption
- Cost

---

# Why SAR?

The original SP-1200 uses a Successive Approximation Register (SAR) conversion architecture. Project SP therefore studies SAR conversion in detail before considering other ADC types. **A dedicated document explains its operation.**

---

# What Determines ADC Performance?

Several parameters influence conversion quality.

These include:

- Resolution
- Sampling rate
- Accuracy
- Offset error
- Gain error
- INL
- DNL
- Noise
- Aperture uncertainty

Each parameter will be discussed separately throughout the Project SP documentation.

---

# Project SP Design Philosophy

Project SP does not treat the ADC as a black box. Instead, the complete conversion process is analysed from first principles. The objective is not merely to use an ADC, but to understand every stage involved in converting analog audio into digital information.

---

# Future Documents

The following documents continue this journey:

08_SAR_ADC.md

09_Quantization.md

10_Dither.md

11_Sampling_Rate.md

12_Clock_and_Jitter.md

---

# Project SP Design Decision

## Current Status

🟡 Foundation Complete

## Current Concept

Project SP adopts a bottom-up approach to ADC design.

Rather than selecting a converter immediately, the conversion process itself will be understood before implementation.

## Design Rationale

Understanding the limitations and behaviour of analog-to-digital conversion is essential for reproducing the characteristics of vintage digital samplers.

Every design decision should be supported by engineering principles, simulation and experimental verification.

## Future Validation

The ADC implementation will later be evaluated through:

- Static accuracy measurements
- Dynamic performance testing
- Quantization analysis
- Noise measurements
- Comparison with the original SP-1200 architecture