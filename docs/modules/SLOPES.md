# Slope stability

[Module index](../../MODULES.md) · [Bibliography](BIBLIOGRAPHY.md#slopes)

Open **Computation > Slope stability**. Enter the ground profile in increasing X,
with elevations Y and a lower model boundary. Set the material strength basis,
moist/saturated unit weights, layers and groundwater. Choose a prescribed circle
or the bounded circular search, select the method and calculate. Inspect the
surface, slice schedule, convergence messages and parameter basis before saving
the case or exporting its report.

## Strength and water conventions

```math
s_i=c'_i+\left(\frac{N_i}{\ell_i}-u_i\right)\tan\phi'_i
```

si is available shear strength on a slice base, Ni total base-normal force, ℓi
base length, and ui pore pressure. In effective-stress mode the entered strength
parameters are c′ and φ′. Dry total-stress mode uses su and φu=0.

```math
u_i=\gamma_w\max(0,Y_w-Y_{base,i})
```

The shared piezometric line establishes base pressure and the moist/saturated
weight partition. Groundwater is a hydrostatic modelling assumption, not a
seepage solution. Layers are defined by reviewed non-crossing top-contact
polylines; contacts may outcrop. The slice schedule records the actual base
material and water pressure.

## Methods

<a id="oms"></a>
### Ordinary / Fellenius

The ordinary method uses moment equilibrium and neglects interslice forces.
For an unreinforced circular surface the familiar form is:

```math
F=\frac{\sum_i\left[c'_i\ell_i+(W_i\cos\alpha_i-u_i\ell_i)\tan\phi'_i\right]}{\sum_i W_i\sin\alpha_i}
```

Wi is slice weight and αi base inclination. Treat the result as this method's
equilibrium idealization, not as an automatic conservative bound.

<a id="bishop"></a>
### Bishop simplified

The simplified method satisfies overall moment and vertical slice-force
equilibrium with interslice shear neglected. For the standard unreinforced
circular case:

```math
F=\frac{1}{\sum_i W_i\sin\alpha_i}
\sum_i\frac{c'_i b_i+(W_i-u_i b_i)\tan\phi'_i}
{\cos\alpha_i+\sin\alpha_i\tan\phi'_i/F}
```

bi is horizontal slice width. F occurs on both sides and is solved iteratively.
Inspect the slice and convergence messages as well as the reported F.

<a id="janbu"></a>
### Janbu simplified

The application reports the **uncorrected simplified force-equilibrium result**.
The empirical Janbu correction factor f0 is not applied. Interslice shear is
neglected. Identify this variant when comparing a result with a reference that
reports corrected Janbu. A corrected result and an uncorrected result are not
the same method variant.

<a id="spencer"></a>
### Spencer

Overall force and moment equilibrium are satisfied with a constant inclination
of the interslice resultant. The solver determines both factor of safety and
the inclination parameter. Review warnings, including any interslice tension,
and compare slice refinement on the same geometry and strength basis.

<a id="mprice"></a>
### Morgenstern–Price

Force and moment equilibrium use the prescribed **half-sine** interslice-force
function:

```math
X(x)=\lambda f(x)E(x),\qquad f(\xi)=\sin(\pi\xi),\quad 0\leq\xi\leq1
```

X and E are the interslice shear and normal components, ξ normalized horizontal
position between the surface endpoints, and λ a solved scale parameter. The function is part of the
method definition and must match when comparing implementations.

## Circular search

Enter the centre-coordinate and radius bounds and their sampling counts.
The application evaluates this deterministic grid and retains the candidate
ledger, method-specific minima, warnings and failed candidates. Its reported
minimum is the lowest converged value sampled in that grid. Expand the bounds
and refine circle sampling and slice resolution to assess the selected surface,
particularly if a minimum lies on a search boundary.

## Active tiebacks

Enter head coordinates, downward angle, free length, bonded length, spacing,
working load, allowable tendon and connection loads, bond diameter, allowable
ground-bond shear and required setback. The capacity comparison is:

```math
T_{allow}=\min\left(T_{tendon},T_{connection},\pi D_bL_b\tau_{allow}\right),
\qquad T_{working}\leq T_{allow},\qquad T_{2D}=T_{working}/s
```

Db and Lb are bond diameter/length, τallow adopted allowable bond shear, and s
out-of-plane spacing. For each evaluated surface, contribution requires the
active tieback to cross the surface and its bonded zone to remain outside the
moving mass at the stated setback. Geometry and force-per-metre conversions are
recorded in the surface audit. The working load is an adopted load after the
project's losses/acceptance decisions, not a calculated prestress history.

## Outputs, interpretation and references

Results include the evaluated circle, materials and water, method-specific
factor of safety, slice forces and warnings, plus the search or anchor ledger
when selected. A numerical minimum or converged factor of safety requires
interpretation against the chosen design scenario and acceptance criteria.

The application exposes circular surfaces, the stated groundwater convention
and active-load idealization. Enter justified strength parameters and preserve
the scenario and geometry provenance. Geological sections supply geometry,
not automatically assigned design strengths.

The numerical engine distributed with this version is **XSLOPE 1.0.5**, by
Norman L. Jones, under Apache-2.0. The adapter's exposed method variants are
documented above; upstream software may expose a wider range of analyses.
See [method bibliography](BIBLIOGRAPHY.md#slopes),
[anchor bibliography](BIBLIOGRAPHY.md#anchors) and
[third-party notices](../../THIRD_PARTY_NOTICES.md).
