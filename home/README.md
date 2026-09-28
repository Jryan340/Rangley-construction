# Home

A first-person walkthrough of the proposed first and second floors from
sheets PR-01 and PR-02 of the 09/27/26 floor plans. One self-contained HTML
file. The stair is walkable: climb it from the entry and you are upstairs, or
use the floor buttons.

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

## The second floor

Sheet PR-02 is drawn 9 points higher and 2.3 points to the left of PR-01.
Registered by the addition and the old rear wall, which then coincide
exactly, every second-floor wall is stored in PR-01's coordinates, and the
stairwell lands over the stair. One thing the registration shows: the
second floor's front wall is 14.7 points, about 13", further forward than
the first floor's, so the front bedrooms overhang the entry by that much,
and the model builds it that way.

Over the addition, the primary suite: the bedroom, 12'-6" x 15'-11" against
the sheet's 12'6" x 16', with three windows west and three over the bed; the
bath, 14'-3" x 8'-7" against 8'6" x 14', with a double vanity, a walled
shower and a water closet; a vestibule between them; and the closet, 8'-4" x
7'-1" against 8'6" x 7', with a window. Over the existing house, three
bedrooms, a bath with a shower, the hall, the stairwell, and five closets.

The stairwell in the second floor is cut over the upper part of the stair
only, to where the sheet draws the stair's break line and its east wall
stops; the lower third of the stair passes under the second floor, and the
floor over it is the foot of the attic stair, which is not modelled; a solid
door in the hall wall, kept shut, closes it off.

The kids' bath is dressed after the powder-room reference: black shiplap on
the vanity wall, white on the rest, the rustic open vanity, a round mirror,
lanterns, a shelf over the toilet, a towel bar and a rug, with the sheet's
shower in white subway tile and glass. Its east window, which the sheet puts
inside the shower, is made small and high: 2' wide with a 5' sill, in place
of the sheet's 3'-3" wide, 2'-7" sill. That and the dropped bedroom window
are the two places the model departs from the sheet's openings.

Heights are again assumed: floor to floor 10'-0", the 9' ceiling plus a foot
of structure. The stair climbs that in sixteen risers over the sheet's run,
which makes it steep; the sheet's stair is shorter than a straight run to a
10' floor needs, so the real one likely turns. Furniture upstairs is blocks
placed from the sheet: beds with headboards, dressers, nightstands, vanities,
toilets, tiled showers with glass, wardrobes in the closet.

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
at a horizontal angle regardless of window shape, 120° by default because
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

The bathroom is dressed after a second reference, a farmhouse powder room:
black shiplap on the wall behind the vanity and white shiplap on the others,
crown at the ceiling, an open rustic wood vanity with three drawers, a quartz
top with an undermount sink and a bronze faucet, a round wood-framed mirror,
lantern sconces, a shelf over the toilet, a plant, a towel bar, a basket and
towels on the vanity's lower shelf, marble tile and a patterned rug. The
sheet's shower stays, tiled in subway with a glass panel and a 2' opening.

The study is dressed after a third reference, a dark library-style office:
12"-deep charcoal built-ins down the west wall with shaker bases, three rows
of lit shelves full of books and objects, and a painting bay in the middle
with a framed abstract under a brass picture light. A walnut desk on a black
frame floats in front of them with a laptop, a lamp, books and a plant, with
a leather chair on a five-star base between the desk and the shelves, facing
the room. A grey rug lies under both, curtains flank the side and front
windows, and a black ring chandelier with brass candles hangs from the
centre. The sheet's desk was against the wall; it moves out far enough to
seat the chair behind it. The study's door is left off, an open doorway.

The screened porch is dressed after a fourth: a wicker sectional along the
north and west screens with beige cushions and patterned pillows, a concrete
coffee table with two plants on a jute rug, a lantern by the west screens,
three runs of string lights with a bulb every foot and a half, and a bronze
ceiling fan under a grey plank ceiling. The sheet's round table comes out to
make room.

Every door on both floors is left off, an open doorway with no jambs, on
request; only the closets keep their double doors, closed.

The primary bath is dressed after its reference: a black shaker double
vanity along the wall it shares with the bedroom, with brass knobs, a pair of
doors at each end and three drawers between, an open shelf below with
baskets and towels, a marble top, two white vessel sinks with black
wall-mounted taps, a black-framed mirror over each, three brass sconces, a
plant and bottles between the sinks, a towel ring by the door, a runner
along the vanity, recessed lights. The shower follows its own reference:
charcoal subway tile on every wall, cut around the window the sheet puts
inside it, a pebble floor on a low curb, a tiled bench along the east wall,
a fixed glass panel with a thin black frame at the entry, a black rain head
from the ceiling, and a black hand shower on a slide bar with its mixer on
the partition. The reference's freestanding tub is not on the sheet and is
left out. The water closet keeps its toilet.

The primary bedroom is dressed after its reference: greige walls with panel
moulding on the bed wall and the south wall, a lit cove under the crown, an
upholstered bed with a tall headboard where the sheet puts it, its head on
the wall shared with the vestibule, layered pillows and a taupe throw, wood
nightstands with lamps and a cylinder sconce over each, a painting over the
bed, a large rug, a curved armchair in the corner from the sheet, curtains at
the west and north windows, and a television on a console on the wall
opposite the bed. That wall carries three of the sheet's windows; the middle
one is dropped, on request, so the television hangs on solid wall between
the other two.

