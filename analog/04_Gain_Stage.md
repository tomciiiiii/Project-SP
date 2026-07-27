# Gain Stage

## Purpose

The gain stage adjusts the amplitude of the incoming audio signal so that the ADC operates close to its full-scale input range without clipping.

Proper gain maximizes the available dynamic range while minimizing the risk of distortion.

---

# Why is Gain Necessary?

Audio sources produce different output levels.

Examples include:

- Mixers
- Synthesizers
- Samplers
- Audio interfaces

The gain stage normalizes these signals before analog-to-digital conversion.

---

# Design Goals

The gain stage should:

- Maximize ADC resolution
- Prevent clipping
- Introduce minimal noise
- Introduce minimal distortion
- Remain stable
- Preserve frequency response

---

# Fixed or Adjustable Gain?

## Fixed Gain

Advantages

- Simple
- Low cost
- Repeatable performance

Disadvantages

- Less flexible

---

## Adjustable Gain

Advantages

- Supports different sources
- Better headroom control

Disadvantages

- More components
- Potentiometer wear
- Increased complexity

Project SP will initially investigate a fixed-gain design.

---

# Non-Inverting Amplifier

The first implementation is expected to use a non-inverting operational amplifier configuration.

Advantages include:

- High input impedance
- Simple gain calculation
- Excellent stability
- Widely used in audio circuits

Gain is defined by:

Gain = 1 + (Rf / Rin)

---

# Design Considerations

The following parameters will be determined during the design phase:

- ADC full-scale input voltage
- Expected maximum input level
- Required gain
- Feedback resistor
- Input resistor

---

# Future Calculations

The following calculations remain to be completed:

- Required gain
- Feedback resistor value
- Input resistor value
- Headroom analysis
- Noise contribution

---

# References

- OPA2134 Datasheet
- Analog Devices application notes
- Douglas Self – Small Signal Audio Design

---

# Project SP Design Decision

## Current Status

🟡 Under Investigation

## Current Concept

Non-inverting OPA2134 gain stage.

## Design Rationale

A non-inverting topology offers high input impedance, predictable gain and excellent compatibility with audio applications.

## Future Validation

The final gain will be verified using laboratory measurements, oscilloscope testing and ADC full-scale measurements.

# Project SP Design Decision