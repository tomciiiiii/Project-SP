# Jitter

> Perfect timing exists only in mathematics.

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

**▶ Jitter ◀**

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

Jitter describes the uncertainty in the timing of digital events. Rather than occurring at perfectly regular intervals, clock edges exhibit extremely small timing variations. Although these variations may only be measured in picoseconds or nanoseconds, they directly influence when analog signals are sampled and reconstructed. For high-performance digital audio systems, timing precision is just as important as voltage accuracy.

---

# Why Jitter Exists

No physical clock is perfectly stable.

Every oscillator is affected by:

- Thermal noise
- Electronic noise
- Power supply variations
- Component tolerances
- Electromagnetic interference
- Phase noise

These effects introduce tiny deviations in clock timing. This uncertainty is called jitter.

---

# Perfect Clock

Ideal Clock

|----|----|----|----|

Every interval is identical.

Every sample occurs exactly when expected. This exists only as a mathematical ideal.

---

# Real Clock

Real Clock

|----|---|-----|----|

The average frequency may remain correct. The exact timing of individual edges varies slightly. Those variations are jitter.

---

# Time Uncertainty

Sampling assumes that every measurement occurs at an exact instant. Jitter changes that instant.

Instead of

10.000000 μs

the sample might occur at

9.999998 μs

or

10.000003 μs

Although extremely small, these timing errors become measurable.

---

# Why Timing Matters

The ADC measures voltage at one specific instant. If that instant changes, the measured voltage may also change. Especially for rapidly changing signals, small timing errors become voltage errors.

Time error

↓

Voltage error

↓

Conversion error

---

# Slow Signals vs Fast Signals

A slowly varying waveform changes very little between adjacent clock edges. Small timing errors have minimal effect. A high-frequency waveform changes rapidly. The same timing error now produces a larger voltage error. High frequencies are therefore much more sensitive to jitter.

---

# Types of Jitter

Several forms of jitter exist.

Examples include:

- Random Jitter
- Deterministic Jitter
- Periodic Jitter
- Cycle-to-Cycle Jitter
- Aperture Jitter
- Sampling Jitter

Each affects system performance differently.

---

# Aperture Jitter

One of the most important forms in ADC systems. Aperture jitter describes uncertainty in the exact instant when the Sample and Hold circuit captures the analog voltage. Since the sampled voltage depends on time, timing uncertainty becomes conversion uncertainty.

---

# Phase Noise

Jitter and phase noise are closely related. Phase noise is commonly measured in the frequency domain. Jitter is usually discussed in the time domain. Both describe imperfections in oscillator stability.

---

# Audible Effects

Excessive jitter may contribute to:

- Increased noise
- Reduced dynamic range
- Distortion
- Loss of stereo imaging
- Reduced conversion accuracy

Modern audio systems are generally designed to minimise these effects.

---

# Jitter in Vintage Hardware

Classic digital samplers were designed using the best available technology of their time. Oscillator stability, converter design and PCB layout all influenced timing performance. Rather than assuming ideal behaviour,

Project SP studies timing imperfections as part of the original engineering design.

---

# Jitter Cannot Be Corrected Afterwards

Unlike some digital processing errors, timing uncertainty during sampling cannot simply be removed later. If the analog signal is sampled at the wrong instant, the original timing information has already been lost. This is why stable clock design is fundamental.

---

# Engineering Questions

Several important questions remain.

- What level of jitter is acceptable?
- Which oscillator technology should Project SP use?
- Can jitter be measured experimentally?
- Should vintage timing imperfections be emulated?
- Which parts of the system contribute most to timing uncertainty?

These questions will guide future hardware development.

---

# Future Validation

Project SP will investigate jitter using:

- Oscilloscope measurements
- Phase noise analysis
- Frequency stability measurements
- FFT analysis
- Comparison with modern oscillators
- Comparison with vintage hardware

---

# Project SP Design Decision

## Current Status

🟢 Timing Behaviour Understood

## Current Concept

Project SP recognises timing stability as an essential component of accurate digital audio conversion. Clock quality will therefore be evaluated alongside analog circuitry and ADC performance.

## Design Rationale

The quality of a digital audio system depends not only on voltage accuracy but also on temporal accuracy. Understanding jitter provides the final foundation before entering digital signal processing.

## Future Validation

Future work includes:

- Oscillator comparison
- Jitter measurements
- Clock distribution optimisation
- Experimental evaluation
- Original SP-1200 comparison