## Paint

Walls follow a warm farmhouse palette the owner chose, Sherwin-Williams
names: Mushroom is the base on every wall in place of white; the living room
and the south-east bedroom are Acacia Haze, a grey sage; the study and the
north-west bedroom are Morning Fog, a blue grey; the south-west bedroom is
Beachcomber, a warm tan; the halls, entry and both vestibules are Illusion, a
warm grey; the primary bath is Sunbleached; the porch's knee walls are Studio
Clay. Trim, crown and ceilings stay light. A room that names a colour has
every wall face that bounds it painted, with its windows and doorways left
open, so a wall shared by two rooms carries each room's colour on its own
side.

## Basement

From sheet PR-00, registered to the first-floor sheet by the centre of the
footprint (PR-00 is drawn 36.2 points right and 9.2 points down). The plan
view's **Show drawing** overlays the sheet's own lines on the basement too.
Rec room and gym across the back with the rec room's slider and the gym's
three windows; the side entry on the driveway side; mudroom with two closets,
powder room and vestibule in the middle; storage and mechanical rooms either
side of the stair at the front.

Two things follow the existing-conditions set and the owner rather than
PR-00. The stair comes **down toward the front of the house**, under the
stair that goes up, landing in the existing nook at the front (the sheet's
arrow points the other way). And the **existing hallway** west of the stair
is kept as it is, with its joists exposed and painted black, a beam along
the stair wall, conduit and a shop light, so the west storage room's east
wall stays where it is instead of taking in the hall. The hall meets the new
vestibule, powder room and mudroom at its north end.

The nook at the foot of the stair is the laundry: a front-loading washer
and dryer under a butcher-block folding counter along the front wall, a
shelf of baskets above, a hanging rod, a utility sink at the end, under the
exposed joists.

The basement floor is 7'-10" below the first floor, from the existing set,
with 6'-8" under the joists everywhere; the addition's basement is assumed
to match. The lot falls from the street: the first floor is at grade at the
front, the basement is at grade at the back, and the side entry on the
east is at basement level off a driveway that runs down that side. The lawn
is built to that slope, in pieces around the house, and the deck and porch
stand on posts down to it.

## The lot, from the surveyor's plot plan

The ground is no longer a guess. The DWG in the repo's Temple-street folder
is the surveyor's plot plan of the lot (1" = 20', March 2025): 60 feet on
the street by 132 feet deep, 7,919 square feet, with the house 29.9 feet
back from the front line and 14.4 feet off the west line, the driveway down
the east side, the sidewalk, curb and street, the neighbours' trees and a
chain-link fence along the rear line, and 170 surveyed spot elevations.
Those points are interpolated onto a 2.5-foot grid and the whole ground
follows it, heights relative to the first floor at elevation 120.0 (NGVD
1988): the front yard sits about 2'-4" below the floor and is near flat,
the ground at the back wall is at basement level, and the rear line is a
foot lower still. The lot lines are drawn on the grass, the fence is where
the survey has it, and labels name the front and back yards. The lawn is
built only where there is lawn, around the driveway, sidewalk and street,
so the grass cannot show through the paving. A basketball hoop stands at
the top of the driveway, its backboard facing down the drive.

## Roofs

From the existing-conditions elevations: a 9-in-12 gable over the house with
its ridge running east-west and gables on the side walls, eaves at the top of
the second-floor walls (the scan's eaves are 8 feet above the second floor;
the model's second-floor walls are the assumed 9 feet, so the roof sits a
foot higher), the chimney carried above the ridge. The addition gets a cross
gable at the same pitch with its ridge running north-south and its gable
facing the back yard, as the one-storey rear ell it replaces had; the two
roofs are let into each other. The addition's roof is not on the new sheets,
so that is a choice, not a reading.

## Deck stair

Off the deck's east side, the driveway side: a railed landing outside the
rail at the north-east corner, then thirteen risers south along the deck's
east edge to a pad at the end of the driveway, a few steps from the side
entry. Rails both sides. From the driveway you climb it; you cannot walk
in under its lower half.

## Under the deck

The rec room's slider opens under the screened porch, at basement grade,
and the whole under-deck is dressed as a covered outdoor lounge after the
owner's reference: charcoal tile across it and a few feet into the yard; a
cedar-slat soffit under the deck with an amber cove along the house and
warm downlights; an outdoor television on a dark slat wall at the west end
with a hedge planter under it; a deep sectional with orange pillows and a
teak coffee table facing the screen; a teak dining table for six with a
bench under the open deck; a built-in grill on the yard side at the east end, under the open deck (a
wood-clad island with a stone top, a stainless grill under a rounded hood,
doors and a drawer), a hedge along the yard side at the west end, the
middle open across from the slider; grasses in planters. A walkway runs along the yard
side from the slider to the dining end and out to the lawn.

## Shed

