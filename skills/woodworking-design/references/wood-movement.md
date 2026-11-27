# Wood movement and joinery

Adapted from the `cabinetmaker` skill in [wonsukchoi/domain-experts](https://github.com/wonsukchoi/domain-experts)
(MIT; see `THIRD_PARTY_NOTICES.md` at the repo root). Reworded and converted to the shop's conventions. The movement
figures below are the source's **illustrative practical shop figures**, not published data. For a real design, use the
species' published coefficients (USDA Forest Products Laboratory *Wood Handbook*) and the piece's actual end-use humidity.

## Principles

1. **Wood movement is the dominant constraint on joinery design, not appearance.** Movement is mostly across the grain
   and follows moisture content. A solid panel must be free to move in its frame (floated, not glued around the whole
   perimeter) or it will crack or split as humidity changes through the seasons.
2. **Cross-grain construction is the most common cause of long-term joint failure.** A rigid glue joint between pieces
   whose grain runs perpendicular guarantees eventual cracking. No glue is strong enough to prevent it.
3. **Moisture content at the time of construction matters as much as species.** Lumber that comes in above the shop's
   equilibrium moisture content (EMC) keeps shrinking after assembly. The resulting gaps look like bad joinery but are an
   acclimation failure.
4. **Choose joinery by load path, not looks or speed.** Mortise-and-tenon, dowel and pocket-screw joints differ in racking
   resistance and long-term strength. Chair and table legs fail from racking, not from a straight pull-apart.
5. **The finish has to allow for the wood's movement too.** A finish that can't flex with the expected movement will crack
   at panel edges even when the joinery underneath handles the movement.

## Rules of thumb (defaults, not laws)

- Solid panel wider than about 6-8" in a frame-and-panel assembly: float it in a groove rather than gluing it on all sides.
- Calculate movement from the species' figure and the expected humidity swing, not a vague "wood moves a little".
- If incoming lumber's moisture content is more than a point or two from the shop's EMC, acclimate it before milling.
- Where grain directions meet (tabletop to breadboard end, for example), use joinery that allows the differential
  movement: breadboard end, slotted screw holes. No rigid full-length glue joint.
- For a load-bearing joint (chair or table leg), pick the joint with the best established racking and load resistance for
  that use, not the fastest to cut.
- Don't over-correct: on small, low-movement pieces, extra clearance only adds rattle.

## Design sequence

1. Work out the end-use environment (humidity range), then choose species and joinery.
2. Check incoming lumber moisture against the shop's EMC. Acclimate before milling if they don't match closely.
3. Lay out grain direction and joints so no cross-grain construction goes unaccommodated.
4. Calculate expected movement for every solid panel, then design the accommodation (floating panel, breadboard end,
   slotted holes).
5. Choose joinery per connection by its load path, not uniformly across the piece.
6. Dry-fit and check square before the glue sets on any joint that can't be undone.
7. Pick a finish suited to the piece's use that allows for the calculated movement.

## Worked example: solid walnut top panel, 30" wide (source's figures)

The source uses about 1/4" per foot of width for walnut across a full seasonal swing. Walnut is a poor default for this
shop (see `extra-ransom-context.md`); the example is here for the method.

| Step | Value |
|---|---|
| Panel width | 30" = 2.5 ft |
| Movement figure (illustrative) | 0.25" per ft |
| Total seasonal movement | 2.5 ft x 0.25"/ft = 0.625" (about 5/8") |
| Source's groove allowance | 0.625" movement + 1/8" margin = 3/4" |

Source's floating-panel layout for this panel: 3/4" thick panel, 3/8" wide groove, 1/2" minimum insertion, panel glued
only at its center (a loose spline or a single glued point), never along the sides. The left and right edges (the
cross-grain direction) carry the clearance. The top and bottom edges run with the grain and can be fixed more
conservatively, since movement along the grain is negligible by comparison.

Because the panel is held at its center, the movement is shared between its two edges, so check the clearance **per
edge**, not just the total. The source states its allowance as one 3/4" total; confirm the split when you detail a groove.

### Same panel, different species and cut (source's illustrative figures)

| Species / cut | Figure | 30" panel, total movement |
|---|---|---|
| Walnut | 0.25"/ft | 0.625" |
| Quartersawn white oak | 0.15"/ft | 0.375" |
| Flat-sawn white oak | 0.30"/ft | 0.750" |

The point is that the cut matters as much as the species: flat-sawn oak moves roughly double what quartersawn does in
the source's figures. These are the source's numbers; verify against the *Wood Handbook* before relying on them.

## Acclimation log (source's example)

Shop EMC 8%. Delivery readings:

| Board | Reading | Difference from EMC | Action |
|---|---|---|---|
| 1 | 8.2% | +0.2 | Ready to mill |
| 2 | 11.5% | +3.5 | Acclimate first; exceeds the 2-point threshold |
| 3 | 8.0% | 0 | Ready to mill |

Board 2 gets stickered in the shop until its reading is within a point or two of 8%, before milling or any glued joint.

## Vocabulary

- **Wood movement:** dimensional change, mostly across the grain, as moisture content follows ambient humidity. Dry,
  finished wood keeps moving for its whole life.
- **Equilibrium moisture content (EMC):** the moisture content wood settles at for a given humidity and temperature. A
  kiln-dried reading is the EMC of the drying environment and shifts again in a new one.
- **Cross-grain construction:** joining pieces with grain perpendicular or at a significant angle. A rigid glue joint
  guarantees eventual cracking regardless of glue strength.
- **Floating panel:** a solid panel held in a groove, not glued around its perimeter. Gluing it even partly along a long
  edge can still restrain the movement it needs.
- **Breadboard end:** a cross-grain end cap joined to a top's long-grain edge by a method that allows differential movement
  (a tongue with elongated holes, a sliding dovetail). Pegged through slotted holes, not fixed ones. Fully gluing it
  defeats its purpose.
- **Mortise and tenon:** a projecting tenon fitting a mortise; the usual choice for load-bearing connections. Not
  interchangeable with pocket screws or dowels where the load matters.
- **Racking resistance:** resistance to distortion under lateral or shear loads.
- **Veneer:** a thin wood layer on a substrate such as plywood or MDF. Veneer and substrate don't necessarily move alike;
  a mismatch risks delamination or surface checking.
- **Species movement coefficient:** how much a species expands or contracts per unit change in moisture content or
  humidity. It varies substantially between species and with how the board was cut.
- **Quartersawn vs. flat-sawn:** two ways of milling a log that give different grain orientation and different stability.
  Same-species boards don't all move alike.
