# Initial Gain Calculation

The Daisy Seed audio input accepts approximately 3.6 Vpp at full
scale.

A consumer line-level signal of −10 dBV corresponds to:

\[
V_{RMS}=0.316\text{ V}
\]

\[
V_{PP}=2\sqrt{2}\cdot0.316=0.894\text{ Vpp}
\]

The required gain is therefore:

\[
A_v=\frac{3.6}{0.894}=4.03
\]

A nominal gain of 4 was selected for the initial design.

For a non-inverting amplifier:

\[
A_v=1+\frac{R_f}{R_g}
\]

Using:

\[
R_g=10.0\text{ k}\Omega
\]

\[
R_f=30.1\text{ k}\Omega
\]

results in:

\[
A_v=1+\frac{30.1}{10}=4.01
\]

Because professional line-level signals may already approach the
ADC full-scale range, a level potentiometer will be placed before
the fixed-gain stage. This allows the complete input stage to
provide both attenuation and amplification.

# Project SP Design Decision

## Current Status

🟡 Initial Design Candidate

## Current Concept

Project SP will initially use a level control followed by a fixed-gain,
non-inverting OPA2134 stage.

## Initial Component Values

- Input level potentiometer: 10 kΩ logarithmic
- Gain resistor: 10.0 kΩ
- Feedback resistor: 30.1 kΩ
- Calculated voltage gain: 4.01×
- Overall adjustable gain range: approximately 0…4×
- Target ADC level: approximately 3.6 Vpp maximum

## Design Rationale

A fixed gain of approximately four allows a −10 dBV consumer
line-level source to approach the full-scale input range of the ADC.

Placing the level control before the gain stage also allows stronger
professional line-level signals to be attenuated before amplification.

## Future Validation

The design will be verified using:

- Measured Daisy audio-input clipping level
- Oscilloscope measurements
- Maximum supported input-level testing
- Noise-floor measurements
- THD+N measurements
- Potentiometer range and usability testing