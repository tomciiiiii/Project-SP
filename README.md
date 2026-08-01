# Project-SP

Project SP began with a simple question:
What actually makes a sampler sound like a sampler?

Project SP is an open-source research project focused on understanding how classic digital samplers create their characteristic sound.
Rather than cloning a specific machine, the goal is to study and document every engineering decision involved in sampler design—from the analog input stage to the digital signal processing pipeline and audio output.
Every design choice will be explained, calculated, measured and documented.

---

## Reading Order

### Part I – Analog Input
1. Input Interface
2. Operational Amplifier
3. Input Protection
4. Gain Stage
5. Anti-Alias Filter

### Part II – Analog to Digital Conversion
6. Sample and Hold
7. ADC Introduction
8. SAR ADC
9. Quantization
10. Dither
11. Sampling Rate
12. Clock
13. Jitter

### Part III – Digital Domain
14. Digital Audio Memory
15. Sample Playback
16. Pitch Shifting
17. Interpolation

### Part IV – Back to Analog
18. DAC
19. Reconstruction Filter
20. Output Stage

---

## Mission

Build knowledge before building hardware.
The objective is not simply to reproduce a vintage sampler, but to understand:

- Analog audio front-end design
- Anti-alias filtering
- Sample & Hold circuits
- ADC architecture
- Memory organization
- Pitch algorithms
- DAC behaviour
- Reconstruction filters
- Output amplifier design
- DSP implementation
- System architecture

---

## Project Philosophy
> Understanding before implementation.

Every resistor.
Every capacitor.
Every filter.
Every algorithm.

If it exists in the design, there should be a reason for it.
Whenever possible, decisions will be supported by:

- Engineering calculations
- Measurements
- Datasheets
- Listening tests
- References to original service manuals

---

## Repository Structure

```
analog/00_input/
    01_Input_Interface.md
    02_Operational_Amplifier.md
    03_Input_Protection.md
    04_Gain_Stage.md
    05_Anti_Alias_Filter.md

analog/01_conversion/
    06_Sample_And_Hold.md
    07_ADC_Introduction.md
    08_SAR_ADC.md
    09_Quantization.md
    10_Dither.md
    11_Sampling_Rate.md
    12_Clock.md
    13_Jitter.md

digital/
    14_Digital_Audio_Memory.md
    15_Sample_Playback.md
    16_Pitch_Shifting.md
    17_Interpolation.md

output/
    18_DAC.md
    19_Reconstruction_Filter.md
    20_Output_Stage.md


docs/
    Theory
    Service Manual Notes
    Analog
    ADC
    DSP
    DAC
    Measurements

hardware/
    Schematics
    PCB

firmware/

media/

tests/
```

---

## Current Status

- [x] Project created
- [x] Engineering notebook started
- [x] Original SP-1200 service manual available
- [x] Daisy Seed 3 development board ordered
- [ ] Analog front-end
- [ ] Prototype v0.1

---

## Long-term Goal

Create a fully documented educational platform that helps engineers, students and audio enthusiasts understand sampler architecture through practical experimentation and open documentation.

---

*"The journey is just as important as the hardware."*