In the back-right corner of the lot (east, by the rear line), after the
owner's photo but in the house's colours: 8 by 10, a shingled gable roof,
corner boards and white trim, a white door facing the house with a step, a
window either side of it with black shutters and a box of red flowers. It
is not walkable inside.

## Gym

After the owner's photos: their 3' by 7' folding treadmill with a console
and screen along the west wall, short of the door; a squat rack with a
7'-2" bar against the east wall, centred in the room's 10' depth so there is about 2' beyond each
end of the bar for loading plates, its bar running front to back so the
doorway and the floor stay clear; a yoga mat between them on the rubber
floor. The room is 11'-10" by 10'-0".

## Primary bedroom's bike

The owner's exercise bike stands in the north-west corner of the primary
bedroom, beside the television, facing down the room: black frame with a
red spar, flywheel, saddle, handlebars and a screen.

## Primary closet

Dressed after the owner's walk-in photo. The sheet's closet is 8'-4" by
7'-1" with the door on the west and the window opposite on the east, so the
photo's layout fits as drawn: cream built-ins down both long walls, two
drawers deep below a counter, a hanging bay at each end and shelves of
folded stacks in the middle, baskets on the top shelf; a window seat with
drawers, a cushion and pillows under the east window, with a roman shade
drawn up; a cream and slate-blue runner down the aisle.

## Deck

The open deck beyond the screened porch is dressed after the owner's deck
photo: a dark wood dining table with a cushioned bench on the rail side,
three wicker chairs on the house side and one at the far end, set with
plates, glasses, candles and flowers, on a striped outdoor rug, with
lanterns by the porch and planters of hydrangeas at the far rail. The set
sits toward the rail so the walk from the screen door runs along the house.

## The girls' room

The south-west bedroom is shared by two girls: two twin beds against the
north wall with a nightstand between them, and the dresser. Bunk beds are
the alternative if the floor needs to be freer.

## Art

The entry's console is after the owner's foyer photo: a slim white-oak
table with tapered legs under the round mirror, a stone vase of olive
branches, two books and a bowl on it.

On walls that were blank: a round black mirror over the entry bench; a
botanical print in oak and a monochrome abstract in black down the
first-floor hall; a small landscape in the first-floor vestibule; an
abstract facing you at the top of the stairs; a small botanical on the
upstairs hall; a pair of botanicals over the north-west bed, a landscape
over the south-west bed, a monochrome abstract over the south-east bed; and
a small oak mirror in the upstairs vestibule. All are drawn pictures, placed
where a wall was bare and a room needed a focus.

## Keeping the frame rate up

Every point light costs every pixel, so only the floor you are on has its
lamps lit; the sun's shadow map is drawn when something changes rather than
every frame; the render is capped at 1.5x pixel density on Retina screens;
the lawn is built with the fewest triangles that follow the slope; and the
minimap redraws every other frame.

## The fridge

The sheet draws a 36" fridge beside a 36" pantry in the 8'-0" run between
the hall wall and the corner cabinet. The owner wants a big one, so the
model has a 48" built-in, 27" deep like the sheet's alcove, with the pantry
a 24" cabinet: 48 + 24 + 24 fills the run.

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
kitchen seam, 6'-11" wide and open to the kitchen, is the coffee bar, dressed
after a reference: charcoal shaker bases with brass pulls, a door and drawer
on the left, a glass-front beverage fridge stocked with bottles in the
middle, three drawers on the right, a white marble counter with the marble
carried up the back wall to the ceiling, and on it an espresso machine, a
grinder, a wood tray of bottles, a stoneware vase of greenery and mugs. No
uppers: a television that looks like a picture frame when it is off hangs on
the marble, an oak bezel and mat around a landscape. The two hairline rectangles 2'-7" wide, one
down the hall and one down the east side of the study, are built as runner
rugs.

The kitchen is dressed after a reference photo, a modern farmhouse room, with
none of the sheet's footprints moved: white shaker cabinets with black pulls
and a quartz top down the east wall, a stainless range with a plaster hood
where the sheet had the wall ovens, subway tile behind, glass-front uppers
with a light strip under them, a dark shaker island with a quartz top that
overhangs a foot on the seating side, four wood-seat iron stools, a black
gooseneck tap, four black dome pendants over the island, recessed cans across
the ceiling, a trestle-base plank dining table with black iron chairs four a
side, a french-door fridge and a white two-door pantry. The floor is a
lighter, wider oak. The fridge, pantry, range, island and coffee bar carry a
small floating label that shows when you are within about 18' of them.

Furniture follows the sheet's placement and is mostly blocks, there for
scale and to keep you from walking through the dining table. The living
room keeps the one couch, built as a couch with cushions, back and arms,
and is dressed lightly after a reference: recessed cans, a black
wagon-wheel chandelier over the coffee table, an oak mantel with the
television above it and a fire in the firebox, the couch in cream linen with
pillows and a throw, a chunky oak coffee table with a tray and bowl on a jute
rug, round black side tables, a tall plant and a basket, and cream curtains
on black rods at all three windows. The reference's ceiling beams, built-in
shelves and armchair were tried and taken out as too much. The walls stay in
the sage from the palette.

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
