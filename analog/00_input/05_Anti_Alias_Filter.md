# Anti-Alias Filter

> A sampling system must decide which frequencies are allowed to become data.

---

## Signal Path

Input Interface

↓

Input Protection

↓

Gain Stage

↓

**▶ Anti-Alias Filter ◀**

↓

Sample and Hold

↓

ADC

↓

Digital Processing

↓

DAC

↓

Output Stage

---

## Purpose

The anti-alias filter is an analog low-pass filter placed before the
sample-and-hold and analog-to-digital conversion stages.

Its primary purpose is to reduce signal energy above the usable input
bandwidth before sampling takes place.

Frequencies that enter the ADC above the Nyquist frequency cannot be
represented correctly. Instead, they fold back into the sampled spectrum
and appear as new frequencies that were not present at those locations in
the original signal.

This process is called aliasing.

The anti-alias filter therefore acts as a boundary between the continuous
analog world and the discrete-time digital system.

---

## Position in the Signal Path

The proposed Project SP recording path is:

```text
Audio Input
    │
    ▼
Input Protection
    │
    ▼
AC Coupling
    │
    ▼
Gain Stage
    │
    ▼
Anti-Alias Filter
    │
    ▼
Sample and Hold
    │
    ▼
ADC
    │
    ▼
Sample Memory
```

The filter must be placed before sampling.

Once an out-of-band frequency has been sampled and folded into the usable
spectrum, it cannot be reliably distinguished from a legitimate
in-band frequency.

Digital processing after the ADC cannot undo this ambiguity.

---

# Sampling and the Nyquist Frequency

A continuous-time signal is measured at discrete moments separated by the
sampling period.

The sampling frequency is:

\[
f_s = \frac{1}{T_s}
\]

where:

- \(f_s\) is the sampling frequency,
- \(T_s\) is the time between samples.

The Nyquist frequency is half the sampling frequency:

\[
f_N = \frac{f_s}{2}
\]

For the Project SP reference sampling rate:

\[
f_s = 26.04\,\mathrm{kHz}
\]

therefore:

\[
f_N = \frac{26.04\,\mathrm{kHz}}{2}
\]

\[
\boxed{f_N = 13.02\,\mathrm{kHz}}
\]

This does not mean that an ideal 13.02 kHz audio bandwidth is automatically
available.

A real analog filter cannot pass all frequencies below 13.02 kHz unchanged
and completely remove everything immediately above 13.02 kHz.

The filter requires a transition band.

---

# What is Aliasing?

Aliasing occurs when a continuous-time frequency above the Nyquist limit is
sampled and becomes indistinguishable from a lower frequency.

For a single input tone, the aliased frequency can be described by folding
the input frequency around integer multiples of the sampling frequency.

A useful practical form is:

\[
f_{\mathrm{alias}} = \left|f_{\mathrm{in}} - kf_s\right|
\]

where \(k\) is selected so that the result falls between 0 Hz and the Nyquist
frequency.

---

## Example 1 — 15 kHz Input

For:

\[
f_s = 26.04\,\mathrm{kHz}
\]

and:

\[
f_{\mathrm{in}} = 15\,\mathrm{kHz}
\]

the aliased component becomes:

\[
f_{\mathrm{alias}}
=
\left|15\,\mathrm{kHz} - 26.04\,\mathrm{kHz}\right|
\]

\[
\boxed{f_{\mathrm{alias}} = 11.04\,\mathrm{kHz}}
\]

A 15 kHz analog component therefore appears as an 11.04 kHz digital
component.

---

## Example 2 — 18 kHz Input

\[
f_{\mathrm{alias}}
=
\left|18\,\mathrm{kHz} - 26.04\,\mathrm{kHz}\right|
\]

\[
\boxed{f_{\mathrm{alias}} = 8.04\,\mathrm{kHz}}
\]

The original 18 kHz component is transformed into an audible 8.04 kHz
component.

---

## Example 3 — 20 kHz Input

\[
f_{\mathrm{alias}}
=
\left|20\,\mathrm{kHz} - 26.04\,\mathrm{kHz}\right|
\]

