Below is a **theory-tight synthesis** of the passage you shared, focused on **multileveled tonal function, secondary systems, and embellishing vs passing tonics**, with **Python formalizations throughout**. I keep the language aligned with the author’s framework and avoid reducing it to chord-label shorthand.



---

## 1. Tonics as Reductive Objects (Not Sounding Lines)

The author draws a crucial methodological distinction:

- **Tonics can be represented reductively** (like structural/auxiliary harmonies or pitches)
- **But** a *stream of tonics* is **not** a sounding melodic line
- It is a **hierarchic, analytical construct**

This parallels Schenkerian reduction, but the objects are **tonal centers**, not notes.

### Python: Non-sounding Tonic Stream

```python
class TonicEvent:
    def __init__(self, tonic, level, function):
        self.tonic = tonic
        self.level = level          # foreground / middleground / background
        self.function = function    # primary, secondary, passing, embellishing

    def __repr__(self):
        return f"{self.tonic} ({self.function}, {self.level})"

tonic_stream = [
    TonicEvent("C", "background", "primary"),
    TonicEvent("G", "foreground", "secondary"),
    TonicEvent("C", "background", "primary"),
]

tonic_stream
```

This explicitly enforces:
> *“A stream of tonics … can in no sense be interpreted as a sounding line.”*

---

## 2. Structural Level Governs Tonal Meaning

A tonic’s **structural level** determines its **authority**:

- **Primary tonic** → first-order, always governing
- **Secondary tonic** → may be structural *locally*
- **Departure tonic** → subordinate if return is expected

Thus:
- A tonic can be **structural at a low level**
- Yet **submissive** at a higher level

### Python: Level-Sensitive Authority

```python
def tonic_authority(tonic, level):
    hierarchy = {"background": 3, "middleground": 2, "foreground": 1}
    return hierarchy[level]

tonic_authority("F", "foreground"), tonic_authority("C", "background")
```

This encodes:
> *“Low-level predominance does not imply structural supremacy.”*

---

## 3. Multileveled Tonal-Harmonic Function

The core concept introduced:

> **Multileveled tonal-harmonic function**

A single harmonic or melodic event can carry:
- **Immediate function** (local tonic)
- **Secondary function** (system component)
- **Ultimate function** (relation to primary tonic)

This is **ambivalence**, not ambiguity.

### Python: Multiple Functions per Event

```python
class HarmonicEvent:
    def __init__(self, label):
        self.label = label
        self.functions = {}

    def add_function(self, level, tonic, role):
        self.functions[level] = (tonic, role)

event = HarmonicEvent("C major triad")
event.add_function("foreground", "G", "subdominant")
event.add_function("background", "C", "tonic")

event.functions
```

This mirrors:
> *“The ‘true’ interpretation … is often one of numerous terms.”*

---

## 4. Schoenberg’s Monotonality and Hierarchic Components

If a work has **one primary system** (Schoenberg’s *monotonality*), then:

- All secondary systems are **hierarchically ordered**
- Their emergence is **stylistically predictable**
  - Dominant
  - Relative
  - Fifth- or third-related centers
- But their **particular deployment** defines the work’s character

### Python: Hierarchic System Components

```python
tonal_system = {
    "primary": "C",
    "secondary": ["G", "F"],
    "parenthetical": ["Bb"]
}

tonal_system
```

---

## 5. Secondary Tonics and Triadic Eligibility

Only **major and minor triads** can serve as **secondary tonics**.

Thus:
- vii° → must be altered to major/minor to tonicize
- III+ → must be respelled/altered
- Diminished & augmented triads **cannot** be tonic centers

### Python: Tonic Eligibility Rule

```python
def tonic_capable(triad_quality):
    return triad_quality in {"major", "minor"}

tonic_capable("diminished"), tonic_capable("major")
```

---

## 6. The Leading-Tone as Systemic Force

A decisive historical claim:

