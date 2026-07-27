# Input Interface

## Goal

Create an unbalanced line-level input stage inspired by the SP-1200 sampling input.

The original SP-1200 accepts microphone-to-line-level signals and specifies a 10 kΩ input impedance.

## Initial Design Targets

- Unbalanced mono input
- Nominal input level: 1 Vrms
- Maximum clean input target: 2 Vrms
- Input impedance target: approximately 10 kΩ
- Bipolar analog supply: ±12 V
- Main audio opamp: OPA2134

## Initial Circuit

- Series input resistor: 470 Ω
- Coupling capacitor: 2.2 µF
- Input impedance resistor: 10 kΩ

## High-Pass Corner

fc = 1 / (2πRC)

For R = 10 kΩ and C = 2.2 µF:

fc ≈ 7.23 Hz

## Open Questions

- Final gain range
- Potentiometer position and value
- Input clipping strategy
- RF filtering
- ESD protection
- Whether microphone mode will be added later
