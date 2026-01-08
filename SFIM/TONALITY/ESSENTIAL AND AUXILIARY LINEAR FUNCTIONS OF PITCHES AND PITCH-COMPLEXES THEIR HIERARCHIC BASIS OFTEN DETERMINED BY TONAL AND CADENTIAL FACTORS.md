Below is a **focused synthesis of the passage**, centered on the **complementarity of tonal function and linear function**, the **interpretive (non-absolute) nature of linear hierarchy**, and the **primacy of cadence and multileveled function**—with **Python examples throughout** that formalize the ideas without reducing them to mere chord labels.



---

## 1. Central Premise: Linear Function as Interpretive Structure

The chapter’s premise is explicit:

> Harmonic and melodic analysis complements tonal function by **identifying essential vs auxiliary linear functions** in the stream of events.

Key consequences:
- Linear analysis is **interpretive**, not absolute
- Judgments are **context-dependent**
- Multiple interpretations can be **equally plausible**
- Only in rare cases is there a single “right” reading

### Python: Interpretive (Non-Boolean) Linear Classification

```python
class LinearAssessment:
    def __init__(self, event):
        self.event = event
        self.weights = {}  # degrees of plausibility

    def add_interpretation(self, label, weight):
        self.weights[label] = weight  # not exclusive

assessment = LinearAssessment("A minor triad")
assessment.add_interpretation("essential", 0.6)
assessment.add_interpretation("auxiliary", 0.4)

assessment.weights
```

This encodes:
> “The conclusions reached constitute an interpretation of linear functions.”

---

## 2. Linear Function Is Conditioned by Tonal Function (and More)

Linear value is shaped by:
- **Tonal function** (primary vs secondary systems)
- **Rhythm / meter**
- **Stress**
- **Duration**
- **Reiteration**
- **Cadential placement**

At lower levels—and in non-tonal styles—**non-PC factors dominate**.

### Python: Multi-Factor Structural Weight

```python
def structural_weight(tonal_role, cadence, stress, duration):
    score = 0
    score += {"primary": 3, "secondary": 2, "auxiliary": 1}[tonal_role]
    score += 3 if cadence else 0
    score += stress
    score += duration
    return score

structural_weight("secondary", cadence=True, stress=1, duration=2)
```

---

## 3. Cadence as the Anchor of Essential Function

A core claim:

> **Cadential events are invariably essential at some level.**

But:
- Weaker cadences are **auxiliary** to stronger ones
- Strength depends on:
  - registral placement
  - harmonic distribution
  - metric prominence
  - approach
  - **position in form**
  - **position within primary vs secondary systems**

### Python: Cadence Strength Model

```python
class Cadence:
    def __init__(self, level, form_role):
        self.level = level              # foreground/middle/background
        self.form_role = form_role      # preliminary/conclusive

    def strength(self):
        return {"conclusive": 3, "preliminary": 1}[self.form_role] + \
               {"background": 3, "middleground": 2, "foreground": 1}[self.level]

Cadence("background", "conclusive").strength()
```

---

## 4. Tonal Music: Essential Frame = I and V

In conventionally tonal music:
- **I and V** dominate the essential structural frame
- **IV** is a frequent auxiliary
- Other diatonic harmonies are heard as **derivatives or substitutes**:

| Harmony | Typical Interpretation |
|------|----------------|
| ii | IV-like |
| vi (after V) | delayed I |
| vii° | V-like |
| iii | V-like (PC overlap) |

### Python: Functional Substitution Map

```python
functional_equivalence = {
    "ii": "IV-like",
    "vi": "delayed-I",
    "vii°": "V-like",
    "iii": "V-like"
}

functional_equivalence
```

This underlies distinctions between **essential vs auxiliary** in the linear stream.

---

## 5. Tonal Primacy Overrides Duration (Agogic Illusion)

A decisive empirical observation:

> Even if a dissonant harmony lasts longer than its resolution,  
> the **resolution remains structurally superior**.

Examples:
- Dominant 7th vs tonic
- Appoggiatura vs resolution
- Dominant over tonic pedal

### Python: Resolution Supremacy Test

```python
def structural_priority(dissonant_duration, resolution_duration):
    return "resolution-superior"

structural_priority(8, 1)
```

This encodes:
> “No ear would deny the superior structural value of the resolution.”

---

## 6. Case Study: Bach, WTC I, Prelude No. 1

[Well-Tempered Clavier, Book I](chatgpt://generic-entity?number=0)

The prelude illustrates:
- **Prolongation of I**
- **Auxiliary embellishments**
- **Passing harmonic streams**
- **Cadential affirmation**

Linear descent complements tonal recession toward the cadence.

### Python: Prolongation with Passing Auxiliaries

```python
harmonic_stream = [
    {"chord": "I", "role": "essential"},
    {"chord": "iii", "role": "auxiliary"},
    {"chord": "V", "role": "auxiliary"},
    {"chord": "I", "role": "essential"}
]

harmonic_stream
```

---

## 7. Multiple (Multileveled) Harmonic Function

A cornerstone of the theory:

> A harmony can have **two or three simultaneous functional identities**.

Example from the text:
- **A minor triad** =
  - vi (primary system)
  - ii (secondary system)
  - ii/V (primary system)

This is **not inconsistency**—it reflects how harmony is heard.

### Python: Multileveled Roman-Numeral Encoding

```python
class MultiFunctionHarmony:
    def __init__(self, chord):
        self.chord = chord
        self.functions = []

    def add_function(self, system, rn):
        self.functions.append((system, rn))

A_minor = MultiFunctionHarmony("A minor")
A_minor.add_function("primary", "vi")
A_minor.add_function("secondary", "ii")
A_minor.add_function("primary", "ii/V")

A_minor.functions
```

---

## 8. Passing vs Embellishing Secondary Systems

Secondary systems divide into:
1. **Embellishing** (neighboring, surrounding)
2. **Passing / transitional** (linking regions)
3. **Parenthetical** (structurally informative, perceptually weak)

At the **broadest level**, *all* expand the primary system.

### Python: Secondary System Typology

```python
secondary_systems = [
    {"tonic": "G", "type": "embellishing"},
    {"tonic": "F", "type": "embellishing"},
    {"tonic": "Bb", "type": "parenthetical"}
]

secondary_systems
```

---

## 9. Linear Descent as Melodic–Tonal Complement

In the Bach example:
- Harmonic motion → I
- Linear motion → descending
- Together they produce **recessive closure**

### Python: Complementary Motion

```python
tonal_motion = ["ii", "V", "I"]
linear_motion = ["E", "D", "C"]

list(zip(tonal_motion, linear_motion))
```

---

## 10. Key Takeaways (Compressed)

| Principle | Meaning |
|---|---|
| Linear function | Interpretive, contextual |
| Essential vs auxiliary | Not absolute |
| Cadence | Anchor of structure |
| I & V | Core of tonal frame |
| Duration | Secondary to resolution |
| Multileveled function | Normal, not exceptional |
| Roman numerals | May legitimately multiply |

---

## 11. Why This Matters

This framework:
- Explains **depth of tonal hearing**
- Accounts for **simultaneous meanings**
- Avoids false binaries (right/wrong analysis)
- Bridges **Schenkerian reduction** and **functional harmony**
- Scales from **Bach to late chromatic tonality**

If you want next, I can:
- Encode a **linear–tonal reduction engine**
- Formalize **cadence strength metrics**
- Apply this to **Mozart, Beethoven, Brahms**
- Translate this into **MIDI or symbolic analysis**
- Build a **graph of multileveled harmonic meaning**

Just tell me the direction.