# Finite elements

[Module index](../MODULES.md) · [Bibliography](BIBLIOGRAPHY.md)

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

E is Young modulus in kPa, ν Poisson ratio, Ae triangle area, Be the constant strain-displacement matrix and t=1 m out of plane. Each element uses its material's D matrix. A flexible downward pressure strip loads the surface. The base restrains both displacements and side boundaries restrain horizontal movement. Outputs are displacements, reactions and element stresses with tension-positive stress signs. Refine the mesh and enlarge the finite domain independently. The drawing magnification does not alter the solution.

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
| Calculation engine |

**Layers table:** Top depth (m); Bottom depth (m); Layer Young modulus E (kPa);
Layer Poisson ratio.

### Outputs and application

Results include maximum downward displacement (mm), applied downward force (kN/m), vertical support reaction (kN/m), strain energy (kN m/m), nodal movements and unsmoothed element stresses.

For homogeneous ground, leave **Layers** empty and enter E and Poisson ratio
in Parameters. For stratified ground, enter contiguous layers from surface to
domain bottom with top/bottom depths, E and Poisson ratio. The complete layer
profile overrides the homogeneous values, which may then be blank. Materials
are perfectly bonded: no interface slip or separation is represented. Layer
boundaries are inserted into the mesh, preventing elements from mixing
materials; those additional node rows count towards the selected engine's limit.

**Calculation engine:** BoreholeDesk CST is the default and supports up to
225 nodes, with horizontal/vertical cell counts from 2 to 20. CalculiX 2.23
uses local sparse CPE3 analysis and supports up to 2601 nodes, with cell counts
from 2 to 50. Both engines solve the same linear elastic problem. Selecting
CalculiX does not activate plastic soil behaviour, excavation stages, groundwater
or strength reduction. The installer obtains the pinned solver directly from
its author's distribution and checks both the archive and executable hashes.
Once installed, calculations run offline. Missing or modified solver files
produce an error; the program does not silently substitute another engine.

**Application conditions:** Homogeneous or horizontally layered linear plane strain, rectangular finite domain; E,width,depth>0; 0<=nu<=0.45; q>=0; 0<=left<right<=width. Engine-specific mesh limits include inserted material boundaries. Fixed bottom, horizontal rollers on sides. No soil failure, pore water or stages.

**References:** [fem](BIBLIOGRAPHY.md#fem); [CalculiX CPE3 engine](BIBLIOGRAPHY.md#calculix).
