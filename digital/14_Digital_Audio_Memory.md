# Digital Audio Memory

> A sample becomes immortal the moment it is written into memory.

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

**▶ Digital Audio Memory ◀**

↓

Sample Playback

↓

Pitch Shifting

↓

Interpolation

↓

DAC

↓

Output Stage

---

# Purpose

Once the Analog-to-Digital Converter has completed its conversion, the analog waveform no longer exists as a continuously varying voltage.

Instead, it becomes digital information.

The purpose of digital memory is to store these numerical representations so they can later be retrieved, processed and reconstructed back into audio.

Without memory, sampling would not exist.

---

# From Voltage to Data

Before conversion:

Analog Voltage

↓

Continuous Signal

After conversion:

101011001101

↓

Digital Sample

The sample is now information rather than electricity.

---

# What is Stored?

The memory does not store music. It does not store notes. It does not store frequencies. It stores only numbers. Each number represents one measured voltage at one specific moment in time. Music appears only when thousands of these numbers are replayed in the correct order.

---

# Samples Form a Sequence

One sample contains almost no useful information. Thousands of consecutive samples reconstruct the waveform.

Example

Sample 1

↓

2048

Sample 2

↓

2056

Sample 3

↓

2081

Sample 4

↓

2120

...

Each value represents one instant in time.

---

# Addressing

Every stored sample occupies a unique memory location.

Address

↓

Sample

0000

↓

2048

0001

↓

2056

0002

↓

2081

0003

↓

2120

...

Playback simply reads these addresses one after another.

---

# Sequential Storage

Audio samples are normally stored sequentially.

Address

↓

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

This makes continuous playback simple and efficient.

---

# Memory Capacity

The available recording time depends on three parameters.

- Sampling Rate
- Bit Depth
- Available Memory

Higher values improve quality but require more storage. This trade-off shaped every classic sampler.

---

# Why Memory Was Expensive

During the 1980s memory was one of the most expensive components in a digital sampler.

Designers constantly balanced:

- Audio quality
- Recording time
- Manufacturing cost

Many legendary instruments owe part of their character to these engineering compromises.

---

# Words and Bytes

Digital memory stores binary data.

Common units include:

Bit

↓

Byte (8 bits)

↓

Word

↓

Memory Block

A 12-bit sample typically occupies more than one byte. Efficient storage therefore becomes an important engineering challenge.

---

# Reading and Writing

Sampling consists of two operations.

Write

ADC

↓

Memory

Playback consists of the opposite operation.

Memory

↓

DAC

Understanding both directions is essential for understanding a digital sampler.

---

# Memory Does Not Understand Audio

Memory has no concept of sound. To memory, every sample is simply another binary number. Meaning appears only when those numbers are interpreted correctly by the playback system.

---

# Engineering Questions

Several important questions remain.

- How should samples be organised?
- How should playback addresses be generated?
- Should memory emulate vintage limitations?
- How were classic samplers organised internally?
- Which memory architecture best suits Project SP?

These questions will guide future development.

---

# Future Validation

Project SP will investigate:

- Memory organisation
- Binary storage
- Sample addressing
- Playback bandwidth
- Original SP-1200 memory behaviour

---

# Project SP Design Decision

## Current Status

🟢 Digital Storage Understood

## Current Concept

Project SP treats digital memory as an integral part of the signal chain rather than passive storage. The organisation of sample data directly influences playback behaviour and future DSP operations.

## Design Rationale

Understanding how samples are represented and organised in memory provides the necessary foundation for playback, pitch manipulation and digital signal processing.

## Future Validation

Future work includes:

- Memory mapping
- Address generation
- Vintage architecture comparison
- Playback verification