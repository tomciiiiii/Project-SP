# Sample and Hold

> Holding one moment still long enough for the digital world to understand it.

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

**▶ Sample and Hold ◀**

↓

ADC

↓

Digital Processing

↓

DAC

↓

Output Stage

---

# Purpose

The Sample and Hold (S/H) stage forms the bridge between the continuous analog world and the discrete digital domain.
Its purpose is simple but essential:
Capture the instantaneous voltage of the analog signal and keep it constant while the Analog-to-Digital Converter (ADC) performs its conversion. Without this stage, the input voltage would continue changing during the conversion process, producing inaccurate digital samples.
The Sample and Hold circuit ensures that every conversion represents a single, well-defined moment in time.

---

# Why Sample and Hold Exists

Unlike digital signals, analog signals never stop changing. Even a simple sine wave continuously varies in voltage. An ADC, however, cannot convert an analog voltage instantaneously. Every conversion requires a finite amount of time. If the input voltage changes during this interval, the ADC no longer measures a single voltage level.

Instead, it measures a moving target.

The Sample and Hold circuit solves this problem by temporarily freezing the analog voltage before conversion begins.

---

# Continuous-Time vs Sampled Signals

An analog signal exists continuously in time. The ADC only observes individual points.

Without Sample and Hold:

Analog Signal

~~~~~~~~~~~~~~

ADC Conversion

|------|

Input changes during conversion

↓

Conversion error

With Sample and Hold:

Analog Signal

~~~~~~~~~~~~~~

Switch closes

↓

Capacitor charges

↓

Switch opens

↓

Voltage remains constant

↓

ADC converts accurately

---

# Operating Principle

The Sample and Hold circuit operates in two distinct phases.

## Sample Phase

During the sample phase, the electronic switch closes. The hold capacitor is connected directly to the input signal. The capacitor charges until its voltage matches the input voltage. The capacitor continuously follows the incoming signal while the switch remains closed.

---

## Hold Phase

Once sampling is complete, the switch opens. The capacitor becomes electrically isolated. Because the capacitor stores electrical charge, its voltage remains nearly constant. During this short period the ADC performs the conversion. Once conversion has finished, the process repeats.

---

# Internal Building Blocks

A typical Sample and Hold circuit consists of four basic elements.

Analog Input

↓

Sampling Switch

↓

Hold Capacitor

↓

Buffer Amplifier

↓

ADC

Each block contributes to overall conversion accuracy.

---

## Sampling Switch

Usually implemented using a MOSFET or dedicated analog switch. Its job is to connect and disconnect the capacitor from the input signal with precise timing.

Important parameters include:

- ON resistance
- Switching speed
- Charge injection
- Leakage current

---

## Hold Capacitor

The capacitor temporarily stores the sampled voltage.

Its value directly affects:

- Acquisition time
- Hold accuracy
- Droop rate
- Noise

Capacitor selection is therefore a compromise between speed and stability.

---

## Buffer Amplifier

The buffer isolates the capacitor from the ADC input.

Without a buffer, the ADC itself could discharge the capacitor and introduce conversion errors.

The buffer should have:

- High input impedance
- Low output impedance
- Low noise
- Low offset voltage

---

# Acquisition Time

Acquisition time is the time required for the capacitor voltage to settle to the input voltage after the sampling switch closes.

It depends primarily on:

- Source impedance
- Switch resistance
- Hold capacitor value

If acquisition time is too short, the capacitor never fully reaches the input voltage. This introduces conversion error before the ADC even begins.

---

# Hold Time

During Hold mode, the capacitor slowly loses charge. The stored voltage gradually decreases. This effect is known as droop.
For accurate conversion:

Hold Time << Time required for significant droop

---

# Sources of Error

Every Sample and Hold circuit introduces imperfections.

Common error sources include:

- Droop Rate
- Charge Injection
- Clock Feedthrough
- Aperture Delay
- Aperture Jitter
- Leakage Current
- Capacitor Dielectric Absorption

Understanding these mechanisms is essential for designing accurate conversion systems.

---

# Design Trade-Offs

Increasing capacitor value:

Advantages

- Lower droop
- Better hold accuracy

Disadvantages

- Longer acquisition time
- Slower sampling

Reducing capacitor value:

Advantages

- Faster acquisition
- Higher sampling speed

Disadvantages

- Increased droop
- Greater sensitivity to leakage

The optimal value depends on the sampling frequency and the required accuracy.

---

# Sample and Hold in Vintage Samplers

Classic digital samplers commonly employed external Sample and Hold circuitry ahead of the ADC.

Although often overlooked, this stage plays an important role in overall conversion accuracy and therefore contributes indirectly to the sonic character of the instrument.

Project SP investigates this stage as an independent analog subsystem rather than treating it as an internal ADC detail.

---

# Future Validation

The final implementation will be validated using:

- Oscilloscope measurements
- Acquisition time testing
- Hold voltage measurements
- Droop measurements
- Signal generator verification
- Comparison between theoretical calculations and hardware measurements

---

# Project SP Design Decision

Project SP considers the Sample and Hold stage to be a fundamental part of the analog signal path rather than merely an ADC accessory.

Its behaviour will be analysed, calculated, simulated and experimentally verified before implementation.

Every design choice—including switch technology, capacitor value and timing—must be justified through engineering principles and supported by measurements.