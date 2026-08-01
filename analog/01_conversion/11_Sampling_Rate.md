# Sampling Rate

> Every sample is a moment in time.

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

**▶ Sampling Rate ◀**

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

The sampling rate defines how often an analog signal is measured and converted into digital data. It establishes the time resolution of a digital audio system. While ADC resolution determines how accurately voltage is represented, the sampling rate determines how accurately time is represented.

Together, these two parameters define the quality and behaviour of digital audio.

---

# What is Sampling Rate?

Sampling rate is the number of individual samples acquired every second.

It is measured in:

Samples per second

or

Hertz (Hz)

Examples:

8 kHz

8000 samples/second

26.04 kHz

26040 samples/second

44.1 kHz

44100 samples/second

48 kHz

48000 samples/second

96 kHz

96000 samples/second

---

# Every Sample is a Snapshot

Imagine photographing a moving object. One photograph captures only a single instant. A movie becomes smooth because thousands of photographs are taken every second. Digital audio works exactly the same way. Each sample is one instantaneous measurement of voltage. A continuous waveform is reconstructed from many individual samples.

---

# Time Resolution

Higher sampling rates provide finer resolution in time.

Example

10 samples

↓

Rough approximation

100 samples

↓

Better approximation

1000 samples

↓

Very accurate representation

The waveform itself has not changed.

Only the number of observations has increased.

---

# The Nyquist-Shannon Sampling Theorem

One of the fundamental principles of digital signal processing states:

A signal can only be reconstructed correctly if the sampling frequency is greater than twice the highest frequency contained within the signal.

Therefore:

Maximum Reproducible Frequency

=

Sampling Rate

──────────────

2

This limit is called the Nyquist Frequency.

---

# Nyquist Frequency

Examples:

8 kHz Sampling

↓

4 kHz Maximum Frequency

26.04 kHz Sampling

↓

13.02 kHz Maximum Frequency

44.1 kHz Sampling

↓

22.05 kHz Maximum Frequency

48 kHz Sampling

↓

24 kHz Maximum Frequency

Signals above this limit create aliasing unless removed before conversion.

---

# Why Higher is Not Always Better

A higher sampling rate increases:

- Time resolution
- Available bandwidth
- Data rate
- Storage requirements
- Processing requirements

Every engineering decision involves trade-offs.

Project SP studies these trade-offs rather than assuming that higher values are always preferable.

---

# Sampling Rate and Vintage Samplers

Classic samplers often used comparatively low sampling rates.

This was primarily due to:

- Memory limitations
- ADC technology
- Processing speed
- Cost

Although these limitations reduced bandwidth, they also became part of the instrument's characteristic sound.

Project SP investigates these behaviours as intentional engineering constraints rather than flaws.

---

# Why 26.04 kHz?

One of the defining characteristics of the original SP-1200 is its sampling frequency of approximately:

26.04 kHz

This results in a theoretical Nyquist frequency of approximately:

13.02 kHz

Combined with analog filtering, converter behaviour and playback characteristics, this contributes significantly to the recognisable sound of the instrument.

The sampling rate alone does not create the SP-1200 sound, but it is one important part of the overall system.

---

# Sampling Rate vs Bit Depth

Sampling Rate answers:

"How often?"

Bit Depth answers:

"How accurately?"

Both are independent parameters.

Changing one does not automatically improve the other.

---

# Engineering Questions

Several important questions remain.

- Should Project SP operate at exactly 26.04 kHz?
- How accurately should the original timing be reproduced?
- Should multiple sampling rates be available?
- Should oversampling be investigated?
- How does sampling rate interact with anti-alias filtering?

These questions will be investigated experimentally.

---

# Future Validation

Project SP will investigate sampling rate through:

- Frequency response measurements
- Listening tests
- FFT analysis
- Aliasing demonstrations
- Comparison with the original SP-1200
- Controlled resampling experiments

---

# Project SP Design Decision

## Current Status

🟢 Fundamental Principle Understood

## Current Concept

Project SP recognises sampling rate as one of the defining parameters of digital audio conversion.

The original SP-1200 sampling frequency will be studied, measured and reproduced where appropriate.

## Design Rationale

Sampling rate determines temporal resolution and available audio bandwidth.

Understanding its interaction with filtering and conversion is essential before implementing the digital signal chain.

## Future Validation

Future work includes:

- Sampling frequency verification
- Frequency response analysis
- Listening comparisons
- Aliasing measurements
- Original hardware comparison