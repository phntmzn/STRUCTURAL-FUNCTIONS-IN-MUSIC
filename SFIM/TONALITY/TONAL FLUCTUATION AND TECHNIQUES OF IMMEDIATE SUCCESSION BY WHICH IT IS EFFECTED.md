Below is a **concise but structurally complete exposition** of **TONAL FLUCTUATION AND TECHNIQUES OF IMMEDIATE SUCCESSION BY WHICH IT IS EFFECTED**, aligned with the theoretical framework you’ve been developing. I treat **tonal fluctuation as inflated harmonic succession**, operating through **immediate linear techniques**, and I formalize each idea with **Python examples**, as requested.



---

## 1. Tonal Fluctuation: Definition

**Tonal fluctuation** is the **temporary displacement of tonal reference** away from the primary tonic through **local or extended tonicization**, without necessarily constituting large-scale modulation.

Key properties:
- Always **hierarchic**
- Defined by **level** and **duration**
- Can be **embellishing**, **passing**, or **structurally transformative**
- Operates through **immediate succession**, not abstract key change

> Tonal fluctuation is to tonality what **passing motion** is to harmony.

---

## 2. Tonal Fluctuation as Inflated Harmonic Succession

At its core:

| Harmonic level | Tonal level |
|---|---|
| V → I | D/T → T |
| IV → V | SD → D |
| passing chord | passing tonic |

Thus, tonal fluctuation is an **inflation of harmonic motion** into **tonic motion**.

### Python: Harmonic → Tonal Inflation

```python
def inflate_harmony_to_tonality(harmonic_function, primary_tonic):
    inflation_map = {
        "I": primary_tonic,
        "V": f"D/{primary_tonic}",
        "IV": f"SD/{primary_tonic}",
        "ii": f"SD/SD/{primary_tonic}"
    }
    return inflation_map.get(harmonic_function, "auxiliary")

inflate_harmony_to_tonality("V", "C")
```

---

## 3. Immediate Techniques of Tonal Fluctuation

Tonal fluctuation is effected **locally**, through **immediate successions**, not abstract modulation plans. The principal techniques are below.

---

## 4. Secondary Dominants (Direct Tonicization)

**Mechanism**  
A harmony acquires tonic force by being preceded by its dominant.

**Effect**
- Creates a **local tonic**
- Embellishes the primary system
- Rarely threatens primary dominance at higher levels

### Python: Secondary Dominant Detection

```python
def is_secondary_dominant(chord, resolves_to):
    return chord.startswith("V/") and chord.endswith(resolves_to)

is_secondary_dominant("V/G", "G")
```

---

## 5. Chromatic Linear Motion (Especially in the Bass)

A **chromatic bass line** can smooth otherwise remote tonal shifts, making fluctuation feel inevitable.

**Function**
- Reduces perceptual distance
- Masks tonal departure
- Conditions return

### Python: Chromatic Descent as Tonal Bridge

```python
chromatic_bass = ["C", "B", "Bb", "A", "Ab", "G"]
tonal_targets = ["C", "G"]

list(zip(chromatic_bass, tonal_targets + ["passing"]*(len(chromatic_bass)-2)))
```

---

## 6. Enharmonic Reinterpretation (Pivot Technique)

A pitch or harmony:
- **Looks backward** as part of one system
- **Looks forward** as a functional agent in another

This is especially powerful with:
- diminished 7th chords
- augmented sixth reinterpretations

### Python: Enharmonic Pivot Object

```python
pivot = {
    "symbol": "dim7",
    "retrospective_function": "leading-tone of F",
    "prospective_function": "dominant of A"
}

pivot
```

---

## 7. Passing Secondary Tonics (Connective Fluctuation)

Some secondary tonics:
- Do **not** embellish the primary tonic directly
- Instead **link** two systems
- Function like **passing harmonies**

### Python: Passing Tonal Systems

```python
passing_tonics = [
    {"tonic": "G", "role": "passing"},
    {"tonic": "F", "role": "passing"}
]

passing_tonics
```

---

## 8. Parenthetical Tonal Systems

A **parenthetical system**:
- Is **structurally implied**
- Has **weak perceptual force**
- Helps explain **direction**, not focus

### Python: Parenthetical System Flag

```python
def classify_tonal_system(duration, cadential_support):
    if duration < 2 and not cadential_support:
        return "parenthetical"
    return "active"

classify_tonal_system(duration=1, cadential_support=False)
```

---

## 9. Cadential Strength Governs Tonal Weight

Tonal fluctuation is **validated or negated** by cadence.

| Cadence type | Tonal status |
|---|---|
| strong authentic | structural |
| weak / evaded | auxiliary |
| absent | parenthetical |

### Python: Cadential Validation

```python
def tonal_validity(cadence_strength):
    if cadence_strength >= 3:
        return "structural tonic"
    if cadence_strength == 2:
        return "secondary tonic"
    return "embellishing tonic"

tonal_validity(1)
```

---

## 10. Multileveled Tonal Interpretation

A single tonal event may simultaneously be:
- Tonic at one level
- Dominant at another
- Passing at a broader level

This is **ambivalence**, not contradiction.

### Python: Multilevel Tonal Meaning

```python
tonal_event = {
    "foreground": "G (tonicized)",
    "middleground": "D/T",
    "background": "embellishment of C"
}

tonal_event
```

---

## 11. Tonal Fluctuation vs Modulation

| Feature | Fluctuation | Modulation |
|---|---|---|
| duration | brief | extended |
| cadence | weak / absent | strong |
| hierarchy | subordinate | reorganized |
| return expected | yes | no |

### Python: Classification Rule

```python
def classify_change(duration, cadence):
    if duration > 8 and cadence >= 3:
        return "modulation"
    return "tonal fluctuation"

classify_change(duration=3, cadence=1)
```

---

## 12. Summary of Techniques

| Technique | Function |
|---|---|
| secondary dominants | direct tonicization |
| chromatic bass motion | smoothing distance |
| enharmonic pivots | directional ambiguity |
| passing tonics | connective expansion |
| parenthetical systems | directional logic |
| cadential validation | structural authority |

---

## 13. Core Theoretical Claim (Condensed)

> **Tonal fluctuation is the linear, hierarchical expansion of harmonic motion into tonic motion, effected through immediate successions and validated by cadence and return.**

This concept:
- Unifies harmony, tonality, and form
- Explains chromatic idioms without abandoning tonal hearing
- Scales from Bach → Chopin → Liszt → late Romantic music
- Is directly translatable into computational analysis

---

If you want next, I can:

- Formalize **tonal fluctuation graphs**
- Build a **tonal-distance metric**
- Encode **immediate succession rules**
- Apply this framework to **one complete work**
- Translate it into **algorithmic composition logic**

Just tell me where to go next.