Below is a **theory-driven exposition** of  
## **Some examples of quasi-tonal order in melodic and composite functions**  
showing how **melodic lines and composite textures** can project **tonal hierarchy, progression, and recession** even when harmony is sparse, ambiguous, or post-tonal. I keep the focus on **essential vs auxiliary pitch functions**, **relative centers**, and **composite alignment**, and I formalize each idea with **Python examples**, as you requested.



---

## 1. Quasi-tonal order: what it means

**Quasi-tonal order** refers to situations where:

- There is **no fully articulated harmonic system**, yet
- Pitch behavior exhibits:
  - hierarchy
  - directed motion
  - essential vs auxiliary functions
  - progression and recession

> Tonal order here is **inferred from melodic and composite behavior**, not imposed by harmonic syntax.

This applies equally to:
- modal polyphony (Josquin)
- late-Romantic / early modern melody (Berg)
- Webern’s highly compressed post-tonal lyricism

---

## 2. Melodic tonal fluctuation in modal polyphony (Josquin)

In the **De profundis** subject entries:

- Most voices fluctuate between **final (C)** and **cofinal (G)**
- One voice (altus) is **structured at the level of the fifth above**
- That voice’s most essential point is **G**, not C

This demonstrates:

- **Multiple melodic tonal levels**
- **Local melodic tonics**
- Independence of melodic tonal structure from the global final

### Python: melodic center detection (conceptual)

```python
from collections import Counter

def melodic_center(pitches):
    return Counter(pitches).most_common(1)[0]

# simplified pitch collections
superius = ["G", "A", "G", "F", "G"]
tenor = ["C", "D", "E", "D", "C"]

melodic_center(superius), melodic_center(tenor)
```

---

## 3. Composite tonal function: alignment across voices

When multiple melodic statements are aligned:

- Individual fluctuations **cohere**
- A **composite V → I motion** emerges
- The global tonal order becomes perceptible

The composite sketch (Ex. 1-26b) shows:

- Reduction to **degrees 5–1**
- Omission of local neighbors and passing tones
- Extraction of **structural tonal motion**

### Python: composite reduction

```python
voices = {
    "voice1": ["G", "C"],
    "voice2": ["G", "C"],
    "voice3": ["G", "C"],
    "voice4": ["C", "C"]
}

composite = [v[-1] for v in voices.values()]
composite
```

Result: **collective affirmation of C** despite local divergence.

---

## 4. Auxiliary vs essential pitches in modern melody (Berg)

In the Berg melody:

- Some notes are **clearly auxiliary**
  - appoggiatura-like
  - neighbor tones
  - unfulfilled leading-tones
- Others function as **structural anchors**

Examples:
- db♭ → resolves like an appoggiatura
- g♭ → neighbor to a♭
- f♭ → strong expectation of e♭, left unresolved
- a♭ → functions as a **local tonic**

### Python: classify melodic function by resolution

```python
def melodic_function(note, resolves):
    return "auxiliary" if resolves else "structural"

melodic_function("db♭", resolves=True)
melodic_function("a♭", resolves=False)
```

---

## 5. Rhythm as reinforcement of melodic hierarchy

Although rhythm is not the main focus:

- **Agogic emphasis**
- **Repetition**
- **Placement near peaks or cadences**

All reinforce **essential melodic points**.

In Berg:
- a♭₂ and e♭₃ receive rhythmic emphasis
- ascent is intensified by spacing
- descent is accelerated and conjunct

### Python: agogic weighting

```python
def agogic_weight(duration, repetition):
    return duration + repetition

agogic_weight(duration=2, repetition=1)  # essential
agogic_weight(duration=0.5, repetition=0)  # auxiliary
```

---

## 6. Large-scale melodic architecture (Berg)

The synoptic sketch reveals:

- Triadic basis on **A♭**
- Two-octave ascent to **e♭**
- High point near the midpoint
- Accelerated recessive descent
- Final arrival on **D** (tritone from A♭)

This produces:

- **Strong tonal implication**
- **Deliberate non-closure**
- **Open tonal structure**

### Python: contour analysis

```python
melodic_contour = {
    "start": "A♭",
    "high_point": "E♭",
    "end": "D",
    "relation_end": "tritone"
}

melodic_contour
```

---

## 7. Anticipation and delayed resolution

A crucial quasi-tonal device:

- Early pitch (bb♭) functions as an **anticipation**
- Resolution is **deferred**
- Fulfillment occurs only after intervening motion

This reinforces:
- long-range melodic coherence
- tonal expectation without harmonic confirmation

### Python: anticipation model

```python
anticipation = {
    "pitch": "bb♭",
    "expected_resolution": "a♭",
    "fulfilled_later": True
}

anticipation
```

---

## 8. Bitonal interaction in composite texture (Berg)

The clarinet and piano exhibit:

- **Different tonal trajectories**
- Clarinet → open, tritone-ending line
- Piano → chromatic descent from D to B♭

Yet:
- The clarinet’s final D aligns with
- The piano’s initial tonic D

This produces **composite tonal reconciliation** despite individual ambiguity.

### Python: composite alignment

```python
clarinet_end = "D"
piano_start = "D"

clarinet_end == piano_start
```

---

## 9. Extreme melodic tonality (Webern)

The Webern example shows:

- Strong **leading-tone auxiliaries**
- Clear structural **A**
- G♯ as lower leading-tone
- Carefully bounded registral curve

Despite extreme compression:

- The line behaves **tonally**
- Auxiliaries strongly support a structural center

### Python: leading-tone support

```python
def leading_tone_support(leading, tonic):
    return abs(ord(leading[0]) - ord(tonic[0])) == 1

leading_tone_support("G♯", "A")
```

---

## 10. General principles extracted

From these examples:

1. **Melody alone can project tonal hierarchy**
2. Tonal centers may be **local, relative, or composite**
3. Essential vs auxiliary pitch function is perceptually real
4. Quasi-tonal order persists without harmonic syntax
5. Composite textures often clarify ambiguous lines
6. Tonal implication does not guarantee tonal closure

---

## 11. Summary (condensed)

> **Quasi-tonal order arises when melodic and composite pitch behavior establishes hierarchy, direction, and expectation—even in the absence of functional harmony. Essential pitches, auxiliary orientations, registral design, and composite alignment together create a tonal logic that is felt rather than declared.**

This framework:
- bridges modal, tonal, and post-tonal analysis
- explains tonal perception in sparse textures
- scales from Renaissance polyphony to Webern
- maps cleanly to computational modeling

---

If you want next, I can:

- Build a **melodic-tonal reduction algorithm**
- Quantify **essential vs auxiliary pitch weight**
- Compare **modal vs quasi-tonal melodic order**
- Apply this to **your own generated melodies**
- Integrate this with **Markov or automata models**

Just tell me where to go next.