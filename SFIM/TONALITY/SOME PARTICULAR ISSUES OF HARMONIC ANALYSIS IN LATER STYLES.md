Below is a **synthesized, late-style–oriented harmonic-analysis guide** drawn directly from your text, reframed into **operational analytical principles**, each paired with **Python examples** that show how one could *model* or *probe* these ideas computationally.  
(As requested for the MUSIC THEORY project, **every section includes Python**.)



---

# Some Particular Issues of Harmonic Analysis in Later Styles  
### (Operationalized + Computationally Testable)

---

## 1. Harmony is **never irrelevant** (except at extremes)

Later styles often **weaken or abandon traditional tonality**, but this does **not** imply harmonic arbitrariness.

Instead, harmonic organization may be governed by:
- dissonance fluctuation
- density change
- registral motion
- voice-leading logic
- agogic emphasis
- cadential isolation

### Python: reject “random harmony” hypothesis

```python
def harmonic_is_structured(events):
    return any(
        e["voice_leading"] or
        e["density_change"] or
        e["dissonance_profile"]
        for e in events
    )

harmonic_is_structured([
    {"voice_leading": True, "density_change": False, "dissonance_profile": False}
])
```

---

## 2. When tonal function weakens → **dissonance fluctuation** becomes primary

In post-tonal or quasi-tonal contexts, **motion and punctuation** arise from:
- increase / decrease of dissonance
- not from I–V–I syntax

This allows **cadential effect without tonality**.

### Python: abstract dissonance profile

```python
# hypothetical dissonance values (context-dependent)
DISSONANCE = {
    "m2": 5, "M2": 4,
    "tritone": 4,
    "m7": 3, "M7": 3,
    "P4": 2,
    "m3": 1, "M3": 1,
    "P5": 0, "octave": 0
}

def chord_dissonance(intervals):
    return sum(DISSONANCE.get(i, 2) for i in intervals)

chord_dissonance(["tritone", "m2", "P4"])
```

---

## 3. **Density** as harmonic intensity (especially post-1900)

Harmonic tension may be created by:
- number of simultaneities
- registral compression
- textural thickness

Release may occur by **reduction**, not consonance.

### Python: density curve

```python
def density(chord):
    return len(chord)

progression = [
    ["C", "E"],
    ["C", "E", "G", "Bb"],
    ["C"]
]

[density(ch) for ch in progression]
```

---

## 4. Voice-leading as a **primary harmonic determinant**

Later harmony often derives from:
- semitone motion
- retention of common tones
- registral adjacency

Even without tonal syntax, **leading-tone–like motion** persists perceptually.

### Python: detect semitone-driven succession

```python
def semitone_motion(p1, p2):
    return abs(p2 - p1) == 1

line = [60, 61, 62, 63]
[semitone_motion(line[i], line[i+1]) for i in range(len(line)-1)]
```

---

## 5. Extrinsic cadential forces can override harmonic content

A **dissonant sonority** may feel cadential if it has:
- registral finality
- temporal isolation (fermata)
- diminuendo
- reduction of texture

### Python: cadential likelihood estimator

```python
def cadential_force(duration, register_drop, density_drop):
    return duration + register_drop + density_drop

cadential_force(duration=3, register_drop=2, density_drop=2)
```

---

## 6. Quasi-tonics emerge through **cadential isolation**

In later music:
- final bass pitch may act as “root”
- even if harmony is highly dissonant
- especially when isolated temporally and registrally

### Python: emergent tonic candidate

```python
def emergent_root(final_pitch, lowest_pitch, duration):
    if final_pitch == lowest_pitch and duration > 2:
        return "quasi-tonic"
    return "non-tonic"

emergent_root("F#", "F#", duration=4)
```

---

## 7. Functional harmony may be **concealed but intact**

Later styles often:
- obscure resolution
- displace chord tones
- delay arrivals
- disguise functional roles

Yet **voice-leading reveals function**.

### Python: hidden dominant detection

```python
def dominant_signature(chord, tonic):
    leading = tonic - 1
    fifth = (tonic + 7) % 12
    return leading in chord or fifth in chord

dominant_signature({11, 2, 5}, tonic=0)  # B–D–F resolving to C
```

---

## 8. Parallelism + common-tone retention replaces syntax (Impressionism)

Parallel motion:
- negates traditional counterpoint
- sustains harmonic coherence via **pitch continuity**

### Python: common-tone tracking

```python
def common_tones(chord1, chord2):
    return chord1.intersection(chord2)

common_tones({0, 3, 6, 9}, {3, 6, 9, 0})
```

---

## 9. Dissonance fluctuation is **multi-parametric**

Interval content alone is insufficient.  
Dissonance perception also depends on:
- spacing
- register
- simultaneity
- articulation
- dynamics
- rhythm

### Python: composite dissonance metric

```python
def composite_dissonance(interval_score, density, register_span):
    return interval_score * 0.4 + density * 0.3 + register_span * 0.3

composite_dissonance(
    interval_score=6,
    density=4,
    register_span=3
)
```

---

## 10. Dissonance curves can shape **cadential form**

Even without tonality, a piece may end with:
- peak dissonance → release
- jagged surface → smooth envelope

### Python: dissonance envelope

```python
import numpy as np

dissonance_curve = np.array([3, 5, 7, 6, 4, 2])
envelope = np.convolve(dissonance_curve, np.ones(3)/3, mode="same")
envelope
```

---

## 11. Structural vs auxiliary harmony (non-tonal)

A harmony may be **structural** if emphasized by:
- duration
- repetition
- cadence
- registral prominence

Even if not tonal.

### Python: structural harmonic tagging

```python
def harmonic_role(duration, repetition, cadence):
    if cadence and duration > 2:
        return "structural"
    return "auxiliary"

harmonic_role(duration=4, repetition=1, cadence=True)
```

---

## 12. Meta-principle for late-style harmonic analysis

> **Structure arises from the dominant element-actions of a given context.**  
> Harmony may be decisive—or irrelevant—depending on the compositional system.

### Python: dominant-parameter selector

```python
def dominant_parameter(context):
    return max(context, key=context.get)

dominant_parameter({
    "pitch_class": 2,
    "rhythm": 5,
    "density": 4,
    "register": 3
})
```

---

## Condensed Analytical Takeaway

- Tonality may recede, but **harmonic organization persists**
- Voice-leading, density, dissonance, and cadence replace syntax
- Dissonance fluctuation becomes a **primary expressive axis**
- Structural harmony may be **non-tonal yet decisive**
- Analysis must identify **what actually shapes form** in the given work

---

If you want next, I can:

- Formalize a **dissonance-curve analyzer**
- Build a **voice-leading–first harmonic parser**
- Apply this framework to **Schoenberg, Debussy, Webern, or Boulez**
- Translate this into **algorithmic composition rules**
- Integrate harmonic density with **spectral analysis**

Just tell me where you want to go.