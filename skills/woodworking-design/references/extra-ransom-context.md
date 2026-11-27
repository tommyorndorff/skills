# Woodworking context from the extra-ransom site

Knowledge, preferences and lessons collected while building the woodworking plans on
`extra-ransom` (https://www.extra-ransom.net, repo `tommyorndorff/extra-ransom`, cloned at
`~/Projects/git/extra-ransom`). Read this before designing a piece for this user, or before
editing that site. Facts here were true as of 2026-11-27; check the repo for newer state.

## Who the plans are for

- A hobbyist builder with a **SawStop PCS table saw (36" rip capacity), a track saw, band saw, router, drill press, mortiser and a Festool Domino**.
  The 36" rip and the track saw mean full sheets can be broken down in the shop and panels up to about 36" wide can be ripped on the
  table saw; design sheet-good and wide-panel parts around that. Also has **hand planes, block planes, dovetail and carcass
  saws, chisels**, and a **Sherline lathe and Sherline mill**. **Prefers Domino joinery** wherever
  a joint can be made with it (butt joints into a flat, square face; shelf-to-leg; bar-to-leg). Reserve true mortise-and-tenon
  and half-laps for where a Domino can't work (a half-lap X, a long cantilever). The swoop hanger plan on the site
  says there is no drill press; that is wrong, the user has one. Treat "table-saw and band-saw work, plus track-saw sheet breakdown and hand-tool fitting" as the default skill set.
- **Units: SAE/imperial by default** (inches and fractions to 1/16″, decimal inches only where a tool needs them; board feet
  for lumber; nominal sheet sizes such as 4×8 and 3/4″ ply). Can work in metric, so give metric only when asked or when
  copying a metric source, and then show both. Convert imported metric material (for example the mm-based openscad-cutlist
  skill and sheet-good thicknesses like 18 mm) to imperial and say what real stock it maps to (18 mm is about 23/32″ ply).
- Likes **square stock, Domino joints, half-laps**; drawbored mortise-and-tenon where a Domino won't do. Dislikes anything that needs a special jig it can't make from the shop's own tools. When a design has a splay or
  taper, prefer **cutting the shape into the part** (template, taper jig) over **leaning a part** and
  angling every joint around it.
- Lumber: prefers **4/4 and 8/4**, **locally sourced**. Default species are **cherry, white oak and
  soft maple**. **Walnut is pricey, so avoid it** unless it is an important accent. Ash and hickory are fine. Prefers woods that behave well with hand tools. Size parts so they come out of 4/4 and 8/4, and price boards for the local species, not walnut.
- Finishes seen in the plans: hardwax oil (Osmo Polyx, Rubio Monocoat), wipe-on or spar poly where water
  will drip. Glue: Titebond III by default; epoxy or urea glue for long-lived cantilever joints (PVA creeps).
- Safety defaults the user accepts: anchor anything tall to a stud; call out tipping angle; use rated hardware
  (WLL stated) for anything hung from a chain.
- Builds are real. The **Fixed Swoop Plant Hanger** has been built a couple of times; most other plans in
  `furniture-plans/` are still "(Proposed) / designed, not yet built". Don't invent as-built findings;
  ask what changed in the build and record it as "as built".

## How plans on the site are written (follow this format)

Location: `src/content/docs/docs/woodworking/furniture-plans/<name>.md`, with an entry in `index.md`.
Front matter: `title`, optional `weight` (legacy, ignored), `sidebar: { order: N }`. Titles of unbuilt plans end in
**(Proposed)**; drop that when it's built and change the index blurb from "designed, not yet built".

Every plan follows the same skeleton:
1. One-paragraph description, then a **provenance box** that defines the labels below.
2. Drawings (true scale), the numbers table, a "how the pieces close" table.
3. Cut list (T × W × L, notes), board feet (net, and what to buy).
4. Build sequence, finish, stability/safety, **Open questions**.

**Provenance labels** (use them on every number that isn't obvious):
- **(stated)**: given by the user or the maker.
- **(maker)**: a maker's published figure, rounded.
- **(derived)**: worked out from others so everything closes.
- **(chosen)**: a design decision.
- **(est.)**: a guess nobody verified (measured off a photo, assumed spigot height, weight).
Plans copied from a maker's piece end with an "Open questions" list of everything marked est.

**Drawings are generated, not hand-drawn.** One script per plan in `tools/woodworking/<name>_drawings.py`
writes SVGs into `public/static/woodworking/`. Edit constants and re-run; the script prints the numbers for the
page, so drawings and page can't drift apart. The tables on the page are written by hand, so update them after
re-running. Embed as `[![alt](/static/woodworking/x.svg)](/static/woodworking/x.svg)`. White backgrounds so they
read in dark mode. Rename the file (or invalidate CloudFront) if you change a published SVG, because SVGs are cached for a year.

Script conventions worth reusing:
- `from modern_craftsman_drawings import Drawing` gives `rect/poly/text/dim_h/dim_v/leader/add/save`. `x()/y()` map inches to pixels;
  `dim_h/dim_v` take inches along the axis and a pixel position across. Add your own CSS classes through the `EXTRA` string.
- Its `frac(v)` glues the whole number to sixteenths with no space (`12 11/16` prints as `1211/16″`). Define a local
  `frac` that inserts a space when there is a whole part and an ASCII fraction.
- Put **asserts in `main()`** for geometry that must close (cup fits on the shelf, filter fits between legs, mortise leaves wood).
  They catch a changed constant before a wrong drawing gets published.
- Render and look: `rsvg-convert -w 1000 file.svg -o out.png`, then view the PNG. Check text overlaps and cropped footnotes every time.
- Isometric renderings use a painter's-algorithm `Iso` class (sort key = x + y). Slanted parts can be split into stacked
  hexahedra. Good enough for concept views, labelled "concept rendering, not a photograph".
- `print_tiles.py <svg> --ppi N [--grid]` tiles a 1:1 template onto letter sheets.

Other site rules: plain Markdown, tables and blockquotes, no Starlight components. External links pair with a Wayback
URL (`https://web.archive.org/web/2024/<url>`) except retail product pages. Build with `npm run build` (fails on broken
internal links). Deploys come from CI on push to `main`; PRs are squash-merged.

## Environment quirks (Claude Code on this machine)

- In the Bash tool, `node`/`npm` are broken zsh lazy-load stubs: `export PATH=~/.nvm/versions/node/v22.23.1/bin:$PATH`
  and call `/usr/bin/env npm ...`.
- `gh` needs `GH_TOKEN="$(gh auth token --user tommyorndorff)"` for the personal repo.
- Git commits and pushes happen only when asked; never commit unprompted.

## Working with reference products and screenshots (lessons)

- **The user's screenshots are ground truth; a printed PDF of a product page is not.** A 73-page "print to PDF" of a
  store page held 144 × 144 px lazy-load placeholders instead of the real diagrams, so the dimension callouts were unreadable.
  When numbers come from an image, ask for (or wait for) a full-resolution screenshot, and say which figures you read from it.
- **Don't guess the layout from one angle.** The first draft of the filter stand assumed a square four-corner frame with
  a drop-in plate; the photos showed legs at the compass points, two half-lapped cross members (an X), tapered legs and a
  corner shelf. Before choosing a structure, list what the photos show (leg layout, what the object rests on, how parts
  taper) and write down what is ambiguous. Let the user's annotations override your reading.
- **Treat the user's one-line corrections as design constraints**, and re-derive downstream numbers (fit table, tipping,
  cut list, build steps) rather than patching the one line. A changed leg shape changed the joints, the fit slack,
  the glue-up and the jig list.
- Remove leftover text from superseded designs (grep for old terms: "plate", "cleat", "apron", "bevel", old angles)
  after a redesign. The first full rewrite of the stand page left several.
- Ask a second reader (an Opus subagent with the images and files, *not* your conclusions) to review a redesign
  before calling it done. Give it the ground-truth images and tell it to write its own reading first. On the filter
  stand it caught real errors: a claim that the countertop version "clears a wall cabinet" (it sits on a 36″ counter, so
  it reaches 67″ against a 54″ underside), an "no angled mortising" claim (a tapered leg rests on its sloped edge in a
  mortiser), a spigot clearance stated two different ways, and a build step that couldn't work as written.
- **Add up heights from the floor** for anything that sits on a counter or under a cabinet, and say it in the plan.
- **Do the mortises on the square blank, then shape the part.** A jointed edge that becomes the plumb face is the datum.
  Domino mortises cut on the square blank also never end up on a sloped face. Design joints so the Domino machine can register
  off a flat, square surface (a butt joint into a plumb face, an end square-cut), not on a tapered or sloped one.
- **Domino sizing used here:** 8×40 (8 mm thick, 40 mm long: 20 mm into each part; about 22 mm wide) for 1″ stock, two stacked
  up a 2½″ bar end (30 mm apart); 5×30 (15 mm into each part, about 19 mm wide) for ¾″ shelf edges, two side by side per leg.
  Check the leg is wide enough that the mortise leaves wood (the script asserts it). Use the narrow mortise width for indexed joints.
- **Actually run "change a constant and re-run".** The first version asserted exact numbers, so editing a constant
  crashed the script. Derive dependent values from the constants; keep asserts for real geometry (fit, clearance, wood left).

## Worked example: gravity water-filter stand (BOROUX 3-Gallon)

Page: `furniture-plans/water-filter-stand.md`; script: `tools/woodworking/water_filter_stand_drawings.py`.
Status: proposed. The page is the model for "adapt a maker's product to a hobbyist build".

**Maker figures (BOROUX teak floor stand, from its spec table and height diagram):** 39″ tall; top platform 12″ OD with
9½″ between legs at the top; 20¾″ OD base; filter-base shelf 33¾″ off the floor; lower shelf 23″; 10¾″ between shelves;
supports 50 lb; stand weighs 11 lb; spigot "lifted to 34″"; accepts filters with a base ≤ 9½″. 3-Gallon on the stand is 56¾″
overall (so the filter is 23″ tall) and the 1.8-Gallon is 51¼″. The diagram also draws a 36″ counter with 18″ to the wall
cabinet (54″ underside): the 3-Gallon does not fit under that, the 1.8-Gallon does. Assembly: two interlocking leg sets with
cross pieces and a lower shelf on four black bolts.

**Design as read from the photos (some of it inferred, flagged on the page):**
- Four legs at the **compass points**; each opposite pair splays only in its own plane (so no compound angles).
- Legs are **tapered**: about 1¼″ wide at the top, about 2¾″ at the foot. The **inside face is plumb at the top**
  ("tapered to vertical", read from a user's annotation), then tapers out.
- Two cross members **half-lapped into an X**, Domino'd into the legs. The **filter's base ring sits on the X** between the legs;
  the legs stand 5¼″ above it as posts.
- A small **corner shelf** between two legs, with the spigot pointing at that corner. The cup sits there; the front is open.

**Numbers worth reusing** (floor stand): legs 1¼″ thick, 39″ vertical, 1¼″ wide at the top and 2¾″ at the foot; inside faces
9¾″ apart (¼″ more than the 9½″ base); bars 1″ × 2½″ × 9¾″ butting the legs, joined with two 8×40 Dominos per end; half-lap
1″ × 1¼″, one bar notched from the underside and one from the top so tops are flush; panels glue up as two flat A-frames, the
half-lap is left unglued, but the glued shelf locks the frames together, so it is a permanent assembly;
shelf ¾″ × 8⅜″ square with a 2½″ chamfer, glued to two legs with two 5×30 Dominos each (permanent; for BOROUX's knockdown use
inserts and bolts instead). Spigot underside 34″
(maker), so about 11″ clear over the 23″ shelf. Tipping ~13° along a leg axis and ~10° across the diagonals (CoM about 44″ up,
est.); anchor to a stud. Fit slack for a 9½″ base is ⅛″ per side; Imperial, Crown and the 8.5 L Berkefeld don't fit without
widening `GAP`. **Neither** the floor stand (56¾″) **nor** the countertop stand (31″ on a 36″ counter = 67″) fits under a
54″ wall cabinet with the 3-Gallon. Buy 6/4 for the leg blanks and **5/4 for the 1″ bars** (4/4 mills to about ⅞″).

**Open questions that need the builder's measurements:** the nozzle's reach (height is BOROUX's 34″); the 3-Gallon's body
width in its lowest 5¼″; leg thickness (1¼″ chosen). **Chosen simplification:** the plan carries the plumb inside face down to
the *bottom* of the X (31¼″) so the bar shoulders stay square, whereas BOROUX's diagram turns it at the *top* of the bar with
bevelled shoulders (about 5°). Say so on the page and keep it a one-function change (`kink()`).

## Design rules of thumb that came up

- A gravity filter wants to **nest**: legs taller than the base ring by a few inches, a clearance of about ⅛–¼″ per side, and
  the load carried on a cross member or plate, not on the legs' joints alone.
- Raise the **spigot and shelf** to hip/counter height (BOROUX: spigot ~34″, shelf 23″) instead of putting a shelf near the
  floor; the cost is overall height, so check lid height and wall-cabinet clearance (54″ in the maker's own diagram).
- With legs at compass points, the **diagonal** tips first (footprint/√2). Report both axes. Put the open side (spigot) on
  a diagonal where there is no cross member.
- For a long, thin, tapered leg, **draw the leg 1:1 as a template** and cut to it. It's easier than angling joints.
- Half-laps for a flush X: notch one bar from the top and the other from the underside; glue-up as two flat frames and
  lower one onto the other. Leaving the lap dry makes the stand knock down.
- A 1:1 template for a tapered/kinked part is the drawing itself: print it, glue it to ply, rout to it.
- Estimate board feet on **blank** sizes (a 3″-wide blank for a tapered leg), then buy ~1.5–2× net for long thin parts.