\[
\boxed{f_{\mathrm{alias}} = 6.04\,\mathrm{kHz}}
\]

A high-frequency component near the upper limit of human hearing can
therefore reappear in the middle of the audible spectrum.

---

# Why Aliasing is Irreversible

Consider a sampled digital signal containing an 8.04 kHz component.

After sampling, the system cannot determine whether that component originated
from:

- a real 8.04 kHz analog tone, or
- an 18 kHz analog tone folded around the sampling frequency.

Both produce the same discrete-time sample sequence.

The original identity of the signal has been lost.

For this reason:

> Anti-alias filtering must occur before the ADC.

---

# An Ideal Anti-Alias Filter

An ideal anti-alias filter would have the following response:

```text
Gain
  │
1 ├───────────────────────┐
  │                       │
0 └───────────────────────┴──────── Frequency
                          fN
```

It would provide:

- zero attenuation below the Nyquist frequency,
- infinite attenuation above the Nyquist frequency,
- no phase shift,
- no delay,
- no ringing,
- no noise,
- no component tolerances.

Such a filter cannot be constructed physically.

Every real filter must transition gradually from passband to stopband.

---

# The Transition Band

A real anti-alias filter has three important regions:

```text
Passband        Transition Band         Stopband
───────────────╲
                ╲
                 ╲____________________________
```

## Passband

The passband contains the frequencies that should remain useful.

Important parameters include:

- passband edge,
- passband ripple,
- amplitude accuracy,
- phase response.

## Transition Band

The transition band is the frequency interval over which attenuation
increases.

A narrower transition band requires:

- a higher-order filter,
- greater component accuracy,
- more active stages,
- more complex phase behaviour.

## Stopband

The stopband contains frequencies that must be attenuated sufficiently before
sampling.

The required stopband attenuation depends on:

- ADC resolution,
- expected out-of-band signal level,
- acceptable alias level,
- intended sound character.

---

# Filter Order

The filter order describes the number of poles in the transfer function.

Each pole contributes approximately:

\[
-20\,\mathrm{dB/decade}
\]

or:

\[
-6\,\mathrm{dB/octave}
\]

of asymptotic roll-off.

| Filter Order | Approximate Roll-Off |
|---:|---:|
| First order | −20 dB/decade, −6 dB/octave |
| Second order | −40 dB/decade, −12 dB/octave |
| Third order | −60 dB/decade, −18 dB/octave |
| Fourth order | −80 dB/decade, −24 dB/octave |
| Sixth order | −120 dB/decade, −36 dB/octave |
| Eighth order | −160 dB/decade, −48 dB/octave |

A higher-order filter can provide stronger attenuation in a limited
transition band.

However, higher order also introduces:

- more components,
- more tolerance sensitivity,
- more phase rotation,
- potentially more ringing,
- greater stability requirements,
- more difficult calibration and verification.

Filter order is therefore a system-level compromise.

---

# First-Order RC Low-Pass Filter

The simplest low-pass filter consists of one resistor and one capacitor.

```text
Input ─── R ─────┬──── Output
                 │
                 C
                 │
                GND
```

Its cutoff frequency is:

\[
f_c = \frac{1}{2\pi RC}
\]

At the cutoff frequency:

\[
\left|H(f_c)\right| = \frac{1}{\sqrt{2}}
\]

which corresponds to approximately:

\[
-3.01\,\mathrm{dB}
\]

The magnitude response is:

\[
\left|H(f)\right|
=
\frac{1}
{\sqrt{1+\left(\frac{f}{f_c}\right)^2}}
\]

The phase response is:

\[
\phi(f)
=
-\tan^{-1}\left(\frac{f}{f_c}\right)
\]

A first-order filter is easy to understand and build, but it is normally too
gentle to serve as the complete anti-alias filter for a 26.04 kHz sampling
system.

---

## Example First-Order Candidate

Assume:

\[
R = 10\,\mathrm{k}\Omega
\]

and:

\[
C = 1.5\,\mathrm{nF}
\]

Then:

\[
f_c
=
\frac{1}
{2\pi
\left(10\times10^3\,\Omega\right)
\left(1.5\times10^{-9}\,\mathrm{F}\right)}
\]

