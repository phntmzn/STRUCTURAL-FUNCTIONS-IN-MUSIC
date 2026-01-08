Below is a **conceptual synthesis of the passage** you provided, organized around its **main analytical claims**, with **Python examples throughout** that *formalize* the ideas of **tonal systems (generic vs particular)**, **hierarchic pitch relations**, and **fluctuation**.  
I’ll keep the focus on *theory → analytical method → representation*, exactly as the text intends.



---

## 1. Tonality as a Historically Conditioned Convention

The discussion begins by asserting that even **very broad conceptions of tonality** tend to be articulated by reference to the **conventions of the tonal period** (major–minor practice). This does **not** mean tonality is restricted to that period—rather:

- Tonal order is *recognized through historically stabilized pitch relations*
- Earlier and later styles are often explained **analogically**
- The *idea* of tonic survives beyond stylistic boundaries

> “The word tonic will be freely used…including those which predate and postdate the period of major-minor tonal conventions.”

### Python: Style-Agnostic Tonic Concept

```python
class Tonic:
    def __init__(self, pc, style):
        self.pc = pc
        self.style = style  # tonal, modal, post-tonal, etc.

    def __repr__(self):
        return f"Tonic({self.pc}, style={self.style})"

Tonic("D", "phrygian")
Tonic("C", "common_practice")
```

This encodes the idea that **tonic ≠ major/minor key**.

---

## 2. Primary Pitch Relations That Define Tonal Order

Across tonal practices, the **central pitch factor** is most strongly defined by:

1. **Semitone relations**
   - Below (leading tone)
   - Sometimes above
2. **Perfect fifth / fourth**
   - Dominant–tonic axis
3. **Cadential arrival**
   - Tonic as *terminal goal*

These relations form the **core gravitational network** of tonality.

### Python: Pitch Affiliation Weights

```python
import math

def tonal_affiliation(pc, tonic):
    intervals = {
        "semitone_below": 1,
        "semitone_above": 11,
        "perfect_fifth": 7,
        "perfect_fourth": 5
    }
    return intervals

tonal_affiliation("B", "C")
```

This reflects:
> “The leaning force of the semitone and the natural relation of the 5th.”

---

## 3. Generic Tonal System (Style-Level)

The **tonal system of a style** is described as:

- A **generic, expected collection**
- Typically:
  - A diatonic or modal set
  - Vertical derivatives (triads, sevenths)
  - Predictable chromatic affiliates

Examples:
- Major/minor system
- Phrygian with raised leading tones
- Modal systems with habitual inflections

### Python: Generic Tonal System

```python
class GenericTonalSystem:
    def __init__(self, scale, chromatic_extensions):
        self.scale = scale
        self.extensions = chromatic_extensions

generic_c_major = GenericTonalSystem(
    scale={"C","D","E","F","G","A","B"},
    chromatic_extensions={"F#","Bb"}
)

generic_c_major.scale | generic_c_major.extensions
```

This models:
> “The normal range and ordering of PC material reasonably to be expected.”

---

## 4. Particular Tonal System (Work-Specific)

More important analytically is the **tonal system of a particular work**:

- The *actual* PC resources used
- Their **hierarchic ordering**
- Their **directions and rates of fluctuation**
- Their expressive anomalies

A work may:
- Elevate chromatic centers (e.g., Neapolitan)
- Extend modal ambitus
- Emphasize plagal motion
- Operate on reduced collections (tri-/tetrachords)

### Python: Work-Specific Tonal System

```python
class ParticularTonalSystem:
    def __init__(self, primary_tonic):
        self.primary_tonic = primary_tonic
        self.secondary_centers = set()
        self.pc_inventory = set()

    def add_center(self, pc):
        self.secondary_centers.add(pc)

    def add_pc(self, pc):
        self.pc_inventory.add(pc)

work_system = ParticularTonalSystem("E")
work_system.add_center("F")   # Neapolitan
work_system.add_center("B")
work_system.add_pc("G")
work_system.add_pc("Bb")

work_system.__dict__
```

This directly implements:
> “The tonal system specific to a composition represents the total resource of PC content basic to that work.”

---

## 5. Tonal Fluctuation = Level + Duration

**Modulation / fluctuation** is not binary (modulated vs not), but depends on:

- **Structural level**
- **Extent of time over which a tonic prevails**
- **Strength of cadential affirmation**

A tonic briefly touched ≠ tonic structurally prevailing.

### Python: Tonal Fluctuation Tracking

```python
class TonalFluctuation:
    def __init__(self, tonic, duration, level):
        self.tonic = tonic
        self.duration = duration
        self.level = level

fluctuations = [
    TonalFluctuation("C", 120, "background"),
    TonalFluctuation("Ab", 16, "middleground"),
    TonalFluctuation("D", 4, "foreground")
]

[(f.tonic, f.level, f.duration) for f in fluctuations]
```

This encodes:
> “The significance of fluctuation corresponds to the breadth of structural level.”

---

## 6. Analytical Representation: Tonal “Image” of a Work

The author proposes **methods of representation** that:

- Make the tonal system *visible*
- Show:
  - Latitude
  - Direction
  - Secondary centers
- Allow inference of **rate of fluctuation**
  - (Rhythm treated later)

### Python: Tonal Image Data Structure

```python
tonal_image = {
    "primary_tonic": "C",
    "secondary_centers": ["Db", "F", "Ab"],
    "modal_extensions": True,
    "plagal_bias": False,
    "collection_size": "heptachordal"
}

tonal_image
```

This is a direct abstraction of:
> “Methods by which the tonal image of a work can be portrayed.”

---

## 7. Key Theoretical Distinctions (Condensed)

| Concept | Meaning |
|------|--------|
| Generic tonal system | Stylistic norm |
| Particular tonal system | Work-specific realization |
| Tonic | Hierarchic pitch center (style-independent) |
| Fluctuation | Tonal movement defined by level |
| Chromatic factor | May be structural, not decorative |
| Rate of fluctuation | Rhythmic property |

---

## 8. Why This Matters Analytically

This framework allows you to:
- Analyze **modal, tonal, and hybrid works** uniformly
- Treat chromaticism as **systemic**, not exceptional
- Compare works by **tonal latitude**, not just key
- Formalize tonality in **computational / algorithmic analysis**

If you want next, I can:
- Build a **graph model** of tonal systems
- Map tonal fluctuation over time (timeline plots)
- Reduce works to **PC-system signatures**
- Apply this to **post-tonal but hierarchic music**

Just say the direction.