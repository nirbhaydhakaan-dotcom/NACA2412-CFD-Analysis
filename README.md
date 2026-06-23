# NACA 2412 Airfoil — CFD Analysis Across Angle of Attack

2D steady-state CFD study of the NACA 2412 airfoil at Re = 3.1×10⁶, using ANSYS Fluent (SST k-ω) 
across angles of attack from -8° to 20°. Includes a full mesh independence study (GCI method) 
and validation against NACA TR-824 experimental data.

## Key Results

| Parameter | Value | AoA |
|---|---|---|
| Maximum Cl | 1.6428 | 17° (stall) |
| Maximum Cl/Cd | 73.28 | 8° (optimal efficiency) |
| Minimum Cd | 0.009193 | -2° |

**Validation against NACA TR-824 (at α = 14°, Re = 3.1×10⁶):**

| Coefficient | CFD (extrapolated) | Experimental | Deviation |
|---|---|---|---|
| Cl | 1.5457 | 1.52 | 1.69% |
| Cd | 0.02614 | 0.0233 | 12.2% |

![Cl vs AoA](plots/Cl%20vs%20AoA.png)
![Cd vs AoA](plots/Cd%20vs%20AoA.png)
![Lift-to-Drag Ratio vs AoA](plots/Lift-to-Drag%20Ratio%20vs%20AoA.png)
![Velocity contour at 17°](plots/17%20deg%20velocity%20contour%20fixed.png)

## What's in this repo

- `report/` — full technical report (PDF), including methodology, mesh independence study (GCI/Richardson extrapolation), validation, and results
- `data/` — raw Cl/Cd data for all simulated angles of attack
- `plots/` — key result figures
- `mesh/` — mesh independence study figures

## Methodology Summary

- **Solver:** ANSYS Fluent 2026 R1 (Student), pressure-based, steady-state, Coupled scheme
- **Turbulence model:** SST k-ω, wall y⁺ < 1.24 across all cases
- **Mesh:** Structured C-type, 400,020 cells (fine), GCI < 1% for both Cl and Cd
- **Validation:** NACA TR-824 (Abbott & Von Doenhoff, 1945) at Re = 3.1×10⁶

Full details, including domain setup, boundary conditions, and discussion of results, are in the [full report](report/Aerodynamic%20Analysis%20of%20the%20NACA%202412%20Airfoil%20at%20Varying%20Angles%20of%20Attack.pdf).

## Limitations

Fully turbulent RANS (no laminar-turbulent transition modelling) leads to Cd overprediction, 
consistent with known SST k-ω behaviour at this Reynolds number. Post-stall angles (≥18°) show 
oscillatory convergence due to unsteady separated flow; values reported are iteration-averaged.
