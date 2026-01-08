Below is a **complete, publication-ready `README.md`** for **Structural Functions in Music (SFIM)**, written as a **theoretical + computational research project**, with **explicit Python examples** embedded throughout.

You can paste this directly into `/Users/x86/SFIM/README.md`.

---

# Structural Functions in Music (SFIM)

**Structural Functions in Music (SFIM)** is a research-driven theoretical and computational framework for analyzing **rhythm, meter, accent, and hierarchical structure** in music beyond the limitations of notated bar-lines and regular metric grids.

SFIM treats meter as a **dynamic, multilevel system of functional impulses**—initiative, anticipative, reactive, and conclusive—operating across time at multiple structural depths.

This project unifies **advanced music theory** with **formal modeling and algorithmic analysis**, enabling reproducible, machine-assisted study of real metric structure.

---

## Core Premise

> **Meter is not regularity.**  
> Meter is the functional organization of **accent-delineated grouping**, often **irregular, fluctuant, polymetric, and noncongruent** with notation.

SFIM focuses on **real meter**, not notated meter.

---

## Key Concepts

### 1. Impulse Functions

Every musical event (including silence) may function as one or more of the following:

| Function | Description |
|--------|-------------|
| **Initiative (I)** | Begins a metric unit (structural “downbeat”) |
| **Anticipative (A)** | Weak impulse leading toward an initiative |
| **Reactive (R)** | Absorbs and carries initiative energy |
| **Conclusive (C)** | Ends a unit; metrically weak |

Impulses may have **dual or multiple functions**, even at the same structural level.

---

### 2. Metric Levels

Metric structure exists simultaneously at many levels:

- Intramensural (sub-beat)
- Mensural (notated bar)
- Intermensural (hypermetric)
- Phrase
- Period
- Formal divisions
- Entire work

A **higher-level impulse** subsumes lower-level impulses across time.

---

### 3. Symmetry vs Fluctuation

| Term | Meaning |
|----|--------|
| **Congruity** | Symmetrical, stable metric relations |
| **Noncongruity** | Asymmetrical or irregular relations |
| **Horizontal noncongruity** | Asymmetry between successive units |
| **Vertical noncongruity** | Polymeter across voices |
| **Metric dissonance** | Persistent noncongruity |
| **Metric resolution** | Restoration of congruity |

---

### 4. Preconditioning

Previously established metric patterns **shape perception of later events**.

Key analytical question:
> Is a conflicting accent a **true metric shift** or **syncopation against a preconditioned meter**?

This distinction is **contextual**, not absolute.

---

### 5. Metric Progression and Recession

Metric structure undergoes **directional processes**:

#### Progressive (Accelerative)
- Smaller units
- Increased asymmetry
- Polymeter
- Instability
- Rising intensity

#### Recessive (Decelerative)
- Larger units
- Increased symmetry
- Homometer
- Stability
- Cadential closure

Metric change itself has **rhythm**.

---

## Computational Modeling Philosophy

SFIM is designed to be:

- **Level-aware**
- **Context-sensitive**
- **Non-grid-based**
- **Process-oriented**
- **Algorithmically reproducible**

The goal is not beat tracking, but **structural inference**.

---

## Python Examples

### Representing Metric Impulses

```python
from dataclasses import dataclass
from enum import Enum

class ImpulseFunction(Enum):
    INITIATIVE = "I"
    ANTICIPATIVE = "A"
    REACTIVE = "R"
    CONCLUSIVE = "C"

@dataclass
class Impulse:
    onset: float
    duration: float
    pitch: float | None
    intensity: float
    function: set[ImpulseFunction]
    level: str
```

---

### Metric Units at a Given Level

```python
@dataclass
class MetricUnit:
    impulses: list[Impulse]
    level: str

    def initiative(self):
        return [i for i in self.impulses if ImpulseFunction.INITIATIVE in i.function]
```

---

### Measuring Horizontal Metric Fluctuation

```python
def horizontal_fluctuation(units):
    durations = [sum(i.duration for i in u.impulses) for u in units]
    mean = sum(durations) / len(durations)
    return sum((d - mean) ** 2 for d in durations) / len(durations)
```

Higher values indicate greater **horizontal noncongruity**.

---

### Detecting Metric Progression vs Recession

```python
def metric_process(units):
    sizes = [sum(i.duration for i in u.impulses) for u in units]
    deltas = [sizes[i+1] - sizes[i] for i in range(len(sizes)-1)]

    avg = sum(deltas) / len(deltas)

    if avg < 0:
        return "progressive (contractive)"
    elif avg > 0:
        return "recessive (expansive)"
    else:
        return "stable"
```

---

### Modeling Metric Rhythm

```python
def metric_rhythm(units):
    return [
        sum(units[i+1].impulses[j].duration
            for j in range(len(units[i+1].impulses)))
        -
        sum(units[i].impulses[j].duration
            for j in range(len(units[i].impulses)))
        for i in range(len(units)-1)
    ]
```

Metric rhythm is the **pattern of change in metric relations**, not pulse.

---

### Blacher-Style Variable Meter

```python
def variable_meter_series(series):
    units = []
    for size in series:
        units.append(size)
    return units

# Fibonacci-based metric progression
series = [3, 5, 8, 13, 21]
print(variable_meter_series(series))
```

---

## Applications

SFIM is applicable to:

- Classical and Romantic hypermeter
- Renaissance polyphony
- 20th-century polymeter
- Atonal and post-tonal music
- Free rhythm, chant, recitative
- Algorithmic composition
- Performance analysis
- Music-theory AI systems

---

## Design Principles

- **No equation of meter with regularity**
- **No assumption of bar-line primacy**
- **No single dominant structural level**
- **Accent is contextual**
- **Fluctuation is expressive**
- **Analysis is inferential, not absolute**

---

## Project Status

SFIM is an **ongoing research framework** intended for:

- theoretical expansion
- computational experimentation
- integration with symbolic music formats (MIDI, MusicXML)
- generative systems
- machine listening research

---

## License

MIT License (or specify otherwise)

---

## Author / Project

**Structural Functions in Music (SFIM)**  
A research framework for **multilevel metric structure**

---

If you want next:
- a **formal API spec**
- a **theory → code mapping table**
- a **notation-free analysis pipeline**
- or a **SFIM-based generative engine**

say the word.