Below is a **theory-centered exposition** of the passage you provided, focused on **melodic curve (pitch-profile) analysis** and how it supports **tonal, quasi-tonal, and non-tonal organization**. I keep the discussion anchored in **curve as structure**, **essential vs auxiliary points**, and **perceptual consequences**, and I formalize each idea with **Python examples**, as you requested.



---

## 1. Melodic curve (pitch-profile): what it represents

A **melodic curve** is a graphic abstraction of pitch over time that shows:

- upward vs downward motion  
- points of stasis vs activity  
- registral range (ambitus)  
- distribution of motion (conjunct vs disjunct)  
- locations of high and low points  
- symmetry or asymmetry of phrases  

Crucially:

> The curve is **not the melody**, but a **structural image** of its tonal or expressive behavior.

---

## 2. Same melody, different curve interpretations

As the text notes (Brahms, Ex. 1-29):

- At one level, the melody shows **many up/down motions**
- At another level, it behaves as a **static melodic element**

This illustrates a core principle:

> **Curve interpretation depends on level of abstraction.**

### Python: raw vs smoothed contour

```python
import numpy as np

# example pitch sequence (MIDI numbers for simplicity)
melody = np.array([69, 71, 70, 72, 71, 70, 71, 69])

# raw contour (intervals)
raw_intervals = np.diff(melody)

# smoothed contour (moving average)
smoothed = np.convolve(melody, np.ones(3)/3, mode="valid")

raw_intervals, smoothed
```

- Raw intervals → busy surface motion  
- Smoothed curve → relative stasis

---

## 3. What curve analysis reveals structurally

A pitch-profile can be designed to show:

- **where activity is concentrated**
- **where the line rests**
- **breadth or narrowness of ambitus**
- **balance of skips vs steps**
- **symmetry vs asymmetry**
- **rate of motion (acceleration / deceleration)**

### Python: ambitus and motion density

```python
def melodic_stats(pitches):
    ambitus = max(pitches) - min(pitches)
    motion = np.abs(np.diff(pitches))
    return {
        "ambitus": ambitus,
        "avg_motion": motion.mean(),
        "max_leap": motion.max()
    }

melodic_stats(melody)
```

---

## 4. Essential points vs ornamental detail

A **critical part of curve analysis** is reduction:

- isolate **essential points**
- suppress **auxiliary neighbors and passings**
- reveal **higher-level direction**

This parallels:
- tonal reduction
- linear-function analysis
- Schenkerian abstraction (without requiring its ideology)

### Python: extracting essential points (simple heuristic)

```python
def essential_points(pitches, threshold=2):
    essentials = [pitches[0]]
    for i in range(1, len(pitches)-1):
        if abs(pitches[i] - pitches[i-1]) >= threshold:
            essentials.append(pitches[i])
    essentials.append(pitches[-1])
    return essentials

essential_points(melody)
```

---

## 5. Period melody (Haydn): curve as form

In Ex. 1-30:

- Phrase 1: **overall descent**
- Phrase 2: **descent + ascent**
- Phrase 2 exceeds Phrase 1 → **new high point**

Thus:
- motivic sameness
- registral expansion
- formal differentiation

### Python: phrase-level curves

```python
phrase1 = np.array([65, 64, 62])
phrase2 = np.array([65, 67, 72, 65])

melodic_stats(phrase1), melodic_stats(phrase2)
```

---

## 6. Reduced curve = higher structural level

Ex. 1-30b shows:

- f² → c² → f² → c³ → f²  

These pitches are essential because of:
- formal role (initiation / cadence)
- duration / repetition
- metric placement
- registral extremity
- manner of approach
- **central tonal function**

> **Centrality in the tonality** is the decisive criterion.

### Python: tonal centrality weighting

```python
def tonal_weight(pitch, tonic, prominence):
    distance = abs(pitch - tonic)
    return prominence / (distance + 1)

# tonic F = 65
tonal_weight(65, 65, prominence=3), tonal_weight(72, 65, prominence=2)
```

---

## 7. Dominant-based melodic design (important insight)

The Haydn example avoids tonic repose:

- Essential pitches are **dominant and supertonic of dominant**
- Melody expresses **dominant harmony**
- Resolution deferred to the Allegro

Thus:

> Melodic curve can **project harmonic function** without harmonic change.

### Python: dominant emphasis detector

```python
def dominant_bias(essential_pitches, tonic, dominant):
    return sum(1 for p in essential_pitches if p in [dominant, dominant+2])

essential = [65, 60, 65, 72, 65]  # f–c–f–c–f
dominant_bias(essential, tonic=65, dominant=72)
```

---

## 8. Extreme curve: Boulez (serial context)

In Boulez (Ex. 1-31):

- Curve spans nearly entire keyboard
- Leaps are extreme and constant
- High/low points are adjacent
- No repetition of pitch, rhythm, or motive
- Contrast is **permanent**

Result:

> Extreme differentiation paradoxically **destroys contrast**.

### Python: contrast saturation

```python
def contrast_saturation(intervals):
    return np.std(intervals)

# extreme intervals
extreme_intervals = np.array([24, 19, 17, 22, 21, 18])
contrast_saturation(extreme_intervals)
```

High variance → perceptual overload.

---

## 9. Why coherence fails perceptually (Boulez)

Despite strict serial order:

- no hierarchy
- no repetition
- no tonal gravity
- no stable curve regions

Hence:
- difficulty in segmentation
- resistance to memory
- “Brownian motion” effect

### Python: predictability proxy

```python
def predictability(pitches):
    unique = len(set(pitches))
    return 1 / unique

predictability(melody), predictability(np.arange(88))
```

Lower predictability → weaker apprehension.

---

## 10. Curve alone is not enough

Even in Boulez, some unity exists:

- wedge-like overall shape
- convergence toward middle register
- consistent dynamics

But:

> Without **hierarchy**, curve becomes **statistical**, not expressive.

---

## 11. Core analytical conclusions

1. Melodic curve is a **primary structural dimension**
2. Curve must be read at **multiple levels**
3. Essential points define **direction and meaning**
4. Tonal music uses curve to project **function**
5. Atonal serial music may retain curve but lose **hierarchy**
6. Extreme contrast can negate perceptual contrast
7. Curve without hierarchy risks **randomness of effect**

---

## 12. Condensed theoretical statement

> **The melodic curve is a graphic image of tonal and expressive behavior. Its analytical value depends not on the amount of motion it displays, but on the hierarchical organization of that motion into essential and auxiliary levels. Where hierarchy collapses, curve persists only as statistical fluctuation, resisting apprehension and memory.**

---

If you want next, I can:

- Build a **melodic-curve reduction tool**
- Compare **tonal vs serial curve perception**
- Apply this to **your own generated melodies**
- Integrate curve analysis with **tonal progression/recession**
- Formalize **hierarchy vs randomness metrics**

Just say the direction.