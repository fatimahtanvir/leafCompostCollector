# Rake roller design

The rake roller is the part that actually picks leaves up. It spins at the front of the robot and flicks leaves up into the bin.

## How the design evolved

1. **Sketches.** Paper sketches of a crank-arm rake, a paddle wheel, a spiked wheel and curved tines.
2. **Straight paddle.** A hub with two flat blades. Simple, but leaves slipped through the gaps.
3. **Curved three-blade paddle.** Curved blades scoop better than flat ones, but a full-width solid paddle was too long for the printer's plate and the 4-hour print limit.
4. **Rotary rake (final).** Inspired by a garden rake: instead of one long paddle, the roller is a stack of thin tine wheels on a shaft, with gaps between them. Each piece prints fast, and the gaps let the tines comb leaves up like rake fingers.

## Final geometry

### Tine wheel (×5)

| Feature | Value |
|---|---|
| Tines | 3, curved, 120° apart, all curving the same way |
| Tine width | 5 mm, rounded tips |
| Reach | 76 mm from center (152 mm tip to tip) |
| Hub | 40 mm diameter |
| Thickness | 6 mm (hub and tines flush) |
| Shaft hole | 7 mm round |
| Fillets | 2 mm where each tine meets the hub |

### Spacers

| Spacer | Count | Length |
|---|---|---|
| Between tine wheels | 4 | 19 mm |
| Ends | 2 | 14.5 mm |

Spacer cross-section: about the size of an M8 nut (13 mm across the flats) with a 7 mm hole.

### Stack on the 135 mm dowel

```
[end 14.5][wheel 6][spacer 19][wheel 6][spacer 19][wheel 6][spacer 19][wheel 6][spacer 19][wheel 6][end 14.5]
```

5 × 6 + 4 × 19 + 2 × 14.5 = 135 mm, with tines spaced 25 mm (about 1 in) apart.

The 7 mm hole is a loose fit on the 6.6 mm dowel, so each piece is glued in place once the tines are lined up.

## CAD

Modeled in Autodesk Fusion 360:

1. Sketch 1 on the XY plane: 40 mm hub circle, extruded 6 mm.
2. Sketch 2 on the XY plane: one Three Point Arc Slot (5 mm wide, from 12 mm to 73 mm from center), then a Circular Pattern ×3, extruded 6 mm and joined to the hub.
3. 2 mm fillets on the six tine-root edges.
4. A 7 mm hole cut through the center.

Source and STL files are in [`../cad`](../cad).

## Printing

Printed on a Bambu Lab A1 mini (180 × 180 × 180 mm build volume). One tine wheel fits per plate; all spacers fit on one plate.

| Setting | Tine wheel | Spacers |
|---|---|---|
| Layer height | 0.20 mm | 0.20 mm |
| Infill | 20–25 %, gyroid | 15 % |
| Wall loops | 3 | 3 |
| Top and bottom layers | 4–5 | 4–5 |
| Supports | None | None |
| Orientation | Flat, tines on the bed | Standing upright |

## Lessons

- Design around the printer first. Plate size and the print-time limit shaped the whole roller.
- Print one small part to test the shaft fit before printing the full set.
- Curved tines scoop. Flat paddles push.
