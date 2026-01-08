Below is a **precise functional formalization of impulse roles in meter**, exactly matching the passage, followed by **Python models** that make these roles *computable, multi-level, and non-confused*.  
This section is where *meter stops being abstract* and becomes **event-function logic**.

---

# 1. Fundamental Premise (Restated Exactly)

> **Meter arises from perceived differences among impulses**  
> — differences of *function*, not merely time placement.

Analysis of meter therefore asks:

- which impulses are **strong / weak**
- how weaker impulses are **grouped around stronger**
- how impulses **function**, not just when they occur

Silences qualify as impulses **if pulsation continues through them**.

---

# 2. Four Exclusive Impulse Functions (Canonical Set)

Every impulse (sound *or* silence) belongs—**at a given level**—to **one and only one** of these four functional identities:

---

## (1) Initiative Impulse (I)
- Initiates a metric unit  
- Accentual, strong **at that level**
- Determines *where* the unit exists

> analogous to “downbeat” (but not identical to notation)

---

## (2) Conclusive Impulse (C)
- Terminates a metric unit  
- Weak **at the level of the unit concluded**
- Often coincides with cadences

⚠️ structurally central ≠ metrically strong

---

## (3) Reactive Impulse (R)
- Absorbs / carries forward initiative energy
- Increasingly weak as distance from initiative grows
- Neither prepares nor initiates

---

## (4) Anticipative Impulse (A)
- Directs energy *toward* a later initiative
- Weak **at the level it prepares**
- Anacrustic (upbeat) function

> allied to, not independent of, the initiative it supports

---

# 3. Impulse Function Is **Level-Dependent**

The same event may have **different functions at different structural levels**.

Example (Brahms-like situation):

- chord is **initiative** locally
- entire measure is **anticipative** at phrase level

---

## Python: impulse with level-dependent function

```python
from dataclasses import dataclass
from typing import Dict

@dataclass
class Impulse:
    time: float
    label: str
    functions: Dict[str, str]  # level → I, C, R, A
```

```python
impulse = Impulse(
    time=0.0,
    label="chord",
    functions={
        "foreground": "I",
        "phrase": "A"
    }
)
```

No contradiction—**hierarchy explains it**.

---

# 4. Functional Classification Is About Energy Direction

The four functions differ by **direction of metric energy**:

| Function | Energy Direction |
|--------|------------------|
| Initiative | outward |
| Reactive | absorptive |
| Conclusive | dissipative |
| Anticipative | forward-directed |

---

## Python: symbolic encoding

```python
ENERGY_DIRECTION = {
    "I": "outward",
    "R": "absorptive",
    "C": "dissipative",
    "A": "forward"
}
```

---

# 5. Impulse ≠ Single Event at Higher Levels

At higher levels, an *impulse* may be a **complex of lower-level events**.

- foreground: single note
- mensural: group of notes
- phrase: several measures

---

## Python: composite impulse

```python
@dataclass
class CompositeImpulse:
    impulses: list
    level: str
    function: str
```

```python
anticipative_group = CompositeImpulse(
    impulses=["16th1", "16th2", "16th3", "16th4"],
    level="mensural",
    function="A"
)
```

This models exactly **Ex. 3-10**.

---

# 6. Anticipative–Initiative Relation (Crucial)

> Anticipative impulses are **functionally allied** to the initiative they prepare.

This alliance may be established by:
- temporal proximity
- articulation
- tonal relation
- precedent

Absence of this alliance ⇒ **functional separation**.

---

## Python: anticipative linkage

```python
def is_anticipative(impulse, following_initiative, max_gap=0.5):
    return (
        impulse.time < following_initiative.time and
        (following_initiative.time - impulse.time) <= max_gap
    )
```

---

# 7. Metric Character Depends on Anticipation

Whether a unit feels like:

- **iamb** (weak–strong)
- **trochee** (strong–weak)
- **anapest**
- **dactyl**

depends on **presence and placement of anticipative impulses**.

---

## Python: determine metric character

```python
def metric_character(functions):
    if functions[0] == "A" and functions[1] == "I":
        return "iambic"
    if functions[0] == "I" and functions[1] == "R":
        return "trochaic"
    return "complex"
```

---

# 8. Functional Duality and Elision

An impulse may serve **two functions simultaneously**:

### Same level:
- C + A → conclusive–anticipative
- C + I → conclusive–initiative (formal elision)

### Different levels:
- I locally, A globally
- C locally, R globally

---

## Python: dual-function impulse

```python
@dataclass
class DualImpulse:
    time: float
    functions: list  # e.g. ["C", "I"]
```

```python
elision = DualImpulse(
    time=4.0,
    functions=["C", "I"]
)
```

This models **formal elision**, not ambiguity.

---

# 9. Why Conclusive Can Feel Strong (But Isn’t)

In elision:
- the inherently weak **conclusive**
- inherits strength from imposed **initiative**

> strength is **vicarious**, not intrinsic

---

## Python: inherited accent

```python
def effective_strength(functions):
    if "I" in functions:
        return "strong"
    if "C" in functions:
        return "weak"
    return "weak"
```

---

# 10. Structural Summary (Exact to the Theory)

```python
@dataclass
class MetricImpulseSystem:
    impulses: list  # Impulse or CompositeImpulse
    levels: list    # foreground, mensural, phrase, etc.
```

**Key invariants:**

1. Every impulse has **one function per level**
2. Functions are **exclusive at a given level**
3. The same event may have **multiple functions across levels**
4. Meter is the **pattern of initiative impulses**
5. Cadential events are usually **conclusive, not initiative**
6. Anticipation determines **metric character**
7. Elision is **functional conjunction**, not confusion

---

# Final Conceptual Closure

This passage gives meter its **grammar**.

- Rhythm = temporal field  
- Grouping = perceptual segmentation  
- **Meter = logic of impulse function**

Without this functional vocabulary (I–R–C–A),  
analysis collapses into **notation, loudness, or guesswork**.

With it, **metric dissonance, elision, cadential weakness, anticipation, and fluctuation** become rigorously intelligible.

If you want next, we can:

- formalize **metric dissonance / resolution** using impulse functions  
- build **automatic impulse-function labeling** from MIDI  
- connect impulse functions to **conducting / performance timing**  
- integrate this with **tonal and harmonic prolongation**

Just tell me where to continue.