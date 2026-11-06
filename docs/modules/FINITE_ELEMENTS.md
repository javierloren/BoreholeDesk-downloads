# Finite elements

[Module index](../../MODULES.md) · [Bibliography](BIBLIOGRAPHY.md)

Open **Computation > Calculation worksheet**, choose the named method, enter the parameters and tables, then calculate. Review the schedule and method conditions, save the case to the project and export its calculation report. The following equations describe the implemented variant; symbols are local to each method.

- [Incremental linear plane-strain elasticity with constant-strain triangles](#fem_elastic)

<a id="fem_elastic"></a>

## Incremental linear plane-strain elasticity with constant-strain triangles

**Worksheet:** FEM - elastic plane-strain ground block (incremental).

### Formulation

```math
\begin{gathered}
K_e=tA_eB_e^TD B_e,\qquad K_{ff}u_f=F_f,\qquad\sigma_e=D B_eu_e\\
D=\frac{E}{(1+\nu)(1-2\nu)}\begin{bmatrix}1-\nu&\nu&0\\\nu&1-\nu&0\\0&0&(1-2\nu)/2\end{bmatrix}
\end{gathered}
```

E is Young modulus in kPa, ν Poisson ratio, Ae triangle area, Be the constant strain-displacement matrix and t=1 m out of plane. A flexible downward pressure strip loads the surface. The base restrains both displacements and side boundaries restrain horizontal movement. Outputs are displacements, reactions and element stresses with tension-positive stress signs. Refine the mesh and enlarge the finite domain independently. The drawing magnification does not alter the solution.

### Inputs and units

| Input |
| --- |
| Domain width (m) |
| Domain depth (m) |
| Young modulus E (kPa) |
| Poisson ratio |
| Horizontal cells (integer) |
| Vertical cells (integer) |
| Loaded strip left X (m) |
| Loaded strip right X (m) |
| Net downward pressure increment (kPa) |
| Drawing displacement magnification |

### Outputs and application

Results include Maximum downward displacement (mm); Applied downward force (kN/m); Vertical reaction sum (kN/m); Force X residual (kN/m); Force Y residual (kN/m); Moment residual (kN m/m); Strain energy (kN m/m); Scaled stiffness condition number.

**Application conditions:** Homogeneous linear plane strain, rectangular finite domain; E,width,depth>0; 0<=nu<=0.45; q>=0; 0<=left<right<=width; nx,ny integers 2..20, <=225 nodes. Fixed bottom, horizontal rollers on sides. No soil failure, pore water or stages.

**References:** [fem](BIBLIOGRAPHY.md#fem).
