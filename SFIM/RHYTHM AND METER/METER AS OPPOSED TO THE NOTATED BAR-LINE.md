Below is a **clean structural resolution of the issue of “real meter vs notated meter”**, followed by **Python models** that let you *decide where the true bar-line lies* by analyzing accent, not notation.  
This passage is about **metric dissonance, displacement, and resolution**—not ambiguity or looseness.

I will treat both the Chopin and Mozart cases as **general metric mechanisms**, not repertoire anecdotes.

---

## 1. Fundamental Principle (Restated Precisely)

> **Meter is defined by accentual grouping, not by the printed bar-line.**

Therefore, the *first question of metric analysis* is always:

> **Do accentual determinants coincide with the notated bar-line?**  
> If not → **where is the real bar-line?**

This is not rhetorical. It is a **testable analytical problem**.

---

## 2. Accelerating Metric Change (Chopin Case)

[Frédéric Chopin](chatgpt://generic-entity?number=0)  

The Chopin example shows:

- Stable **triple mensural reference**
- Then **accentual contraction**
- Then **metric restoration**

Crucially, this is **not meterlessness**, but **metric fluctuation**.

### Python: detect contraction of metric unit

```python
import numpy as np

def accent_density(accent_times, window):
    densities = []
    for t in np.arange(0, max(accent_times), window):
        count = sum((a >= t) and (a < t + window) for a in accent_times)
        densities.append(count)
    return densities
```

```python
accent_times = [0, 3, 6, 8, 10, 12, 13, 14, 15, 18]  # example
accent_density(accent_times, window=3)
```

Increasing density ⇒ **metric contraction**, even if bar-lines stay fixed.

---

## 3. Mensural vs Incipient Metric Change

The text raises a crucial perceptual distinction:

- **Actual mensural change**  
- **Incipient metric fluctuation against a prevailing reference**

This is about **preconditioning**.

### Python: reference-preserving vs reference-breaking change

```python
def metric_deviation(accent_times, reference_unit):
    intervals = np.diff(accent_times)
    return [abs(i - reference_unit) for i in intervals]
```

Small deviations → fluctuation against reference  
Large sustained deviations → new metric unit

---

## 4. Mozart Example: Displaced Triple Meter (Not Latent Duple)

[Wolfgang Amadeus Mozart](chatgpt://generic-entity?number=1)  

This is the critical theoretical disagreement with Cooper & Meyer.

### Cooper–Meyer view:
- Triple meter is “real”
- Duple is latent
- Performer must assert triple

### View argued in the text:
- **Triple meter remains**
- **Bar-line is displaced**
- Accents **shift the real bar-line**
- Result = **metric dissonance → resolution**

This is not ambiguity. It is **directed metric motion**.

---

## 5. Accent Evidence Overrides Notation

Mozart marks the second beat as accentual by:

- duration
- dynamic stress
- pitch prominence
- texture
- anacrusis
- melodic contour

### Python: aggregate accentual evidence

```python
def accent_score(duration, dynamic, pitch_height, leap):
    return (
        0.3 * duration +
        0.3 * dynamic +
        0.2 * pitch_height +
        0.2 * leap
    )
```

```python
beats = [
    ("beat1", accent_score(0.3, 0.2, 0.4, 0.1)),
    ("beat2", accent_score(0.8, 0.9, 0.7, 0.4)),
    ("beat3", accent_score(0.2, 0.1, 0.3, 0.1)),
]

max(beats, key=lambda x: x[1])
```

If **beat 2 consistently wins**, it is **metric initiation**, regardless of bar-line.

---

## 6. Displaced Bar-Line vs Latent Meter

The key distinction:

| Concept | Meaning |
|------|--------|
| Latent duple | competing meter underneath |
| Displaced triple | same meter, shifted origin |

The text argues **for the second**.

### Python: bar-line displacement detection

```python
def infer_barline_shift(accent_positions, expected_positions):
    return [
        a - e
        for a, e in zip(accent_positions, expected_positions)
    ]
```

Consistent non-zero offset = **shifted bar-line**, not new meter.

---

## 7. Asymmetrical Metric Units

Mozart creates a **5-beat unit (3+2)** before resolution.

This asymmetry is **intentional and directional**.

### Python: detect asymmetric units

```python
def metric_units(accent_times):
    return np.diff(accent_times)

units = metric_units([0, 3, 6, 11])  # 3,3,5
```

Asymmetry ≠ error  
Asymmetry = **metric tension**

---

## 8. Harmonic Rhythm as Counter-Grouping

Important subtlety:

> Only harmonic rhythm aligns with the notated bar-line.

Thus:
- melodic meter = displaced
- harmonic meter = stable

### Python: compare meters by element

```python
def compare_element_meters(melodic_accents, harmonic_accents):
    return {
        "melodic": melodic_accents,
        "harmonic": harmonic_accents
    }
```

Counter-grouping = **poly-metric tension**, not confusion.

---

## 9. Metric Resolution (m. 7)

Resolution is marked by:
- downbeat confirmation
- harmonic change
- motivic renewal
- registral leap
- dynamic emphasis

This is **structural clarification**, not mere emphasis.

### Python: resolution detection

```python
def is_metric_resolution(event, threshold=0.8):
    return event["accent"] > threshold and event["harmonic_change"]
```

---

## 10. Why This Must Be Performed, Not Smoothed

The text is explicit:

> The anomaly is **not weakening**  
> It is **expressive dissonance → resolution**

Flattening it destroys the form.

---

## Structural Summary (Formal)

```python
class MetricState:
    def __init__(self, barline_offset, unit_size, stability):
        self.barline_offset = barline_offset
        self.unit_size = unit_size
        self.stability = stability
```

Mozart mm. 1–6:
```python
MetricState(barline_offset=+1, unit_size=[3,2], stability="unstable")
```

m. 7:
```python
MetricState(barline_offset=0, unit_size=[3], stability="resolved")
```

---

## Final Theoretical Conclusions (Exact to the Passage)

1. Meter is often **independent of notation**
2. Bar-lines may be **wrong**
3. Metric change may be **incipient or actual**
4. Accent frequency may contract without meter loss
5. Displaced meter ≠ latent meter
6. Metric dissonance is **directional**
7. Resolution restores **coincidence of real and notated meter**
8. Performance must **project the dissonance**, not neutralize it

This passage defines **metric motion** as clearly as tonal motion.  
If you want, next we can:

- formalize **metric dissonance / consonance**
- model **preconditioning and expectation**
- build **automatic real bar-line detection**
- connect metric resolution to **formal cadence**

Just tell me which path to take.