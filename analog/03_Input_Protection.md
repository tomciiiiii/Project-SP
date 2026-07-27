# Input Protection

## Purpose

The input protection stage is the first electrical interface between the outside world and Project SP.

Its purpose is to protect the analog circuitry from accidental overvoltage, electrostatic discharge (ESD), wiring mistakes and other abnormal operating conditions while preserving normal audio performance.

Protection should remain electrically transparent during normal operation.

---

# Why is Input Protection Necessary?

Audio equipment is often connected and disconnected while powered.

Possible fault conditions include:

- Electrostatic discharge (ESD)
- Accidental overvoltage
- Incorrect cable connections
- Phantom power exposure
- Transient voltage spikes
- User mistakes

Without protection, these events may permanently damage the operational amplifier or ADC.

---

# Design Goals

The protection network should:

- Have negligible effect on audio quality
- Protect the op-amp input
- Protect the ADC
- Limit excessive input current
- Preserve frequency response
- Be simple and reliable

---

# Proposed Protection Strategy

The current concept includes:

- Series protection resistor
- AC coupling capacitor
- Optional ESD protection diodes
- Proper PCB grounding

Additional protection may be added after prototype measurements.

---

# Candidate Components

## Series Resistor

A small resistor placed directly after the input connector limits fault current.

Typical values:

- 100 Ω
- 220 Ω
- 470 Ω
- 1 kΩ

The final value will be selected after analysing bandwidth, noise and protection requirements.

---

## ESD Protection

Optional low-capacitance protection diodes may be used to protect against electrostatic discharge.

Care must be be taken to avoid increasing input capacitance and degrading high-frequency performance.

---

## AC Coupling Capacitor

Although primarily part of the signal conditioning stage, the coupling capacitor also prevents unwanted DC voltage from entering the analog circuitry.

This protects both the operational amplifier and the ADC from external DC offsets.

---

# Trade-Offs

Increasing protection generally increases component count and may slightly influence signal integrity.

The objective is to find the simplest circuit that provides adequate protection without compromising audio performance.

---

# Future Work

Future revisions will determine:

- Final series resistor value
- Need for ESD protection
- Maximum supported input voltage
- Verification through laboratory testing

---

# References

- Texas Instruments application notes
- Analog Devices input protection guides
- IEC 61000-4-2 (ESD immunity)
- OPA2134 Datasheet

---

# Project SP Design Decision

## Current Status

🟡 Under Investigation

## Current Concept

Series resistor followed by AC coupling and optional ESD protection.

## Design Rationale

The protection network should be electrically transparent during normal operation while preventing damage during abnormal operating conditions.

## Future Validation

The final implementation will be validated using oscilloscope measurements, signal generator testing and real-world fault scenarios.

# Project SP Design Decision