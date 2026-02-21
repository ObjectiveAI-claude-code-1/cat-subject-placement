# Cat Subject Placement: On the Art of Where a Cat Belongs in a Frame

## Purpose

A photograph of a cat is, at its heart, an act of framing. Someone — a person with a camera, a phone, or even a webcam — looked at a cat and decided that a particular slice of the world, bounded by four edges, was worth capturing. The function `cat-subject-placement` exists to evaluate the quality of that decision. Specifically, it answers a deceptively simple question: *does the cat look like it belongs where it is in the photograph?*

This is not a question about the cat itself — whether it is beautiful, expressive, or caught mid-yawn. Nor is it a question about technical photographic merit such as exposure or focus. It is a question about composition, and more precisely, about the relationship between the subject and the space that surrounds it. The function returns a single scalar value — one number — that represents how well the cat has been placed within the frame. A high score means the placement feels intentional, anchored, and visually coherent. A low score means the cat feels like an afterthought, a subject that wandered into a frame that was never designed around it.

The purpose of reducing this evaluation to a single number is not to flatten the richness of photographic composition into a crude ranking. Rather, it is to create a usable signal — one that can be incorporated into larger systems for curating, sorting, or recommending cat photographs. A scalar value can be compared, averaged, thresholded, and combined with other scores. It becomes a building block. But to be a trustworthy building block, it must be rooted in a clear and defensible philosophy of what "good placement" actually means.

## Input

The input to `cat-subject-placement` is a single cat photograph. This means an image — a rectangular grid of pixels — that contains at least one cat as the apparent subject. The function does not need to detect whether a cat is present; it assumes the photograph has already been identified as a cat photograph. What it receives is the full image as its input, and from that image it must reason about spatial relationships: where the cat sits relative to the edges, to the center, to the negative space, and to the overall visual weight of the scene.

It is worth dwelling on what "a cat photograph" means in practice, because the input space is enormously varied. The cat might be a tiny silhouette on a windowsill in a wide landscape-oriented shot. It might be a tight close-up where the cat's face fills nearly every pixel. The cat might be one of two cats, though the function concerns itself with the primary subject. The background might be a cluttered living room, a stark white wall, or a garden bursting with color. The photograph might be vertical or horizontal, square or cinematic. In every case, the function must evaluate the same fundamental question — is the cat well-placed? — but the answer will depend entirely on the specific spatial and visual context of that particular image.

The input is also, implicitly, the product of a human moment. Someone pointed a camera at a cat. The photograph may have been composed carefully by a skilled photographer, or it may have been snapped hastily as the cat leapt off a table. The function does not judge the photographer's skill or intent directly, but it does evaluate the outcome of their choices. A hurried snapshot that happens to place the cat beautifully in the frame should score well. A labored composition that nonetheless leaves the cat feeling adrift should not.

## Use Cases

The most immediate use case is photo curation. Anyone who has scrolled through hundreds of cat photographs — whether a social media platform, a shelter's adoption gallery, or a personal photo library — knows that some images simply *work* better than others, even before you consciously analyze why. Subject placement is one of the invisible forces behind that feeling. A curation system that incorporates `cat-subject-placement` can surface photographs that feel composed and intentional, filtering out those where the cat is awkwardly cropped, shoved into a corner, or lost in a sea of irrelevant background.

A second use case is feedback and education. An aspiring pet photographer, or simply a cat owner who wants better pictures of their companion, could use this function as a gentle guide. By scoring placement, the function offers a structured way to reflect on composition without requiring the user to understand formal photographic terminology. It can answer the question: "I took ten photos of my cat — which ones have the strongest composition?" Over time, a user who pays attention to which photos score well may internalize the principles of placement without ever reading a textbook on the subject.

A third use case is as a component in a larger composite evaluation system. Photograph quality is multi-dimensional. A single image might have gorgeous lighting but poor placement, or perfect placement but an unflattering angle. By isolating placement as its own scalar signal, `cat-subject-placement` becomes one voice in a chorus of evaluators. It can be weighted and combined with scores for lighting, sharpness, expression, and other dimensions to produce a holistic quality assessment. Its power in this context comes precisely from its narrow focus — it does one thing, and it does it legibly.

## Three Qualities to Evaluate

To arrive at a single scalar score for subject placement, the function must evaluate three distinct but interrelated qualities of the input photograph. Each quality captures a different dimension of what it means for a cat to be well-placed in a frame.