> Major-minor tonality evolved primarily through **leading-tone inflection**

Consequences:
- Minor mode relies on **harmonic form**
- Tonicization of **R/t (relative major of minor)** is *more disruptive*
- Dominant fluctuation is **less disruptive** because it preserves the leading-tone

### Python: Disruption Metric

```python
def disruption(target_relation):
    if target_relation == "R/t":
        return "high"
    if target_relation in {"D/T", "D/t"}:
        return "low"
    return "medium"

disruption("R/t"), disruption("D/T")
```

---

## 7. Dominant Function: Structural Definition

A chord has **dominant function** if it implies:

1. A **leading-tone**
2. A **root a fifth above** the affiliate tonic

Thus:
- vii° and V are functionally interchangeable
- III* and cadential 6⁴ are **dependent dominants**
- Diminished 7th is privileged for its versatility

### Python: Dominant Detection

```python
def is_dominant(contains_leading_tone, fifth_relation):
    return contains_leading_tone and fifth_relation

is_dominant(True, True)
```

---

## 8. Beethoven, Waldstein (Op. 53): Symmetrical Embellishment

[Piano Sonata No. 21 in C major, Op. 53](chatgpt://generic-entity?number=0)

In Ex. 1-12:

- **C** = primary system
- **G** and **F** = secondary systems
- They **symmetrically neighbor** C
- Each is prepared by a **secondary IV**
- Bass descends chromatically to **C:V7**

Crucial insight:
- G is **passing at one level**
- **Neighboring/encircling** at a broader level
- Ultimately **embellishing C**

### Python: Symmetric Secondary Systems

```python
secondary_systems = [
    {"tonic": "G", "role": "embellishing"},
    {"tonic": "F", "role": "embellishing"}
]

secondary_systems
```

---

## 9. Classes of Secondary Tonal Systems

Two principal classes:

1. **Embellishing secondary systems**
   - Return to primary tonic
2. **Passing / transitional secondary systems**
   - Link distant regions

Plus:
- **Parenthetical systems**
  - Weakly present
  - Structurally informative
  - Perceptually negligible

### Python: System Classification

```python
def system_class(system):
    if system == "parenthetical":
        return "structural_hint"
    if system == "passing":
        return "connective"
    return "embellishing"

system_class("parenthetical")
```

---

## 10. Chromatic Bass as Tonal Engine

In Beethoven and Liszt alike:
- **Chromatic bass descent**
- Links I → V
- Conditions extreme fluctuation
- Makes return inevitable

[Transcendental Études No. 3](chatgpt://generic-entity?number=1)

### Python: Chromatic Descent Model

```python
bass_descent = ["C", "B", "Bb", "A", "Ab", "G"]
bass_descent
```

---

## 11. Broad Formal Principle (Late Tonal Music)

Later tonal music often:
- Begins with **violent fluctuation**
- Stabilizes **late**
- Can be graphed as:
  - early instability
  - final convergence

This is a **form-shaping principle**, not a surface effect.

### Python: Tonal Stability Curve

```python
stability_curve = {
    "opening": "unstable",
    "middle": "fluctuating",
    "ending": "focused"
}

stability_curve
```

---

## 12. Core Takeaways (Compressed)

| Concept | Meaning |
|---|---|
| Tonic stream | Analytical, not sonic |
| Structural level | Determines authority |
| Multileveled function | Ambivalent, not ambiguous |
| Secondary systems | Embellishing or passing |
| Parenthetical systems | Structurally informative |
| Leading-tone | Expansion engine |
| Chromatic bass | Tonal inevitability |
| Late tonal form | Fluctuate → converge |

---

If you want next, I can:

- Encode **Ex. 1-12 fully** as a multilevel tonal graph  
- Formalize **tonal distance metrics**  
- Build a **tonic-stream reduction algorithm**  
- Apply this to **Wolf, Liszt, or Brahms**  
- Translate this system into **MIDI-driven analysis**

Just say the direction.