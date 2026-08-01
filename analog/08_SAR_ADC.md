# Successive Approximation Register (SAR) ADC

> Teaching hardware how to think in binary.

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

Sample and Hold

↓

ADC Introduction

↓

**▶ Successive Approximation Register (SAR) ◀**

↓

Quantization

↓

Digital Processing

↓

Memory

↓

DAC

↓

Output Stage

---

# Purpose

The Successive Approximation Register (SAR) Analog-to-Digital Converter is one of the most elegant methods ever developed for converting an analog voltage into a digital number. Instead of comparing every possible voltage level, a SAR ADC determines the correct digital value through a sequence of binary decisions. Each conversion answers one simple question at a time:

"Is the input voltage higher or lower than the current estimate?"

After a fixed number of decisions, the converter produces the final binary result.

---

# Why SAR?

Many ADC architectures exist.

Some prioritize speed.

Others prioritize resolution.

Others prioritize extremely low noise.

The original E-mu SP-1200 uses a Successive Approximation Register conversion architecture.

Understanding SAR conversion is therefore essential for understanding the sampling process used by the original instrument.

---

# The Main Idea

Imagine guessing a number between 0 and 4095.

Instead of testing every possible value one after another:

1
2
3
4
...

the converter always asks about the middle value.

If the answer is "higher"

↓

Search the upper half.

If the answer is "lower"

↓

Search the lower half.

This process is called binary search.

A SAR ADC performs exactly this operation in hardware.

---

# Internal Building Blocks

A typical SAR ADC consists of five major blocks.

Sample and Hold

↓

Comparator

↓

DAC

↓

Successive Approximation Register

↓

Control Logic

Each block performs one specific task.

---

# Sample and Hold

The Sample and Hold stage freezes the analog voltage. The converter now sees a constant voltage throughout the entire conversion. Without this stage, the input voltage could change before conversion finishes.

---

# Comparator

The comparator is the decision maker.

It answers only one question:

Is VIN greater than VDAC ?

If YES

↓

Output = HIGH

If NO

↓

Output = LOW

Every conversion consists of multiple comparator decisions.

---

# Internal DAC

The converter contains its own Digital-to-Analog Converter. The DAC generates a reference voltage corresponding to the current binary estimate. This voltage is continuously compared against the sampled input.

**The SAR algorithm repeatedly adjusts this estimate until both voltages match as closely as possible.**

---

# Successive Approximation Register

The SAR register stores the current binary guess.

Initially:

000000000000

The most significant bit is tested first.
Then the next bit.
Then the next.
Each decision is permanently stored before moving to the next bit.

---

# Binary Search

Instead of testing every possible level:

0

1

2

3

...

4095

the SAR converter reduces the search space by half after every comparison.

For a 12-bit converter:

4096 possible values

↓

12 comparisons

The conversion always requires exactly one comparison per bit.

---

# Example Conversion

Suppose:

Reference Voltage

5 V

Measured Voltage

3.10 V

The converter begins.

---

## Step 1

Test MSB

100000000000

DAC Output

2.50 V

Comparator

3.10 V > 2.50 V

YES

Keep the bit.

---

## Step 2

Test second bit.

110000000000

DAC Output

3.75 V

Comparator

3.10 V < 3.75 V

NO

Clear the bit.

Current value

100000000000

---

## Step 3

Next bit.

101000000000

DAC Output

3.125 V

Comparator

3.10 V < 3.125 V

NO

Clear the bit.

---

The process continues until every bit has been tested.

The final binary number represents the closest available digital approximation.

---

# Why "Successive Approximation"?

Every decision improves the previous estimate.

The converter never starts over.

It continuously refines the approximation.

Each comparison reduces the remaining uncertainty by half.

---

# Conversion Time

One comparison is required per bit.

For an N-bit converter:

Conversion Time

≈

N Comparator Cycles

Example

12-bit

↓

12 comparisons

16-bit

↓

16 comparisons

Unlike some other ADC architectures, SAR conversion time is fixed and predictable.

---

# Resolution

Resolution determines how many voltage levels the converter can distinguish.

Number of Levels

2^N

Examples

8-bit

256

10-bit

1024

12-bit

4096

16-bit

65536

Increasing resolution reduces quantization step size.

---

# Advantages

SAR ADCs provide:

- Excellent accuracy
- Deterministic conversion time
- Moderate power consumption
- Good audio performance
- Simple timing
- Excellent medium-speed operation

These characteristics explain why SAR converters became popular in digital audio equipment.

---

# Limitations

Compared to other ADC architectures:

- Requires accurate internal DAC
- Comparator offset influences accuracy
- Limited maximum conversion speed compared to Flash ADCs
- Conversion cannot tolerate changing input voltage

These limitations explain why Sample and Hold is essential.

---

# SAR and Project SP

Project SP studies the SAR conversion process because it represents one of the defining characteristics of the original SP-1200 sampling architecture.

Rather than treating the ADC as a black box, Project SP analyses every individual decision involved in the conversion process.

Understanding the binary search performed by the converter provides valuable insight into how analog voltages become digital audio samples.

---

# Future Documents

09_Quantization.md

10_Dither.md

11_Sampling_Rate.md

12_Clock_and_Jitter.md

---

# Project SP Design Decision

## Current Status

🟢 Architecture Understood

## Current Concept

Project SP adopts the Successive Approximation Register conversion model as the primary reference architecture for studying vintage sampler behaviour.

## Design Rationale

The SAR converter offers an intuitive and deterministic conversion process based entirely on binary decisions.

Studying this architecture provides the necessary foundation for understanding quantization, conversion accuracy and the behaviour of the original SP-1200.

## Future Validation

The complete SAR conversion process will later be validated through:

- Mathematical analysis
- Timing diagrams
- Laboratory measurements
- Comparator behaviour
- DAC analysis
- Binary conversion examples
- Comparison with the original SP-1200 implementation