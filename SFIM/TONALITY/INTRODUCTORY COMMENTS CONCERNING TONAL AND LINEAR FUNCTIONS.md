Below is a **structured explanation of the passage** you shared, framed in **music-theoretic terms** and paired with **Python examples** that *formalize* the ideas (as requested). The Python is not “sound-producing” but **analytical / structural**, modeling **tonal vs linear function**, **neighbor vs passing**, and **multi-level hierarchy**.

---

## 1. Two Kinds of Musical Function (Core Thesis)

The text defines **two simultaneous, non-exclusive kinds of function** in tonal music:

### A. **Tonal Function**
- Concerned with **position, identity, and hierarchy** inside a tonal system  
- Examples: **Tonic (I), Dominant (V), Subdominant (IV)**  
- Exists at **multiple levels** (global key vs local tonicization)

### B. **Linear Function**
- Concerned with **how events behave in time**
- Whether a harmony or pitch is:
  - **Structural (essential)**
  - **Auxiliary** (neighbor, passing, embellishing, prolonging)
- Also **hierarchical** and **multi-leveled**

**Key claim:**  
> Tonal and linear functions are *complementary*, not contradictory.

---

## 2. Linear Function Types: Neighbor vs Passing

### Neighbor Auxiliary
- Decorates a **single structural event**
- Returns to the same harmony or pitch
- Often stepwise

### Passing Auxiliary
- Connects **two distinct structural events**
- Fills a larger interval (3rd or more)
- Produces directional motion

### Python Model: Linear Function Classification

```python
from enum import Enum

class LinearFunction(Enum):
    STRUCTURAL = "structural"
    NEIGHBOR = "neighbor"
    PASSING = "passing"
    PROLONGATION = "prolongation"

class Event:
    def __init__(self, pitch, harmony, level, linear_function):
        self.pitch = pitch
        self.harmony = harmony
        self.level = level
        self.linear_function = linear_function

    def __repr__(self):
        return f"{self.pitch} | {self.harmony} | L{self.level} | {self.linear_function.value}"

# Example: neighbor configuration
events = [
    Event("G", "V", 1, LinearFunction.STRUCTURAL),
    Event("A", "V6", 1, LinearFunction.NEIGHBOR),
    Event("G", "V", 1, LinearFunction.STRUCTURAL)
]

for e in events:
    print(e)
```

This mirrors the text’s idea:
> “Often a neighbor separates two appearances of the structural harmony it elaborates.”

---

## 3. Multilevel Linear & Tonal Function

An event can be:
- **Essential at one level**
- **Auxiliary at another**

Example from the text:
- A **V cadence** is structurally essential at the **phrase level**
- But auxiliary relative to a larger **I → I** motion

### Python: Hierarchical Function Graph

```python
class HierarchicalEvent:
    def __init__(self, name):
        self.name = name
        self.functions = {}  # level → function

    def set_function(self, level, function):
        self.functions[level] = function

    def describe(self):
        return {
            "event": self.name,
            "functions_by_level": self.functions
        }

cadence_V = HierarchicalEvent("V cadence")
cadence_V.set_function("phrase", "structural")
cadence_V.set_function("period", "auxiliary")

print(cadence_V.describe())
```

This **directly encodes**:
> “An event may be auxiliary at a broad level, essential at a more immediate level.”

---

## 4. Tonal vs Linear: Beethoven Example



In **[Beethoven Symphony No. 2](chatgpt://generic-entity?number=0)**:
- **iv → V** is the *essential harmonic motion*
- Chromatic ascent creates a **strong linear force**
- Yet **tonal function remains perceptible**
- Local tonicizations: iv/iv, V, etc.

### Python: Tonal + Linear Coexistence

```python
class HarmonyEvent:
    def __init__(self, rn, tonal_level, linear_role):
        self.rn = rn
        self.tonal_level = tonal_level
        self.linear_role = linear_role

sequence = [
    HarmonyEvent("iv", "primary", "structural"),
    HarmonyEvent("iv°7", "secondary", "passing"),
    HarmonyEvent("V", "primary", "structural"),
]

for h in sequence:
    print(h.rn, h.tonal_level, h.linear_role)
```

This models the claim:
> Harmonic successions can be linear **space-filling streams** while still retaining tonal meaning.

---

## 5. When Tonal Function Breaks Down: Chopin



In Chopin:
- Chains of **parallel diminished 7ths**
- Avoid resolution, tonicization, or leading-tone fulfillment
- Linear function **overpowers tonal inference**

### Python: Tonal Suppression Detection

```python
def tonal_function_active(chords):
    for c in chords:
        if "V" in c or "I" in c:
            return True
    return False

chopin_stream = ["°7", "°7", "°7", "°7"]

print("Tonal function present?", tonal_function_active(chopin_stream))
```

This encodes:
> “At some point tonal function is superseded by straight linear function.”

---

## 6. Key Analytical Outcome

The passage argues:

| Dimension | Tonal Function | Linear Function |
|--------|---------------|----------------|
| Domain | Harmonic identity | Temporal behavior |
| Hierarchy | Multilevel | Multilevel |
| Can coexist? | Yes | Yes |
| Can dominate? | Sometimes | Sometimes |

### Python Summary Object

```python
analysis_summary = {
    "tonal_function": {
        "hierarchical": True,
        "foreground_present": True,
        "can_be_suspended": True
    },
    "linear_function": {
        "neighbor": True,
        "passing": True,
        "can_override_tonality": True
    }
}

analysis_summary
```

---

## 7. Why This Matters (Conceptual Payoff)

This framework allows you to:
- Analyze **chromatic music without abandoning tonality**
- Explain why some passages feel **directional but non-tonal**
- Model music as a **multi-layered system** instead of a flat Roman-numeral chain

If you want next:
- Convert this into a **graph-based analyzer**
- Encode **Schenker-style reductions**
- Apply it to **algorithmic composition / Markov models**
- Map it onto **MIDI streams**

Just say which direction you want to go.