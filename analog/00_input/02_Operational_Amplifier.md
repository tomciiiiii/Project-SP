# Operational Amplifier

## Purpose

Operational amplifiers are one of the fundamental building blocks of analog electronics.

Within Project SP, the operational amplifier is responsible for conditioning the incoming audio signal before it reaches the analog-to-digital converter (ADC).

Its job is not to "improve" the sound, but to provide a predictable and well-controlled electrical environment for the following stages.

---

# What is an Operational Amplifier?

An operational amplifier (op-amp) is a high-gain differential voltage amplifier that, when combined with external feedback components, can perform a wide range of analog signal processing tasks.

In audio circuits, op-amps are commonly used for:

- Signal buffering
- Voltage amplification
- Active filtering
- Impedance conversion
- Mixing
- Summing

Project SP primarily uses an op-amp for buffering, gain control and active filtering.

---

# Requirements for Project SP

The selected operational amplifier should provide:

- Low noise
- Low distortion
- Stable operation
- Good bandwidth
- Sufficient slew rate
- Audio transparency
- Wide supply voltage range
- Good availability

---

# Candidate Devices

Several devices were considered during the design phase.

| Device | Notes |
|---------|------|
| TL072 | Classic JFET audio op-amp |
| NE5532 | Industry standard bipolar audio op-amp |
| OPA2134 | High-performance audio JFET op-amp |
| LM4562 | Extremely low distortion audio op-amp |
| MCP6002 | Rail-to-rail, general-purpose op-amp |

---

# Why OPA2134?

The OPA2134 was selected as the primary candidate because it offers an excellent balance between performance, simplicity and availability.

Advantages include:

- Low input noise
- Very low harmonic distortion
- High slew rate
- JFET inputs
- Wide supply voltage range
- Unity-gain stability
- Excellent documentation

For audio applications it has become something of a modern reference device.

---

# Why not...

## TL072

Pros

- Cheap
- Proven
- JFET inputs

Cons

- Higher noise
- Lower overall performance

---

## NE5532

Pros

- Excellent audio reputation
- Low noise

Cons

- Bipolar input stage
- Higher input bias current

---

## MCP6002

Pros

- Rail-to-rail
- Low power

Cons

- Not intended primarily for high-performance audio

---

# Design Philosophy

Project SP does not choose components because they are considered "audiophile".

Components are selected because they satisfy measurable engineering requirements.

Every component should be justifiable through electrical performance rather than marketing claims.

---

# Future Work

Future revisions may evaluate additional operational amplifiers, including:

- OPA1642
- OPA1656
- LM4562
- NJM2068

Measurements and listening tests will determine whether any alternative offers meaningful advantages.

---

# References

- Texas Instruments OPA2134 Datasheet
- Douglas Self – Small Signal Audio Design
- Walt Jung – Op Amp Applications Handbook

---

# Project SP Design Decision

Current Status

🟢 Selected Candidate

Selected Device

OPA2134

Reason

The OPA2134 currently provides the best balance between measured performance, documentation quality, availability and simplicity.

This decision may change as Project SP evolves and new measurements become available.

## Verification

The following measurements will validate this decision:
- Input noise
- Frequency response
- THD+N
- Output swing
- Stability
- Listening evaluation