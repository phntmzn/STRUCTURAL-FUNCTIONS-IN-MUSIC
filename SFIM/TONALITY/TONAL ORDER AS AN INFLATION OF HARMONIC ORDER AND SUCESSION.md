Below is a **tight theoretical unpacking** of the passage you shared, centered on the idea that **tonal order is an inflation of harmonic order**, with **tonal rhythm**, **tonicization as structural expansion**, and **secondary tonal systems** functioning like enlarged harmonic events. As requested, **every section includes Python examples** that formalize the ideas.



---

## 1. Tonal Order as an Inflation of Harmonic Order

The author pauses to make an explicit equivalence:

> **Tonal hierarchy is directly analogous to harmonic hierarchy—only inflated.**

This means:
- Harmonic rhythm → **tonal rhythm**
- Harmonic succession → **tonal succession**
- Harmonic function → **tonal-system function**

What changes is **scale**, not **principle**.

### Python: Harmonic → Tonal Inflation

```python
class HarmonicFunction:
    def __init__(self, label):
        self.label = label

class TonalFunction:
    def __init__(self, tonic, role):
        self.tonic = tonic
        self.role = role  # primary, secondary, passing

# IV as harmony vs SD as tonal system
IV_harmony = HarmonicFunction("IV")
SD_tonal = TonalFunction("F", "secondary")

IV_harmony.label, SD_tonal.tonic, SD_tonal.role
```

This captures:
> “IV becomes SD… the basis for a secondary tonal system.”

---

## 2. Tonicization = Structural Expansion

Tonicization is not merely:
- adding accidentals
- coloring harmony

It is:
- the **creation of a temporary tonal system**
- expanding the **primary tonal system**

Thus:
- IV → SD
- V → D
- ii → SD/SD (etc.)

### Python: Tonicization as System Creation

```python
def tonicize(scale_degree, primary_tonic):
    return {
        "new_tonic": scale_degree,
        "parent_tonic": primary_tonic,
        "type": "secondary tonal system"
    }

tonicize("F", "C")
```

---

## 3. Tonal Rhythm vs Harmonic Rhythm

Just as chords occur with rhythmic pacing, **tonics also appear with duration, emphasis, and succession**.

- Short tonicization → weak tonal beat
- Extended tonicization → strong tonal beat

### Python: Tonal Rhythm Timeline

```python
tonal_rhythm = [
    ("E", 8),   # prolonged tonic
    ("F#", 2),  # brief tonicization
    ("B", 2),
    ("E", 6)
]

tonal_rhythm
```

---

## 4. Large-Scale Form as Inflated Harmony

The author’s hypothetical example is striking:

> A five-part rondo can be understood as an **inflation of a simple harmonic progression**.

This implies:
- Formal sections = **expanded harmonic functions**
- Tonal returns = **prolonged resolutions**

### Python: Rondo as Harmonic Inflation

```python
harmonic_skeleton = ["I", "V", "IV", "V", "I"]

rondo_form = {
    "A": "I",
    "B": "V",
    "A'": "I",
    "C": "IV",
    "A''": "I"
}

harmonic_skeleton, rondo_form
```

---

## 5. Chopin, Prelude No. 9: Tonal Expansion in Practice

[Prelude No. 9 in E major, Op. 28](chatgpt://generic-entity?number=0)

In **Ex. 1-18a**, Chopin presents:
- A **primary tonic**: E
- A sequence of **tonicized factors**
- A sense of **continuous tonal expansion**

In **Ex. 1-18b**, the entire passage is shown as:
- a **prolongation of E:I**
- with **passing secondary tonics** embellishing it

### Python: Prolonged Tonic with Passing Tonics

```python
tonal_expansion = [
    {"tonic": "E", "role": "primary"},
    {"tonic": "F#", "role": "passing"},
    {"tonic": "C#", "role": "passing"},
    {"tonic": "E", "role": "restoration"}
]

tonal_expansion
```

---

## 6. Linear Expression of a Prolonged Tonic

The reduction in Ex. 1-18b shows:
- Root
- Third
- Fifth  

…of the tonic **distributed linearly**, not vertically.

### Python: Linearized Tonic Components

```python
prolonged_tonic = {
    "tonic": "E",
    "linear_factors": ["E", "G#", "B"]
}

prolonged_tonic
```

This shows:
> “Linear expression of the factors of the prolonged tonic.”

---

## 7. Enharmonic–Diatonic Succession (Pivot Function)

A crucial device here is:
- **Enharmonic reinterpretation**
- Allowing a pitch to:
  - look backward (as part of one tonicization)
  - look forward (as dominant of another)

Example:
- E♯ ↔ F  
- Diminished 7th chord acting pivotally

### Python: Enharmonic Pivot Model

```python
enharmonic_pivot = {
    "pitch": "E#",
    "backward_function": "leading-tone of F",
    "forward_function": "iii of E"
}

enharmonic_pivot
```

---

## 8. The “Vagrant” Diminished Seventh

The diminished 7th chord is described as:
- **Vagrant**
- Directionally ambiguous
- Capable of resolving in multiple tonal directions

It:
- Looks back to the prior tonicization
- Looks forward to the next

### Python: Vagrant Diminished 7th

```python
diminished_7th = {
    "type": "vagrant",
    "can_resolve_to": ["F", "Ab", "B", "D"],
    "function": "pivot dominant"
}

diminished_7th
```

---

## 9. Key Theoretical Takeaways (Compressed)

| Concept | Meaning |
|------|--------|
| Tonal order | Inflated harmonic order |
| Tonal rhythm | Duration & pacing of tonics |
| Tonicization | Creation of secondary systems |
| Form | Expanded harmonic process |
| Passing tonics | Linear embellishments |
| Enharmonic pivot | Directional hinge |
| Diminished 7th | Multi-directional dominant |

---

## 10. Why This Matters

This framework allows you to:
- Hear **form as harmony at scale**
- Understand **tonal motion as rhythm**
- Analyze Chopin, Liszt, Wagner, Brahms without key-chasing
- Model tonal structure computationally
- Unify harmony, tonality, and form under one logic

If you want next, I can:
- Build a **tonal-rhythm analyzer**
- Encode **enharmonic pivot detection**
- Map **form → harmonic inflation**
- Apply this to **late Romantic or Wagnerian tonality**
- Translate this into **algorithmic composition rules**

Just say the direction.