\[
\boxed{f_c \approx 10.61\,\mathrm{kHz}}
\]

At the Nyquist frequency:

\[
f_N = 13.02\,\mathrm{kHz}
\]

the attenuation would be:

\[
\left|H(f_N)\right|
=
\frac{1}
{\sqrt{1+\left(\frac{13.02}{10.61}\right)^2}}
\]

\[
\left|H(f_N)\right| \approx 0.632
\]

\[
20\log_{10}(0.632)
\approx
-3.98\,\mathrm{dB}
\]

Only approximately 4 dB of attenuation at Nyquist is clearly insufficient
for a conventional high-fidelity anti-alias filter.

This demonstrates why multiple poles are normally required.

---

# Cascaded Filter Sections

Higher-order filters may be constructed by cascading multiple first- or
second-order sections.

For example:

```text
Input
  │
  ▼
Second-Order Section
  │
  ▼
Second-Order Section
  │
  ▼
ADC
```

Two second-order sections form a fourth-order filter.

The complete transfer function is the product of the individual section
transfer functions:

\[
H_{\mathrm{total}}(s)
=
H_1(s)\,H_2(s)
\]

This modular approach is useful because each section can be:

- calculated independently,
- simulated independently,
- measured independently,
- adjusted independently.

It also fits the Project SP philosophy of modular thinking.

---

# Active Filter Topologies

## Sallen-Key

The Sallen-Key topology uses an op-amp as a voltage-controlled voltage
source.

Advantages:

- relatively simple,
- low component count,
- suitable for unity-gain operation,
- easy to divide into second-order sections,
- commonly used in audio equipment.

Disadvantages:

- Q depends on component ratios and amplifier gain,
- sensitive to component tolerances at higher Q,
- op-amp bandwidth influences the result,
- some configurations are less flexible.

---

## Multiple-Feedback Filter

The multiple-feedback topology uses both the inverting and feedback paths of
an op-amp.

Advantages:

- useful for higher-Q sections,
- good stopband behaviour,
- convenient for certain response alignments.

Disadvantages:

- inverting operation,
- input impedance depends on the network,
- design equations are less intuitive,
- component interactions are stronger.

---

## State-Variable Filter

A state-variable filter typically uses multiple op-amps and provides
simultaneous low-pass, band-pass and high-pass outputs.

Advantages:

- independent control of cutoff frequency and Q,
- accurate and flexible,
- useful as a laboratory platform.

Disadvantages:

- higher component count,
- more op-amp sections,
- unnecessary complexity for a fixed anti-alias filter.

---

## Passive RC Followed by Active Sections

A small passive RC pole may be placed before or after the main active filter.

Possible purposes include:

- RF suppression,
- reducing high-frequency energy before the op-amp,
- isolating stages,
- providing one additional pole,
- improving ADC-driver stability.

A passive RC network should not automatically be counted as the entire
anti-alias solution.

Its interaction with source and load impedances must be included in the
calculation.

---

# Filter Response Families

Selecting the filter order is not enough.

The pole locations determine the shape of the response.

---

## Butterworth Response

A Butterworth filter is maximally flat in amplitude within the passband.

Characteristics:

- no intentional passband ripple,
- moderate transition steepness,
- smooth amplitude response,
- moderate phase distortion,
- common general-purpose choice.

A Butterworth response is often suitable when amplitude flatness is more
important than extremely sharp cutoff.

---

## Bessel Response

A Bessel filter prioritizes approximately constant group delay and good
transient behaviour.

Characteristics:

- smooth step response,
- minimal overshoot,
- relatively linear phase,
- slow transition compared with Butterworth or Chebyshev.

A Bessel response may preserve percussive transient shape well, but requires
a higher order to achieve the same stopband attenuation.

---

## Chebyshev Type I Response

A Chebyshev Type I filter permits ripple in the passband to obtain a steeper
transition.

Characteristics:

- sharper cutoff than Butterworth for the same order,
- defined passband ripple,
- increased phase nonlinearity,
- more ringing and overshoot.

This response may be useful where the transition band is very narrow, but the
passband ripple must be accepted deliberately.

