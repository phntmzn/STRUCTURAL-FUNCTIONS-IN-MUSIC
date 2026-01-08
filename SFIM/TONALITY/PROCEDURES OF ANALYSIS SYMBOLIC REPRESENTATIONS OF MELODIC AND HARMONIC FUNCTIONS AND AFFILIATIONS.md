Below is a **clean, operational synthesis** of the symbolic system you just introduced, reframed as a **usable analytical toolkit** and accompanied throughout by **Python examples**, as requested for the MUSIC THEORY project.  
The aim is not to re-theorize Schenker, but to show **how your symbols encode multileveled tonal–linear hierarchy** and how that hierarchy can be **modeled, reduced, and reinterpreted computationally**.

---

# Symbolic Representation of Tonal & Linear Hierarchy  
*(with Computational Analogues)*

---

## 1. Governing Principle: Tonal Order Supersedes Agogic Weight (When Tonality Is Active)

- In **tonal or quasi-tonal systems**, hierarchy is determined first by **tonal function**
- Agogic stress (duration, accent, dynamics) is **subordinate** at higher levels
- In **nontonal systems**, agogic dominance may define first-order structure

### Python: decide governing hierarchy

```python
def governing_hierarchy(style):
    if style in {"tonal", "modal", "quasi-tonal"}:
        return "tonal_function"
    else:
        return "agogic_prominence"

governing_hierarchy("tonal")
```

---

## 2. Multileveled Linear Function (Core Concept)

An event’s **structural rank changes with level of reference**:
- Locally essential → globally auxiliary
- Reduction increases as analytical scope widens

This is the **core divergence from orthodox Schenkerian dogma**.

### Python: level-dependent structural status

```python
def structural_role(event, level):
    if level == "local":
        return event["local_role"]
    elif level == "global":
        return event["global_role"]

note = {"local_role": "essential", "global_role": "auxiliary"}
structural_role(note, "global")
```

---

## 3. Pitch-Factor Hierarchy (Item 1)

Pitch events are ordered by **relative structural weight** within the example:

```
Highest → Lowest significance
●   ○   ◦   ·
```

(Exact number of tiers is context-dependent.)

### Python: rank pitch events

```python
HIERARCHY = {"●": 3, "○": 2, "◦": 1, "·": 0}

def rank(symbol):
    return HIERARCHY[symbol]

rank("○")
```

---

## 4. Beams = Prolongation & Hierarchic Affiliation (Item 2)

- Outer beams = higher structural level
- Inner / dotted beams = lower levels
- Beam choice is **methodological**, not fixed

### Python: represent beams as nesting

```python
structure = {
    "level_1": ["F2", "C2"],
    "level_2": ["A1", "G1"],
    "level_3": ["passing_notes"]
}
```

---

## 5. Rectangular Enclosure = Analytical Attention (Item 3)

Boxes mark:
- Tonal pivots
- Structural anomalies
- Events under special scrutiny

### Python: flag marked events

```python
def highlight(event, reason):
    event["highlighted"] = True
    event["reason"] = reason
    return event

highlight({"pitch": "Bb"}, "parenthetical tonic")
```

---

## 6. Extrinsic Emphasis Accent (Item 4)

Accent marks denote:
- agogic stress
- durational prominence
- dynamic projection

But **do not override tonal primacy**.

### Python: separate tonal vs agogic weight

```python
def effective_weight(tonal, agogic, style):
    if style == "tonal":
        return tonal * 2 + agogic
    return agogic * 2 + tonal

effective_weight(tonal=5, agogic=8, style="tonal")
```

---

## 7. Passing Configurations as Diagonal Lines (Item 5)

Passing motion:
- summarized
- pitches omitted
- function > content

### Python: abstract passing motion

```python
def passing_motion(start, end, steps):
    return {"from": start, "to": end, "type": "passing", "steps": steps}

passing_motion("C", "G", 3)
```

---

## 8. Formal Punctuation Dashes (Item 6)

Vertical dashes indicate:
- phrase boundaries
- cadential hierarchy
- relative closure strength

### Python: cadence strength tagging

```python
def cadence(level):
    return "|" * level

cadence(3)
```

---

## 9. Arrows = Registral or Structural Extremes (Item 7)

Arrows identify:
- high points
- low points
- focal extremes

Dotted arrows = lower-level significance

### Python: detect extrema

```python
def extrema(pitches):
    return min(pitches), max(pitches)

extrema([60, 64, 67, 72, 69])
```

---

## 10. Brackets = Sequential / Iterative Groupings (Item 8)

Used for:
- sequences
- motivic repetition
- harmonic cycles

### Python: detect sequences

```python
def is_sequence(intervals):
    return len(set(intervals)) == 1

is_sequence([2, 2, 2])
```

---

## 11. Wavy Line = Excision (Item 9)

Indicates:
- omitted repetition
- analytically irrelevant material

### Python: excise redundancy

```python
def excise(events, keep):
    return events[:keep]

excise(["A","B","C","D"], 2)
```

---

## 12. Arrowed Dominant Relations (Item 11)

Arrows point **toward tonic of reference**, not root motion per se.

### Python: dominant resolution map

```python
def dominant_to_tonic(dominant, tonic):
    return f"{dominant} → {tonic}"

dominant_to_tonic("V/V", "V")
```

---

## 13. Vertical Brackets = Multiple Tonal Function (Item 12)

Single harmony may be:
- vi (primary)
- ii (secondary)
- ii/V (tertiary)

All are **simultaneously valid**.

### Python: multilevel function

```python
def multilevel_function(*functions):
    return list(functions)

multilevel_function("vi", "ii/V", "ii")
```

---

## 14. Upper vs Lower Case (Item 13)

- Uppercase = major
- Lowercase = minor
- Abandoned when concept is abstract

### Python: normalize abstract symbols

```python
def abstract(symbol):
    return symbol.upper()

abstract("vi")
```

---

## 15. Reduction Is Purpose-Driven, Not Universal

Key methodological stance:

> **No single sketch can show all functions.**

- Tonal function may be isolated from voice-leading
- Voice-leading may be isolated from harmony
- Density, dissonance, or register may dominate instead

### Python: analytical lens selector

```python
def analysis_mode(focus):
    return f"Analyzing primarily for {focus}"

analysis_mode("tonal identity")
```

---

## 16. Example Logic (Corelli → Couperin → Krenek)

Across styles:
- Corelli: melody = horizontalized harmony
- Couperin: fifth-cycle root motion with parenthetical tonics
- Krenek: voice-leading + density + quasi-leading tone

All remain **hierarchically interpretable**.

### Python: style-adaptive analysis

```python
def analysis_strategy(style):
    return {
        "Corelli": "tonal hierarchy",
        "Couperin": "root motion + secondary tonics",
        "Krenek": "voice-leading + density"
    }.get(style, "hybrid")

analysis_strategy("Krenek")
```

---

## Final Synthesis

- Your system is **not anti-Schenkerian**  
- It is **post-Schenkerian, pluralistic, and context-adaptive**
- Hierarchy is real, but **methods vary**
- Reduction is **functional, not doctrinal**
- Tonal, modal, quasi-tonal, and non-tonal music are all analyzable within a unified symbolic logic

---

If you want next, I can:

- Formalize this into a **JSON / DSL for tonal sketches**
- Build a **Python-based reduction engine**
- Translate these symbols into **SVG or staff-notation graphics**
- Apply the full system to **one complete movement**
- Encode **multileveled tonal rhythm + linear hierarchy together**

Just say the word.