# Building a walkthrough from an architect's PDF

What was learned building the first floor of the house. Read this before
starting another floor or another house. The method is in `index.html`; this
is the reasoning and the traps.

## 1. Get the walls from the vectors, never from a picture

An architect's PDF is a vector drawing. Every wall line has exact coordinates
in the file, so measuring a raster of it throws away accuracy for nothing.

```
pdfinfo plan.pdf                      # page size, page count
pdftotext -layout plan.pdf -          # usually only the title block; the plan is geometry
pdftocairo -svg -f N -l N plan.pdf pN.svg
```

Parse the SVG's `<path d="...">` elements, applying every enclosing `<g
transform>` (matrix and translate both occur). Keep the coordinates in PDF
points. The sheet's scale is in its title block: 3/16" = 1'-0" means 13.5 pt
per foot. The model stores every wall in points and converts with one
constant, so any number can be checked against the sheet.

Line style tells you what a line is, on this architect's sheets:

| Stroke | Colour | Meaning |
|---|---|---|
| 1.08 | black | new walls, wall faces |
| 0.72 | black | windows in new walls |
| fill 91.8% grey, outline 66.7% grey | | existing walls, hatched |
| 0.48 | black | counters, fixtures |
| 0.25 | black | furniture, rugs, hairline symbols |

Cluster axis-aligned segments by coordinate and read them like a table. Two
parallel lines a few points apart are a wall; the gap between two collinear
pieces is an opening; a 0.72 stroke inside a wall zone is a window. Closed
rectangles found by matching horizontal and vertical pairs are fixtures, and
their sizes identify them (a 3'x3' square in a bathroom is the shower, a
2'-7"-wide hairline rectangle is a runner rug, a 2' deep run is counter).

Check the scale against the sheet's own labels before building: the kitchen
came out 27'-4" x 15'-11" against a labelled 27' x 16'. If that does not
agree, the scale or the page rotation is wrong.

## 2. Coordinates: the one thing that keeps biting

The sheet's y grows toward the front of the house (down the page). The model's
z is `(py - 691.8) / 13.5`, so z also grows toward the front. **North is the
smaller y and the more negative z.** Every bug of the form "the range's
north end was really its south end", "the wall box's z extent was reversed",
"the floor test never recognised the footprint" came from forgetting this.
When naming two ends of something, name them from z, not from y, and when
writing a range test, order the pair with `Math.min/max` or check with
`fz(a) < fz(b)`.

## 3. Build everything from the data, and make the check part of the page

- Walls are rectangles in points with openings cut out of them: separate
  pieces for the wall beside a window, the sill below it and the head above.
- Plan view is an orthographic camera looking down, and **Show drawing**
  draws the sheet's own vector lines over the 3D model through the same
  mapping. If a wall is wrong you see it. This is the accuracy proof; keep it.
- Rooms are rectangles too, for the readout and labels. A room whose edge
  steps (the study around its closet) needs its paint, crown and cladding
  to follow the real outline, not the bounding rectangle, or a panel stands
  across the doorway.
- Never paint or clad a wall face across a window or a doorway. Cut around
  them. Same for upper cabinets and backsplash: find the window spans from
  the wall list and only fill the solid stretches.

## 4. Collision, and what goes wrong with it

- The `box()` helper registers a collision box for every box unless told
  `solid: false`. Headers over doors and the slider are boxes. The first
  version sealed every doorway on the floor this way.
- Door leaves standing open land in the wrong place easily: the front door
  hung on the west jamb stood across the living-room opening; the closet's
  open leaf stood in the hall opening because the closet's jamb *is* that
  opening. Rehanging a door means removing the old leaf, not adding one.
  The owner said doors are not needed: `leaf: false` gives an open doorway.
- Furniture placed from the sheet can block things the sheet did not have:
  the deck sofa sat behind the new screen door.
- Visual-only pieces need no collider; the shower glass, the range and the
  island overhang each needed one added by hand because they are not boxes.
- A player standing inside a collider is allowed to move freely so they can
  get out. This is right for play and wrong for tests: a walk test started
  inside the toilet walks through everything and proves nothing. Check
  `collide(x, z)` is false at the start of every scripted walk.

## 5. Verification that actually catches things

All driven through `window.__house` in the page.

- **Flood fill** on a 6" grid through `collide()` from the entry. Every
  room, the porch, deck, stoop and lawn must be reached; zero reached cells
  may lie inside a solid wall. Probe points must be on clear floor; room
  centres land in furniture and fail for the wrong reason.
- **Scripted walks** with `tick(1/60)`. The automation tab is hidden, so
  `requestAnimationFrame` never fires between commands; the loop's body is
  exposed as `tick` for exactly this reason. Reload with a cache-busting
  query string, or a stale page is tested.
- **Range finder** against known distances: stand 10 ft from a wall, read
  10'-0". Two readings from the middle of a room sum to its width.
- **Eye height through every doorway**: the lowest camera height seen on a
  walk across each kind of opening. A dip means the floor test is wrong.
- A screenshot from a stated position and heading after each change. Look
  at it; the walk tests do not see a shiplap panel across a doorway.

## 6. Scale on a screen

The walls were right and the rooms still felt small. It was the lens. A
monitor at arm's length covers about 50° of view; the first version rendered
70° vertical, about 100° across on a widescreen, so everything sat at half
size. Hold the horizontal field of view constant regardless of window shape
and expose it. The owner settled on 100° after trying 55°; leave the choice
to them.

Everything the eye uses as a ruler must be the standard size, since the
sheet has no heights: doors 6'-8", window heads level with door heads, 36"
counters, 7-1/2" risers, 4-1/2" baseboards, floor planks and tile drawn at
true size. Eye at 5'-5", walking at an indoor 3.2 ft/s, body radius 8".
Ceiling height is a guess; put it on the page and rebuild on change.

## 7. Dressing rooms to a reference photo

Keep every footprint from the sheet; change only detail and look. Read the
photo for a short list of what makes it: cabinet colour and style, pulls,
counter, backsplash, lighting, the two or three signature objects. Build
those from boxes, cylinders and canvas textures, and stop. Give every fixed
piece a floating label so nothing has to be guessed at. After dressing a
room, re-run the flood fill: a small room fills up fast and the walkable
area can drop to a sliver without anything looking wrong.

## 8. Working method

- One HTML file. Edits are Python patch scripts with exact-match asserts
  that abort before writing; if a step says NOT FOUND, nothing changed, so
  fix the anchor and re-run the whole script.
- `node --check` on the extracted script after every edit.
- Serve from the repo root; verify in the browser; commit per change with a
  message that says what was wrong and how it was verified; republish the
  same artifact URL.

## 9. For the next floor

PR-02 and PR-00 are on the same PDF at the same scale, so the extraction is
the same command with a different page. The stair position agrees across the
three sheets within a few inches, which fixes the floors' registration to
each other. The build is already a function that can be torn down and
rebuilt, so a floor selector is a matter of swapping the data and the floor
height. The second floor's rooms are on the sheet; its heights are not.

## 7. A third sheet, and a stair that goes both ways

The basement sheet registered by the centre of the footprint, not by any
one wall: its foundation is drawn a few inches inside the framing above, so
inner and outer faces cannot both match. Check the registration with the
plan view's drawing overlay before trusting a single room.

Where the architect's sheet contradicts the existing-conditions set and the
owner (the stair arrow, a hallway absorbed into storage), the existing set
wins for existing construction: the owner's photo of the hall settled it.
Note the departure in the README so the next person does not "fix" it back.

One stair box carries two runs: up from the south end, down from the north
end beneath it. The ramp for the feet computes both heights and takes the
one nearer the player's current height, so entering from either end does
the right thing and a sideways step mid-run keeps you on the run you were
on. The floor above needs a hole over the box, the treads above need a
soffit, and the space under the top of the down-run is closed off.

Sloping ground cannot be one plane once there is a basement: it would pass
through the rooms. Build it in pieces around the footprint, each following
the same grade function the player's feet use, and choose the colliders by
the player's height when they are outside at basement level, or the first
floor's walls stop them at the side entry.

## 8. The lot came from a DWG

The surveyor's plot plan was a DWG in the repo. `dwg2dxf` (libredwg) turns
it into text; the DXF's ENTITIES section pairs group codes with values, and
a hundred lines of Python read LINE, LWPOLYLINE, INSERT, TEXT and the
survey-point blocks with their ELEV attributes. Bearings on the property
lines give the lot's orientation (the street runs N75°E), and the house
footprint on the plan is the same 30'-3" wall as the sheets, which is how
the plan registers to the model: rotate into the lot's frame, then shift
so the house's west and front walls land where the sheets put them.

Interpolate the spot elevations (inverse distance) onto a grid in the
model's frame and embed the grid; the ground, the driveway, the walk and
the player's feet all read the same function. Add a few synthetic points
where the design regrades (under the deck, at the side entry) so the built
surfaces sit on the ground rather than in it.

Do not render 700 frames in one scripted call to test a walk: the browser
drops the WebGL context. Two hundred is fine.