---

## Chebyshev Type II Response

A Chebyshev Type II filter has a monotonic passband and ripple in the
stopband.

Characteristics:

- no passband ripple,
- transmission zeros in the stopband,
- steep attenuation near selected frequencies,
- more complex pole-zero behaviour.

---

## Elliptic Response

An elliptic filter permits ripple in both the passband and stopband.

Characteristics:

- steepest transition for a given order,
- passband ripple,
- stopband ripple,
- strong nonlinear phase behaviour,
- potentially significant ringing.

It maximizes frequency-domain selectivity but may produce less desirable
time-domain behaviour.

---

# Amplitude Response is Not the Whole Story

A filter changes more than amplitude.

It may also change:

- phase,
- group delay,
- impulse response,
- step response,
- transient shape,
- overshoot,
- ringing.

Two filters with similar magnitude responses may sound different when
processing sharp transients.

This is especially important for percussion sampling.

Project SP must therefore evaluate the anti-alias filter in both:

- the frequency domain,
- the time domain.

---

# Phase Response

The phase response describes how much each frequency component is delayed in
phase.

A first-order low-pass filter produces:

\[
\phi(f)
=
-\tan^{-1}\left(\frac{f}{f_c}\right)
\]

At the cutoff frequency:

\[
\phi(f_c) = -45^\circ
\]

A filter with multiple poles can produce significantly more phase rotation
near the cutoff region.

Phase shift alone does not necessarily produce an audible problem.

The important question is whether different parts of the spectrum are
delayed differently enough to change the waveform or transient structure.

---

# Group Delay

Group delay is defined as:

\[
\tau_g(\omega)
=
-\frac{\mathrm{d}\phi(\omega)}
{\mathrm{d}\omega}
\]

It represents how the envelope of a narrowband signal is delayed through the
system.

A constant group delay means that spectral components experience
approximately the same time delay.

Strongly frequency-dependent group delay can reshape complex transients.

This may be relevant to:

- kick drum attacks,
- snare transients,
- hi-hat edges,
- chopped sample boundaries.

---

# Step Response and Ringing

A sharp transient contains energy across a wide frequency range.

A steep low-pass filter removes high-frequency components and may produce:

- slower rise time,
- overshoot,
- pre-ringing or post-ringing depending on architecture,
- damped oscillation near the cutoff region.

Analog causal filters do not create true pre-ringing in the same way as
linear-phase FIR filters, but they may produce post-ringing and overshoot.

The amount of ringing depends on:

- filter order,
- Q,
- response family,
- pole locations,
- component tolerances.

---

# Required Stopband Attenuation

The required attenuation cannot be selected without defining an acceptable
alias level.

A useful engineering relationship is:

\[
A_{\mathrm{req}}
=
L_{\mathrm{OOB}}
-
L_{\mathrm{alias,max}}
\]

For example, if an out-of-band component may reach 0 dBFS-equivalent at the
analog input, and aliases should remain below −60 dBFS, the anti-alias system
must provide approximately:

\[
\boxed{A_{\mathrm{req}} = 60\,\mathrm{dB}}
\]

of attenuation at the relevant out-of-band frequency.

However, the complete attenuation may come from multiple sources:

- analog input filter,
- codec internal filtering,
- digital decimation filtering,
- source bandwidth limitation,
- later DSP processing.

The analog filter must therefore be designed as part of the complete
conversion chain.

---

# Relationship to ADC Resolution

An ideal \(N\)-bit converter has an approximate quantization signal-to-noise
ratio of:

\[
\mathrm{SNR}_{\mathrm{ideal}}
\approx
6.02N + 1.76\,\mathrm{dB}
\]

For 12 bits:

\[
\mathrm{SNR}_{\mathrm{ideal}}
\approx
6.02\cdot12 + 1.76\,\mathrm{dB}
\]

\[
\boxed{\mathrm{SNR}_{\mathrm{ideal}}
\approx
74\,\mathrm{dB}}
\]

This does not automatically mean that the anti-alias filter must provide
74 dB attenuation at the Nyquist frequency.

The necessary attenuation depends on:

