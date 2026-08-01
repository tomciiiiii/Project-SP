# Clock

> Every digital system begins with time.

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

**▶ Clock ◀**

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

The clock provides the timing reference for every digital operation within the system. It determines precisely when each audio sample is taken, when the ADC begins conversion and when digital processing occurs. Without a stable clock, digital audio cannot exist. Time is the foundation upon which all digital systems are built.

---

# Why a Clock is Necessary

Unlike analog circuits, digital systems cannot operate continuously. Every digital operation happens at a specific instant. The clock provides these instants. Each clock pulse tells the system:

"Do the next operation now."

Without this timing reference, every digital block would operate independently, producing unpredictable behaviour.

---

# What is a Clock?

A clock is simply a highly stable periodic electrical signal. Typically it is a square wave.

Example

□□□□□□□□□□□□

Each rising (or falling) edge represents a precise moment in time. Digital circuits synchronize their operation to these edges.

---

# Clock Frequency

Clock frequency describes how many cycles occur every second. It is measured in Hertz (Hz).

Examples

1 MHz

↓

1,000,000 cycles/second

10 MHz

↓

10,000,000 cycles/second

24.576 MHz

↓

24,576,000 cycles/second

Clock frequency should not be confused with sampling frequency. The clock often operates many hundreds of times faster than the audio sampling rate.

---

# Clock vs Sampling Rate

These two concepts are closely related but fundamentally different.

Clock

↓

Controls every digital operation.

Sampling Rate

↓

Determines how often audio is sampled. The sampling frequency is usually derived from the master clock using counters or frequency dividers.

---

# Master Clock

Most digital audio systems use one primary timing reference. This is known as the Master Clock. Every subsystem synchronizes to this single source.

Typical subsystems include:

- ADC
- DAC
- DSP
- Memory
- Serial interfaces

Using one common clock prevents timing conflicts.

---

# Clock Sources

Several technologies can generate clock signals.

Examples include:

- Crystal Oscillators
- Ceramic Resonators
- MEMS Oscillators
- External Clock Sources

For precision audio systems, crystal oscillators are by far the most common choice due to their excellent long-term stability.

---

# Why Crystal Oscillators?

Quartz crystals resonate at an extremely stable frequency.

Advantages include:

- Excellent frequency stability
- Low drift
- High accuracy
- Low phase noise
- Long-term reliability

For audio applications, timing stability is often more important than absolute frequency accuracy.

---

# Clock Distribution

Generating a stable clock is only the first step. The clock signal must also be distributed throughout the circuit.

Poor PCB layout can introduce:

- Delay
- Reflections
- Crosstalk
- Additional jitter

Clock routing therefore becomes an important part of high-speed digital design.

---

# Timing Relationships

Many digital operations depend on precise timing relationships.

Examples include:

Sample

↓

Hold

↓

Convert

↓

Store

↓

Process

↓

Playback

Every stage relies on the same timing reference. A single unstable clock affects the entire signal chain.

---

# Clock Accuracy

Clock accuracy describes how closely the actual frequency matches its intended value.

Example

Nominal

26.040000 kHz

Measured

26.039998 kHz

For most audio systems, extremely small frequency deviations are acceptable. Short-term stability is generally more important than absolute accuracy.

---

# Clock Stability

Clock stability describes how constant the timing remains over time. A perfectly stable clock produces equally spaced timing intervals.

Ideal

|----|----|----|----|

Unstable

|---|-----|--|------|

These tiny variations lead directly to jitter.

---

# Relationship with Jitter

Clock instability produces timing uncertainty. This uncertainty is known as jitter. Although often extremely small, jitter influences the exact instant at which every sample is taken. The next document examines this behaviour in detail.

---

# Engineering Questions

Several important questions remain.

- Which master clock frequency should Project SP use?
- Should clock generation match the original SP-1200?
- How should clock distribution be implemented?
- What level of stability is required?
- Which oscillator technology is most appropriate?

These questions will be answered through measurement and implementation.

---

# Future Validation

Project SP will investigate clock performance using:

- Oscilloscope measurements
- Frequency measurements
- Stability analysis
- Long-term drift measurements
- Clock divider verification
- Comparison with the original SP-1200

---

# Project SP Design Decision

## Current Status

🟢 Timing Foundation Understood

## Current Concept

Project SP treats the system clock as the fundamental timing reference for the entire digital signal chain. Every subsystem shall derive its timing from a common master clock to ensure deterministic behaviour.

## Design Rationale

Accurate timing is essential for reliable digital audio conversion. Before investigating jitter, the fundamental role of the clock itself must be fully understood.

## Future Validation

Future work includes:

- Oscillator selection
- Frequency verification
- Clock distribution analysis
- Stability measurements
- Original hardware comparison