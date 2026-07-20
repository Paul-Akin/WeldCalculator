# WeldCalculator

A self-contained, single-file calculator for the strength of welded connections
subject to bending or twisting, using the **"treating the weld as a line"**
method described in:

> Blodgett, O.W. and Miller, D.K., "Welded Connections," *Structural
> Engineering Handbook*, Ed. Chen Wai-Fah, Boca Raton: CRC Press LLC, 1999,
> §22.3 — Table 22.2 (Standard Design Formulas Used for Determining Force on
> Weld), Table 22.3 (Properties of Welded Connection; Treating Weld as a
> Line), and Table 22.4 (Stress Allowables for Weld Metal, AWS D1.1).

## Usage

Open `index.html` directly in any browser — no build step, server, or
internet connection required.

1. **Weld configuration** — pick one of the 13 weld-group shapes from
   Table 22.3 (single/parallel lines, L, channels, rectangle, tees,
   I-shapes, single and double circles).
2. **Weld dimensions** — enter the group's width `b` and depth `d` (and `D`
   for the two-circle shape), plus the fillet weld leg size `ω`.
3. **Materials** — pick an electrode class (F<sub>EXX</sub>), base metal
   yield `F_y`, and the thinner connected plate thickness `t`.
4. **Applied loads** *(optional)* — enter any combination of axial `P`,
   vertical shear `V`, bending `M`, and torsion `T` to check an actual
   connection; leave them at 0 to see only the weld line's capacities.

The worksheet on the right shows every step MathCAD-style — the symbolic
formula, the same formula with your numbers substituted, and the numeric
result with units — for:

- **① Line properties** (Table 22.3): weld area `A_w`, centroid location,
  section modulus `S_w` (top/bottom), polar moment of inertia `J_w`.
- **② Allowable unit force** (Table 22.4): 0.30·F<sub>EXX</sub> on the
  0.707ω throat, capped by the 0.40·F<sub>y</sub>·t base-metal shear limit,
  with AWS D1.1 minimum/maximum fillet size checks.
- **③ Capacity of the weld line**: allowable `P`, `V`, `M`, `T` for the
  chosen weld size.
- **④ Force under applied loads** (Table 22.2): unit forces from each load
  combined vectorially at the governing corner of the weld group, giving
  the resultant force, required weld leg size, and a pass/fail utilization
  check.

## Notes on Table 22.3

A few formulas in the widely circulated CRC scan of Table 22.3 contain
printing errors (an extra power on some centroid terms, a repeated
expression for one shape's bottom section modulus, and a swapped exponent
in one polar-moment term). These were found by cross-checking every
formula against direct line-integration of each weld group and are called
out in the calculator (marked with `†`) alongside the corrected values used
for the actual calculations.

## Disclaimer

For preliminary design and educational use. Final connection designs must
be verified by a licensed engineer against the governing building code and
AWS D1.1 *Structural Welding Code — Steel*.
