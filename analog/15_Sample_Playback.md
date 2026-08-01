# Sample Playback

> A sample becomes sound again when memory is read in time.

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

**▶ Sample Playback ◀**

↓

Pitch Shifting

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

Recording is only half of the story.

Once audio samples have been stored in memory, they must later be retrieved in exactly the correct order and at precisely the correct speed. Sample playback is the process of reading stored digital values and sending them towards the Digital-to-Analog Converter. Correct playback recreates the original waveform. Changing the playback process changes the sound itself.

---

# Reading Memory

Playback is fundamentally simple. Instead of writing samples into memory, the system now reads them.

Memory

↓

Sample

Address 0

↓

2048

Address 1

↓

2056

Address 2

↓

2081

Address 3

↓

2120

...

The DAC receives these numbers one after another.

---

# Sequential Playback

Normal playback reads consecutive memory locations.

Address

0

↓

1

↓

2

↓

3

↓

4

↓

5

↓

...

Reading samples sequentially reconstructs the original recording.

---

# Playback Speed

The speed at which memory is read determines the duration of the sound.

Normal Speed

↓

Original pitch

Faster

↓

Shorter playback

Higher pitch

Slower

↓

Longer playback

Lower pitch

Playback speed therefore controls both pitch and time.

---

# Sample Pointer

A playback engine keeps track of its current position using a pointer.

Example

Pointer

↓

Address 0

↓

Address 1

↓

Address 2

↓

Address 3

↓

...

Every playback cycle advances the pointer.

---

# Start Address

Playback does not always begin at the first sample. Instead, the system selects a start address.

Example

Memory

0

1

2

3

4

5

6

7

8

Playback may begin directly at:

Address 4

This allows editing and trimming.

---

# End Address

Playback also requires a stopping point.

Once the end address is reached,

playback may:

- Stop
- Loop
- Trigger another event

The chosen behaviour depends on the instrument.

---

# Looping

Many samplers repeatedly play part of a recording.

Start

↓

Loop

↓

Loop

↓

Loop

↓

Stop

Looping allows sustained sounds using relatively little memory.

---

# One-Shot Playback

Some sounds should never loop.

Examples include:

- Drum hits
- Percussion
- Sound effects

Playback simply begins,

continues once,

and stops.

---

# Polyphony

Multiple playback engines may operate simultaneously.

Each voice maintains its own:

- Pointer
- Playback speed
- Envelope
- Volume
- State

The mixer combines every active voice into a single output.

---

# Playback Timing

Playback relies on the same master clock used throughout the digital system. Every clock event advances playback by one sample. Stable timing therefore remains essential even after recording has finished.

---

# Vintage Samplers

Classic samplers often used surprisingly simple playback engines. Rather than sophisticated DSP, many relied on direct memory addressing and fixed-rate playback. Their limitations became part of their unmistakable sonic character. Project SP studies these playback methods as engineering decisions rather than shortcomings.

---

# Engineering Questions

Several important questions remain.

- Should playback use integer or fractional addressing?
- How should looping behave?
- How should voice allocation work?
- How closely should the original SP-1200 playback engine be reproduced?
- Which playback limitations contribute to vintage character?

These questions will guide future implementation.

---

# Future Validation

Project SP will investigate playback through:

- Timing measurements
- Listening tests
- Memory tracing
- Pointer analysis
- Loop behaviour
- Original SP-1200 comparison

---

# Project SP Design Decision

## Current Status

🟢 Playback Architecture Understood

## Current Concept

Project SP treats playback as an active digital process rather than simple memory reading. Accurate pointer control, timing and memory organisation are considered essential parts of reproducing vintage sampler behaviour.

## Design Rationale

The playback engine transforms stored numerical values back into a continuous stream of digital samples.Understanding this process provides the foundation for pitch manipulation, interpolation and digital voice management.

## Future Validation

Future work includes:

- Playback implementation
- Pointer verification
- Loop testing
- Voice allocation
- Comparison with the original SP-1200