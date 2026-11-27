# Design review checklist

Adapted from the `red-flags` reference of the `cabinetmaker` skill in
[wonsukchoi/domain-experts](https://github.com/wonsukchoi/domain-experts) (MIT; see `THIRD_PARTY_NOTICES.md`). Run a
design through these before calling it done. Each item gives the signal, what it usually means, and what to ask.

| Signal in the design | Usually means | Ask / check |
|---|---|---|
| Solid panel wider than about 6-8" glued rigidly on all edges into a frame | No allowance for movement; likely to crack as humidity changes | Has seasonal movement been calculated for this width and species? |
| Incoming lumber more than about 2 points off the shop's EMC | It hasn't acclimated and will keep moving after assembly | How long has it sat in the shop? Compare meter reading to the EMC log |
| Pieces with different grain directions joined by a rigid full-length glue joint | Guaranteed eventual cross-grain cracking | What direction does each piece run, and how is the joint glued? Sketch the grain |
| Load-bearing joint (chair or table leg) chosen for speed | Shorter life under real stress | What load path and racking will this connection see? |
| Finish applied without regard to expected movement; early cracking at panel edges or joints | The finish, not the joinery, is where the movement stress shows first | Does the finish's flexibility accommodate the movement allowance? |
| Client reports gaps after delivery on solid wood furniture | Built with unacclimated lumber or too little movement allowance, not a joinery defect | Moisture content at build time vs. typical humidity where it was delivered |
| Veneer on a plywood or MDF substrate with no movement check | Differential movement risks delamination or surface checking | Does the substrate's movement match the veneer species' coefficient? |

The thresholds (6-8" panel width, about 2 points of moisture content) are the source's defaults. Treat them as
prompts to calculate, not as hard limits.
