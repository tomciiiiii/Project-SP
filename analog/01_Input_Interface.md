# Input Interface

## Purpose

The input interface is the first stage of the Project SP signal path.

Its purpose is to receive external audio signals, protect the analog circuitry and prepare the signal for accurate analog-to-digital conversion.

Rather than colouring the sound intentionally, this stage should preserve signal integrity while providing a well-defined electrical environment for the following circuitry.

---

# Functional Requirements

The input stage should:

- Accept standard line-level audio signals
- Reject unwanted DC voltage
- Present a suitable input impedance
- Protect downstream circuitry
- Prevent ADC overvoltage
- Introduce minimal noise and distortion
- Be simple to analyse and measure

---

# Signal Flow

Audio Input

↓

Protection

↓

AC Coupling

↓

Bias Network

↓

Gain Stage

↓

Anti-Alias Filter

↓

ADC

---

# Engineering Questions

Before selecting any components, several questions must be answered.

- What maximum input level should be supported?
- What input impedance is appropriate?
- How should the ADC be protected?
- Should gain be fixed or adjustable?
- Which op-amp best fits the design goals?
- Where should the anti-alias filter be located?

The following sections investigate each of these questions individually.