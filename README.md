# Project-SP
Understanding sampler design through engineering.

Project SP is an open-source research project focused on understanding how classic digital samplers create their characteristic sound.

Rather than cloning a specific machine, the goal is to study and document every engineering decision involved in sampler design—from the analog input stage to the digital signal processing pipeline and audio output.

Every design choice will be explained, calculated, measured and documented.

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