# cat-subject-placement

A scalar function that scores how well a cat is placed within the frame of a photograph.

## Overview

`cat-subject-placement` answers a deceptively simple question: **does the cat look like it belongs where it is in the photograph?** It returns a single scalar value between 0 and 1 representing the quality of the cat's placement within the frame. This is not a judgment of the cat itself, nor of technical photographic qualities like exposure or focus. It is purely a measure of composition — the relationship between the subject and the space that surrounds it.

A score near **1.0** means the cat's placement feels intentional, anchored, and visually coherent — as though the frame was drawn around the cat. A score near **0.0** means the cat feels like an afterthought, a subject that wandered into a frame that was never designed around it.

The function is agnostic to rigid compositional rules. A cat sitting dead center in a minimalist frame can score just as highly as one placed off-center in a sweeping landscape. What matters is whether the placement feels *chosen*.

## Input

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `cat_photograph` | `image` | Yes | A photograph containing at least one cat as the apparent subject. |

The function assumes the photograph has already been identified as a cat photograph — it does not perform cat detection. The image may be of any orientation, aspect ratio, or style, from tight close-ups to wide environmental shots, and with any kind of background.

### Example

```json
{
  "cat_photograph": "<image>"
}
```

## Output

A scalar value in the range **[0, 1]**, where:

- **1.0** — The cat is perfectly placed. The composition feels effortless and inevitable.
- **0.75** — Strong placement with minor imperfections.
- **0.5** — Adequate placement. The cat is present but the composition is unremarkable.
- **0.25** — Weak placement. The cat feels poorly situated within the frame.
- **0.0** — The cat's placement feels entirely accidental or compositionally absent.

The final score is the averaged result of three independent evaluations, each targeting a distinct quality of subject placement.

## What It Evaluates

The function assesses three compositional qualities. Each captures a different dimension of what it means for a cat to be well-placed in a frame.

### 1. Positional Intentionality

Does the cat's position within the frame feel **deliberately chosen** rather than accidental?

This evaluation examines where the cat sits relative to the frame's geometry — its edges, center, diagonals, and natural anchor points. Strong intentionality means the viewer feels, even subconsciously, that the frame was drawn around the cat. The boundaries of the photograph exist *because* the cat is where it is. Weak intentionality creates dissonance — the cat might be technically visible but feels like it drifted into the frame by coincidence, occupying a position that creates no meaningful relationship with the rest of the image.

**Scores high when:** The cat's position tells a story — whether centered, offset, or unconventionally placed — and the frame feels purposefully constructed around it.

**Scores low when:** The cat sits at an edge or in a position with no compositional justification, creating no visual relationship with the frame's geometry.

### 2. Spatial Equilibrium

Is there **visual balance** between the cat and the surrounding space?

This evaluation examines the distribution of visual weight across the frame. The cat carries significant weight as the subject; the surrounding space — whether blank wall, busy street, or soft bokeh — carries its own. Equilibrium means these weights feel stable. The cat has enough breathing room to feel situated but not so much that it feels stranded. Crucially, balance is not the same as symmetry. An asymmetrical image can be perfectly balanced if the visual weights complement each other — for instance, open space in the direction of a cat's gaze.

**Scores high when:** The cat inhabits the frame naturally, with stable visual weight distribution and any asymmetry feeling purposeful and resolved.

**Scores low when:** The cat is crammed against an edge with vast opposing emptiness, pressed into a corner while clutter dominates the frame, or marooned in space without compositional reason — creating unresolved tension.

### 3. Compositional Gravity

Does the cat serve as the **clear focal anchor** of the image?

This evaluation examines whether the viewer's eye is naturally and immediately drawn to the cat by the arrangement of shapes, lines, spaces, and visual elements. When compositional gravity is strong, the photograph feels cohesive — the background supports the subject, negative space frames rather than competes, and everything exists in relation to the cat. When it is weak, the viewer's eye wanders without a clear destination, or the cat carries the same visual weight as surrounding objects like furniture or carpet patterns, failing to assert itself as the subject.

**Scores high when:** The cat is the unmistakable focal point. The image is clearly *about* the cat, with every other element organized around it.

**Scores low when:** The eye wanders without settling on the cat, or the cat blends into the scene with no more visual authority than the objects around it — making the image feel like it merely *contains* a cat.

## Use Cases

- **Photo curation** — Surface the best-composed cat photographs from large collections, whether for social media platforms, shelter adoption galleries, or personal photo libraries. Filter out images where the cat is awkwardly cropped, shoved into a corner, or lost in irrelevant background.

- **Photography feedback** — Give aspiring pet photographers or cat owners a structured way to evaluate and improve their composition. Score a batch of photos to identify which ones have the strongest placement, building compositional intuition over time.

- **Composite quality systems** — Combine with other scalar evaluators (lighting, sharpness, expression, angle) to build a holistic photograph quality score. `cat-subject-placement` provides an isolated, legible signal for one specific dimension of photographic merit.

## Philosophy

The function is grounded in the belief that good subject placement is not a formula but a feeling — the feeling that a cat belongs exactly where it is in the frame. The three qualities it evaluates capture different facets of that feeling: intentionality asks whether the placement was *chosen*, equilibrium asks whether it is *balanced*, and gravity asks whether it *anchors*. A photograph that excels in all three feels effortless and inevitable. A photograph that fails in all three feels like a missed opportunity — a cat that deserved a better frame.