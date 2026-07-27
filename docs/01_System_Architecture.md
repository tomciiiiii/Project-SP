# System Architecture

## Overview

Project SP is divided into two independent signal paths:

1. Recording Path
2. Playback Path

Treating them separately allows each stage to be studied, measured and implemented independently.

---

# Recording Path

```
Analog Input
    │
    ▼
Input Interface
    │
    ▼
Variable Gain Stage
    │
    ▼
Anti-Alias Filter
    │
    ▼
Sample & Hold
    │
    ▼
ADC
    │
    ▼
Sample Memory
```

The recording path defines how audio enters the system.

Every stage introduces its own characteristics that contribute to the final sound.

---

# Playback Path

```
Sample Memory
    │
    ▼
Pitch Engine
    │
    ▼
DAC
    │
    ▼
Reconstruction Filter
    │
    ▼
Output Amplifier
    │
    ▼
Line Output
```

The playback path determines how stored samples are reconstructed into analog audio.

---

# Engineering Principle

Each block must answer three questions:

- What does it do?
- Why does it exist?
- How much does it affect the sound?

---

# Project Philosophy

Understanding before implementation.

Every component should have an engineering reason.

Whenever possible, design decisions will be supported by:

- calculations
- measurements
- listening tests
- datasheets
- service manuals
## Research Questions

- Which stages define the recording character?
- Which stages define the playback character?
- Which behaviours should be reproduced in analog hardware?
- Which behaviours should be implemented in DSP?
- Which stages should be switchable for comparison?
