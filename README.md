# Hypersonic Shock Wave / Boundary Layer Interaction — SU2 CFD

RANS simulation of two-dimensional hypersonic shock wave and boundary layer interaction (SWBLI) using the SU2 open-source multiphysics CFD solver.

---

## Case Description

| Parameter | Value |
|-----------|-------|
| Solver | RANS + Spalart-Allmaras (SA) |
| Mach number | 5.0 |
| Reynolds number | 37,000,000 |
| Freestream pressure | 4006.8 Pa |
| Freestream temperature | 68.306 K |
| Freestream velocity | 829.20 m/s |
| Angle of attack | 0° |

---

## Numerical Setup

| Setting | Value |
|---------|-------|
| Spatial discretisation | ROE scheme + MUSCL reconstruction |
| Slope limiter | Venkatakrishnan (coeff = 0.1) |
| Gradient method | Green-Gauss |
| Time integration | Euler Implicit |
| Multigrid | 3-level V-cycle |
| Linear solver | FGMRES + ILU preconditioner |
| Convergence acceleration | Newton-Krylov |
| CFL | Adaptive (max 100) |
| Convergence target | Residual < 10⁻¹⁵ |
| Max iterations | 10,000 |

---

## Boundary Conditions

| Boundary | Type | Value |
|----------|------|-------|
| Inlet | Supersonic inlet | T=68.306 K, P=4006.8 Pa, V=829.20 m/s |
| Outlet | Pressure outlet | 4006.8 Pa |
| Wall (top/bottom) | Adiabatic no-slip | Zero heat flux |
| Symmetry | Symmetry plane | — |

---

## Fluid Model

- Standard Air (ideal gas), γ = 1.4, R = 287.058 J/kg·K
- Viscosity: Sutherland's law (μ_ref = 1.716×10⁻⁵, T_ref = 273.15 K)
- Conductivity: Constant Prandtl (Pr_lam = 0.72, Pr_turb = 0.90)

---

## Files

```
mach5_swbli_rans_sa.cfg    — SU2 configuration file
```

> Mesh file not included. Generated separately using Pointwise mesh generation software.

---

## How to Run

```bash
SU2_CFD mach5_swbli_rans_sa.cfg
```

Post-process volume output (`flow.vtu`) using ParaView.
Convergence history available in `history.csv`.

---

## Requirements

- SU2 v7.3.0 "Blackbird" or later
- ParaView (post-processing)
- Pointwise (mesh generation, if regenerating mesh)

---

## Author

**Agadheesh Sivakumar**
github.com/agad-flosim
