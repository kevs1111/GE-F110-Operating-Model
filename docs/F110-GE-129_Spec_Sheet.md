# F110-GE-129 — Model Reference Spec Sheet

Engine for the F-16C Block 50/70 (also used in the F-15K/SG/EX and the F-2). These figures are the baseline for the 3D operating model.

## Published figures (sea-level static, standard day)
| Parameter | Value | Source |
|---|---|---|
| Type | 2-spool afterburning turbofan | Wikipedia, GE |
| Length | 181.9 in (4.62 m) | GE datasheet |
| Max diameter | 46.5 in (1.18 m) | GE datasheet |
| Dry weight | 3,920 lb | Wikipedia |
| Airflow | 270 lb/s (122.4 kg/s) | GE datasheet |
| Bypass ratio | 0.76 | GE datasheet |
| Overall pressure ratio | 30.7 | Wikipedia |
| Turbine inlet temperature | 2,750 °F (1,780 K) | Wikipedia |
| Thrust, intermediate (MIL) | 17,155 lbf | Wikipedia |
| Thrust, max AB | 29,500 lbf (GE lists the 29,000 lb class) | Wikipedia / GE |
| Controls | FADEC | Wikipedia |
| Commonality with -100 | ~81% | GE datasheet |

## Architecture (module order, front to rear)
1. Inlet / front frame, with variable fan inlet guide vanes
2. Fan: 3 stages (LP spool)
3. Fan frame / splitter: bypass duct begins, and the inlet gearbox / radial drive shaft is taken off here
4. HPC: 9 stages; IGV and stages 1–3 have variable stators (VSV)
5. Annular combustor with a fuel nozzle ring
6. HPT: 1 stage (drives the HPC)
7. LPT: 2 stages (drives the fan)
8. Turbine rear frame / mixer, where the bypass and core flows mix
9. Augmentor: spray bars, flameholders, cooling liner
10. Variable convergent-divergent nozzle (A8 throat / A9 exit)
11. Accessory gearbox (AGB), mounted under the core: main and augmentor fuel pumps, lube/scavenge pump, PMA, main fuel control

## F-16 cockpit operating limits (GE-129, from training flashcards — not official; verify against the -1 manual)
| Item | Value |
|---|---|
| Idle RPM | 62–80% |
| Idle FTIT | ≤ 650 °C |
| Idle fuel flow | 700–1,700 pph |
| Idle nozzle | > 94% open |
| Idle oil pressure | 15 psi min |
| MIL/AB RPM | 108% max steady, 109% transient |
| MIL/AB FTIT | 980 °C max |
| Start FTIT | 935 °C max |
| MIL/AB oil pressure | 25–65 psi, at least 10 psi above idle |
| MIL nozzle | ≤ 15% |
| Max AB nozzle | 40–70% |

## Model cycle calibration (derived values, not published)
- Airflow ∝ n⁴, fan PR = 1 + 2.3·n^4.5, OPR = 1 + 29.7·n⁵, where n = N2/N2_MIL
- Fan efficiency 0.86, HPC efficiency 0.85, combustor efficiency 0.99, LHV 43 MJ/kg
- Rotor inlet T41 includes about 20% cooling-air dilution. This makes MIL FTIT (T4.5) come out near 935 °C.
- Mixed-flow augmentor. Max AB T7 is about 2,050 K.
- A8 is computed from the choked-flow requirement. NOZ POS maps area 0.22 m² → 0% and 0.62 m² → 100%. This gives about 10% at MIL and about 60% at max AB.
- Thrust is calibrated to 17,155 lbf at MIL and 29,500 lbf at max AB.
- AB is modeled as 5 staged spray-ring zones (representative).

## Sources
- https://en.wikipedia.org/wiki/General_Electric_F110
- https://www.geaerospace.com/sites/default/files/datasheet-F110-GE-129.pdf
- https://brainscape.com/flashcards/ge-129-ops-limits-8717355/packs/12457764 (user flashcards)
- https://forum.falcon-bms.com/post/246233