### 1. Positional Intentionality

The first quality is positional intentionality — the degree to which the cat's position within the frame feels deliberately chosen rather than accidental. This is not about whether the cat is centered or placed on a rule-of-thirds intersection. A cat sitting dead center in a minimalist frame can radiate intentionality. A cat placed in the lower-left third of a sweeping landscape can feel equally purposeful. What matters is whether the placement communicates a sense of *decision*. The viewer should feel, even subconsciously, that the frame was drawn around the cat — that the boundaries of the photograph exist *because* the cat is where it is.

Accidental placement, by contrast, creates a sense of dissonance. The cat might be technically visible but feel like it drifted into the frame by coincidence. Perhaps it sits at an edge with no compositional reason to be there. Perhaps it occupies a position that creates no visual relationship with the rest of the image. Positional intentionality is, in essence, a measure of whether the cat's location in the frame tells a story — even if that story is simply "here is a cat, and this is exactly where it should be."

Evaluating this quality requires reasoning about the cat's position relative to the frame's geometry — its center, edges, diagonals, and natural anchor points — as well as relative to any other visual elements that might justify an off-center or unconventional placement.

### 2. Spatial Equilibrium

The second quality is spatial equilibrium — the visual balance between the cat and the space that surrounds it. Every photograph is a distribution of visual weight. The cat, as the subject, carries significant weight simply by being the thing the viewer's eye is drawn to. The surrounding space — whether it is a blank wall, a busy street, or a soft bokeh of garden lights — carries its own weight. Spatial equilibrium asks whether these weights feel balanced.

A cat crammed against the right edge of the frame, with a vast expanse of empty floor stretching to the left, is spatially unbalanced — the image feels like it is tipping over. A cat pressed into a corner, with the frame's remaining three-quarters filled with irrelevant clutter, creates a sense of suffocation or neglect. Conversely, a cat given appropriate breathing room — enough surrounding space to feel situated but not stranded — achieves equilibrium. The image feels stable. The viewer's eye can rest on the cat without being pulled uncomfortably toward the void or the clutter.

Spatial equilibrium is not the same as symmetry. An image can be asymmetrical and perfectly balanced if the visual weights on either side of the cat complement each other. A cat looking to the right, with open space in its line of gaze, is asymmetrical but balanced — the empty space has purpose. What spatial equilibrium rejects is *unresolved tension*: the feeling that the cat is fighting the frame rather than inhabiting it.

### 3. Compositional Gravity

The third quality is compositional gravity — whether the cat serves as a clear and stable center of gravity for the image. In a well-composed photograph, the viewer's eye knows where to go. It lands on the subject naturally, drawn there by the arrangement of shapes, lines, and spaces. The cat should be the anchor — the point around which the rest of the image organizes itself.

When compositional gravity is strong, the photograph feels cohesive. The background supports the subject. Leading lines, if present, guide the eye toward the cat. Negative space frames rather than competes. Even in a busy scene, a cat with strong compositional gravity will assert itself as the reason the photograph exists.

When compositional gravity is weak, the image feels unfocused. The viewer's eye may wander, unsure where to settle. The cat might be present but not dominant — perhaps it is the same visual weight as a lamp, a book, or a pattern on the carpet. Or perhaps the cat is isolated in a way that gives the eye nowhere to travel *from* — it lands on the cat but finds no compositional journey, no sense that the image was constructed around this particular anchor point.

Compositional gravity is ultimately about hierarchy. The cat should sit at the top of the visual hierarchy, not because it is the largest object in the frame, but because the composition makes clear that everything else exists in relation to it. This is the quality that transforms a photograph that *contains* a cat into a photograph that is *about* a cat.

## Conclusion

These three qualities — positional intentionality, spatial equilibrium, and compositional gravity — form the philosophical foundation of `cat-subject-placement`. Together, they capture the essence of what it means for a cat to be well-placed in a photograph. Intentionality asks whether the placement was chosen. Equilibrium asks whether the placement is balanced. Gravity asks whether the placement anchors the image. A photograph that excels in all three dimensions will feel effortless and inevitable — as though no other framing could have been right. A photograph that fails in all three will feel like a missed opportunity, a cat that deserved a better frame. The scalar output of this function is, in the end, a measure of that gap — between where the cat is and where the photograph wants it to be.