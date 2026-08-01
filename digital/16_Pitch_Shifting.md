# Pitch Shifting

> Pitch is nothing more than time viewed from another perspective.

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

**▶ Pitch Shifting ◀**

↓

Interpolation

↓

DAC

↓

Reconstruction Filter

↓

Output Stage

---

# Purpose

Pitch shifting changes the perceived musical pitch of a recorded sample. In classic hardware samplers, this is achieved by changing the playback speed rather than modifying the recorded data itself. The stored digital samples remain completely unchanged. Only the rate at which memory is read is altered.

---

# One Sample Never Changes

Suppose memory contains:

2048

2056

2081

2120

2114

2097

These numbers never change. Pitch shifting does not modify them. Instead, it changes how quickly they are read.

---

# Normal Playback

Memory

↓

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

Playback Speed

1×

Result:
- Original pitch
- Original duration

---

# Faster Playback

Memory

↓

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

Playback Speed

2×

The samples are consumed twice as quickly.

Result:
- Higher pitch
- Shorter duration

---

# Slower Playback

Playback Speed

0.5×

The samples are consumed more slowly.

Result

Lower pitch

Longer duration

---

# Time and Pitch are Connected

Classic samplers cannot independently control pitch and duration. Changing playback speed changes both simultaneously.

Higher Pitch

↓

Shorter Sound

Lower Pitch

↓

Longer Sound

This behaviour became one of the defining characteristics of vintage samplers.

---

# Why Does Pitch Change?

Pitch depends on how frequently the waveform repeats. When playback becomes faster, the waveform repeats more frequently.

Higher repetition frequency

↓

Higher perceived pitch.

When playback becomes slower, the waveform repeats less frequently.

Lower repetition frequency

↓

Lower perceived pitch.

---

# Memory is Passive

Memory has no concept of musical notes. It simply stores numbers. The playback engine determines pitch entirely by deciding how rapidly those numbers are read.

---

# Fractional Playback

Suppose playback needs to occur at

1.37×

normal speed.

The pointer can no longer move:

0

↓

1

↓

2

↓

3

Instead, it moves by fractional amounts.

Example

0.00

↓

1.37

↓

2.74

↓

4.11

↓

5.48

The pointer now lands between stored samples. A new challenge appears. How should the missing values be calculated? This leads directly to interpolation.

---

# Vintage Samplers

Many early samplers used relatively simple playback engines. Rather than calculating complex spectral transformations, they simply varied the memory read rate. This produced the familiar behaviour:

Lower Pitch

↓

Longer

↓

Darker

Higher Pitch

↓

Shorter

↓

Brighter

Project SP studies this behaviour because it forms an important part of vintage sampler character.

---

# Musical Consequences

Changing playback speed simultaneously affects:

- Pitch
- Duration
- Envelope timing
- Harmonic content
- Perceived energy

These effects contribute significantly to the recognisable sound of classic hardware samplers.

---

# Engineering Questions

Several important questions remain.

- Should Project SP reproduce original playback behaviour exactly?
- Should playback speed be continuously variable?
- Should fractional addressing be supported?
- Which interpolation method best preserves vintage character?
- How accurately should original pitch behaviour be reproduced?

These questions will guide future implementation.

---

# Future Validation

Project SP will investigate:

- Playback speed measurements
- Pitch accuracy
- Fractional addressing
- Listening comparisons
- Original SP-1200 behaviour
- Experimental interpolation methods

---

# Project SP Design Decision

## Current Status

🟢 Playback Principle Understood

## Current Concept

Project SP adopts classic variable-speed playback as the primary method of pitch manipulation. Rather than modifying sample contents, the playback engine changes only the memory read speed.

## Design Rationale

This architecture accurately reflects the behaviour of many legendary hardware samplers and preserves the natural relationship between pitch and playback duration.

## Future Validation

Future work includes:

- Fractional pointer implementation
- Playback speed verification
- Musical listening tests
- Comparison with the original SP-1200