- actual out-of-band energy,
- analog noise floor,
- converter performance,
- desired character,
- where stopband requirements are specified.

Nevertheless, there is little value in allowing strong aliases far above
the converter's own noise floor unless that behaviour is intentional.

---

# Component Tolerances

Real resistors and capacitors do not have exact values.

Typical tolerances may be:

- resistors: ±1% or ±0.1%,
- film capacitors: ±5%, ±2% or ±1%,
- common ceramic capacitors: potentially much wider and voltage-dependent.

For a basic RC pole:

\[
f_c = \frac{1}{2\pi RC}
\]

the approximate worst-case fractional cutoff error is:

\[
\left|
\frac{\Delta f_c}{f_c}
\right|
\approx
\left|
\frac{\Delta R}{R}
\right|
+
\left|
\frac{\Delta C}{C}
\right|
\]

If:

\[
\frac{\Delta R}{R} = \pm1\%
\]

and:

\[
\frac{\Delta C}{C} = \pm5\%
\]

then the cutoff frequency may shift by approximately:

\[
\boxed{
\left|
\frac{\Delta f_c}{f_c}
\right|
\approx 6\%
}
\]

in the simple worst-case estimate.

In higher-order filters, component errors can also change Q, passband ripple
and section alignment.

---

# Capacitor Selection

Capacitor type may influence:

- tolerance,
- temperature coefficient,
- voltage coefficient,
- dielectric absorption,
- physical size,
- long-term stability.

Possible candidates include:

## C0G/NP0 Ceramic

Advantages:

- excellent stability,
- low voltage dependence,
- low loss,
- good for small capacitance values.

Disadvantages:

- limited practical capacitance range,
- may become physically larger at higher values.

## Film Capacitors

Advantages:

- good linearity,
- stable value,
- low dielectric absorption,
- suitable for audio filters.

Disadvantages:

- physically larger,
- potentially more expensive.

## X7R Ceramic

Advantages:

- small,
- inexpensive,
- widely available.

Disadvantages:

- capacitance varies with DC bias,
- wider tolerance,
- higher dielectric nonlinearity,
- less desirable for precision filter poles.

Project SP should prefer C0G/NP0 or film capacitors for critical filter
components whenever practical.

---

# Resistor Selection

Metal-film resistors are suitable candidates because they provide:

- low excess noise,
- good tolerance,
- good temperature stability,
- wide availability.

Very large resistor values may increase:

- thermal noise,
- bias-current error,
- susceptibility to leakage and contamination.

Very small resistor values may:

- unnecessarily load the previous stage,
- require larger capacitors,
- increase op-amp output current.

A practical active audio-filter range is often between several kilohms and
several tens of kilohms, but the final values must be selected according to
the complete circuit.

---

# Op-Amp Requirements

The anti-alias filter op-amp must support the intended response without
significant deviation.

Important parameters include:

- gain-bandwidth product,
- slew rate,
- input noise,
- output noise,
- input common-mode range,
- output swing,
- stability,
- capacitive-load behaviour,
- supply voltage.

A practical rule is that the op-amp gain-bandwidth should be comfortably
higher than the filter cutoff frequency multiplied by the section noise gain
and Q-related demands.

The OPA2134 is the current Project SP candidate because it offers:

- unity-gain stability,
- approximately audio-oriented bandwidth,
- high slew rate,
- JFET inputs,
- low distortion,
- operation from bipolar supplies.

Its suitability must still be verified in the final filter topology.

---

# Filter and Gain-Stage Interaction

The gain stage and anti-alias filter cannot be designed independently without
checking their interaction.

Possible architectures include:

## Separate Gain and Filter Stages

```text
Level Control
    │
    ▼
Gain Stage
    │
    ▼
Active Filter
    │
    ▼
ADC
```

Advantages:

- easier to understand,
- easier to measure,
- gain and filtering can be optimized separately,
- modular debugging.

Disadvantages:

- more op-amp sections,
- more components,
- more noise contributions,
- additional headroom considerations.

## Combined Gain and Filter Stage

```text
Level Control
    │
    ▼
Active Gain + Filter Stage
    │
    ▼
ADC
```

