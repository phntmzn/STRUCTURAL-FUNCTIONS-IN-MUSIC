Below is a **high-level theoretical consolidation** of the topics you list, organized as a **single analytical framework**, and paired throughout with **Python examples** that show how these ideas can be **formalized, measured, and simulated** for analysis or composition.

This section sits **above local harmony** and **below full formal analysis**: it is about how *tonal systems relate to each other in motion*.

---

# Tonal Intersection, Direction, Distance, and High-Level Chromatic Fluctuation  
*(with Computational Models)*

---

## 1. Tonal Intersection  
**What it is:**  
Tonal intersection occurs when **two tonal systems share pitch-class content, functional tendencies, or cadential logic**, allowing one system to *emerge from inside* another rather than replacing it abruptly.

### Types of Tonal Intersection
- **PC intersection** (shared pitch classes)
- **Functional intersection** (shared dominant/subdominant behavior)
- **Cadential intersection** (cadence interpretable in multiple systems)
- **Voice-leading intersection** (semitonal or stepwise pivots)

> Tonal intersection is the *mechanism* that makes tonal fluctuation perceptible rather than arbitrary.

### Python: pitch-class intersection

```python
def tonal_intersection(system_a, system_b):
    return set(system_a) & set(system_b)

C_major = {"C","D","E","F","G","A","B"}
G_major = {"G","A","B","C","D","E","F#"}

tonal_intersection(C_major, G_major)
```

---

## 2. Direction of Tonal Motion  
**Direction** is not “up” or “down” in pitch, but **toward or away from stability**.

### Primary Tonal Directions
- **Progressive**: away from tonic (↑ tension)
- **Recessive**: toward tonic (↓ tension)
- **Encircling**: symmetric motion around tonic
- **Passing**: tonic-to-tonic linkage
- **Inflating**: tonic → secondary tonic → return

> Direction is defined by *function*, not chord labels.

### Python: classify tonal direction

```python
def tonal_direction(from_tonic, to_tonic, primary):
    if to_tonic == primary:
        return "recessive"
    elif from_tonic == primary:
        return "progressive"
    else:
        return "passing"

tonal_direction("C", "G", "C")
```

---

## 3. Tonal Distance  
**Distance** is not intervallic size alone. It is **functional distance**.

### Determinants of Tonal Distance
1. Number of diatonic alterations required
2. Loss or cancellation of the primary leading-tone
3. Mode disruption (major ↔ minor)
4. Removal from dominant–tonic axis
5. Cadential plausibility

> The dominant is often *closer* than the relative major, despite fewer accidentals in the latter.

### Python: functional distance heuristic

```python
def tonal_distance(alterations, cancels_leading_tone, mode_shift):
    distance = alterations
    if cancels_leading_tone:
        distance += 2
    if mode_shift:
        distance += 1
    return distance

# C → G
tonal_distance(alterations=1, cancels_leading_tone=False, mode_shift=False)

# C → Eb
tonal_distance(alterations=3, cancels_leading_tone=True, mode_shift=True)
```

---

## 4. Intervals of Tonal Fluctuation  
These are **successive tonic references**, not melodic intervals.

### Common Fluctuation Intervals
- **Perfect 5th** → dominant expansion
- **Minor 3rd** → relative exchange
- **Major 3rd** → chromatic mediant
- **Semitone** → Neapolitan / leading-tone drift
- **Tritone** → high instability, ambiguous polarity

### Python: classify fluctuation interval

```python
def fluctuation_interval(semitones):
    mapping = {
        1: "semitonal (leading / Neapolitan)",
        3: "relative / chromatic mediant",
        5: "dominant axis",
        6: "tritone instability",
        7: "subdominant axis"
    }
    return mapping.get(semitones % 12, "remote")

fluctuation_interval(7)
```

---

## 5. High-Level Chromatic Successions  
These are **tonal motions that cannot be explained diatonically**, even locally.

### Characteristics
- Successions of *tonics*, not chords
- Often justified by:
  - enharmonic reinterpretation
  - voice-leading continuity
  - symmetrical interval cycles
- Typical of late-Romantic and 20th-century tonality

> Chromatic successions operate at the **system level**, not the harmonic level.

### Python: chromatic tonic chain

```python
def chromatic_chain(start, steps):
    pc = ["C","C#","D","Eb","E","F","F#","G","Ab","A","Bb","B"]
    i = pc.index(start)
    return [pc[(i + step) % 12] for step in steps]

chromatic_chain("C", [0, 3, 6, 9])
```

---

## 6. Nondiatonic Tonics  
A nondiatonic tonic:
- Is **not part of the primary scale**
- Gains legitimacy via **functional preparation**
- Often appears as:
  - Neapolitan
  - Chromatic mediant
  - Altered dominant resolution
  - Modal borrowing pivot

> Nondiatonic ≠ nonfunctional.

### Python: detect nondiatonic tonic

```python
def is_nondiatonic(tonic, scale):
    return tonic not in scale

is_nondiatonic("Eb", C_major)
```

---

## 7. Interchangeability of Modes  
Modes are interchangeable when:
- **Function remains intact**
- Leading-tone pressure is preserved or compensated
- Voice-leading sustains expectation

Examples:
- C major ↔ C minor
- Dorian ↔ Aeolian
- Harmonic minor ↔ melodic minor

> Mode is often **surface color**, not system identity.

### Python: parallel mode exchange

```python
def parallel_modes(tonic):
    return {
        "major": f"{tonic} major",
        "minor": f"{tonic} minor"
    }

parallel_modes("C")
```

---

## 8. Equivalence of Parallel Tonics  
Parallel tonics (C major / C minor) are **structurally equivalent** at high levels.

They share:
- tonic identity
- cadential gravity
- registral focus
- formal closure capacity

They differ in:
- color
- degree of tension
- leading-tone treatment

> Parallel tonics differ **qualitatively**, not **hierarchically**.

### Python: treat parallel tonics as equivalent nodes

```python
def tonic_equivalence(tonic_a, tonic_b):
    return tonic_a[0] == tonic_b[0]

tonic_equivalence("C major", "C minor")
```

---

## 9. Integrated Model: Tonal Motion as Vector Space

We can model tonal motion as a **vector with direction and magnitude**:

- **Direction** → progressive / recessive
- **Magnitude** → tonal distance
- **Axis** → dominant, relative, chromatic, modal

### Python: tonal motion object

```python
class TonalMotion:
    def __init__(self, from_tonic, to_tonic, distance, direction):
        self.from_tonic = from_tonic
        self.to_tonic = to_tonic
        self.distance = distance
        self.direction = direction

    def describe(self):
        return f"{self.from_tonic} → {self.to_tonic} ({self.direction}, dist={self.distance})"

motion = TonalMotion("C", "G", 1, "progressive")
motion.describe()
```

---

## 10. Core Synthesis (Conceptual)

- **Tonal intersection** enables perceptibility  
- **Direction** defines expressive trajectory  
- **Distance** defines tension magnitude  
- **Chromatic successions** operate at system level  
- **Nondiatonic tonics** require justification, not apology  
- **Modes are interchangeable** when function persists  
- **Parallel tonics are equivalent centers**, not rivals  

Together, these principles define **tonal fluctuation as a controlled, hierarchical, directional process**, not as arbitrary modulation.

---

### If you want next:
- a **formal metric for tonal distance**
- a **graph-based tonal space**
- a **Python engine that tracks tonal rhythm over time**
- or a **full applied analysis** (Mozart, Brahms, Debussy, Berg, Webern)

say the word and specify the repertoire or computational depth.