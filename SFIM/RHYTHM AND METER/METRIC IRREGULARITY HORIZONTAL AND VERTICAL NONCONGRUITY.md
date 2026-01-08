Below is a **clean synthesis of metric noncongruity (horizontal & vertical)** exactly in the sense of the passage, followed by **explicit Python models** that let you *analyze, compare, and classify* congruity vs noncongruity across levels—without reducing meter to bar-lines or constant beats.

I will keep the focus on **structure and function**, not historical narration.

---

## 1. Congruity vs noncongruity (precise meanings)

### Congruity
Metric **conformity**:  
> Units **align exactly** when superimposed, in **size and function**, at a given level.

Congruity may occur:
- within a single line (horizontal)
- across multiple voices (vertical)
- at one level but **not** another

Congruity ≠ regularity  
A structure can be congruent and irregular, or regular and noncongruent.

---

### Horizontal noncongruity
Asymmetry **between successive units** in time.

Examples:
- unequal spacing of phrase-level initiatives
- irregular accent-to-accent distances
- fermatas, expansions, contractions
- accelerative / recessive metric spans

This is **contiguous instability**.

---

### Vertical noncongruity (polymeter)
Asymmetry **between simultaneous metric organizations**.

Examples:
- different grouping sizes in different voices
- same unit size but different internal content (e.g., 3 vs 2+1)
- disjunct “real bar-lines” across texture

This is **textural instability**.

Opposite condition:
- **homometric**: parity among concurrent metric units.

---

## 2. Metric dissonance and resolution

Noncongruity is not static—it tends to behave **directionally**:

- **metric dissonance**: sustained nonalignment
- **resolution**: convergence toward congruity (often temporary)

Crucially:
> Resolution does **not** require tonal cadence  
> It may be purely metric (alignment of initiatives).

---

## 3. Real meter vs notated meter

The discussion assumes throughout:

> **Real meter is often disjunct from the notated bar-line**

This applies especially to:
- chant
- recitative
- Renaissance polyphony
- polymetric modern works
- classical works with syncopation and displacement

Bar-lines are **editorial conveniences**, not structural facts.

---

## 4. Measuring proportion between metric units

The passage explicitly allows **multiple proportional metrics**:

1. **Real time duration** (with tempo changes)
2. **Initiative-to-initiative span**
3. **Number of active pulses** (activity-tempo)
4. **Total pulses** (active + inactive)
5. **Hybrid measures** (e.g., activity density)

Each yields **different functional insight**.

---

## 5. Horizontal noncongruity: Python model

### 5.1 Accent-to-accent spans

```python
def accent_spans(accent_positions):
    """
    accent_positions: list of time positions (beats or seconds)
    returns list of successive spans
    """
    return [
        accent_positions[i+1] - accent_positions[i]
        for i in range(len(accent_positions) - 1)
    ]
```

---

### 5.2 Congruity test (horizontal)

```python
def horizontal_congruity(spans, tolerance=0.05):
    """
    Returns True if spans are effectively equal.
    """
    avg = sum(spans) / len(spans)
    return all(abs(s - avg) <= tolerance * avg for s in spans)
```

- `True` → horizontal congruity  
- `False` → horizontal noncongruity

This directly models:
- Beethoven Op. 93/2 opening (noncongruent)
- fermata-separated units
- Classical hypermetric expansions

---

### 5.3 Directional tendency (fluctuation)

```python
def fluctuation_type(spans):
    """
    Detects accelerative vs recessive tendency.
    """
    diffs = [spans[i+1] - spans[i] for i in range(len(spans)-1)]
    if all(d < 0 for d in diffs):
        return "accelerative"
    if all(d > 0 for d in diffs):
        return "recessive"
    return "mixed"
```

This corresponds to:
- accelerative instability → intensification
- recessive instability → release / decay

---

## 6. Vertical noncongruity (polymeter)

### 6.1 Representing concurrent metric layers

```python
from dataclasses import dataclass

@dataclass
class MetricLayer:
    name: str
    unit_size: float       # duration
    internal_pattern: tuple  # e.g. (2,1) vs (3,)
```

---

### 6.2 Vertical congruity test

```python
def vertical_congruity(layer_a: MetricLayer, layer_b: MetricLayer):
    """
    Tests congruity in size and content.
    """
    size_match = layer_a.unit_size == layer_b.unit_size
    content_match = layer_a.internal_pattern == layer_b.internal_pattern
    return size_match and content_match
```

Interpretation:
- size match + content mismatch → **polymeter (content)**
- size mismatch → **polymeter (size)**
- both mismatch → **strong vertical noncongruity**

---

## 7. Disjunct bar-line (non-perpendicular time)

A **real bar-line** can be modeled as **layer-specific initiative points**.

```python
def real_barline_positions(layer_units):
    """
    layer_units: list of initiative times per layer
    """
    return {
        layer: positions
        for layer, positions in layer_units.items()
    }
```

If bar-lines differ across layers → **vertical noncongruity**.

This directly models:

- [Igor Stravinsky](chatgpt://generic-entity?number=0) – *L’Histoire du soldat*
- polymetric Renaissance polyphony
- Brahms inner-voice metric divergence

---

## 8. Fermatas and indeterminate durations

A fermata is **metric asymmetry by definition**, unless interpreted as an exact multiple.

```python
def fermata_asymmetry(fermata_duration, reference_unit):
    return fermata_duration / reference_unit
```

Values ≠ integer → **functional asymmetry**

Meter **persists**, but regular pulse does not.

---

## 9. Case-study anchors (structural relevance)

- [Ludwig van Beethoven](chatgpt://generic-entity?number=1)  
  Horizontal noncongruity → metric dissonance → resolution

- [Josquin des Prez](chatgpt://generic-entity?number=2)  
  Constant horizontal + vertical noncongruity, resolved locally

- [Johannes Brahms](chatgpt://generic-entity?number=3)  
  Controlled fluctuation under notated regularity

- [Igor Stravinsky](chatgpt://generic-entity?number=4)  
  Explicit polymeter with eventual perpendicular convergence

---

## 10. Why noncongruity matters musically

Noncongruity:
- creates **instability**
- activates **directional force**
- enables **metric dissonance / resolution**
- produces **rhythmic vitality**

Congruity:
- stabilizes
- clarifies
- frames fluctuation
- enables perception of resolution

Great music alternates **between them**.

---

## 11. Final synthesis (compressed)

1. **Horizontal noncongruity** = unequal successive metric spans  
2. **Vertical noncongruity** = unequal simultaneous metric structures  
3. Polymeter = vertical noncongruity  
4. Congruity may occur at one level and not another  
5. Metric dissonance is functional, not defective  
6. Resolution = convergence of real bar-lines  
7. Meter survives without constant beat  
8. Proportion is the real metric substance  
9. Text, texture, and activity shape noncongruity  
10. Rhythmic vitality emerges from **controlled instability**

If you want next, we can:
- formalize **metric dissonance → resolution curves**
- connect noncongruity to **syncopation theory**
- model **text-driven metric instability**
- or build a **Brahms-style polymetric motive analyzer**

Just say the direction.