Advantages:

- lower component count,
- fewer amplifier stages,
- potentially lower power consumption.

Disadvantages:

- component values affect both gain and filter response,
- more difficult to analyse,
- gain adjustment may change Q or cutoff frequency,
- less modular.

The first Project SP prototype should prioritize measurement and
understanding over component-count minimization.

---

# Headroom

Filtering can create internal node voltages larger than the final output
voltage, particularly in higher-Q sections.

The design must verify:

- maximum input signal,
- gain-stage output,
- filter-section internal peaks,
- op-amp output swing,
- ADC full-scale input.

A circuit that does not clip at the final output may still clip internally.

The complete chain should therefore be simulated and measured using:

- sine waves,
- swept frequency,
- impulses,
- square waves,
- high-level broadband signals.

---

# Noise

Each resistor and op-amp contributes noise.

The thermal-noise voltage density of a resistor is:

\[
e_n = \sqrt{4k_{\mathrm{B}}TR}
\]


\[
k_{\mathrm{B}}
=
1.380649\times10^{-23}\,
\mathrm{J/K}
\]

where:

- \(k\) is Boltzmann's constant,
- \(T\) is absolute temperature,
- \(R\) is resistance.

Higher resistor values generate more thermal voltage noise.

The complete output noise depends on:

- resistor noise,
- op-amp voltage noise,
- op-amp current noise,
- filter noise gain,
- total bandwidth.

Because an anti-alias filter limits bandwidth, it may also reduce integrated
wideband noise reaching the ADC.

---

# The Original SP-1200 Context

The original SP-1200 uses an analog anti-alias filter before its
sample-and-hold and successive-approximation conversion circuitry.

The filter was part of the complete sampling architecture rather than an
independent creative effect.

Its behaviour must be studied from:

- the service-manual theory section,
- the sampling schematic,
- the component values,
- the active-device characteristics,
- measured frequency and phase response.

Project SP will not assume that the original filter alone creates the
recognizable SP sound.

Its contribution must be isolated and evaluated alongside:

- sample rate,
- quantization,
- sample-and-hold behaviour,
- ADC nonlinearities,
- pitch engine,
- playback DAC,
- reconstruction filters.

---

# Project SP Implementation Strategies

Several implementation strategies are possible.

---

## Strategy A — Modern High-Rate ADC with Digital Emulation

```text
Analog Input
    │
    ▼
Modern Anti-Alias Filter
    │
    ▼
High-Rate ADC
    │
    ▼
Digital SP Filter Model
    │
    ▼
26.04 kHz Processing Domain
```

Advantages:

- safe and measurable acquisition,
- original filter behaviour can be switched on and off,
- easy A/B testing,
- filter models can be revised without changing hardware.

Disadvantages:

- does not reproduce every analog nonlinearity automatically,
- requires a validated digital model,
- high-rate conversion path must remain transparent.

---

## Strategy B — Analog SP-Inspired Filter Before Conversion

```text
Analog Input
    │
    ▼
SP-Inspired Analog Anti-Alias Filter
    │
    ▼
ADC
```

Advantages:

- physical analog response,
- natural component tolerances and noise,
- direct experimental relationship to the original architecture.

Disadvantages:

- harder to switch or modify,
- component tolerances complicate repeatability,
- exact original behaviour requires accurate reverse engineering,
- aliases cannot be removed after conversion.

---

## Strategy C — Switchable Dual Path

```text
                  ┌── Transparent Path ──────┐
Analog Input ─────┤                          ├── ADC
                  └── SP-Inspired Filter ────┘
```

Advantages:

- direct A/B comparison,
- supports educational laboratory use,
- separates transparent acquisition from character experiments.

Disadvantages:

- more hardware,
- switching circuitry may introduce its own effects,
- layout and routing become more complex.

---

# Proposed Development Method

The anti-alias filter should be developed in stages.

## Stage 1 — Define the Conversion Architecture

Determine:

- actual hardware ADC,
- native ADC sampling frequency,
- internal codec filtering,
- intended Project SP processing rate,
- analog input range.

## Stage 2 — Extract the Original SP Circuit

From the service manual:

