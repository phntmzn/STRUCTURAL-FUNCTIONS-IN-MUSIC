Below is a **focused analytical synthesis** of the passage you provided, centered on the idea of the **specific tonal system** as a *hierarchically organized collection of tonic references*, with **Python formalizations throughout**. I also include **graphic intuition** (via image groups) and **historical anchoring** (via entity references), exactly aligned with the text’s intent.

---

## 1. Definition: The *Specific* Tonal System

The passage gives a precise working definition:

> **A specific tonal system** =  
> the collection of **tonics (tonicized PCS / PCGs)**  
> **plus** the *supportive pitch factors* (encircling, leading, preparing)  
> oriented toward **each tonic of reference**.

This is **not**:
- a generic scale
- a theoretical key system
- a stylistic norm

It *is*:
- the **actual tonal resource of a single work**
- hierarchically ordered
- expandable by **secondary system components**

### Python: Specific Tonal System Object

```python
class TonalSystem:
    def __init__(self, primary_tonic):
        self.primary_tonic = primary_tonic
        self.secondary_tonics = {}
        self.supportive_factors = {}

    def add_secondary(self, tonic, status="secondary"):
        self.secondary_tonics[tonic] = status

    def add_support(self, tonic, pitch_factor):
        self.supportive_factors.setdefault(tonic, set()).add(pitch_factor)

mozart_system = TonalSystem("F")
mozart_system.add_secondary("C", "dominant")
mozart_system.add_secondary("Bb", "subdominant")
mozart_system.add_secondary("d", "inferior")
mozart_system.add_support("C", "E")   # leading tone
mozart_system.add_support("F", "E")   # lower neighbor

mozart_system.__dict__
```

This mirrors the text’s definition *exactly*.

---

## 2. Mozart K.332: Expanded Primary System



In **[Piano Sonata No. 12 in F major, K. 332](chatgpt://generic-entity?number=0)**, the tonal system:

- **Primary system**: F
- **Secondary systems**:  
  C, Bb, d, Eb, G, a
- Some systems are **parenthetical** (inferior status)
- Expansion is *directional* and *hierarchic*

Key insight:
> The chart can represent **chronology** *or* **hierarchy**

### Python: Tonal Range and Hierarchy

```python
tonal_hierarchy = {
    "F": {"level": 0, "role": "primary"},
    "C": {"level": 1, "role": "dominant"},
    "Bb": {"level": 1, "role": "subdominant"},
    "d": {"level": 2, "role": "inferior"},
    "Eb": {"level": 2, "role": "inferior"},
    "G": {"level": 2, "role": "inferior"},
    "a": {"level": 2, "role": "inferior"},
}

tonal_hierarchy
```

This encodes **tonal latitude (expanse, scope)**.

---

## 3. Tonal Components and System Components

The text introduces a crucial distinction:

> A **system component** is itself a tonal system  
> but of **inferior hierarchical status**

Thus:
- F = primary system
- C = second-order system
- d = inferior system component of C (and F)

### Python: Nested System Components

```python
class SystemComponent:
    def __init__(self, tonic, parent=None):
        self.tonic = tonic
        self.parent = parent
        self.subsystems = []

    def add_subsystem(self, sub):
        self.subsystems.append(sub)

F = SystemComponent("F")
C = SystemComponent("C", parent=F)
d = SystemComponent("d", parent=C)

F.add_subsystem(C)
C.add_subsystem(d)

[(s.tonic, s.parent.tonic if s.parent else None) for s in C.subsystems]
```

This formalizes:
> “d is a system component of relatively inferior status.”

---

## 4. Fluctuation as Structural Phenomenon

The Mozart diagram includes:
- **Curved arrows** → dominant–tonic paths
- A **sense of distance and return**
- Fluctuation *within* the expanded system

Fluctuation is:
- Structural
- Directional
- Hierarchically meaningful

### Python: Tonal Fluctuation Path

```python
fluctuation_path = [
    "F", "C", "g", "d", "Bb", "F"
]

def fluctuation_distance(path):
    return len(set(path)) - 1

fluctuation_distance(fluctuation_path)
```

This approximates **tonal excursion**.

---

## 5. Josquin: Emergent Secondary Tonal Systems



In **[Tu pauperum refugium](chatgpt://generic-entity?number=1)**, we see:

- A **primary modal system**
- Emergent **secondary tonal system on iv**
- Mild tonicization via:
  - plagal motion
  - applied leading tones (musica ficta)
- Early foreshadowing of later tonal expansion

### Python: Modal System with Emergent Tonics

```python
josquin_system = TonalSystem("E")
josquin_system.add_secondary("A", "secondary")
josquin_system.add_support("A", "G#")  # musica ficta leading tone

josquin_system.__dict__
```

This captures:
> “The concept of an emergent secondary tonal system.”

---

## 6. Cadential Hierarchy = Tonal Hierarchy



In Ex. 1-7b, tonal order is revealed by **cadences**, not scales:

Hierarchic cadential centers:
1. e (primary)
2. a (secondary)
3. C (tertiary)

### Python: Cadential Weighting

```python
cadences = [
    ("e", 3),
    ("a", 2),
    ("C", 1),
]

sorted(cadences, key=lambda x: -x[1])
```

This expresses:
> “The hierarchic order of cadential centers.”

---

## 7. Broad Concept of Tonality (Cross-Historical)

The author emphasizes:

- Tonality applies to:
  - chant
  - Renaissance polyphony
  - common-practice harmony
  - 20th-century music
- Wherever:
  - a **PC resource**
  - is **hierarchically disposed**
  - through **cadential focus**

### Python: Style-Independent Tonality Test

```python
def has_tonality(pc_set, cadential_centers):
    return len(cadential_centers) > 0 and len(pc_set) > 1

has_tonality({"D","E","F","G","A"}, ["D"])
```

This reflects:
> “It is implicit and essential in the idea of a scalar PC resource hierarchically disposed.”

---

## 8. Core Takeaways (Compressed)

| Concept | Meaning |
|------|--------|
| Specific tonal system | Work-specific tonal resource |
| System component | Hierarchically inferior tonal system |
| Tonal expansion | Controlled fluctuation |
| Fluctuation | Structural, not decorative |
| Cadence | Primary indicator of tonal hierarchy |
| Tonality | Cross-historical principle |

---

## 9. Why This Framework Is Powerful

It allows you to:
- Map **entire works as tonal systems**
- Compare **tonal latitude** between pieces
- Analyze **modal → tonal evolution**
- Represent tonality **graphically or computationally**
- Avoid false binaries (tonal vs non-tonal)

If you want next, I can:
- Build a **network graph** of tonal systems
- Encode **Mozart K.332 fully in Python**
- Create **automatic tonal-system extractors**
- Translate this into **pitch-class set analytics**

Just say the direction.