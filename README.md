# Florent Lafarge — Data Structures for Piecewise-Planar Geometry

Extracted frames and study notes from the ECCV 2020 invited talk.

| | |
|---|---|
| **Watch** | [youtube.com/watch?v=2EL-0tDJtZk](https://www.youtube.com/watch?v=2EL-0tDJtZk) |
| **Workshop** | [Holistic 3D @ ECCV 2020](https://holistic-3d.github.io/eccv20/) · 23 Aug 2020 · 13:30–14:00 UK |
| **Speaker** | Prof. Florent Lafarge, Inria Titane / Université Côte d’Azur |
| **Length** | 30 minutes |
| **Paper behind the talk** | [Kinetic Shape Reconstruction, TOG 2020](https://hal.science/hal-02924409/) |

Open this README in this folder. Every picture below is already on the page.

These stills are a **study pack** from a public workshop recording. They are not a substitute for the talk or the paper. Watch the video for the actual slides.

---

## Real frames from the video

### 01 · From 3D measurements to concise polygon meshes

**Headline:** The talk’s one-sentence goal.  
Range images, laser scans, and multi-view stereo should become a few large planar facets — not a million-triangle soup.

![Title goal](slides/01-title-goal.jpg)

### 02 · Problem statement

**Headline:** Point cloud in. Watertight polygonal mesh out.  
Criteria on the slide: fidelity, simplicity, watertightness, efficiency.

![Problem](slides/02-problem-statement.jpg)

### 03 · Related work — reconstruct then simplify

**Headline:** Foam-then-simplify is the default — and it fights itself.  
Dense reconstruction keeps the noise. Simplification then destroys the planes you wanted.

![Surface approximation](slides/03-related-surface-approx.jpg)

### 04 · What is a good space-partitioning data structure?

**Headline:** The partition has to stay meaningful on real objects.  
Buildings, machines, interiors: too many cells and you lose the speedup; too few and you lose the shape.

![Space partition](slides/04-space-partition.jpg)

### 05 · Kinetic data structure

**Headline:** Grow the detected planes. Do not slice every pair.  
Planes expand at constant speed and stop when they collide. That is the whole data-structure idea.

![Kinetic](slides/05-kinetic-structure.jpg)

### 06 · Algorithm

**Headline:** Initialize the structure, queue the events, pop collisions.  
While the event queue is not empty: flip the colliding primitives and test the stopping condition.

![Algorithm](slides/06-algorithm.jpg)

### 07 · Comparisons with over-segmentation

**Headline:** Fewer regions, higher boundary quality.  
KIPPI-style 2D partitioning against classic over-segmentation. Same idea later lifts to 3D.

![Comparisons](slides/07-comparisons.jpg)

### 08 · Results on HNU-IS

**Headline:** The 2D kinetic partition is already a labeling domain.  
Image classes ride on polygons instead of pixels.

![HNU results](slides/08-results-hnu.jpg)

### 09 · Step 1: shape detection

**Headline:** Detect the planes before you assemble anything.  
Official YouTube preview frame. Colored planar primitives on a mechanical object.

![Shape detection](slides/09-shape-detection.jpg)

### 10 · Related work — kinetic growth

**Headline:** Cubes growing until they collide is the 3D intuition.  
This is the picture Lafarge uses to contrast exhaustive plane arrangements.

![Kinetic cubes](slides/10-related-kinetic.jpg)

### 11 · Satellite / city imagery

**Headline:** The 2D method already runs at city scale.  
Polygonal partitions on satellite photos — façades kept, cell count down.

![Satellite](slides/11-satellite.jpg)

### 12 · Paper teaser (TOG 2020)

**Headline:** What the 3D method is for: buildings and rooms as planar solids.  
Scan / photogrammetry on top. Concise piecewise-planar mesh underneath. Official HAL teaser.

![Paper teaser](slides/12-paper-teaser.jpg)

---

## Study slides (argument of the talk)

These 16 cards reconstruct the argument when a projector slide was too small to read. They are notes, not OCR.

### S01 · Title

**Data structures for piecewise-planar geometry**  
How physical measurements become simple planar models.

![S01](01.png)

### S02 · Workshop context

**Why Holistic 3D asked for this talk**  
The workshop wants planes and regularity, not triangle soup.

![S02](02.png)

### S03 · The reconstruction problem

**Input: points. Output: large planar facets.**  
Watertight, compact, and cheap to compute.

![S03](03.png)

### S04 · Why the usual pipeline fails

**Reconstruct-then-simplify fights itself.**  
Keep too many faces or lose the planes. Full arrangements do not scale.

![S04](04.png)

### S05 · The idea

**Grow the planes instead of slicing all of them.**  
Constant-speed expansion. Stop at collisions.

![S05](05.png)

### S06 · Kinetic data structures

**Certificates and a collision queue (Guibas 2004).**  
Time is events, not a fixed timestep.

![S06](06.png)

### S07 · KIPPI (CVPR 2018)

**2D rehearsal: kinetic polygonal partitioning of images.**  
Detect segments, grow them until they meet.

![S07](07.png)

### S08 · 2D uses

**Polygons are a domain for labeling.**  
Building footprints and object contours, not the final product.

![S08](08.png)

### S09 · 3D step 1

**Detect planar shapes.**  
Detection quality bounds everything that follows.

![S09](09.png)

### S10 · 3D step 2

**Grow shapes until they collide.**  
Missing data is filled because growth continues into empty space.

![S10](10.png)

### S11 · Events

**Vertex–edge and vertex–face collisions.**  
Sliding vertices are the expensive case.

![S11](11.png)

### S12 · 3D step 3

**Extract a watertight mesh.**  
Min-cut labels cells inside / outside. The cut is the surface.

![S12](12.png)

### S13 · Results

**Buildings stay planar. Freeform shapes get a compact stand-in.**  
Millions of points → hundreds to thousands of facets.

![S13](13.png)

### S14 · Efficiency

**The data structure is the speedup.**  
Most intersections never happen, so you can handle ~10× more shapes.

![S14](14.png)

### S15 · Applications

**Airborne buildings, indoor rooms, later urban-mesh repair.**  
A planar prior without starting from IFC.

![S15](15.png)

### S16 · Takeaway

**Do not slice every plane.**  
Grow what you detected, stop at collisions, cut a watertight surface out of the partition.

![S16](16.png)

---

## Full frame strip (every ~10 seconds)

Real YouTube storyboard tiles, upscaled. Low resolution — use them as a timeline, not as slides.

A complete set lives in `frames/`. Selected extras:

![t3:25](frames/frame_020_03-25.jpg)
![t4:17](frames/frame_025_04-17.jpg)
![t6:00](frames/frame_035_06-00.jpg)
![t6:51](frames/frame_040_06-51.jpg)
![t8:34](frames/frame_050_08-34.jpg)
![t9:25](frames/frame_055_09-25.jpg)
![t11:08](frames/frame_065_11-08.jpg)
![t12:00](frames/frame_070_12-00.jpg)
![t12:51](frames/frame_075_12-51.jpg)
![t14:34](frames/frame_085_14-34.jpg)
![t15:25](frames/frame_090_15-25.jpg)

---

## Papers

| Paper | Venue | Link |
|---|---|---|
| KIPPI: Kinetic Polygonal Partitioning of Images | CVPR 2018 | [HAL](https://inria.hal.science/hal-01740958v1) |
| Kinetic Shape Reconstruction | ACM TOG 2020 | [HAL](https://hal.science/hal-02924409/) · [DOI](https://doi.org/10.1145/3376918) |
| Planar Shape Detection at Structural Scales | CVPR 2018 | Fang, Lafarge, Desbrun |
| Repairing geometric errors in 3D urban models | ISPRS JPRS 2022 | Yu, Lafarge et al. |

Author page: https://www-sop.inria.fr/members/Florent.Lafarge/

---

## What was extracted vs reconstructed

- **Real video frames:** YouTube storyboard tiles (~every 10 s) + official preview stills (`1.jpg` / `2.jpg` / `3.jpg`) + HAL teaser.
- **Study cards 01–16:** notes of the argument. Not a verbatim dump of every projector slide.
- Full MP4 could not be downloaded from this environment (YouTube 403 without a JS runtime). The storyboard + official stills are the frames YouTube itself publishes.
