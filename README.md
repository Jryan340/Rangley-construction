# 33 Temple St · First Floor

A first-person walkthrough of the proposed first floor from sheet PR-01 of the
09/27/26 floor plans. One self-contained HTML file.

Open [`index.html`](./index.html) in any browser and click to walk. W A S D
moves, the mouse looks, Shift hurries, P switches to a top-down plan view, and
Esc releases the mouse. On a phone the left half of the screen is a stick and
the right half looks.

## Where the dimensions come from

The walls were not measured off a picture of the plan. The PDF is a vector
drawing, so every wall line on the sheet has exact coordinates in it. Those
coordinates were read out of the file and used directly: the model's wall
rectangles are written in the sheet's own units, PDF points, and converted
with the sheet's stated scale of 3/16" = 1'-0", which is 13.5 points per foot.
Nothing was rounded to a whole foot on the way in.

The check is built into the page. **Plan view** looks straight down at the 3D
model, and **Show drawing** lays the architect's wall lines over it through the
same camera. The two either sit on each other or they visibly do not. They sit
on each other, at every wall, window opening and partition, including the 3'
shower stub in the bathroom.

Read back from the model, against the sheet's labels:

| Room | On the sheet | Clear inside, from the vectors |
|---|---|---|
| Kitchen / Dining | 27' x 16' | 27'-4" x 15'-11" |
| Living | 21' x 12'-6" | 21'-2" x 12'-5" |
| Entry | 7' x 8'-6" | 7'-0" x 8'-1" |
| Bathroom | 9' x 6' | 9'-1" x 5'-11" |
| Study | 9' x 8'-6" | 9'-1" x 8'-8" |
| Hall | | 3'-6" wide beside the stair |
| Vestibule to the study | | 9'-1" x 3'-6" |
| Closet | | 4'-11" x 2'-0" |
| Screened porch / deck | | 15'-2" x 9'-5" / 12'-6" x 9'-5" |
| Existing exterior walls | | 6" |
| Addition exterior walls | | 9-1/4" |
| Partitions | | 4-1/2" to 5" |

The entry reads 8'-1" rather than 8'-6" because the model takes the stair's
bottom riser as the room's edge; the sheet's 8'-6" runs under the stair.

## What is on the floor

The addition is the kitchen and dining room across the back, 27' wide, with
three windows on the west wall, two on the east, a 12' four-panel slider onto
the deck between two more windows, an 8' island with three stools, a 2' deep
run of counters down the east wall, and the fridge,
pantry and a corner cabinet along the old rear wall. The old rear wall is
opened across 17' between the living room and the hall.

The existing house keeps its living room with the fireplace on the west wall
and windows either side, the entry with the stair rising from it, the hall
beside the stair, and on the east side the bathroom, a short vestibule off the
hall with the closet's double doors on one side and the study door on the
other, and the study with a window front and side. The front door opens onto a
stoop three steps above the lawn.

The slider opens onto a **screened porch**: the west half of the deck, 15'-2"
by 9'-5", with knee walls, screens to an 8' beam, a roof, and the sheet's round
table. A 3' screen door in the partition leads to the **open deck** on the east
half, 12'-6" by 9'-5", with a rail. The split is at the sheet's middle deck
post. The sheet's deck sofa sat just east of that post, which would put it
behind the screen door, so it moves to the east rail.

## Scale, and why a room can feel small on a screen

The walls are the right size; what makes a rendered room feel small is almost
always the lens. A camera's field of view decides how much of the world is
squeezed onto the screen. A monitor at arm's length covers about 50° of what
you see, so a render at 50° to 55° looks like standing there. The first
version of this page used 70° vertical, which on a widescreen monitor is about
100° across: twice the angle the screen really covers, so every wall was
pushed away and every room read at about half its size. The lens is now held
at a horizontal angle regardless of window shape, 100° by default because
that is what felt right walking it, and there is a **Scale** panel to change
it. Wider shows more of the room at once; narrower is truer to life.

The other things the eye uses as a ruler are set to the standard sizes, since
the sheet has no heights: doors 6'-8", window heads level with the door heads,
counters 36", risers 7-1/2", baseboards 4-1/2". The floor is 5" oak planks in
random lengths, the bathroom 12" tile, the deck 5-1/2" boards, all at true
size. The eye is at
5'-5", walking is 3.2 ft/s, about 2.2 mph, which is an indoor pace, and the
body stops 8" from a wall rather than 11".

The readout shows the distance along your line of sight to the wall you are
facing. Stand in the real room, look at a wall, and compare.

## What was assumed

The sheet is a plan. It has no heights on it, so:

- **Ceilings are 9'-0"** throughout. The Scale panel changes it in 6" steps
  and rebuilds the model; the choice is remembered in the browser.
- **Window sills** are 2'-7" and heads 6'-8" in the existing house; 3'-0" and
  7'-4" in the addition. Doors are 6'-8".
- **Grade** is 2'-6" below the first floor.
- The **stair** is drawn as twelve risers going up from the entry toward the
  hall and cannot be climbed; the second floor is not built yet. The basement
  stair beneath it is not modelled.

Two elements on the sheet are unlabelled. The U of wall-weight lines at the
kitchen seam, 6'-11" wide and open to the kitchen, is the coffee bar: a
counter with base cabinets between two full-height returns, an espresso
machine and grinder, a floating shelf, and a television on the back wall,
which sits on the old wall line. The two hairline rectangles 2'-7" wide, one
down the hall and one down the east side of the study, are built as runner
rugs.

The kitchen's fixed pieces are built to read as what they are: a french-door
fridge with a freezer drawer and a two-door pantry cabinet beside it. Those,
the island and the coffee bar carry a small floating label that shows when you
are within about 18' of them. The sheet's double wall oven in the east counter
run is left out on request; that stretch is counter.

Furniture follows the sheet's placement and is mostly blocks, there for
scale and to keep you from walking through the dining table. The living
room keeps the one couch, built as a couch with cushions, back and arms,
with the coffee table and side tables, and a television on the chimney
breast above the mantel; the sheet's two armchairs and the media console are
left out on request.

## Checks

Driven through the page's `window.__house` hook:

| Check | Result |
|---|---|
| Sheet's wall vectors on the model's walls in plan view | every wall, opening and partition |
| Every room reachable from the entry on a 6" grid | all, plus porch, deck, stoop and lawn |
| Passable cells inside a solid wall | 0 |
| Walking into the kitchen's rear wall stops at the face | 8", the body radius |
| Range finder against known distances | matches to the inch |
| Only way from inside to the lawn | the front door |

## The second floor and basement

Sheets PR-02 and PR-00 are on the same PDF at the same scale, so the same
extraction works for them. The stair position on all three lines up within a
few inches, which is what you would expect of stacked stairs.