- identify the filter topology,
- record all resistor values,
- record all capacitor values,
- identify op-amps and analog switches,
- determine the number of poles,
- trace the signal path to the sample-and-hold stage.

## Stage 3 — Derive the Transfer Function

Calculate or simulate:

- pole frequencies,
- section Q values,
- total magnitude response,
- phase response,
- group delay,
- step response.

## Stage 4 — Build a Reference Model

Create:

- SPICE model,
- numerical transfer-function model,
- ideal mathematical model,
- tolerance analysis.

## Stage 5 — Prototype

Construct the filter using:

- selected op-amp,
- precision resistors,
- stable capacitors,
- test points between sections.

## Stage 6 — Measure

Measure:

- frequency response,
- phase response,
- output noise,
- maximum signal level,
- step response,
- square-wave response,
- alias rejection.

## Stage 7 — Listening Evaluation

Compare:

- transparent input path,
- original-style filter,
- ideal digital low-pass,
- deliberate under-filtering.

---

# Measurement Plan

## Frequency Response

Use a swept sine wave to measure:

- passband flatness,
- −3 dB point,
- transition band,
- stopband attenuation.

## Phase Response

Measure the phase difference between input and output across frequency.

## Step Response

Apply a controlled square-wave or step-like signal and observe:

- rise time,
- overshoot,
- settling,
- ringing.

## Noise

Terminate the input with the intended source impedance and measure:

- RMS noise,
- FFT noise spectrum,
- mains components,
- switching-power-supply components.

## Alias Rejection

Apply sine waves above the Project SP Nyquist frequency and measure the
resulting aliases after conversion.

Test frequencies may include:

- 13 kHz,
- 14 kHz,
- 15 kHz,
- 18 kHz,
- 20 kHz,
- 25 kHz.

For each input frequency, record:

- input amplitude,
- expected alias frequency,
- measured alias frequency,
- alias amplitude,
- calculated attenuation.

---

# Engineering Questions

The following questions remain open:

- Will Project SP sample directly at 26.04 kHz?
- Will the Daisy Seed codec operate at a higher native sample rate?
- Does the Seed 3 audio hardware include internal anti-alias filtering?
- Will the original SP filter be implemented in analog hardware, DSP, or
  both?
- What usable passband should be preserved?
- What stopband attenuation is required?
- What filter order is appropriate?
- Should the response prioritize amplitude flatness or transient behaviour?
- How closely should the original SP phase response be reproduced?
- Should aliasing be prevented completely or made deliberately adjustable?
- How will the analog path be bypassed for A/B testing?
- Which component tolerances are acceptable?

---

# Project SP Design Decision

## Current Status

🟡 Architecture Under Investigation

## Confirmed Principle

Project SP will treat anti-alias filtering as part of the complete sampling
system rather than as an isolated effect.

The final implementation will be based on:

- the native ADC architecture,
- the selected sampling-rate strategy,
- analysis of the original SP-1200 circuit,
- simulation,
- laboratory measurements,
- controlled listening comparisons.

## Current Direction

The preferred research direction is a high-quality acquisition path combined
with a separately modelled or switchable SP-inspired anti-alias response.

This would allow the contribution of the filter to be evaluated independently
from:

- bit depth,
- sampling rate,
- ADC behaviour,
- pitch processing,
- DAC reconstruction.

No final filter order, topology, cutoff frequency or component values have
yet been selected.

## Design Rationale

Selecting component values before the ADC architecture and target response
are known would be premature.

The filter must be designed from measurable requirements rather than from a
single nominal cutoff frequency.

## Future Validation

The final design will be validated through:

- transfer-function calculation,
- SPICE simulation,
- component-tolerance analysis,
- frequency-response measurement,
- phase and group-delay measurement,
- step-response analysis,
- alias-rejection testing,
- noise measurement,
- listening tests.

---

# References

- E-mu SP-1200 Service Manual
- OPA2134 Datasheet
- Selected ADC or audio-codec datasheet
- Analog Devices filter design application notes
- Texas Instruments active-filter design application notes
- Douglas Self — Small Signal Audio Design
- Relevant Project SP measurement files